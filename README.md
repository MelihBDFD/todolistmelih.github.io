# todolistmelih.github.io
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>📋 MELİH TO-DO - Basit HTML Uygulama</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(45deg, #667eea, #764ba2);
            margin: 0;
            padding: 20px;
            min-height: 100vh;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            overflow: hidden;
        }

        .header {
            background: #2c3e50;
            color: white;
            padding: 20px;
            text-align: center;
        }

        .header h1 {
            margin: 0;
            font-size: 24px;
        }

        .creator {
            margin-top: 10px;
            font-size: 14px;
            opacity: 0.8;
        }

        .add-task {
            padding: 20px;
            background: #f8f9fa;
        }

        .input-group {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
        }

        .task-input {
            flex: 1;
            padding: 10px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
        }

        .priority-select {
            padding: 10px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            background: white;
        }

        .add-btn {
            padding: 10px 20px;
            background: #667eea;
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            cursor: pointer;
        }

        .add-btn:hover {
            background: #5a6fd8;
        }

        .actions {
            padding: 20px;
            background: #e9ecef;
        }

        .action-buttons {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .action-btn {
            padding: 10px 15px;
            border: none;
            border-radius: 8px;
            font-size: 14px;
            cursor: pointer;
        }

        .complete-all {
            background: #51cf66;
            color: white;
        }

        .clear-completed {
            background: #ffd43b;
            color: #333;
        }

        .sort-tasks {
            background: #667eea;
            color: white;
        }

        .tasks-container {
            padding: 20px;
        }

        .task-item {
            background: white;
            margin-bottom: 10px;
            padding: 15px;
            border-radius: 8px;
            border-left: 5px solid #667eea;
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .task-checkbox {
            width: 20px;
            height: 20px;
            cursor: pointer;
        }

        .task-text {
            flex: 1;
            font-size: 16px;
        }

        .task-completed {
            text-decoration: line-through;
            color: #888;
        }

        .priority-badge {
            padding: 4px 8px;
            border-radius: 12px;
            font-size: 12px;
            font-weight: bold;
        }

        .priority-high {
            background: #ffe3e3;
            color: #c92a2a;
        }

        .priority-medium {
            background: #fff3cd;
            color: #856404;
        }

        .priority-low {
            background: #d4edda;
            color: #155724;
        }

        .task-actions {
            display: flex;
            gap: 8px;
        }

        .task-btn {
            padding: 6px 10px;
            border: none;
            border-radius: 4px;
            font-size: 12px;
            cursor: pointer;
        }

        .edit-btn {
            background: #17a2b8;
            color: white;
        }

        .delete-btn {
            background: #dc3545;
            color: white;
        }

        .filters {
            padding: 20px;
            background: #f8f9fa;
        }

        .filter-buttons {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
        }

        .filter-btn {
            padding: 8px 16px;
            border: 2px solid #667eea;
            background: transparent;
            color: #667eea;
            border-radius: 20px;
            font-size: 14px;
            cursor: pointer;
        }

        .filter-btn.active {
            background: #667eea;
            color: white;
        }

        .stats {
            background: rgba(255,255,255,0.1);
            padding: 15px;
            margin: 15px 0;
            border-radius: 10px;
            text-align: center;
        }

        .stat-item {
            margin: 0 15px;
            display: inline-block;
        }

        .stat-number {
            font-size: 20px;
            font-weight: bold;
        }

        /* Modal düzenleme */
        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
        }

        .modal-content {
            background-color: white;
            margin: 15% auto;
            padding: 20px;
            border-radius: 10px;
            width: 90%;
            max-width: 500px;
        }

        .modal-header {
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 15px;
            color: #2c3e50;
        }

        .modal-input {
            width: 100%;
            padding: 10px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            margin-bottom: 15px;
        }

        .modal-buttons {
            display: flex;
            gap: 10px;
        }

        .modal-btn {
            flex: 1;
            padding: 10px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            cursor: pointer;
        }

        .modal-btn-primary {
            background: #667eea;
            color: white;
        }

        .modal-btn-secondary {
            background: #6c757d;
            color: white;
        }

        @media (max-width: 600px) {
            .input-group {
                flex-direction: column;
            }

            .action-buttons {
                flex-direction: column;
            }

            .filter-buttons {
                justify-content: center;
            }

            .modal-content {
                margin: 30% auto;
                padding: 15px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>📋 MELİH TO-DO</h1>
            <div class="creator">Yapımcı: Melih Can Çiğdem</div>
            <div class="stats">
                <div class="stat-item">
                    <span class="stat-number" id="total-count">0</span>
                    <span>Toplam</span>
                </div>
                <div class="stat-item">
                    <span class="stat-number" id="completed-count">0</span>
                    <span>Tamamlanan</span>
                </div>
                <div class="stat-item">
                    <span class="stat-number" id="pending-count">0</span>
                    <span>Bekleyen</span>
                </div>
            </div>
        </div>

        <div class="add-task">
            <div class="input-group">
                <select id="priority-select" class="priority-select">
                    <option value="Yüksek">🔴 Yüksek</option>
                    <option value="Orta" selected>🟡 Orta</option>
                    <option value="Düşük">🟢 Düşük</option>
                </select>
                <input type="text" id="task-input" class="task-input" placeholder="Yeni görev ekleyin..." onkeypress="handleKeyPress(event)">
                <button onclick="addTask()" class="add-btn">➕ EKLE</button>
            </div>
        </div>

        <div class="actions">
            <div class="action-buttons">
                <button class="action-btn complete-all" onclick="completeAllTasks()">
                    ✓ TÜMÜNÜ TAMAMLA
                </button>
                <button class="action-btn clear-completed" onclick="clearCompletedTasks()">
                    🧹 TEMİZLE
                </button>
                <button class="action-btn sort-tasks" onclick="sortTasks()">
                    🔄 SIRALA
                </button>
            </div>
        </div>

        <div class="filters">
            <div class="filter-buttons">
                <button class="filter-btn active" onclick="setFilter('all')">Tümü</button>
                <button class="filter-btn" onclick="setFilter('high')">Yüksek Öncelik</button>
                <button class="filter-btn" onclick="setFilter('medium')">Orta Öncelik</button>
                <button class="filter-btn" onclick="setFilter('low')">Düşük Öncelik</button>
                <button class="filter-btn" onclick="setFilter('completed')">Tamamlanan</button>
                <button class="filter-btn" onclick="setFilter('pending')">Bekleyen</button>
            </div>
        </div>

        <div class="tasks-container">
            <div id="tasks-list">
                <!-- Görevler buraya eklenecek -->
            </div>
        </div>
    </div>

    <!-- Düzenleme Modal'ı -->
    <div id="editModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">✏️ Görev Düzenle</div>
            <input type="text" id="edit-input" class="modal-input" placeholder="Görev metni...">
            <select id="edit-priority" class="modal-input" style="margin-bottom: 15px;">
                <option value="Yüksek">🔴 Yüksek</option>
                <option value="Orta">🟡 Orta</option>
                <option value="Düşük">🟢 Düşük</option>
            </select>
            <div class="modal-buttons">
                <button class="modal-btn modal-btn-primary" onclick="saveEdit()">💾 Kaydet</button>
                <button class="modal-btn modal-btn-secondary" onclick="closeEditModal()">❌ İptal</button>
            </div>
        </div>
    </div>

    <script>
        // Veri yönetimi
        let tasks = [];
        let currentFilter = 'all';
        let editingTaskId = null;

        // Sayfa yüklendiğinde
        window.onload = function() {
            loadTasks();
            renderTasks();
            updateStats();
        };

        // LocalStorage'dan görevleri yükle
        function loadTasks() {
            try {
                const saved = localStorage.getItem('melih_html_todo_tasks');
                if (saved) {
                    tasks = JSON.parse(saved);
                }
            } catch (e) {
                console.error('Görevler yüklenemedi:', e);
                tasks = [];
            }
        }

        // Görevleri kaydet
        function saveTasks() {
            try {
                localStorage.setItem('melih_html_todo_tasks', JSON.stringify(tasks));
            } catch (e) {
                console.error('Görevler kaydedilemedi:', e);
            }
        }

        // Görev ekle
        function addTask() {
            const input = document.getElementById('task-input');
            const prioritySelect = document.getElementById('priority-select');

            const taskText = input.value.trim();
            const priority = prioritySelect.value;

            if (taskText) {
                const newTask = {
                    id: Date.now().toString(),
                    text: taskText,
                    completed: false,
                    priority: priority,
                    created: new Date().toISOString()
                };

                tasks.push(newTask);
                saveTasks();
                renderTasks();
                updateStats();

                // Input'u temizle
                input.value = '';

                // Başarı mesajı
                alert('✅ Görev eklendi!');
            }
        }

        // Enter tuşu ile görev ekleme
        function handleKeyPress(event) {
            if (event.key === 'Enter') {
                addTask();
            }
        }

        // Tüm görevleri tamamla
        function completeAllTasks() {
            tasks.forEach(task => task.completed = true);
            saveTasks();
            renderTasks();
            updateStats();
            alert('✅ Tüm görevler tamamlandı!');
        }

        // Tamamlanan görevleri temizle
        function clearCompletedTasks() {
            const completedCount = tasks.filter(task => task.completed).length;
            if (completedCount > 0) {
                tasks = tasks.filter(task => !task.completed);
                saveTasks();
                renderTasks();
                updateStats();
                alert(`🧹 ${completedCount} görev temizlendi!`);
            }
        }

        // Görevleri sırala
        function sortTasks() {
            const priorityOrder = { 'Yüksek': 3, 'Orta': 2, 'Düşük': 1 };

            tasks.sort((a, b) => {
                // Tamamlanmamış görevler önce
                if (a.completed !== b.completed) {
                    return a.completed ? 1 : -1;
                }
                // Öncelik sırası
                return priorityOrder[b.priority] - priorityOrder[a.priority];
            });

            saveTasks();
            renderTasks();
            alert('🔄 Görevler sıralandı!');
        }

        // Görevi tamamla/tamamlanmamış yap
        function toggleTask(taskId) {
            const task = tasks.find(t => t.id === taskId);
            if (task) {
                task.completed = !task.completed;
                saveTasks();
                renderTasks();
                updateStats();
            }
        }

        // Görevi sil
        function deleteTask(taskId) {
            if (confirm('Bu görevi silmek istediğinizden emin misiniz?')) {
                tasks = tasks.filter(task => task.id !== taskId);
                saveTasks();
                renderTasks();
                updateStats();
            }
        }

        // Görevi düzenle - Modal aç
        function editTask(taskId) {
            const task = tasks.find(t => t.id === taskId);
            if (task) {
                editingTaskId = taskId;
                document.getElementById('edit-input').value = task.text;
                document.getElementById('edit-priority').value = task.priority;
                document.getElementById('editModal').style.display = 'block';
            }
        }

        // Düzenlemeyi kaydet
        function saveEdit() {
            if (editingTaskId) {
                const newText = document.getElementById('edit-input').value.trim();
                const newPriority = document.getElementById('edit-priority').value;

                if (newText) {
                    const task = tasks.find(t => t.id === editingTaskId);
                    if (task) {
                        task.text = newText;
                        task.priority = newPriority;
                        saveTasks();
                        renderTasks();
                        updateStats();
                        closeEditModal();
                        alert('✏️ Görev güncellendi!');
                    }
                }
            }
        }

        // Modal'ı kapat
        function closeEditModal() {
            document.getElementById('editModal').style.display = 'none';
            editingTaskId = null;
        }

        // Modal dışına tıklandığında kapat
        window.onclick = function(event) {
            const modal = document.getElementById('editModal');
            if (event.target === modal) {
                closeEditModal();
            }
        }

        // Filtreleme
        function setFilter(filterType) {
            currentFilter = filterType;

            // Aktif butonu işaretle
            document.querySelectorAll('.filter-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');

            renderTasks();
        }

        // Görevleri göster
        function renderTasks() {
            const container = document.getElementById('tasks-list');

            // Filtreleme uygula
            let filteredTasks = tasks;

            switch(currentFilter) {
                case 'high':
                    filteredTasks = tasks.filter(task => task.priority === 'Yüksek');
                    break;
                case 'medium':
                    filteredTasks = tasks.filter(task => task.priority === 'Orta');
                    break;
                case 'low':
                    filteredTasks = tasks.filter(task => task.priority === 'Düşük');
                    break;
                case 'completed':
                    filteredTasks = tasks.filter(task => task.completed);
                    break;
                case 'pending':
                    filteredTasks = tasks.filter(task => !task.completed);
                    break;
            }

            // Öncelik sırasına göre sırala
            const priorityOrder = { 'Yüksek': 3, 'Orta': 2, 'Düşük': 1 };
            filteredTasks.sort((a, b) => {
                if (a.completed !== b.completed) {
                    return a.completed ? 1 : -1;
                }
                return priorityOrder[b.priority] - priorityOrder[a.priority];
            });

            // HTML oluştur
            container.innerHTML = '';

            if (filteredTasks.length === 0) {
                container.innerHTML = '<p style="text-align: center; color: #666; padding: 20px;">Henüz görev yok</p>';
                return;
            }

            filteredTasks.forEach(task => {
                const taskElement = document.createElement('div');
                taskElement.className = 'task-item';

                const priorityClass = `priority-${task.priority.toLowerCase()}`;

                taskElement.innerHTML = `
                    <input type="checkbox" class="task-checkbox" ${task.completed ? 'checked' : ''}
                           onchange="toggleTask('${task.id}')">

                    <div class="task-text ${task.completed ? 'task-completed' : ''}">
                        ${task.text}
                    </div>

                    <span class="priority-badge ${priorityClass}">
                        ${task.priority}
                    </span>

                    <div class="task-actions">
                        <button class="task-btn edit-btn" onclick="editTask('${task.id}')">
                            ✏️
                        </button>
                        <button class="task-btn delete-btn" onclick="deleteTask('${task.id}')">
                            🗑️
                        </button>
                    </div>
                `;

                container.appendChild(taskElement);
            });
        }

        // İstatistikleri güncelle
        function updateStats() {
            const total = tasks.length;
            const completed = tasks.filter(task => task.completed).length;
            const pending = total - completed;

            document.getElementById('total-count').textContent = total;
            document.getElementById('completed-count').textContent = completed;
            document.getElementById('pending-count').textContent = pending;
        }
    </script>
</body>
</html>
