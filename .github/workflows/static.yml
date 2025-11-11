<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Медицинский АРМ - Динамический прототип</title>
    <style>
        :root {
            --primary: #2C5AA0;
            --primary-light: #3A6BC2;
            --primary-dark: #1E3D6F;
            --success: #28A745;
            --warning: #FFC107;
            --error: #D93025;
            --background: #FFFFFF;
            --surface: #F8F9FA;
            --outline: #E9ECEF;
            --text-primary: #1A1A1A;
            --text-secondary: #666666;
            --border-radius: 8px;
            --shadow: 0 4px 12px rgba(0,0,0,0.1);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Arial, sans-serif;
        }
        
        body {
            background: #f5f6fa;
            color: var(--text-primary);
            line-height: 1.5;
        }
        
        .app-container {
            display: grid;
            grid-template-columns: 250px 1fr;
            min-height: 100vh;
            max-width: 1400px;
            margin: 0 auto;
            background: white;
            box-shadow: 0 0 20px rgba(0,0,0,0.1);
        }
        
        /* Навигационная панель */
        .sidebar {
            background: var(--primary-dark);
            color: white;
            padding: 20px 0;
        }
        
        .sidebar-header {
            padding: 0 20px 20px;
            border-bottom: 1px solid rgba(255,255,255,0.1);
            margin-bottom: 20px;
        }
        
        .nav-item {
            padding: 12px 20px;
            display: flex;
            align-items: center;
            gap: 12px;
            cursor: pointer;
            transition: background 0.3s ease;
            color: rgba(255,255,255,0.9);
            text-decoration: none;
            font-size: 14px;
        }
        
        .nav-item:hover, .nav-item.active {
            background: rgba(255,255,255,0.1);
            color: white;
        }
        
        /* Основной контент */
        .main-content {
            display: flex;
            flex-direction: column;
        }
        
        .header {
            height: 60px;
            background: var(--background);
            border-bottom: 1px solid var(--outline);
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 30px;
        }
        
        .header-title {
            font-size: 20px;
            font-weight: 600;
            color: var(--primary);
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 14px;
        }
        
        .content-area {
            flex: 1;
            padding: 0;
            position: relative;
            overflow: hidden;
        }
        
        /* Общие стили для экранов */
        .screen {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            padding: 30px;
            background: var(--background);
            transition: transform 0.3s ease, opacity 0.3s ease;
            overflow-y: auto;
        }
        
        .screen.hidden {
            transform: translateX(100%);
            opacity: 0;
            pointer-events: none;
        }
        
        .screen.active {
            transform: translateX(0);
            opacity: 1;
        }
        
        /* Карточки и компоненты */
        .card {
            background: var(--background);
            border-radius: var(--border-radius);
            padding: 25px;
            box-shadow: var(--shadow);
            margin-bottom: 25px;
        }
        
        .card-header {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 20px;
            color: var(--primary);
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: var(--border-radius);
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }
        
        .btn-primary {
            background: var(--primary);
            color: white;
        }
        
        .btn-primary:hover {
            background: var(--primary-light);
        }
        
        .btn-secondary {
            background: var(--surface);
            color: var(--text-primary);
            border: 1px solid var(--outline);
        }
        
        /* Сетки */
        .grid-2 {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 25px;
        }
        
        .grid-3 {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
        }
        
        .grid-4 {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 20px;
        }
        
        /* Специфичные стили для экранов */
        .notification-item, .appointment-item {
            padding: 12px 0;
            border-bottom: 1px solid var(--outline);
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .notification-item:last-child, .appointment-item:last-child {
            border-bottom: none;
        }
        
        .notification-warning {
            color: var(--error);
            font-weight: 600;
        }
        
        .stat-item {
            text-align: center;
            padding: 20px;
            background: var(--surface);
            border-radius: var(--border-radius);
        }
        
        .stat-value {
            font-size: 32px;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 5px;
        }
        
        .stat-label {
            font-size: 14px;
            color: var(--text-secondary);
        }
        
        /* Стили для карточки пациента */
        .patient-container {
            display: grid;
            grid-template-columns: 300px 1fr;
            gap: 25px;
            height: 100%;
        }
        
        .patient-sidebar {
            background: var(--surface);
            border-radius: var(--border-radius);
            padding: 25px;
        }
        
        .patient-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
        }
        
        .patient-name {
            font-size: 20px;
            font-weight: 600;
            color: var(--primary);
        }
        
        .info-group {
            margin-bottom: 20px;
        }
        
        .info-label {
            font-size: 13px;
            color: var(--text-secondary);
            margin-bottom: 5px;
            font-weight: 500;
        }
        
        .info-value {
            font-size: 15px;
            color: var(--text-primary);
        }
        
        .tabs {
            display: flex;
            border-bottom: 1px solid var(--outline);
            margin-bottom: 25px;
        }
        
        .tab {
            padding: 12px 24px;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            transition: all 0.3s ease;
        }
        
        .tab.active {
            border-bottom-color: var(--primary);
            color: var(--primary);
            font-weight: 600;
        }
        
        /* Стили для модальных окон */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.5);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            padding: 20px;
        }
        
        .modal {
            background: var(--background);
            border-radius: var(--border-radius);
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            width: 800px;
            max-width: 90vw;
            max-height: 90vh;
            overflow: auto;
        }
        
        .modal-header {
            height: 50px;
            background: var(--primary);
            color: white;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 25px;
            font-size: 16px;
            font-weight: 600;
        }
        
        .modal-content {
            padding: 25px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: var(--text-primary);
            font-size: 14px;
        }
        
        .form-input, .form-textarea {
            width: 100%;
            padding: 10px 12px;
            border: 1px solid var(--outline);
            border-radius: var(--border-radius);
            font-size: 14px;
            font-family: inherit;
        }
        
        .form-textarea {
            min-height: 80px;
            resize: vertical;
        }
        
        .form-input:focus, .form-textarea:focus {
            outline: none;
            border-color: var(--primary);
        }
        
        .prescription-item {
            display: flex;
            align-items: flex-start;
            gap: 10px;
            padding: 10px 0;
            border-bottom: 1px solid var(--outline);
        }
        
        .prescription-item:last-child {
            border-bottom: none;
        }
        
        /* Расписание */
        .calendar-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .calendar-nav {
            display: flex;
            gap: 10px;
            align-items: center;
        }
        
        .week-days {
            display: grid;
            grid-template-columns: 100px repeat(7, 1fr);
            gap: 10px;
            margin-bottom: 15px;
            font-weight: 600;
            color: var(--text-primary);
        }
        
        .time-slots {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        
        .time-slot {
            display: grid;
            grid-template-columns: 100px repeat(7, 1fr);
            gap: 10px;
            align-items: center;
        }
        
        .time-label {
            font-weight: 600;
            color: var(--text-primary);
        }
        
        .appointment-slot {
            background: var(--primary);
            color: white;
            padding: 10px;
            border-radius: var(--border-radius);
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .appointment-slot:hover {
            background: var(--primary-light);
        }
        
        .appointment-slot.free {
            background: var(--surface);
            color: var(--text-secondary);
            border: 1px dashed var(--outline);
        }
        
        .appointment-info {
            font-size: 13px;
        }
        
        .patient-name-small {
            font-weight: 600;
            margin-bottom: 2px;
        }
    </style>
</head>
<body>
    <div class="app-container">
        <!-- Навигационная панель -->
        <div class="sidebar">
            <div class="sidebar-header">
                <h2 style="color: white; margin-bottom: 10px;">🏥 АРМ Врача</h2>
                <div style="color: rgba(255,255,255,0.8); font-size: 14px;">👤 Врач Петрова</div>
            </div>
            
            <div class="nav-item active" onclick="showScreen('main')">📊 Главная</div>
            <div class="nav-item" onclick="showScreen('patients')">👥 Пациенты</div>
            <div class="nav-item" onclick="showScreen('schedule')">📅 Расписание</div>
            <div class="nav-item">📋 Назначения</div>
            <div class="nav-item">📄 Документы</div>
            <div class="nav-item">📈 Отчетность</div>
            <div class="nav-item">⚙️ Настройки</div>
        </div>
        
        <!-- Основной контент -->
        <div class="main-content">
            <div class="header">
                <div class="header-title" id="headerTitle">Главная панель</div>
                <div class="user-info">
                    <span id="currentDate">15 декабря 2024</span>
                    <span>•</span>
                    <span>10:30</span>
                </div>
            </div>
            
            <div class="content-area">
                <!-- Экран 1: Главная -->
                <div class="screen active" id="main">
                    <div class="grid-2">
                        <!-- Уведомления -->
                        <div class="card">
                            <div class="card-header">⚡ СРОЧНЫЕ УВЕДОМЛЕНИЯ</div>
                            <div class="notification-item notification-warning">
                                <span>•</span>
                                <span onclick="openPatientCard('Иванов А.П.')" style="cursor: pointer;">Пациент Иванов ожидает осмотра</span>
                            </div>
                            <div class="notification-item">
                                <span>•</span>
                                <span>Поступили новые анализы</span>
                            </div>
                            <div class="notification-item">
                                <span>•</span>
                                <span>Требуется продление больничного</span>
                            </div>
                        </div>
                        
                        <!-- Приемы -->
                        <div class="card">
                            <div class="card-header">📅 СЕГОДНЯШНИЕ ПРИЕМЫ</div>
                            <div class="appointment-item">
                                <span>10:00</span>
                                <span>-</span>
                                <span onclick="openPatientCard('Иванов А.П.')" style="cursor: pointer;">Иванов А.П. (первичный)</span>
                            </div>
                            <div class="appointment-item">
                                <span>11:30</span>
                                <span>-</span>
                                <span onclick="openPatientCard('Петрова М.С.')" style="cursor: pointer;">Петрова М.S. (повторный)</span>
                            </div>
                            <div class="appointment-item">
                                <span>14:00</span>
                                <span>-</span>
                                <span onclick="openPatientCard('Сидоров В.И.')" style="cursor: pointer;">Сидоров В.И. (консультация)</span>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Статистика -->
                    <div class="card">
                        <div class="card-header">📊 СТАТИСТИКА ЗА ДЕНЬ</div>
                        <div class="grid-4">
                            <div class="stat-item">
                                <div class="stat-value">8/12</div>
                                <div class="stat-label">Принято пациентов</div>
                            </div>
                            <div class="stat-item">
                                <div class="stat-value">2</div>
                                <div class="stat-label">Оформлено больничных</div>
                            </div>
                            <div class="stat-item">
                                <div class="stat-value">5</div>
                                <div class="stat-label">Назначено исследований</div>
                            </div>
                            <div class="stat-item">
                                <div class="stat-value">87%</div>
                                <div class="stat-label">Заполнение расписания</div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="card">
                        <button class="btn btn-primary" onclick="showScreen('patients')">
                            👥 Перейти к списку пациентов
                        </button>
                        <button class="btn btn-secondary" onclick="showScreen('schedule')">
                            📅 Посмотреть расписание
                        </button>
                    </div>
                </div>
                
                <!-- Экран 2: Карточка пациента -->
                <div class="screen hidden" id="patients">
                    <div class="patient-container">
                        <div class="patient-sidebar">
                            <div class="patient-header">
                                <div class="patient-name">👤 ИВАНОВ АЛЕКСЕЙ ПЕТРОВИЧ</div>
                                <button class="btn btn-secondary" onclick="showScreen('main')">Назад</button>
                            </div>
                            
                            <div class="info-group">
                                <div class="info-label">ФИО</div>
                                <div class="info-value">Иванов Алексей Петрович</div>
                            </div>
                            
                            <div class="info-group">
                                <div class="info-label">Пол</div>
                                <div class="info-value">Мужской</div>
                            </div>
                            
                            <div class="info-group">
                                <div class="info-label">Возраст</div>
                                <div class="info-value">45 лет (12.03.1979)</div>
                            </div>
                            
                            <div class="info-group">
                                <div class="info-label">Телефон</div>
                                <div class="info-value">+7 (912) 345-67-89</div>
                            </div>
                            
                            <div class="info-group">
                                <div class="info-label">Аллергии</div>
                                <div class="info-value" style="color: var(--error);">Пенициллин, аспирин</div>
                            </div>
                            
                            <div class="info-group">
                                <div class="info-label">Группа крови</div>
                                <div class="info-value" style="color: var(--primary); font-weight: 600;">A(II) Rh+</div>
                            </div>
                            
                            <button class="btn btn-primary" style="width: 100%; margin-top: 20px;" onclick="startExamination()">
                                🩺 Начать осмотр
                            </button>
                        </div>
                        
                        <div>
                            <div class="tabs">
                                <div class="tab active">Общие данные</div>
                                <div class="tab">Анамнез</div>
                                <div class="tab">Назначения</div>
                                <div class="tab">Результаты</div>
                                <div class="tab">Документы</div>
                            </div>
                            
                            <div class="card">
                                <h3 style="margin-bottom: 15px;">История обращений</h3>
                                <div class="appointment-item">
                                    <span>10.12.2024</span>
                                    <span>-</span>
                                    <span>ОРВИ, J06.9</span>
                                </div>
                                <div class="appointment-item">
                                    <span>15.11.2024</span>
                                    <span>-</span>
                                    <span>Консультация, гипертония</span>
                                </div>
                                <div class="appointment-item">
                                    <span>20.09.2024</span>
                                    <span>-</span>
                                    <span>Диспансеризация</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Экран 3: Расписание -->
                <div class="screen hidden" id="schedule">
                    <div class="card">
                        <div class="calendar-header">
                            <div class="card-header">📅 РАСПИСАНИЕ | 15 ДЕКАБРЯ 2024</div>
                            <div class="calendar-nav">
                                <button class="btn btn-secondary">◀</button>
                                <button class="btn btn-secondary">Сегодня</button>
                                <button class="btn btn-secondary">▶</button>
                            </div>
                        </div>
                        
                        <div class="week-days">
                            <div>Время</div>
                            <div>ПН 16</div>
                            <div>ВТ 17</div>
                            <div>СР 18</div>
                            <div>ЧТ 19</div>
                            <div>ПТ 20</div>
                            <div>СБ 21</div>
                            <div>ВС 22</div>
                        </div>
                        
                        <div class="time-slots">
                            <div class="time-slot">
                                <div class="time-label">09:00</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                            </div>
                            
                            <div class="time-slot">
                                <div class="time-label">10:00</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot">
                                    <div class="appointment-info">
                                        <div class="patient-name-small">Иванов А.П.</div>
                                        <div>Первичный осмотр</div>
                                    </div>
                                </div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                            </div>
                            
                            <div class="time-slot">
                                <div class="time-label">11:00</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot">
                                    <div class="appointment-info">
                                        <div class="patient-name-small">Петрова М.С.</div>
                                        <div>Повторный прием</div>
                                    </div>
                                </div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                            </div>
                            
                            <div class="time-slot">
                                <div class="time-label">14:00</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot">
                                    <div class="appointment-info">
                                        <div class="patient-name-small">Сидоров В.И.</div>
                                        <div>Консультация</div>
                                    </div>
                                </div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                                <div class="appointment-slot free">Свободно</div>
                            </div>
                        </div>
                        
                        <div style="margin-top: 20px;">
                            <button class="btn btn-primary" onclick="showScreen('main')">
                                ← Назад на главную
                            </button>
                            <button class="btn btn-secondary" onclick="showScreen('patients')">
                                👥 К списку пациентов
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Модальное окно осмотра -->
    <div class="modal-overlay hidden" id="examinationModal">
        <div class="modal">
            <div class="modal-header">
                <span>🩺 ОСМОТР ПАЦИЕНТА: Иванов А.П.</span>
                <div>
                    <button class="btn btn-secondary" onclick="closeExamination()">× Закрыть</button>
                    <button class="btn btn-primary" onclick="saveExamination()">💾 Сохранить</button>
                </div>
            </div>
            
            <div class="modal-content">
                <div class="form-group">
                    <label class="form-label">ЖАЛОБЫ:</label>
                    <textarea class="form-textarea" placeholder="Введите жалобы пациента...">Кашель, температура 37.8°, общая слабость</textarea>
                </div>
                
                <div class="form-group">
                    <label class="form-label">ОБЪЕКТИВНЫЙ СТАТУС:</label>
                    <textarea class="form-textarea" placeholder="Объективные данные осмотра...">АД: 130/85, ЧД: 18, SatO2: 96%
Состояние удовлетворительное</textarea>
                </div>
                
                <div class="form-group">
                    <label class="form-label">ДИАГНОЗ:</label>
                    <input type="text" class="form-input" value="J06.9 Острая инфекция ВДП" placeholder="Код и название диагноза...">
                </div>
                
                <div class="form-group">
                    <label class="form-label">НАЗНАЧЕНИЯ:</label>
                    <div style="border: 1px solid var(--outline); border-radius: var(--border-radius); padding: 15px;">
                        <div class="prescription-item">
                            <input type="checkbox" checked>
                            <span>Парацетамол 500 мг × 3 раза × 5 дней</span>
                        </div>
                        <div class="prescription-item">
                            <input type="checkbox" checked>
                            <span>Ингаляции с физраствором</span>
                        </div>
                        <div class="prescription-item">
                            <input type="checkbox" checked>
                            <span>Постельный режим</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Текущий активный экран
        let currentScreen = 'main';
        
        // Функция переключения экранов
        function showScreen(screenId) {
            // Скрываем текущий экран
            document.getElementById(currentScreen).classList.add('hidden');
            document.getElementById(currentScreen).classList.remove('active');
            
            // Показываем новый экран
            document.getElementById(screenId).classList.remove('hidden');
            document.getElementById(screenId).classList.add('active');
            
            // Обновляем навигацию
            document.querySelectorAll('.nav-item').forEach(item => {
                item.classList.remove('active');
            });
            
            // Обновляем заголовок
            const titles = {
                'main': 'Главная панель',
                'patients': 'Карточка пациента',
                'schedule': 'Расписание врача'
            };
            
            document.getElementById('headerTitle').textContent = titles[screenId] || 'Медицинский АРМ';
            
            currentScreen = screenId;
        }
        
        // Функция открытия карточки пациента
        function openPatientCard(patientName) {
            // В реальном приложении здесь была бы загрузка данных пациента
            document.querySelector('.patient-name').innerHTML = `👤 ${patientName.toUpperCase()}`;
            showScreen('patients');
        }
        
        // Функция начала осмотра
        function startExamination() {
            document.getElementById('examinationModal').classList.remove('hidden');
        }
        
        // Функция закрытия осмотра
        function closeExamination() {
            document.getElementById('examinationModal').classList.add('hidden');
        }
        
        // Функция сохранения осмотра
        function saveExamination() {
            alert('Осмотр успешно сохранен!');
            closeExamination();
            showScreen('main');
        }
        
        // Обновление даты и времени
        function updateDateTime() {
            const now = new Date();
            const options = { day: 'numeric', month: 'long', year: 'numeric' };
            document.getElementById('currentDate').textContent = now.toLocaleDateString('ru-RU', options);
        }
        
        // Инициализация
        updateDateTime();
        
        // Обновляем время каждую минуту
        setInterval(updateDateTime, 60000);
    </script>
</body>
</html>
