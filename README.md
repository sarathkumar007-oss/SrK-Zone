<!DOCTYPE html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="theme-color" content="#1a73e8">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <title>Facility Manager Pro</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

```
    body {
        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        background: #f5f7fa;
        overflow-x: hidden;
    }

    .header {
        background: linear-gradient(135deg, #1a73e8 0%, #004ba0 100%);
        color: white;
        padding: 20px 16px 16px;
        position: sticky;
        top: 0;
        z-index: 100;
        box-shadow: 0 2px 12px rgba(0,0,0,0.15);
    }

    .header h1 {
        font-size: 20px;
        margin-bottom: 4px;
    }

    .header .subtitle {
        font-size: 12px;
        opacity: 0.9;
    }

    .nav-tabs {
        display: flex;
        background: white;
        overflow-x: auto;
        -webkit-overflow-scrolling: touch;
        border-bottom: 1px solid #e0e0e0;
        position: sticky;
        top: 76px;
        z-index: 99;
    }

    .nav-tab {
        flex: 1;
        min-width: 80px;
        padding: 14px 8px;
        background: white;
        border: none;
        border-bottom: 3px solid transparent;
        font-size: 13px;
        font-weight: 600;
        color: #666;
        cursor: pointer;
        transition: all 0.2s;
        white-space: nowrap;
    }

    .nav-tab.active {
        color: #1a73e8;
        border-bottom-color: #1a73e8;
    }

    .content {
        padding: 16px;
        padding-bottom: 80px;
    }

    .module {
        display: none;
    }

    .module.active {
        display: block;
    }

    .card {
        background: white;
        border-radius: 12px;
        padding: 16px;
        margin-bottom: 12px;
        box-shadow: 0 2px 8px rgba(0,0,0,0.08);
        border-left: 4px solid #1a73e8;
    }

    .card-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 12px;
    }

    .card-title {
        font-size: 16px;
        font-weight: bold;
        color: #333;
    }

    .badge {
        padding: 4px 10px;
        border-radius: 12px;
        font-size: 11px;
        font-weight: 600;
    }

    .badge-success { background: #d4edda; color: #155724; }
    .badge-warning { background: #fff3cd; color: #856404; }
    .badge-danger { background: #f8d7da; color: #721c24; }
    .badge-info { background: #d1ecf1; color: #0c5460; }
    .badge-primary { background: #cce5ff; color: #004085; }

    .form-group {
        margin-bottom: 14px;
    }

    .form-group label {
        display: block;
        font-size: 13px;
        font-weight: 600;
        color: #333;
        margin-bottom: 6px;
    }

    .form-group input,
    .form-group select,
    .form-group textarea {
        width: 100%;
        padding: 12px;
        border: 2px solid #e0e0e0;
        border-radius: 8px;
        font-size: 14px;
        transition: border 0.2s;
    }

    .form-group input:focus,
    .form-group select:focus,
    .form-group textarea:focus {
        outline: none;
        border-color: #1a73e8;
    }

    .form-group textarea {
        min-height: 80px;
        resize: vertical;
    }

    .btn {
        width: 100%;
        padding: 14px;
        border: none;
        border-radius: 8px;
        font-size: 15px;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.2s;
    }

    .btn-primary {
        background: #1a73e8;
        color: white;
    }

    .btn-primary:active {
        background: #1557b0;
    }

    .btn-success {
        background: #28a745;
        color: white;
    }

    .btn-danger {
        background: #dc3545;
        color: white;
    }

    .btn-secondary {
        background: #6c757d;
        color: white;
    }

    .btn-small {
        padding: 8px 12px;
        font-size: 13px;
        width: auto;
    }

    .stats-grid {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 12px;
        margin-bottom: 16px;
    }

    .stat-card {
        background: white;
        border-radius: 12px;
        padding: 16px;
        text-align: center;
        box-shadow: 0 2px 8px rgba(0,0,0,0.08);
    }

    .stat-card .number {
        font-size: 28px;
        font-weight: bold;
        color: #1a73e8;
        margin-bottom: 4px;
    }

    .stat-card .label {
        font-size: 12px;
        color: #666;
        text-transform: uppercase;
    }

    .employee-item {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 12px;
        background: #f8f9fa;
        border-radius: 8px;
        margin-bottom: 8px;
    }

    .employee-info {
        flex: 1;
    }

    .employee-name {
        font-weight: 600;
        color: #333;
        margin-bottom: 4px;
    }

    .employee-meta {
        font-size: 12px;
        color: #666;
    }

    .stock-item {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 12px;
        background: #f8f9fa;
        border-radius: 8px;
        margin-bottom: 8px;
    }

    .stock-item.low-stock {
        background: #fff3cd;
        border-left: 3px solid #ffc107;
    }

    .stock-item.out-stock {
        background: #f8d7da;
        border-left: 3px solid #dc3545;
    }

    .task-item {
        display: flex;
        align-items: center;
        gap: 12px;
        padding: 12px;
        background: #f8f9fa;
        border-radius: 8px;
        margin-bottom: 8px;
    }

    .task-item input[type="checkbox"] {
        width: 20px;
        height: 20px;
    }

    .task-item.completed {
        opacity: 0.6;
        text-decoration: line-through;
    }

    .fab {
        position: fixed;
        bottom: 20px;
        right: 20px;
        width: 56px;
        height: 56px;
        background: #1a73e8;
        border: none;
        border-radius: 50%;
        color: white;
        font-size: 24px;
        box-shadow: 0 4px 12px rgba(26, 115, 232, 0.4);
        cursor: pointer;
        z-index: 98;
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
        background: rgba(0,0,0,0.6);
        z-index: 200;
        align-items: flex-end;
    }

    .modal.show {
        display: flex;
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
        font-size: 20px;
        color: #333;
    }

    .modal-close {
        width: 32px;
        height: 32px;
        border: none;
        background: #f0f0f0;
        border-radius: 50%;
        font-size: 20px;
        cursor: pointer;
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
        z-index: 300;
        max-width: 90%;
    }

    .toast.show {
        display: block;
        animation: fadeIn 0.3s;
    }

    @keyframes fadeIn {
        from { opacity: 0; transform: translateX(-50%) translateY(20px); }
        to { opacity: 1; transform: translateX(-50%) translateY(0); }
    }

    .empty-state {
        text-align: center;
        padding: 40px 20px;
        color: #999;
    }

    .empty-state .icon {
        font-size: 48px;
        margin-bottom: 12px;
        opacity: 0.5;
    }

    .quick-actions {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 8px;
        margin-bottom: 16px;
    }

    .quick-actions button {
        padding: 10px;
        font-size: 13px;
    }

    .incident-priority-high {
        border-left-color: #dc3545 !important;
    }

    .incident-priority-medium {
        border-left-color: #ffc107 !important;
    }

    .incident-priority-low {
        border-left-color: #28a745 !important;
    }
</style>
```

</head>
<body>
    <div class="header">
        <h1>🏢 Facility Manager Pro</h1>
        <p class="subtitle">Complete tracking & management system</p>
    </div>

```
<div class="nav-tabs">
    <button class="nav-tab active" onclick="switchTab('attendance')">👥 Attendance</button>
    <button class="nav-tab" onclick="switchTab('incidents')">⚠️ Incidents</button>
    <button class="nav-tab" onclick="switchTab('stock')">📦 Stock</button>
    <button class="nav-tab" onclick="switchTab('ppm')">🔧 PPM</button>
    <button class="nav-tab" onclick="switchTab('tasks')">✓ Tasks</button>
    <button class="nav-tab" onclick="switchTab('reports')">📊 Reports</button>
</div>

<div class="content">
    <!-- ATTENDANCE MODULE -->
    <div id="attendance" class="module active">
        <div class="stats-grid">
            <div class="stat-card">
                <div class="number" id="stat-present">0</div>
                <div class="label">Present</div>
            </div>
            <div class="stat-card">
                <div class="number" id="stat-total-employees">0</div>
                <div class="label">Total Staff</div>
            </div>
        </div>

        <div class="quick-actions">
            <button class="btn btn-success" onclick="openCheckInModal()">Check In</button>
            <button class="btn btn-danger" onclick="openCheckOutModal()">Check Out</button>
        </div>

        <div class="card">
            <div class="card-header">
                <div class="card-title">Today's Attendance</div>
            </div>
            <div id="attendanceList"></div>
        </div>
    </div>

    <!-- INCIDENTS MODULE -->
    <div id="incidents" class="module">
        <div class="stats-grid">
            <div class="stat-card">
                <div class="number" id="stat-incidents-open">0</div>
                <div class="label">Open</div>
            </div>
            <div class="stat-card">
                <div class="number" id="stat-incidents-total">0</div>
                <div class="label">Total</div>
            </div>
        </div>

        <div id="incidentsList"></div>
    </div>

    <!-- STOCK MODULE -->
    <div id="stock" class="module">
        <div class="stats-grid">
            <div class="stat-card">
                <div class="number" id="stat-stock-low">0</div>
                <div class="label">Low Stock</div>
            </div>
            <div class="stat-card">
                <div class="number" id="stat-stock-items">0</div>
                <div class="label">Total Items</div>
            </div>
        </div>

        <div id="stockList"></div>
    </div>

    <!-- PPM MODULE -->
    <div id="ppm" class="module">
        <div class="stats-grid">
            <div class="stat-card">
                <div class="number" id="stat-ppm-pending">0</div>
                <div class="label">Pending</div>
            </div>
            <div class="stat-card">
                <div class="number" id="stat-ppm-total">0</div>
                <div class="label">Total Tasks</div>
            </div>
        </div>

        <div id="ppmList"></div>
    </div>

    <!-- TASKS MODULE -->
    <div id="tasks" class="module">
        <div class="stats-grid">
            <div class="stat-card">
                <div class="number" id="stat-tasks-completed">0</div>
                <div class="label">Completed</div>
            </div>
            <div class="stat-card">
                <div class="number" id="stat-tasks-total">0</div>
                <div class="label">Total</div>
            </div>
        </div>

        <div id="tasksList"></div>
    </div>

    <!-- REPORTS MODULE -->
    <div id="reports" class="module">
        <div class="card">
            <div class="card-title" style="margin-bottom: 16px;">Export Data</div>
            <button class="btn btn-primary" style="margin-bottom: 8px;" onclick="exportAttendance()">📊 Export Attendance Report</button>
            <button class="btn btn-primary" style="margin-bottom: 8px;" onclick="exportIncidents()">⚠️ Export Incidents Report</button>
            <button class="btn btn-primary" style="margin-bottom: 8px;" onclick="exportStock()">📦 Export Stock Report</button>
            <button class="btn btn-primary" style="margin-bottom: 8px;" onclick="exportPPM()">🔧 Export PPM Schedule</button>
            <button class="btn btn-primary" onclick="exportAll()">📁 Export All Data</button>
        </div>

        <div class="card">
            <div class="card-title" style="margin-bottom: 16px;">Data Management</div>
            <button class="btn btn-secondary" onclick="clearAllData()">🗑️ Clear All Data (Reset)</button>
        </div>
    </div>
</div>

<button class="fab" onclick="openQuickAdd()">+</button>

<!-- Check In Modal -->
<div class="modal" id="checkInModal">
    <div class="modal-content">
        <div class="modal-header">
            <h2>Check In</h2>
            <button class="modal-close" onclick="closeModal('checkInModal')">×</button>
        </div>
        <div class="form-group">
            <label>Employee ID *</label>
            <input type="text" id="checkInId" placeholder="e.g., EMP001">
        </div>
        <div class="form-group">
            <label>Employee Name *</label>
            <input type="text" id="checkInName" placeholder="John Doe">
        </div>
        <div class="form-group">
            <label>Department</label>
            <select id="checkInDept">
                <option value="">Select...</option>
                <option value="Maintenance">Maintenance</option>
                <option value="Security">Security</option>
                <option value="Housekeeping">Housekeeping</option>
                <option value="Administration">Administration</option>
                <option value="Operations">Operations</option>
            </select>
        </div>
        <button class="btn btn-success" onclick="checkIn()">Check In Now</button>
    </div>
</div>

<!-- Check Out Modal -->
<div class="modal" id="checkOutModal">
    <div class="modal-content">
        <div class="modal-header">
            <h2>Check Out</h2>
            <button class="modal-close" onclick="closeModal('checkOutModal')">×</button>
        </div>
        <div class="form-group">
            <label>Employee ID *</label>
            <input type="text" id="checkOutId" placeholder="e.g., EMP001">
        </div>
        <button class="btn btn-danger" onclick="checkOut()">Check Out Now</button>
    </div>
</div>

<!-- Add Incident Modal -->
<div class="modal" id="incidentModal">
    <div class="modal-content">
        <div class="modal-header">
            <h2>Report Incident</h2>
            <button class="modal-close" onclick="closeModal('incidentModal')">×</button>
        </div>
        <div class="form-group">
            <label>Incident Type *</label>
            <select id="incidentType">
                <option value="">Select...</option>
                <option value="Safety">Safety Issue</option>
                <option value="Equipment">Equipment Failure</option>
                <option value="Security">Security Breach</option>
                <option value="Property">Property Damage</option>
                <option value="Other">Other</option>
            </select>
        </div>
        <div class="form-group">
            <label>Priority *</label>
            <select id="incidentPriority">
                <option value="Low">Low</option>
                <option value="Medium">Medium</option>
                <option value="High">High</option>
            </select>
        </div>
        <div class="form-group">
            <label>Location *</label>
            <input type="text" id="incidentLocation" placeholder="e.g., Building A, Floor 3">
        </div>
        <div class="form-group">
            <label>Description *</label>
            <textarea id="incidentDescription" placeholder="Detailed description of the incident..."></textarea>
        </div>
        <div class="form-group">
            <label>Reported By</label>
            <input type="text" id="incidentReporter" placeholder="Your name">
        </div>
        <button class="btn btn-primary" onclick="addIncident()">Submit Report</button>
    </div>
</div>

<!-- Add Stock Modal -->
<div class="modal" id="stockModal">
    <div class="modal-content">
        <div class="modal-header">
            <h2>Add/Update Stock</h2>
            <button class="modal-close" onclick="closeModal('stockModal')">×</button>
        </div>
        <div class="form-group">
            <label>Item Name *</label>
            <input type="text" id="stockName" placeholder="e.g., Cleaning Supplies">
        </div>
        <div class="form-group">
            <label>Category</label>
            <select id="stockCategory">
                <option value="">Select...</option>
                <option value="Cleaning">Cleaning Supplies</option>
                <option value="Maintenance">Maintenance Tools</option>
                <option value="Safety">Safety Equipment</option>
                <option value="Office">Office Supplies</option>
                <option value="Other">Other</option>
            </select>
        </div>
        <div class="form-group">
            <label>Current Quantity *</label>
            <input type="number" id="stockQuantity" placeholder="0" min="0">
        </div>
        <div class="form-group">
            <label>Minimum Stock Level</label>
            <input type="number" id="stockMin" placeholder="10" min="0">
        </div>
        <div class="form-group">
            <label>Unit</label>
            <input type="text" id="stockUnit" placeholder="e.g., pcs, boxes, liters">
        </div>
        <button class="btn btn-primary" onclick="addStock()">Save Stock Item</button>
    </div>
</div>

<!-- Add PPM Modal -->
<div class="modal" id="ppmModal">
    <div class="modal-content">
        <div class="modal-header">
            <h2>Add PPM Task</h2>
            <button class="modal-close" onclick="closeModal('ppmModal')">×</button>
        </div>
        <div class="form-group">
            <label>Equipment/Asset *</label>
            <input type="text" id="ppmEquipment" placeholder="e.g., HVAC Unit A">
        </div>
        <div class="form-group">
            <label>Task Description *</label>
            <textarea id="ppmTask" placeholder="Maintenance task details..."></textarea>
        </div>
        <div class="form-group">
            <label>Frequency *</label>
            <select id="ppmFrequency">
                <option value="Daily">Daily</option>
                <option value="Weekly">Weekly</option>
                <option value="Monthly">Monthly</option>
                <option value="Quarterly">Quarterly</option>
                <option value="Yearly">Yearly</option>
            </select>
        </div>
        <div class="form-group">
            <label>Next Due Date *</label>
            <input type="date" id="ppmDueDate">
        </div>
        <div class="form-group">
            <label>Assigned To</label>
            <input type="text" id="ppmAssignee" placeholder="Technician name">
        </div>
        <button class="btn btn-primary" onclick="addPPM()">Add PPM Task</button>
    </div>
</div>

<!-- Add Task Modal -->
<div class="modal" id="taskModal">
    <div class="modal-content">
        <div class="modal-header">
            <h2>Add Daily Task</h2>
            <button class="modal-close" onclick="closeModal('taskModal')">×</button>
        </div>
        <div class="form-group">
            <label>Task Description *</label>
            <input type="text" id="taskDescription" placeholder="e.g., Check fire extinguishers">
        </div>
        <div class="form-group">
            <label>Category</label>
            <select id="taskCategory">
                <option value="">Select...</option>
                <option value="Safety">Safety Check</option>
                <option value="Inspection">Inspection</option>
                <option value="Maintenance">Maintenance</option>
                <option value="Admin">Administrative</option>
                <option value="Other">Other</option>
            </select>
        </div>
        <div class="form-group">
            <label>Priority</label>
            <select id="taskPriority">
                <option value="Low">Low</option>
                <option value="Medium">Medium</option>
                <option value="High">High</option>
            </select>
        </div>
        <button class="btn btn-primary" onclick="addTask()">Add Task</button>
    </div>
</div>

<!-- Quick Add Menu -->
<div class="modal" id="quickAddModal">
    <div class="modal-content">
        <div class="modal-header">
            <h2>Quick Add</h2>
            <button class="modal-close" onclick="closeModal('quickAddModal')">×</button>
        </div>
        <button class="btn btn-primary" style="margin-bottom: 8px;" onclick="closeModal('quickAddModal'); openCheckInModal();">👥 Check In Employee</button>
        <button class="btn btn-primary" style="margin-bottom: 8px;" onclick="closeModal('quickAddModal'); openModal('incidentModal');">⚠️ Report Incident</button>
        <button class="btn btn-primary" style="margin-bottom: 8px;" onclick="closeModal('quickAddModal'); openModal('stockModal');">📦 Add Stock Item</button>
        <button class="btn btn-primary" style="margin-bottom: 8px;" onclick="closeModal('quickAddModal'); openModal('ppmModal');">🔧 Add PPM Task</button>
        <button class="btn btn-primary" onclick="closeModal('quickAddModal'); openModal('taskModal');">✓ Add Daily Task</button>
    </div>
</div>

<div class="toast" id="toast"></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
<script>
    let data = {
        attendance: [],
        incidents: [],
        stock: [],
        ppm: [],
        tasks: []
    };

    let currentTab = 'attendance';

    function init() {
        const saved = localStorage.getItem('facilityData');
        if (saved) {
            data = JSON.parse(saved);
        }
        renderAll();
    }

    function saveData() {
        localStorage.setItem('facilityData', JSON.stringify(data));
    }

    function switchTab(tab) {
        currentTab = tab;
        document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
        document.querySelectorAll('.module').forEach(m => m.classList.remove('active'));
        event.target.classList.add('active');
        document.getElementById(tab).classList.add('active');
        renderAll();
    }

    function openModal(id) {
        document.getElementById(id).classList.add('show');
    }

    function closeModal(id) {
        document.getElementById(id).classList.remove('show');
    }

    function openQuickAdd() {
        openModal('quickAddModal');
    }

    function openCheckInModal() {
        openModal('checkInModal');
    }

    function openCheckOutModal() {
        openModal('checkOutModal');
    }

    function showToast(msg) {
        const toast = document.getElementById('toast');
        toast.textContent = msg;
        toast.classList.add('show');
        setTimeout(() => toast.classList.remove('show'), 3000);
    }

    // ATTENDANCE FUNCTIONS
    function checkIn() {
        const id = document.getElementById('checkInId').value.trim();
        const name = document.getElementById('checkInName').value.trim();
        const dept = document.getElementById('checkInDept').value;

        if (!id || !name) {
            showToast('⚠️ Employee ID and Name required');
            return;
        }

        const now = new Date();
        const today = now.toISOString().split('T')[0];
        
        const existing = data.attendance.find(a => a.employeeId === id && a.date === today);
        if (existing) {
            showToast('⚠️ Already checked in today');
            return;
        }

        data.attendance.push({
            id: Date.now(),
            employeeId: id,
            employeeName: name,
            department: dept,
            date: today,
            checkIn: now.toISOString(),
            checkOut: null,
            status: 'Present'
        });

        saveData();
        closeModal('checkInModal');
        document.getElementById('checkInId').value = '';
        document.getElementById('checkInName').value = '';
        document.getElementById('checkInDept').value = '';
        renderAll();
        showToast('✅ Checked in successfully');
    }

    function checkOut() {
        const id = document.getElementById('checkOutId').value.trim();
        if (!id) {
            showToast('⚠️ Employee ID required');
            return;
        }

        const today = new Date().toISOString().split('T')[0];
        const record = data.attendance.find(a => a.employeeId === id && a.date === today && !a.checkOut);

        if (!record) {
            showToast('⚠️ No check-in record found for today');
            return;
        }

        record.checkOut = new Date().toISOString();
        record.status = 'Checked Out';

        saveData();
        closeModal('checkOutModal');
        document.getElementById('checkOutId').value = '';
        renderAll();
        showToast('✅ Checked out successfully');
    }

    function renderAttendance() {
        const today = new Date().toISOString().split('T')[0];
        const todayRecords = data.attendance.filter(a => a.date === today);
        const present = todayRecords.filter(a => a.status === 'Present').length;

        document.getElementById('stat-present').textContent = present;
        document.getElementById('stat-total-employees').textContent = todayRecords.length;

        const container = document.getElementById('attendanceList');
        if (todayRecords.length === 0) {
            container.innerHTML = '<div class="empty-state"><div class="icon">👥</div><p>No attendance records today</p></div>';
            return;
        }

        container.innerHTML = todayRecords.map(record => `
            <div class="employee-item">
                <div class="employee-info">
                    <div class="employee-name">${record.employeeName} (${record.employeeId})</div>
                    <div class="employee-meta">
                        ${record.department || 'N/A'} • 
                        In: ${new Date(record.checkIn).toLocaleTimeString()} 
                        ${record.checkOut ? `• Out: ${new Date(record.checkOut).toLocaleTimeString()}` : ''}
                    </div>
                </div>
                <span class="badge ${record.status === 'Present' ? 'badge-success' : 'badge-info'}">${record.status}</span>
            </div>
        `).join('');
    }

    // INCIDENT FUNCTIONS
    function addIncident() {
        const type = document.getElementById('incidentType').value;
        const priority = document.getElementById('incidentPriority').value;
        const location = document.getElementById('incidentLocation').value.trim();
        const description = document.getElementById('incidentDescription').value.trim();
        const reporter = document.getElementById('incidentReporter').value.trim();

        if (!type || !location || !description) {
            showToast('⚠️ Fill all required fields');
            return;
        }

        data.incidents.push({
            id: Date.now(),
            type,
            priority,
            location,
            description,
            reporter,
            reportedDate: new Date().toISOString(),
            status: 'Open',
            resolvedDate: null
        });

        saveData();
        closeModal('incidentModal');
        document.getElementById('incidentType').value = '';
        document.getElementById('incidentLocation').value = '';
        document.getElementById('incidentDescription').value = '';
        document.getElementById('incidentReporter').value = '';
        renderAll();
        showToast('✅ Incident reported');
    }

    function resolveIncident(id) {
        const incident = data.incidents.find(i => i.id === id);
        if (incident) {
            incident.status = 'Resolved';
            incident.resolvedDate = new Date().toISOString();
            saveData();
            renderAll();
            showToast('✅ Incident resolved');
        }
    }

    function deleteIncident(id) {
        if (confirm('Delete this incident?')) {
            data.incidents = data.incidents.filter(i => i.id !== id);
            saveData();
            renderAll();
            showToast('🗑️ Deleted');
        }
    }

    function renderIncidents() {
        const open = data.incidents.filter(i => i.status === 'Open').length;
        document.getElementById('stat-incidents-open').textContent = open;
        document.getElementById('stat-incidents-total').textContent = data.incidents.length;

        const container = document.getElementById('incidentsList');
        if (data.incidents.length === 0) {
            container.innerHTML = '<div class="empty-state"><div class="icon">⚠️</div><p>No incidents reported</p></div>';
            return;
        }

        const sorted = [...data.incidents].sort((a, b) => new Date(b.reportedDate) - new Date(a.reportedDate));

        container.innerHTML = sorted.map(incident => `
            <div class="card incident-priority-${incident.priority.toLowerCase()}">
                <div class="card-header">
                    <div class="card-title">${incident.type} - ${incident.location}</div>
                    <span class="badge badge-${incident.status === 'Open' ? 'danger' : 'success'}">${incident.status}</span>
                </div>
                <div style="font-size: 13px; color: #666; margin-bottom: 8px;">
                    Priority: ${incident.priority} • ${new Date(incident.reportedDate).toLocaleString()}
                </div>
                <div style="font-size: 14px; color: #333; margin-bottom: 8px;">${incident.description}</div>
                ${incident.reporter ? `<div style="font-size: 12px; color: #999;">Reported by: ${incident.reporter}</div>` : ''}
                ${incident.status === 'Open' ? `
                    <div style="margin-top: 12px; display: flex; gap: 8px;">
                        <button class="btn btn-success btn-small" onclick="resolveIncident(${incident.id})">Mark Resolved</button>
                        <button class="btn btn-danger btn-small" onclick="deleteIncident(${incident.id})">Delete</button>
                    </div>
                ` : ''}
            </div>
        `).join('');
    }

    // STOCK FUNCTIONS
    function addStock() {
        const name = document.getElementById('stockName').value.trim();
        const category = document.getElementById('stockCategory').value;
        const quantity = parseInt(document.getElementById('stockQuantity').value);
        const min = parseInt(document.getElementById('stockMin').value) || 10;
        const unit = document.getElementById('stockUnit').value.trim() || 'pcs';

        if (!name || isNaN(quantity)) {
            showToast('⚠️ Name and quantity required');
            return;
        }

        const existing = data.stock.find(s => s.name.toLowerCase() === name.toLowerCase());
        if (existing) {
            existing.quantity = quantity;
            existing.lastUpdated = new Date().toISOString();
            showToast('✅ Stock updated');
        } else {
            data.stock.push({
                id: Date.now(),
                name,
                category,
                quantity,
                minLevel: min,
                unit,
                lastUpdated: new Date().toISOString()
            });
            showToast('✅ Stock item added');
        }

        saveData();
        closeModal('stockModal');
        document.getElementById('stockName').value = '';
        document.getElementById('stockCategory').value = '';
        document.getElementById('stockQuantity').value = '';
        document.getElementById('stockMin').value = '';
        document.getElementById('stockUnit').value = '';
        renderAll();
    }

    function updateStockQuantity(id, change) {
        const item = data.stock.find(s => s.id === id);
        if (item) {
            const newQty = Math.max(0, item.quantity + change);
            item.quantity = newQty;
            item.lastUpdated = new Date().toISOString();
            saveData();
            renderAll();
        }
    }

    function deleteStock(id) {
        if (confirm('Delete this stock item?')) {
            data.stock = data.stock.filter(s => s.id !== id);
            saveData();
            renderAll();
            showToast('🗑️ Deleted');
        }
    }

    function renderStock() {
        const lowStock = data.stock.filter(s => s.quantity <= s.minLevel).length;
        document.getElementById('stat-stock-low').textContent = lowStock;
        document.getElementById('stat-stock-items').textContent = data.stock.length;

        const container = document.getElementById('stockList');
        if (data.stock.length === 0) {
            container.innerHTML = '<div class="empty-state"><div class="icon">📦</div><p>No stock items added</p></div>';
            return;
        }

        container.innerHTML = data.stock.map(item => {
            let itemClass = 'stock-item';
            if (item.quantity === 0) itemClass += ' out-stock';
            else if (item.quantity <= item.minLevel) itemClass += ' low-stock';

            return `
                <div class="${itemClass}">
                    <div style="flex: 1;">
                        <div style="font-weight: 600; color: #333; margin-bottom: 4px;">${item.name}</div>
                        <div style="font-size: 12px; color: #666;">
                            ${item.category || 'N/A'} • Min: ${item.minLevel} ${item.unit}
                        </div>
                    </div>
                    <div style="text-align: right;">
                        <div style="font-size: 24px; font-weight: bold; color: ${item.quantity === 0 ? '#dc3545' : item.quantity <= item.minLevel ? '#ffc107' : '#28a745'};">
                            ${item.quantity}
                        </div>
                        <div style="font-size: 11px; color: #666;">${item.unit}</div>
                        <div style="display: flex; gap: 4px; margin-top: 6px;">
                            <button class="btn btn-success btn-small" onclick="updateStockQuantity(${item.id}, 1)">+</button>
                            <button class="btn btn-danger btn-small" onclick="updateStockQuantity(${item.id}, -1)">-</button>
                            <button class="btn btn-secondary btn-small" onclick="deleteStock(${item.id})">🗑️</button>
                        </div>
                    </div>
                </div>
            `;
        }).join('');
    }

    // PPM FUNCTIONS
    function addPPM() {
        const equipment = document.getElementById('ppmEquipment').value.trim();
        const task = document.getElementById('ppmTask').value.trim();
        const frequency = document.getElementById('ppmFrequency').value;
        const dueDate = document.getElementById('ppmDueDate').value;
        const assignee = document.getElementById('ppmAssignee').value.trim();

        if (!equipment || !task || !dueDate) {
            showToast('⚠️ Fill all required fields');
            return;
        }

        data.ppm.push({
            id: Date.now(),
            equipment,
            task,
            frequency,
            dueDate,
            assignee,
            status: 'Pending',
            lastCompleted: null,
            createdDate: new Date().toISOString()
        });

        saveData();
        closeModal('ppmModal');
        document.getElementById('ppmEquipment').value = '';
        document.getElementById('ppmTask').value = '';
        document.getElementById('ppmDueDate').value = '';
        document.getElementById('ppmAssignee').value = '';
        renderAll();
        showToast('✅ PPM task added');
    }

    function completePPM(id) {
        const task = data.ppm.find(p => p.id === id);
        if (task) {
            task.status = 'Completed';
            task.lastCompleted = new Date().toISOString();
            saveData();
            renderAll();
            showToast('✅ PPM task completed');
        }
    }

    function deletePPM(id) {
        if (confirm('Delete this PPM task?')) {
            data.ppm = data.ppm.filter(p => p.id !== id);
            saveData();
            renderAll();
            showToast('🗑️ Deleted');
        }
    }

    function renderPPM() {
        const pending = data.ppm.filter(p => p.status === 'Pending').length;
        document.getElementById('stat-ppm-pending').textContent = pending;
        document.getElementById('stat-ppm-total').textContent = data.ppm.length;

        const container = document.getElementById('ppmList');
        if (data.ppm.length === 0) {
            container.innerHTML = '<div class="empty-state"><div class="icon">🔧</div><p>No PPM tasks scheduled</p></div>';
            return;
        }

        const sorted = [...data.ppm].sort((a, b) => new Date(a.dueDate) - new Date(b.dueDate));

        container.innerHTML = sorted.map(task => {
            const isOverdue = new Date(task.dueDate) < new Date() && task.status === 'Pending';
            return `
                <div class="card">
                    <div class="card-header">
                        <div class="card-title">${task.equipment}</div>
                        <span class="badge badge-${task.status === 'Pending' ? (isOverdue ? 'danger' : 'warning') : 'success'}">${task.status}</span>
                    </div>
                    <div style="font-size: 14px; color: #333; margin-bottom: 8px;">${task.task}</div>
                    <div style="font-size: 12px; color: #666; margin-bottom: 8px;">
                        ${task.frequency} • Due: ${task.dueDate} ${isOverdue ? '🔴 OVERDUE' : ''}
                        ${task.assignee ? `• Assigned: ${task.assignee}` : ''}
                    </div>
                    ${task.status === 'Pending' ? `
                        <div style="display: flex; gap: 8px;">
                            <button class="btn btn-success btn-small" onclick="completePPM(${task.id})">Complete</button>
                            <button class="btn btn-danger btn-small" onclick="deletePPM(${task.id})">Delete</button>
                        </div>
                    ` : `<div style="font-size: 12px; color: #28a745;">✓ Completed ${new Date(task.lastCompleted).toLocaleDateString()}</div>`}
                </div>
            `;
        }).join('');
    }

    // TASKS FUNCTIONS
    function addTask() {
        const description = document.getElementById('taskDescription').value.trim();
        const category = document.getElementById('taskCategory').value;
        const priority = document.getElementById('taskPriority').value;

        if (!description) {
            showToast('⚠️ Task description required');
            return;
        }

        data.tasks.push({
            id: Date.now(),
            description,
            category,
            priority,
            completed: false,
            createdDate: new Date().toISOString(),
            completedDate: null
        });

        saveData();
        closeModal('taskModal');
        document.getElementById('taskDescription').value = '';
        document.getElementById('taskCategory').value = '';
        renderAll();
        showToast('✅ Task added');
    }

    function toggleTask(id) {
        const task = data.tasks.find(t => t.id === id);
        if (task) {
            task.completed = !task.completed;
            task.completedDate = task.completed ? new Date().toISOString() : null;
            saveData();
            renderAll();
        }
    }

    function deleteTask(id) {
        if (confirm('Delete this task?')) {
            data.tasks = data.tasks.filter(t => t.id !== id);
            saveData();
            renderAll();
            showToast('🗑️ Deleted');
        }
    }

    function renderTasks() {
        const completed = data.tasks.filter(t => t.completed).length;
        document.getElementById('stat-tasks-completed').textContent = completed;
        document.getElementById('stat-tasks-total').textContent = data.tasks.length;

        const container = document.getElementById('tasksList');
        if (data.tasks.length === 0) {
            container.innerHTML = '<div class="empty-state"><div class="icon">✓</div><p>No tasks added</p></div>';
            return;
        }

        const sorted = [...data.tasks].sort((a, b) => a.completed - b.completed);

        container.innerHTML = sorted.map(task => `
            <div class="task-item ${task.completed ? 'completed' : ''}">
                <input type="checkbox" ${task.completed ? 'checked' : ''} onchange="toggleTask(${task.id})">
                <div style="flex: 1;">
                    <div style="font-weight: 600; color: #333;">${task.description}</div>
                    <div style="font-size: 12px; color: #666;">
                        ${task.category || 'General'} • ${task.priority} Priority
                    </div>
                </div>
                <button class="btn btn-danger btn-small" onclick="deleteTask(${task.id})">🗑️</button>
            </div>
        `).join('');
    }

    // EXPORT FUNCTIONS
    function exportAttendance() {
        if (data.attendance.length === 0) {
            showToast('⚠️ No attendance data');
            return;
        }

        const exportData = data.attendance.map(a => ({
            'Employee ID': a.employeeId,
            'Employee Name': a.employeeName,
            'Department': a.department || 'N/A',
            'Date': a.date,
            'Check In': new Date(a.checkIn).toLocaleString(),
            'Check Out': a.checkOut ? new Date(a.checkOut).toLocaleString() : 'N/A',
            'Status': a.status
        }));

        const ws = XLSX.utils.json_to_sheet(exportData);
        const wb = XLSX.utils.book_new();
        XLSX.utils.book_append_sheet(wb, ws, 'Attendance');
        XLSX.writeFile(wb, `attendance_${new Date().toISOString().split('T')[0]}.xlsx`);
        showToast('✅ Attendance exported');
    }

    function exportIncidents() {
        if (data.incidents.length === 0) {
            showToast('⚠️ No incident data');
            return;
        }

        const exportData = data.incidents.map(i => ({
            'Type': i.type,
            'Priority': i.priority,
            'Location': i.location,
            'Description': i.description,
            'Reporter': i.reporter || 'N/A',
            'Reported Date': new Date(i.reportedDate).toLocaleString(),
            'Status': i.status,
            'Resolved Date': i.resolvedDate ? new Date(i.resolvedDate).toLocaleString() : 'N/A'
        }));

        const ws = XLSX.utils.json_to_sheet(exportData);
        const wb = XLSX.utils.book_new();
        XLSX.utils.book_append_sheet(wb, ws, 'Incidents');
        XLSX.writeFile(wb, `incidents_${new Date().toISOString().split('T')[0]}.xlsx`);
        showToast('✅ Incidents exported');
    }

    function exportStock() {
        if (data.stock.length === 0) {
            showToast('⚠️ No stock data');
            return;
        }

        const exportData = data.stock.map(s => ({
            'Item Name': s.name,
            'Category': s.category || 'N/A',
            'Current Quantity': s.quantity,
            'Minimum Level': s.minLevel,
            'Unit': s.unit,
            'Status': s.quantity === 0 ? 'Out of Stock' : s.quantity <= s.minLevel ? 'Low Stock' : 'In Stock',
            'Last Updated': new Date(s.lastUpdated).toLocaleString()
        }));

        const ws = XLSX.utils.json_to_sheet(exportData);
        const wb = XLSX.utils.book_new();
        XLSX.utils.book_append_sheet(wb, ws, 'Stock');
        XLSX.writeFile(wb, `stock_${new Date().toISOString().split('T')[0]}.xlsx`);
        showToast('✅ Stock exported');
    }

    function exportPPM() {
        if (data.ppm.length === 0) {
            showToast('⚠️ No PPM data');
            return;
        }

        const exportData = data.ppm.map(p => ({
            'Equipment': p.equipment,
            'Task': p.task,
            'Frequency': p.frequency,
            'Due Date': p.dueDate,
            'Assigned To': p.assignee || 'N/A',
            'Status': p.status,
            'Last Completed': p.lastCompleted ? new Date(p.lastCompleted).toLocaleString() : 'N/A'
        }));

        const ws = XLSX.utils.json_to_sheet(exportData);
        const wb = XLSX.utils.book_new();
        XLSX.utils.book_append_sheet(wb, ws, 'PPM Schedule');
        XLSX.writeFile(wb, `ppm_${new Date().toISOString().split('T')[0]}.xlsx`);
        showToast('✅ PPM schedule exported');
    }

    function exportAll() {
        const wb = XLSX.utils.book_new();

        if (data.attendance.length > 0) {
            const ws1 = XLSX.utils.json_to_sheet(data.attendance.map(a => ({
                'Employee ID': a.employeeId,
                'Name': a.employeeName,
                'Department': a.department || 'N/A',
                'Date': a.date,
                'Check In': new Date(a.checkIn).toLocaleString(),
                'Check Out': a.checkOut ? new Date(a.checkOut).toLocaleString() : 'N/A'
            })));
            XLSX.utils.book_append_sheet(wb, ws1, 'Attendance');
        }

        if (data.incidents.length > 0) {
            const ws2 = XLSX.utils.json_to_sheet(data.incidents.map(i => ({
                'Type': i.type,
                'Priority': i.priority,
                'Location': i.location,
                'Description': i.description,
                'Status': i.status,
                'Reported': new Date(i.reportedDate).toLocaleString()
            })));
            XLSX.utils.book_append_sheet(wb, ws2, 'Incidents');
        }

        if (data.stock.length > 0) {
            const ws3 = XLSX.utils.json_to_sheet(data.stock.map(s => ({
                'Item': s.name,
                'Category': s.category || 'N/A',
                'Quantity': s.quantity,
                'Min Level': s.minLevel,
                'Unit': s.unit
            })));
            XLSX.utils.book_append_sheet(wb, ws3, 'Stock');
        }

        if (data.ppm.length > 0) {
            const ws4 = XLSX.utils.json_to_sheet(data.ppm.map(p => ({
                'Equipment': p.equipment,
                'Task': p.task,
                'Frequency': p.frequency,
                'Due Date': p.dueDate,
                'Status': p.status
            })));
            XLSX.utils.book_append_sheet(wb, ws4, 'PPM');
        }

        if (data.tasks.length > 0) {
            const ws5 = XLSX.utils.json_to_sheet(data.tasks.map(t => ({
                'Task': t.description,
                'Category': t.category || 'N/A',
                'Priority': t.priority,
                'Completed': t.completed ? 'Yes' : 'No'
            })));
            XLSX.utils.book_append_sheet(wb, ws5, 'Tasks');
        }

        XLSX.writeFile(wb, `facility_data_${new Date().toISOString().split('T')[0]}.xlsx`);
        showToast('✅ All data exported');
    }

    function clearAllData() {
        if (confirm('⚠️ WARNING: This will delete ALL data permanently. Continue?')) {
            if (confirm('Are you ABSOLUTELY sure? This cannot be undone!')) {
                data = {
                    attendance: [],
                    incidents: [],
                    stock: [],
                    ppm: [],
                    tasks: []
                };
                saveData();
                renderAll();
                showToast('🗑️ All data cleared');
            }
        }
    }

    function renderAll() {
        renderAttendance();
        renderIncidents();
        renderStock();
        renderPPM();
        renderTasks();
    }

    document.querySelectorAll('.modal').forEach(modal => {
        modal.addEventListener('click', (e) => {
            if (e.target === modal) {
                modal.classList.remove('show');
            }
        });
    });

    init();
</script>
```

</body>
</html>