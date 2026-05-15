<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>二手出售平台</title>
    <style>
        :root {
            --bg: #f5f5f5;
            --card-bg: #ffffff;
            --text: #1e293b;
            --text-light: #64748b;
            --border: #e2e8f0;
            --primary: #2563eb;
            --primary-hover: #1d4ed8;
            --danger: #ef4444;
            --radius: 10px;
            --shadow: 0 1px 3px rgba(0, 0, 0, 0.06);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
            background: var(--bg);
            color: var(--text);
            min-height: 100vh;
            padding: 32px 16px;
        }

        .app {
            max-width: 1000px;
            margin: 0 auto;
        }

        .app-title {
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 4px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .app-subtitle {
            color: var(--text-light);
            font-size: 0.9rem;
            margin-bottom: 24px;
        }

        .form-card {
            background: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 20px 24px;
            box-shadow: var(--shadow);
            margin-bottom: 24px;
        }
        .form-title {
            font-size: 1rem;
            font-weight: 600;
            margin-bottom: 16px;
        }
        .form-row {
            display: flex;
            flex-wrap: wrap;
            gap: 16px;
            margin-bottom: 16px;
        }
        .form-group {
            display: flex;
            flex-direction: column;
            gap: 5px;
            flex: 1 1 200px;
            min-width: 180px;
        }
        .form-group label {
            font-size: 13px;
            font-weight: 600;
            color: var(--text-light);
            text-transform: uppercase;
            letter-spacing: 0.4px;
        }
        .form-group label .required {
            color: var(--danger);
            font-weight: 700;
        }
        .form-group input,
        .form-group select {
            padding: 10px 14px;
            border: 1px solid var(--border);
            border-radius: 8px;
            font-size: 15px;
            outline: none;
            font-family: inherit;
            background: #fff;
            transition: border 0.2s, box-shadow 0.2s;
        }
        .form-group input:focus,
        .form-group select:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.08);
        }
        .btn-submit {
            background: var(--primary);
            color: #fff;
            border: none;
            padding: 11px 28px;
            border-radius: 8px;
            font-size: 15px;
            font-weight: 600;
            cursor: pointer;
            transition: background 0.2s;
            letter-spacing: 0.3px;
        }
        .btn-submit:hover {
            background: var(--primary-hover);
        }

        .toolbar {
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: space-between;
            gap: 12px;
            margin-bottom: 16px;
        }
        .filter-bar {
            display: flex;
            gap: 6px;
        }
        .filter-btn {
            padding: 7px 18px;
            border: 2px solid var(--border);
            border-radius: 20px;
            background: #fff;
            cursor: pointer;
            font-size: 13px;
            font-weight: 500;
            transition: all 0.2s;
        }
        .filter-btn.active-filter {
            background: var(--text);
            color: #fff;
            border-color: var(--text);
        }
        .record-count {
            color: var(--text-light);
            font-size: 14px;
        }

        .table-wrapper {
            background: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            overflow-x: auto;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 14px;
        }
        thead th {
            background: #f8fafc;
            padding: 12px 16px;
            text-align: left;
            font-weight: 600;
            font-size: 12px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            color: var(--text-light);
            border-bottom: 2px solid var(--border);
            white-space: nowrap;
        }
        tbody td {
            padding: 12px 16px;
            border-bottom: 1px solid var(--border);
            vertical-align: middle;
        }
        tbody tr.done-row {
            background: #f9fafb;
            opacity: 0.55;
        }
        tbody tr.done-row td {
            text-decoration: line-through;
            color: #94a3b8;
        }
        .badge {
            display: inline-block;
            font-size: 11px;
            font-weight: 700;
            padding: 4px 10px;
            border-radius: 14px;
            white-space: nowrap;
            letter-spacing: 0.4px;
        }
        .badge-active {
            background: #dbeafe;
            color: #1e40af;
        }
        .badge-done {
            background: #d1fae5;
            color: #065f46;
        }
        .btn-toggle {
            padding: 5px 14px;
            border-radius: 6px;
            font-size: 12px;
            font-weight: 600;
            cursor: pointer;
            border: 1px solid var(--border);
            background: #fff;
            transition: all 0.2s;
            white-space: nowrap;
        }
        .btn-toggle:hover {
            background: #f1f5f9;
        }
        .empty-state {
            text-align: center;
            padding: 48px;
            color: var(--text-light);
            font-size: 0.95rem;
        }

        @media (max-width: 600px) {
            .form-row {
                flex-direction: column;
            }
            .toolbar {
                flex-direction: column;
                align-items: flex-start;
            }
        }
    </style>
</head>
<body>
    <div class="app">
        <h1 class="app-title">🛒 二手出售平台</h1>
        <p class="app-subtitle">管理你的二手物品，每筆資料為一則「二手物品」</p>

        <div class="form-card">
            <div class="form-title">📝 新增二手物品</div>
            <div class="form-row">
                <div class="form-group">
                    <label for="inputContent">出售內容 <span class="required">*必填</span></label>
                    <input type="text" id="inputContent" placeholder="例如：九成新書桌">
                </div>
                <div class="form-group">
                    <label for="inputPrice">出售價錢 <span class="required">*必填</span></label>
                    <input type="text" id="inputPrice" placeholder="例如：NT$500">
                </div>
                <div class="form-group">
                    <label for="inputCategory">分類 <span class="required">*必填</span></label>
                    <select id="inputCategory">
                        <option value="生活">生活</option>
                        <option value="娱乐">娱乐</option>
                        <option value="其他">其他</option>
                    </select>
                </div>
            </div>
            <button class="btn-submit" id="btnAdd">➕ 新增二手物品</button>
        </div>

        <div class="toolbar">
            <div class="filter-bar" id="filterBar">
                <button class="filter-btn active-filter" data-filter="all">全部</button>
                <button class="filter-btn" data-filter="active">出售中</button>
                <button class="filter-btn" data-filter="done">已完成</button>
            </div>
            <span class="record-count" id="recordCount">共 0 筆</span>
        </div>

        <div id="recordsContainer"></div>
    </div>

    <script>
        (function() {
            const STORAGE_KEY = 'records';

            const inputContent = document.getElementById('inputContent');
            const inputPrice = document.getElementById('inputPrice');
            const inputCategory = document.getElementById('inputCategory');
            const btnAdd = document.getElementById('btnAdd');
            const filterBar = document.getElementById('filterBar');
            const recordCount = document.getElementById('recordCount');
            const recordsContainer = document.getElementById('recordsContainer');

            let currentFilter = 'all';

            function createRecord(formData) {
                return {
                    id: crypto.randomUUID ? crypto.randomUUID() : 'id_' + Date.now() + '_' + Math.random().toString(36).slice(2, 8),
                    createdAt: new Date().toISOString(),
                    status: 'active',
                    content: formData.content.trim(),
                    price: formData.price.trim(),
                    category: formData.category
                };
            }

            function saveData(record) {
                const records = loadData();
                records.push(record);
                localStorage.setItem(STORAGE_KEY, JSON.stringify(records));
            }

            function loadData() {
                try {
                    const raw = localStorage.getItem(STORAGE_KEY);
                    if (!raw) return [];
                    const parsed = JSON.parse(raw);
                    return Array.isArray(parsed) ? parsed : [];
                } catch (e) {
                    return [];
                }
            }

            function updateRecord(id, changes) {
                const records = loadData();
                const idx = records.findIndex(r => r.id === id);
                if (idx === -1) return;
                records[idx] = { ...records[idx], ...changes };
                localStorage.setItem(STORAGE_KEY, JSON.stringify(records));
            }

            function renderList(recordsToShow) {
                recordCount.textContent = `共 ${recordsToShow.length} 筆`;

                if (recordsToShow.length === 0) {
                    recordsContainer.innerHTML = '<div class="empty-state">尚無二手物品，快來新增第一筆吧！</div>';
                    return;
                }

                let html = `
                <div class="table-wrapper">
                    <table>
                        <thead>
                            <tr>
                                <th>出售內容</th>
                                <th>價錢</th>
                                <th>分類</th>
                                <th>狀態</th>
                                <th>建立時間</th>
                                <th>操作</th>
                            </tr>
                        </thead>
                        <tbody>`;

                recordsToShow.forEach(r => {
                    const isDone = r.status === 'done';
                    const statusLabel = isDone ? '已完成' : '出售中';
                    const badgeClass = isDone ? 'badge-done' : 'badge-active';
                    const rowClass = isDone ? 'done-row' : '';
                    const timeStr = new Date(r.createdAt).toLocaleString('zh-TW', {
                        year: 'numeric', month: '2-digit', day: '2-digit',
                        hour: '2-digit', minute: '2-digit'
                    });

                    html += `
                        <tr class="${rowClass}">
                            <td><strong>${escapeHtml(r.content)}</strong></td>
                            <td>${escapeHtml(r.price)}</td>
                            <td>${escapeHtml(r.category)}</td>
                            <td><span class="badge ${badgeClass}">${statusLabel}</span></td>
                            <td>${escapeHtml(timeStr)}</td>
                            <td>
                                <button class="btn-toggle" data-id="${escapeHtml(r.id)}">
                                    ${isDone ? '↩ 設為出售中' : '✅ 標記已完成'}
                                </button>
                            </td>
                        </tr>`;
                });

                html += '</tbody></table></div>';
                recordsContainer.innerHTML = html;

                recordsContainer.querySelectorAll('.btn-toggle').forEach(btn => {
                    btn.addEventListener('click', function() {
                        const id = this.dataset.id;
                        const record = loadData().find(r => r.id === id);
                        if (!record) return;
                        const newStatus = record.status === 'active' ? 'done' : 'active';
                        updateRecord(id, { status: newStatus });
                        refreshUI();
                    });
                });
            }

            function escapeHtml(str) {
                const div = document.createElement('div');
                div.textContent = str;
                return div.innerHTML;
            }

            function getFilteredRecords() {
                const all = loadData();
                if (currentFilter === 'all') return all;
                return all.filter(r => r.status === currentFilter);
            }

            function refreshUI() {
                renderList(getFilteredRecords());
            }

            function handleAdd() {
                const content = inputContent.value;
                const price = inputPrice.value;

                if (!content.trim()) {
                    alert('請填寫「出售內容」！');
                    inputContent.focus();
                    return;
                }
                if (!price.trim()) {
                    alert('請填寫「出售價錢」！');
                    inputPrice.focus();
                    return;
                }

                const record = createRecord({
                    content: content,
                    price: price,
                    category: inputCategory.value
                });

                saveData(record);

                inputContent.value = '';
                inputPrice.value = '';
                inputCategory.value = '生活';
                inputContent.focus();

                refreshUI();
            }

            btnAdd.addEventListener('click', handleAdd);

            [inputContent, inputPrice].forEach(el => {
                el.addEventListener('keydown', function(e) {
                    if (e.key === 'Enter') {
                        e.preventDefault();
                        handleAdd();
                    }
                });
            });

            filterBar.addEventListener('click', function(e) {
                if (e.target.classList.contains('filter-btn')) {
                    filterBar.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active-filter'));
                    e.target.classList.add('active-filter');
                    currentFilter = e.target.dataset.filter;
                    refreshUI();
                }
            });

            refreshUI();
        })();
    </script>
</body>
</html>
