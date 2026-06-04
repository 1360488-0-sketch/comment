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
            --success: #10b981;
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

        .stats-bar {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
            margin-bottom: 16px;
        }
        .stat-card {
            background: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 12px 20px;
            text-align: center;
            min-width: 80px;
            box-shadow: var(--shadow);
        }
        .stat-card .stat-num {
            font-size: 1.5rem;
            font-weight: 700;
        }
        .stat-card .stat-label {
            font-size: 0.75rem;
            color: var(--text-light);
        }
        .stat-total .stat-num { color: var(--text); }
        .stat-active .stat-num { color: var(--primary); }
        .stat-done .stat-num { color: var(--success); }

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
        .sort-bar {
            display: flex;
            gap: 6px;
        }
        .sort-btn {
            padding: 7px 18px;
            border: 2px solid var(--border);
            border-radius: 20px;
            background: #fff;
            cursor: pointer;
            font-size: 13px;
            font-weight: 500;
            transition: all 0.2s;
        }
        .sort-btn.active-sort {
            background: var(--primary);
            color: #fff;
            border-color: var(--primary);
        }
        .search-box input {
            padding: 7px 14px;
            border: 2px solid var(--border);
            border-radius: 20px;
            font-size: 13px;
            outline: none;
            width: 180px;
            transition: border 0.2s;
        }
        .search-box input:focus {
            border-color: var(--primary);
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
            .search-box input {
                width: 100%;
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
                    <input type="text" id="inputContent" placeholder="例如：九成新書桌" maxlength="50">
                </div>
                <div class="form-group">
                    <label for="inputPrice">出售價錢 <span class="required">*必填</span></label>
                    <input type="text" id="inputPrice" placeholder="例如：NT$500" maxlength="30">
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

        <div class="stats-bar" id="statsBar">
            <div class="stat-card stat-total"><div class="stat-num" id="statTotal">0</div><div class="stat-label">全部</div></div>
            <div class="stat-card stat-active"><div class="stat-num" id="statActive">0</div><div class="stat-label">出售中</div></div>
            <div class="stat-card stat-done"><div class="stat-num" id="statDone">0</div><div class="stat-label">已完成</div></div>
        </div>

        <div class="toolbar">
            <div class="filter-bar" id="filterBar">
                <button class="filter-btn active-filter" data-filter="all">全部</button>
                <button class="filter-btn" data-filter="active">出售中</button>
                <button class="filter-btn" data-filter="done">已完成</button>
            </div>
            <div class="sort-bar" id="sortBar">
                <button class="sort-btn active-sort" data-sort="newest">最新</button>
                <button class="sort-btn" data-sort="oldest">最舊</button>
            </div>
            <div class="search-box">
                <input type="text" id="searchInput" placeholder="🔍 搜尋內容...">
            </div>
            <span class="record-count" id="recordCount">共 0 筆</span>
        </div>

        <div id="recordsContainer"></div>
    </div>

    <script>
        (function() {
            // ========== CONFIG ==========
            const APPS_SCRIPT_URL = "PASTE_YOUR_APPS_SCRIPT_URL_HERE";
            const STORAGE_KEY = 'records';

            // ========== DOM ==========
            const inputContent = document.getElementById('inputContent');
            const inputPrice = document.getElementById('inputPrice');
            const inputCategory = document.getElementById('inputCategory');
            const btnAdd = document.getElementById('btnAdd');
            const filterBar = document.getElementById('filterBar');
            const sortBar = document.getElementById('sortBar');
            const searchInput = document.getElementById('searchInput');
            const recordCount = document.getElementById('recordCount');
            const recordsContainer = document.getElementById('recordsContainer');
            const statTotal = document.getElementById('statTotal');
            const statActive = document.getElementById('statActive');
            const statDone = document.getElementById('statDone');

            let currentFilter = 'all';
            let currentSort = 'newest';
            let searchKeyword = '';

            // ========== CORE: createRecord (unchanged) ==========
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

            // ========== Backend Connectors ==========

            async function syncToSheet(payload) {
                try {
                    const res = await fetch(APPS_SCRIPT_URL, {
                        method: "POST",
                        headers: { "Content-Type": "text/plain" },
                        body: JSON.stringify(payload)
                    });
                    const data = await res.json();
                    if (!data.ok) console.warn("syncToSheet error:", data.error);
                    return data;
                } catch (err) {
                    console.warn("syncToSheet network error:", err.message);
                    return { ok: false, error: err.message };
                }
            }

            async function fetchRecordsFromSheet() {
                const res = await fetch(APPS_SCRIPT_URL);
                const data = await res.json();
                if (!data.ok || !Array.isArray(data.records)) {
                    throw new Error(data.error || "Invalid response from Sheet");
                }
                const normalized = data.records.map(normalizeRecord);
                return normalized;
            }

            function normalizeRecord(record) {
                const lookup = {};
                Object.keys(record).forEach(function(key) {
                    lookup[key.toLowerCase().trim()] = record[key];
                });

                const result = {
                    id:        getCaseInsensitive(lookup, 'id'),
                    createdAt: getCaseInsensitive(lookup, 'createdat'),
                    status:    getCaseInsensitive(lookup, 'status'),
                    content:   getCaseInsensitive(lookup, 'content'),
                    price:     getCaseInsensitive(lookup, 'price'),
                    category:  getCaseInsensitive(lookup, 'category')
                };

                if (result.status !== 'active' && result.status !== 'done') {
                    result.status = 'active';
                }

                return result;
            }

            function getCaseInsensitive(lookup, lowerKey) {
                if (lookup[lowerKey] !== undefined) return lookup[lowerKey];
                const keys = Object.keys(lookup);
                for (let i = 0; i < keys.length; i++) {
                    if (keys[i].toLowerCase().trim() === lowerKey) {
                        return lookup[keys[i]];
                    }
                }
                return '';
            }

            // ========== localStorage helpers ==========

            function loadLocalData() {
                try {
                    const raw = localStorage.getItem(STORAGE_KEY);
                    if (!raw) return [];
                    const parsed = JSON.parse(raw);
                    return Array.isArray(parsed) ? parsed : [];
                } catch (e) {
                    return [];
                }
            }

            async function loadData() {
                try {
                    const remoteRecords = await fetchRecordsFromSheet();
                    localStorage.setItem(STORAGE_KEY, JSON.stringify(remoteRecords));
                    return remoteRecords;
                } catch (err) {
                    console.warn("Remote load failed, falling back to localStorage:", err.message);
                    return loadLocalData();
                }
            }

            async function saveData(record) {
                const result = await syncToSheet({ action: "create", record: record });
                const records = loadLocalData();
                records.push(record);
                localStorage.setItem(STORAGE_KEY, JSON.stringify(records));
                return result;
            }

            async function updateRecord(id, changes) {
                const result = await syncToSheet({ action: "update", id: id, changes: changes });
                const records = loadLocalData();
                const idx = records.findIndex(r => r.id === id);
                if (idx !== -1) {
                    records[idx] = { ...records[idx], ...changes };
                    localStorage.setItem(STORAGE_KEY, JSON.stringify(records));
                }
                return result;
            }

            // ========== NEW: Sort ==========
            function sortRecords(records) {
                const sorted = [...records];
                if (currentSort === 'newest') {
                    sorted.sort((a, b) => new Date(b.createdAt) - new Date(a.createdAt));
                } else if (currentSort === 'oldest') {
                    sorted.sort((a, b) => new Date(a.createdAt) - new Date(b.createdAt));
                }
                return sorted;
            }

            // ========== Stats ==========
            function updateStats(records) {
                const total = records.length;
                const active = records.filter(r => r.status === 'active').length;
                const done = records.filter(r => r.status === 'done').length;
                statTotal.textContent = total;
                statActive.textContent = active;
                statDone.textContent = done;
            }

            // ========== Search ==========
            function applySearch(records) {
                if (!searchKeyword.trim()) return records;
                const kw = searchKeyword.trim().toLowerCase();
                return records.filter(r =>
                    r.content.toLowerCase().includes(kw) ||
                    r.price.toLowerCase().includes(kw) ||
                    r.category.toLowerCase().includes(kw)
                );
            }

            // ========== RENDER ==========
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
                    let timeStr = '';
                    try {
                        timeStr = new Date(r.createdAt).toLocaleString('zh-TW', {
                            year: 'numeric', month: '2-digit', day: '2-digit',
                            hour: '2-digit', minute: '2-digit'
                        });
                    } catch (e) {
                        timeStr = r.createdAt || '';
                    }

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
                    btn.addEventListener('click', async function() {
                        const id = this.dataset.id;
                        const allRecords = await loadData();
                        const record = allRecords.find(r => r.id === id);
                        if (!record) return;
                        const newStatus = record.status === 'active' ? 'done' : 'active';
                        await updateRecord(id, { status: newStatus });
                        await refreshUI();
                    });
                });
            }

            function escapeHtml(str) {
                const div = document.createElement('div');
                div.textContent = str;
                return div.innerHTML;
            }

            function getFilteredRecords(allRecords) {
                let filtered = allRecords;
                if (currentFilter !== 'all') {
                    filtered = filtered.filter(r => r.status === currentFilter);
                }
                filtered = applySearch(filtered);
                filtered = sortRecords(filtered);
                return filtered;
            }

            async function refreshUI() {
                const allRecords = await loadData();
                const filtered = getFilteredRecords(allRecords);
                updateStats(allRecords);
                renderList(filtered);
            }

            async function handleAdd() {
                const content = inputContent.value;
                const price = inputPrice.value;

                if (!content.trim()) {
                    alert('請填寫「出售內容」！');
                    inputContent.focus();
                    return;
                }
                if (content.trim().length > 50) {
                    alert('出售內容不可超過 50 字！');
                    inputContent.focus();
                    return;
                }
                if (!price.trim()) {
                    alert('請填寫「出售價錢」！');
                    inputPrice.focus();
                    return;
                }
                if (price.trim().length > 30) {
                    alert('出售價錢不可超過 30 字！');
                    inputPrice.focus();
                    return;
                }

                const record = createRecord({
                    content: content,
                    price: price,
                    category: inputCategory.value
                });

                try {
                    await saveData(record);
                } catch (err) {
                    console.error("saveData failed:", err);
                    alert("儲存失敗：" + err.message);
                    return;
                }

                inputContent.value = '';
                inputPrice.value = '';
                inputCategory.value = '生活';
                inputContent.focus();

                await refreshUI();
            }

            // ========== EVENT BINDINGS ==========

            btnAdd.addEventListener('click', function(e) {
                e.preventDefault();
                handleAdd().catch(err => {
                    console.error("handleAdd error:", err);
                });
            });

            [inputContent, inputPrice].forEach(el => {
                el.addEventListener('keydown', function(e) {
                    if (e.key === 'Enter') {
                        e.preventDefault();
                        handleAdd().catch(err => {
                            console.error("handleAdd error:", err);
                        });
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

            sortBar.addEventListener('click', function(e) {
                if (e.target.classList.contains('sort-btn')) {
                    sortBar.querySelectorAll('.sort-btn').forEach(b => b.classList.remove('active-sort'));
                    e.target.classList.add('active-sort');
                    currentSort = e.target.dataset.sort;
                    refreshUI();
                }
            });

            searchInput.addEventListener('input', function() {
                searchKeyword = this.value;
                refreshUI();
            });

            // ========== INIT ==========
            refreshUI();
        })();
    </script>
</body>
</html>

            refreshUI();
        })();
    </script>
</body>
</html>
