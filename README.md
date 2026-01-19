<html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="theme-color" content="#667eea">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <title>📱 Contract Tracker</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 0;
            overflow-x: hidden;
        }

        .mobile-header {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 20px 15px 15px 15px;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 4px 20px rgba(0,0,0,0.15);
        }

        .mobile-header h1 {
            font-size: 20px;
            margin-bottom: 8px;
        }

        .mobile-header .stats {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 8px;
            margin-top: 12px;
        }

        .mini-stat {
            background: rgba(255,255,255,0.2);
            backdrop-filter: blur(10px);
            border-radius: 12px;
            padding: 10px 5px;
            text-align: center;
        }

        .mini-stat .num {
            font-size: 20px;
            font-weight: bold;
            margin-bottom: 2px;
        }

        .mini-stat .label {
            font-size: 9px;
            text-transform: uppercase;
            opacity: 0.9;
        }

        .tabs {
            display: flex;
            background: white;
            padding: 8px;
            gap: 6px;
            overflow-x: auto;
            -webkit-overflow-scrolling: touch;
        }

        .tab {
            flex: 1;
            min-width: 70px;
            padding: 10px;
            background: #f5f5f5;
            border: none;
            border-radius: 10px;
            font-size: 13px;
            font-weight: 600;
            color: #666;
            cursor: pointer;
            white-space: nowrap;
            transition: all 0.2s;
        }

        .tab.active {
            background: #667eea;
            color: white;
        }

        .contract-list {
            padding: 12px;
        }

        .contract-card {
            background: white;
            border-radius: 16px;
            padding: 16px;
            margin-bottom: 12px;
            box-shadow: 0 2px 12px rgba(0,0,0,0.08);
            border-left: 4px solid #667eea;
        }

        .contract-card.stale {
            border-left-color: #ffc107;
        }

        .contract-card.overdue {
            border-left-color: #dc3545;
        }

        .contract-title {
            font-size: 16px;
            font-weight: bold;
            color: #333;
            margin-bottom: 8px;
        }

        .contract-meta {
            font-size: 11px;
            color: #999;
            margin-bottom: 10px;
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }

        .status-badge {
            display: inline-block;
            padding: 4px 10px;
            border-radius: 12px;
            font-size: 11px;
            font-weight: 600;
            margin-bottom: 10px;
        }

        .status-pending { background: #fff3cd; color: #856404; }
        .status-in-progress { background: #cce5ff; color: #004085; }
        .status-completed { background: #d4edda; color: #155724; }
        .status-cancelled { background: #f8d7da; color: #721c24; }

        .contract-description {
            font-size: 13px;
            color: #666;
            line-height: 1.5;
            margin-bottom: 12px;
        }

        .progress-note {
            background: #f8f9fa;
            border-left: 3px solid #667eea;
            padding: 8px 10px;
            margin-bottom: 12px;
            border-radius: 4px;
            font-size: 12px;
        }

        .progress-note strong {
            color: #667eea;
            font-size: 11px;
        }

        .contract-actions {
            display: flex;
            gap: 8px;
        }

        .contract-actions button {
            flex: 1;
            padding: 10px;
            border: none;
            border-radius: 10px;
            font-size: 13px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s;
        }

        .btn-update {
            background: #667eea;
            color: white;
        }

        .btn-complete {
            background: #28a745;
            color: white;
        }

        .btn-delete {
            background: #dc3545;
            color: white;
            flex: 0.5;
        }

        .fab {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            border: none;
            border-radius: 50%;
            color: white;
            font-size: 28px;
            box-shadow: 0 8px 24px rgba(102, 126, 234, 0.4);
            cursor: pointer;
            z-index: 99;
            transition: all 0.3s;
        }

        .fab:active {
            transform: scale(0.95);
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.7);
            z-index: 1000;
            animation: fadeIn 0.2s;
        }

        .modal.show {
            display: flex;
            align-items: flex-end;
        }

        .modal-content {
            background: white;
            border-radius: 24px 24px 0 0;
            padding: 24px;
            width: 100%;
            max-height: 85vh;
            overflow-y: auto;
            animation: slideUp 0.3s;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes slideUp {
            from { transform: translateY(100%); }
            to { transform: translateY(0); }
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .modal-header h2 {
            color: #667eea;
            font-size: 20px;
        }

        .modal-close {
            background: #f0f0f0;
            border: none;
            width: 32px;
            height: 32px;
            border-radius: 50%;
            font-size: 20px;
            cursor: pointer;
        }

        .form-group {
            margin-bottom: 16px;
        }

        .form-group label {
            display: block;
            font-size: 13px;
            font-weight: 600;
            color: #333;
            margin-bottom: 8px;
        }

        .form-group input,
        .form-group select,
        .form-group textarea {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 12px;
            font-size: 15px;
            transition: all 0.2s;
        }

        .form-group input:focus,
        .form-group select:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: #667eea;
        }

        .form-group textarea {
            min-height: 100px;
            resize: vertical;
        }

        .btn-submit {
            width: 100%;
            padding: 16px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            border: none;
            border-radius: 12px;
            color: white;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            margin-top: 8px;
        }

        .empty-state {
            text-align: center;
            padding: 60px 20px;
            color: white;
        }

        .empty-state .icon {
            font-size: 60px;
            margin-bottom: 16px;
            opacity: 0.5;
        }

        .empty-state p {
            font-size: 16px;
            opacity: 0.9;
        }

        .toast {
            position: fixed;
            bottom: 90px;
            left: 50%;
            transform: translateX(-50%);
            background: #333;
            color: white;
            padding: 12px 24px;
            border-radius: 24px;
            font-size: 14px;
            display: none;
            z-index: 999;
            animation: fadeIn 0.3s;
        }

        .toast.show {
            display: block;
        }

        .action-menu {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: white;
            border-radius: 24px 24px 0 0;
            padding: 20px;
            display: none;
            z-index: 998;
            box-shadow: 0 -4px 24px rgba(0,0,0,0.1);
        }

        .action-menu.show {
            display: block;
            animation: slideUp 0.3s;
        }

        .action-menu button {
            width: 100%;
            padding: 16px;
            border: none;
            background: #f5f5f5;
            border-radius: 12px;
            margin-bottom: 8px;
            font-size: 15px;
            font-weight: 600;
            cursor: pointer;
            text-align: left;
        }

        .action-menu button:active {
            background: #e0e0e0;
        }
    </style>
</head>
<body>
    <div class="mobile-header">
        <h1>🤖 Contract Tracker</h1>
        <div class="stats">
            <div class="mini-stat">
                <div class="num" id="stat-total">0</div>
                <div class="label">Total</div>
            </div>
            <div class="mini-stat">
                <div class="num" id="stat-active">0</div>
                <div class="label">Active</div>
            </div>
            <div class="mini-stat">
                <div class="num" id="stat-alert">0</div>
                <div class="label">Alert</div>
            </div>
            <div class="mini-stat">
                <div class="num" id="stat-done">0</div>
                <div class="label">Done</div>
            </div>
        </div>
    </div>

    <div class="tabs">
        <button class="tab active" onclick="filterContracts('all')">All</button>
        <button class="tab" onclick="filterContracts('Pending')">Pending</button>
        <button class="tab" onclick="filterContracts('In Progress')">Active</button>
        <button class="tab" onclick="filterContracts('Completed')">Done</button>
    </div>

    <div class="contract-list" id="contractList"></div>

    <button class="fab" onclick="openAddModal()">+</button>

    <div class="modal" id="addModal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>New Contract</h2>
                <button class="modal-close" onclick="closeAddModal()">×</button>
            </div>
            <div class="form-group">
                <label>Contract Name *</label>
                <input type="text" id="contractName" placeholder="ABC Services Agreement">
            </div>
            <div class="form-group">
                <label>Type *</label>
                <select id="contractType">
                    <option value="">Select...</option>
                    <option value="Service Agreement">Service Agreement</option>
                    <option value="NDA">NDA</option>
                    <option value="Consulting">Consulting</option>
                    <option value="Purchase Order">Purchase Order</option>
                    <option value="Other">Other</option>
                </select>
            </div>
            <div class="form-group">
                <label>Description *</label>
                <textarea id="contractDescription" placeholder="Key details..."></textarea>
            </div>
            <div class="form-group">
                <label>Status</label>
                <select id="contractStatus">
                    <option value="Pending">Pending</option>
                    <option value="In Progress">In Progress</option>
                </select>
            </div>
            <div class="form-group">
                <label>Due Date</label>
                <input type="date" id="contractDueDate">
            </div>
            <button class="btn-submit" onclick="addContract()">Add Contract</button>
        </div>
    </div>

    <div class="toast" id="toast"></div>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
    <script>
        let contracts = [];
        let currentFilter = 'all';

        function init() {
            const saved = localStorage.getItem('mobileContracts');
            if (saved) {
                contracts = JSON.parse(saved);
            }
            renderContracts();
            updateStats();
            
            // Check reminders on load
            setTimeout(checkReminders, 2000);
        }

        function saveContracts() {
            localStorage.setItem('mobileContracts', JSON.stringify(contracts));
        }

        function openAddModal() {
            document.getElementById('addModal').classList.add('show');
        }

        function closeAddModal() {
            document.getElementById('addModal').classList.remove('show');
        }

        function addContract() {
            const name = document.getElementById('contractName').value.trim();
            const type = document.getElementById('contractType').value;
            const description = document.getElementById('contractDescription').value.trim();
            const status = document.getElementById('contractStatus').value;
            const dueDate = document.getElementById('contractDueDate').value;

            if (!name || !type || !description) {
                showToast('⚠️ Fill all required fields');
                return;
            }

            const contract = {
                id: Date.now(),
                name,
                type,
                description,
                status,
                dueDate,
                createdDate: new Date().toISOString().split('T')[0],
                lastUpdated: new Date().toISOString(),
                progressNotes: []
            };

            contracts.unshift(contract);
            saveContracts();
            
            document.getElementById('contractName').value = '';
            document.getElementById('contractType').value = '';
            document.getElementById('contractDescription').value = '';
            document.getElementById('contractStatus').value = 'Pending';
            document.getElementById('contractDueDate').value = '';
            
            closeAddModal();
            renderContracts();
            updateStats();
            showToast('✅ Contract added!');
        }

        function addProgress(id) {
            const note = prompt('Progress update:');
            if (note && note.trim()) {
                const contract = contracts.find(c => c.id === id);
                if (contract) {
                    contract.progressNotes.push({
                        date: new Date().toISOString().split('T')[0],
                        note: note.trim()
                    });
                    contract.lastUpdated = new Date().toISOString();
                    saveContracts();
                    renderContracts();
                    updateStats();
                    showToast('✅ Progress added');
                }
            }
        }

        function completeContract(id) {
            const contract = contracts.find(c => c.id === id);
            if (contract) {
                contract.status = 'Completed';
                contract.lastUpdated = new Date().toISOString();
                saveContracts();
                renderContracts();
                updateStats();
                showToast('🎉 Contract completed!');
            }
        }

        function deleteContract(id) {
            if (confirm('Delete this contract?')) {
                contracts = contracts.filter(c => c.id !== id);
                saveContracts();
                renderContracts();
                updateStats();
                showToast('🗑️ Deleted');
            }
        }

        function filterContracts(filter) {
            currentFilter = filter;
            document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
            event.target.classList.add('active');
            renderContracts();
        }

        function renderContracts() {
            const container = document.getElementById('contractList');
            
            let filtered = contracts;
            if (currentFilter !== 'all') {
                filtered = contracts.filter(c => c.status === currentFilter);
            }

            if (filtered.length === 0) {
                container.innerHTML = `
                    <div class="empty-state">
                        <div class="icon">📋</div>
                        <p>No contracts yet.<br>Tap + to add one!</p>
                    </div>
                `;
                return;
            }

            container.innerHTML = filtered.map(contract => {
                const daysSinceUpdate = Math.floor((Date.now() - new Date(contract.lastUpdated)) / (1000 * 60 * 60 * 24));
                const isStale = daysSinceUpdate > 1 && contract.status !== 'Completed';
                const isOverdue = contract.dueDate && new Date(contract.dueDate) < new Date() && contract.status !== 'Completed';
                
                let cardClass = 'contract-card';
                if (isOverdue) cardClass += ' overdue';
                else if (isStale) cardClass += ' stale';
                
                return `
                    <div class="${cardClass}">
                        <div class="contract-title">${contract.name}</div>
                        <div class="contract-meta">
                            <span>📅 ${contract.createdDate}</span>
                            <span>📝 ${contract.type}</span>
                            ${contract.dueDate ? `<span>⏰ ${contract.dueDate}</span>` : ''}
                            ${isStale ? `<span style="color: #dc3545;">⚠️ ${daysSinceUpdate}d</span>` : ''}
                        </div>
                        <span class="status-badge status-${contract.status.toLowerCase().replace(' ', '-')}">
                            ${contract.status}
                        </span>
                        <div class="contract-description">${contract.description}</div>
                        ${contract.progressNotes.length > 0 ? `
                            <div class="progress-note">
                                <strong>Latest (${contract.progressNotes[contract.progressNotes.length-1].date}):</strong><br>
                                ${contract.progressNotes[contract.progressNotes.length-1].note}
                            </div>
                        ` : ''}
                        <div class="contract-actions">
                            <button class="btn-update" onclick="addProgress(${contract.id})">+ Progress</button>
                            ${contract.status !== 'Completed' ? `
                                <button class="btn-complete" onclick="completeContract(${contract.id})">Done</button>
                            ` : ''}
                            <button class="btn-delete" onclick="deleteContract(${contract.id})">🗑️</button>
                        </div>
                    </div>
                `;
            }).join('');
        }

        function updateStats() {
            document.getElementById('stat-total').textContent = contracts.length;
            document.getElementById('stat-active').textContent = 
                contracts.filter(c => c.status === 'In Progress' || c.status === 'Pending').length;
            document.getElementById('stat-done').textContent = 
                contracts.filter(c => c.status === 'Completed').length;
            
            const needsAttention = contracts.filter(c => {
                if (c.status === 'Completed') return false;
                const daysSinceUpdate = Math.floor((Date.now() - new Date(c.lastUpdated)) / (1000 * 60 * 60 * 24));
                const isOverdue = c.dueDate && new Date(c.dueDate) < new Date();
                return daysSinceUpdate > 1 || isOverdue;
            }).length;
            document.getElementById('stat-alert').textContent = needsAttention;
        }

        function checkReminders() {
            const stale = contracts.filter(c => {
                if (c.status === 'Completed') return false;
                const daysSinceUpdate = Math.floor((Date.now() - new Date(c.lastUpdated)) / (1000 * 60 * 60 * 24));
                return daysSinceUpdate > 1;
            });

            const overdue = contracts.filter(c => 
                c.status !== 'Completed' && c.dueDate && new Date(c.dueDate) < new Date()
            );

            if (stale.length > 0 || overdue.length > 0) {
                let msg = '';
                if (overdue.length > 0) msg += `${overdue.length} overdue! `;
                if (stale.length > 0) msg += `${stale.length} need updates`;
                showToast('⚠️ ' + msg);
            }
        }

        function showToast(message) {
            const toast = document.getElementById('toast');
            toast.textContent = message;
            toast.classList.add('show');
            setTimeout(() => toast.classList.remove('show'), 3000);
        }

        // Close modal on background click
        document.getElementById('addModal').addEventListener('click', (e) => {
            if (e.target.id === 'addModal') {
                closeAddModal();
            }
        });

        init();
    </script>
</body>
</html>

I 
