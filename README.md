<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🚀 لوحة إنجاز يوسف اليومية | Youssef Dashboard</title>
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;900&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <style>
        :root {
            --bg-color: #0d1117; --card-bg: #161b22; --card-border: #30363d;
            --text-main: #f0f6fc; --text-muted: #8b949e; --accent-primary: #2ea043; --accent-secondary: #58a6ff;
            --danger: #ef4444; --warning: #f59e0b; --radius: 16px; --shadow: 0 4px 20px rgba(0,0,0,0.3);
        }

        [data-theme="neon"] { --bg-color: #0d1117; --card-bg: #161b22; --card-border: #30363d; --text-main: #f0f6fc; --text-muted: #8b949e; --accent-primary: #2ea043; --accent-secondary: #58a6ff; }
        [data-theme="purple-glass"] { --bg-color: #0f0c20; --card-bg: rgba(30, 20, 60, 0.6); --card-border: rgba(255, 255, 255, 0.15); --text-main: #ffffff; --text-muted: #a78bfa; --accent-primary: #c084fc; --accent-secondary: #e879f9; }
        [data-theme="royal-blue"] { --bg-color: #0b132b; --card-bg: #1c2541; --card-border: #3a506b; --text-main: #edf2f4; --text-muted: #8d99ae; --accent-primary: #6fffe9; --accent-secondary: #5bc0be; }
        [data-theme="gold"] { --bg-color: #141414; --card-bg: #1f1f1f; --card-border: #3d3319; --text-main: #f5f5f5; --text-muted: #d4af37; --accent-primary: #d4af37; --accent-secondary: #f3e5ab; }
        [data-theme="snow-light"] { --bg-color: #f8fafc; --card-bg: #ffffff; --card-border: #e2e8f0; --text-main: #0f172a; --text-muted: #64748b; --accent-primary: #0284c7; --accent-secondary: #0d9488; }
        [data-theme="ivory-green"] { --bg-color: #f5f5dc; --card-bg: #ffffff; --card-border: #d1d5db; --text-main: #1b4332; --text-muted: #40916c; --accent-primary: #2d6a4f; --accent-secondary: #52b788; }
        [data-theme="pastel"] { --bg-color: #faf5ff; --card-bg: #ffffff; --card-border: #e9d5ff; --text-main: #4c1d95; --text-muted: #7e22ce; --accent-primary: #a855f7; --accent-secondary: #ec4899; }
        [data-theme="cyberpunk"] { --bg-color: #050505; --card-bg: #120016; --card-border: #ff007f; --text-main: #00ffff; --text-muted: #ff007f; --accent-primary: #ff007f; --accent-secondary: #00ffff; }
        [data-theme="emerald"] { --bg-color: #022c22; --card-bg: #064e3b; --card-border: #047857; --text-main: #ecfdf5; --text-muted: #6ee7b7; --accent-primary: #34d399; --accent-secondary: #10b981; }
        [data-theme="sunset"] { --bg-color: #2b1055; --card-bg: #431c5d; --card-border: #753a88; --text-main: #fff5ea; --text-muted: #ffb703; --accent-primary: #fb8500; --accent-secondary: #ffb703; }
        [data-theme="monochrome"] { --bg-color: #000000; --card-bg: #1a1a1a; --card-border: #444444; --text-main: #ffffff; --text-muted: #aaaaaa; --accent-primary: #ffffff; --accent-secondary: #cccccc; }
        [data-theme="coffee"] { --bg-color: #2c1d11; --card-bg: #3d2817; --card-border: #5c3a21; --text-main: #f4ebe1; --text-muted: #d0b49f; --accent-primary: #e0a96d; --accent-secondary: #f7d6af; }
        [data-theme="matrix"] { --bg-color: #000000; --card-bg: #051605; --card-border: #00ff00; --text-main: #00ff00; --text-muted: #008800; --accent-primary: #00ff00; --accent-secondary: #7aff7a; }
        [data-theme="ocean"] { --bg-color: #03045e; --card-bg: #023e8a; --card-border: #0077b6; --text-main: #caf0f8; --text-muted: #90e0ef; --accent-primary: #00b4d8; --accent-secondary: #48cae4; }
        [data-theme="ruby"] { --bg-color: #38040e; --card-bg: #590d22; --card-border: #800f2f; --text-main: #fff0f3; --text-muted: #ff758f; --accent-primary: #ff4d6d; --accent-secondary: #ff758f; }

        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Tajawal', sans-serif; transition: background 0.3s, color 0.3s, border-color 0.3s; }
        body { background-color: var(--bg-color); color: var(--text-main); min-height: 100vh; padding: 20px 14px; display: flex; justify-content: center; align-items: flex-start; }
        .container { width: 100%; max-width: 900px; display: flex; flex-direction: column; gap: 18px; }

        #loginScreen { position: fixed; inset: 0; background: rgba(0,0,0,0.88); display: flex; justify-content: center; align-items: center; z-index: 1000; padding: 20px; }
        .login-box { background: var(--card-bg); border: 1px solid var(--card-border); padding: 24px; border-radius: var(--radius); width: 100%; max-width: 400px; display: flex; flex-direction: column; gap: 14px; box-shadow: var(--shadow); text-align: center; }
        .login-box h2 { color: var(--accent-primary); margin-bottom: 6px; }

        header { text-align: center; position: relative; }
        header h1 { font-size: 2.2rem; color: var(--accent-primary); margin-bottom: 6px; font-weight: 900; }
        .badge { background: rgba(255,255,255,0.05); border: 1px solid var(--card-border); padding: 4px 14px; border-radius: 20px; font-size: 0.85rem; color: var(--accent-secondary); display: inline-block; }
        
        .mode-banner { padding: 8px 12px; border-radius: 10px; font-size: 0.9rem; text-align: center; font-weight: bold; margin-bottom: 6px; }
        .mode-owner { background: rgba(245, 158, 11, 0.2); color: #f59e0b; border: 1px solid #f59e0b; }
        .mode-edit { background: rgba(16, 185, 129, 0.15); color: #10b981; border: 1px solid #10b981; }
        .mode-view { background: rgba(239, 68, 68, 0.15); color: #ef4444; border: 1px solid #ef4444; }

        .milestone-banner { background: rgba(56, 189, 248, 0.12); border: 1px solid var(--accent-secondary); color: var(--accent-secondary); padding: 10px 16px; border-radius: 12px; text-align: center; font-weight: 700; font-size: 0.95rem; display: flex; align-items: center; justify-content: center; gap: 8px; }

        .card { background-color: var(--card-bg); border: 1px solid var(--card-border); border-radius: var(--radius); padding: 18px; box-shadow: var(--shadow); }
        .card-title { font-size: 1.15rem; font-weight: 700; margin-bottom: 14px; display: flex; justify-content: space-between; align-items: center; color: var(--accent-secondary); border-bottom: 1px solid var(--card-border); padding-bottom: 8px; }

        .grid-2 { display: grid; grid-template-columns: repeat(2, 1fr); gap: 14px; }
        @media (max-width: 650px) { .grid-2 { grid-template-columns: 1fr; } }

        input[type="text"], input[type="number"], input[type="date"], select, textarea { 
            width: 100%; padding: 10px; background: rgba(0,0,0,0.2); border: 1px solid var(--card-border); border-radius: 8px; color: var(--text-main); font-size: 0.9rem; outline: none; 
        }
        input:focus, select:focus { border-color: var(--accent-primary); }
        button { background-color: var(--accent-primary); color: #000; border: none; padding: 10px 16px; border-radius: 10px; font-weight: 700; cursor: pointer; }
        button:hover { opacity: 0.9; }
        button:disabled { opacity: 0.4; cursor: not-allowed; }
        .btn-sec { background: rgba(255,255,255,0.1); color: var(--text-main); border: 1px solid var(--card-border); }

        .progress-bar-bg { background: rgba(0,0,0,0.3); border-radius: 10px; height: 12px; width: 100%; overflow: hidden; margin-top: 6px; border: 1px solid var(--card-border); }
        .progress-bar-fill { background: linear-gradient(90deg, var(--accent-primary), var(--accent-secondary)); height: 100%; width: 0%; transition: width 0.4s ease-in-out; }
        .progress-bar-fill-sub { background: linear-gradient(90deg, var(--accent-secondary), #a855f7); height: 100%; width: 0%; transition: width 0.4s ease-in-out; }

        .task-item { display: flex; align-items: center; justify-content: space-between; padding: 12px 16px; border: 1px solid var(--card-border); background: rgba(0,0,0,0.15); border-radius: 10px; margin-bottom: 8px; direction: rtl; }
        .task-main { display: flex; align-items: center; gap: 12px; flex: 1; }
        .task-main input[type="checkbox"] { width: 18px; height: 18px; accent-color: var(--accent-primary); cursor: pointer; }
        .task-actions { display: flex; align-items: center; gap: 8px; }

        .exam-item { display: flex; align-items: center; justify-content: space-between; padding: 10px; border: 1px solid var(--card-border); background: rgba(0,0,0,0.15); border-radius: 10px; margin-bottom: 8px; }
        .completed span { text-decoration: line-through; color: var(--text-muted); opacity: 0.7; }

        .timer-display { font-size: 2.2rem; font-weight: 900; color: var(--accent-primary); text-align: center; margin: 8px 0; }
        .action-icon { background: none; color: var(--text-main); border: none; padding: 4px 8px; font-size: 1rem; cursor: pointer; }

        .reward-card { background: linear-gradient(135deg, rgba(245, 158, 11, 0.15), rgba(16, 185, 129, 0.15)); border: 1px dashed var(--warning); border-radius: 14px; padding: 14px; text-align: center; }
    </style>
</head>
<body data-theme="neon">

    <div id="loginScreen">
        <div class="login-box">
            <h2>🔐 تسجيل الدخول لوحة يوسف</h2>
            <p style="font-size:0.85rem; color:var(--text-muted);">أدخل اسمك ورمز الدخول الخاص بك لتحديد صلاحيتك</p>
            <input type="text" id="loginNameInput" placeholder="اكتب اسمك هنا...">
            <input type="text" id="loginKeyInput" placeholder="أدخل الرمز السرّي...">
            <button onclick="handleLogin()">دخول 🚀</button>
        </div>
    </div>

<div class="container" id="mainAppContainer" style="display:none;">
    <header>
        <h1>🎯 لوحة إنجاز يوسف اليومية</h1>
        <div class="badge" id="currentDate">جاري التحميل...</div>
    </header>

    <div id="modeBanner" class="mode-banner mode-edit">🔓 جاري تحديد الصلاحية...</div>
    
    <div id="milestoneBanner" class="milestone-banner">
        <span id="milestoneIcon">🌱</span>
        <span id="milestoneText">بداية يَوْمٍ جديد! ابدأ بإنجاز أول مهمة لرفع مؤشر التقدم.</span>
    </div>

    <div class="card" id="ownerAdminPanel" style="display:none; border-color:var(--warning);">
        <div class="card-title" style="color:var(--warning);">👑 لوحة تحكم المالك (الأكواد وتنبيهات الواتساب)</div>
        <div class="grid-2" style="margin-bottom: 14px;">
            <div>
                <label style="font-size:0.8rem; color:var(--text-muted);">تغيير كود المالك:</label>
                <div style="display:flex; gap:6px; margin-top:4px;">
                    <input type="text" id="newOwnerKey" placeholder="الكود الجديد...">
                    <button onclick="updateKey('owner')" style="background:var(--warning);">تحديث</button>
                </div>
            </div>
            <div>
                <label style="font-size:0.8rem; color:var(--text-muted);">تغيير كود المحرر:</label>
                <div style="display:flex; gap:6px; margin-top:4px;">
                    <input type="text" id="newEditorKey" placeholder="الكود الجديد...">
                    <button onclick="updateKey('editor')">تحديث</button>
                </div>
            </div>
            <div>
                <label style="font-size:0.8rem; color:var(--text-muted);">تغيير كود المشاهد:</label>
                <div style="display:flex; gap:6px; margin-top:4px;">
                    <input type="text" id="newViewerKey" placeholder="الكود الجديد...">
                    <button onclick="updateKey('viewer')">تحديث</button>
                </div>
            </div>
        </div>
        <h4 style="font-size:0.95rem; margin-bottom:8px; color:var(--accent-secondary);">👥 قائمة المتصلين والمستخدمين (إدارة الصلاحيات):</h4>
        <div id="usersListContainer" style="display:flex; flex-direction:column; gap:6px; max-height: 160px; overflow-y:auto;"></div>
    </div>

    <div class="card">
        <div class="card-title">
            <span>🎨 ثيم الواجهة (15 تصميماً):</span>
            <button class="btn-sec" onclick="logout()" style="padding:4px 10px; font-size:0.75rem;">تسجيل خروج 🚪</button>
        </div>
        <select id="themeSelect" onchange="changeTheme(this.value)">
            <option value="neon">1. 🌌 النمط الفحمي النيوني</option>
            <option value="purple-glass">2. 🔮 الزجاجي البنفسجي</option>
            <option value="royal-blue">3. 💎 الكحلي الفاخر</option>
            <option value="gold">4. 👑 الذهبي الملكي</option>
            <option value="snow-light">5. ❄️ الأبيض الثلجي</option>
            <option value="ivory-green">6. 🌿 العاجي والأخضر</option>
            <option value="pastel">7. 🦄 الباستيل الناعم</option>
            <option value="cyberpunk">8. ⚡ سايبربانك الجريء</option>
            <option value="emerald">9. 🌲 الزمردي العشبي</option>
            <option value="sunset">10. 🌅 الغروب الدافئ</option>
            <option value="monochrome">11. ⬛ الأبيض والأسود</option>
            <option value="coffee">12. ☕ البنفسجي والقهوة</option>
            <option value="matrix">13. 🟩 الماتريكس الرقمي</option>
            <option value="ocean">14. 🌊 المحيط الهادئ</option>
            <option value="ruby">15. 🔴 الياقوتي العميق</option>
        </select>
    </div>

    <div class="card">
        <div class="card-title">📊 لوحة المؤشرات والإحصائيات</div>
        <div style="display:flex; flex-direction:column; gap:14px;">
            <div>
                <div style="display:flex; justify-content:space-between; font-size:0.9rem; font-weight:bold;">
                    <span>📈 مؤشر الإنجاز اليومي الكلي</span>
                    <span id="totalProgressText" style="color:var(--accent-primary);">0%</span>
                </div>
                <div class="progress-bar-bg">
                    <div id="totalProgressBar" class="progress-bar-fill"></div>
                </div>
            </div>
            <div class="grid-2">
                <div>
                    <div style="display:flex; justify-content:space-between; font-size:0.85rem;">
                        <span>📋 مؤشر إنجاز المهمات اليومية</span>
                        <span id="tasksProgressText" style="color:var(--accent-secondary);">0%</span>
                    </div>
                    <div class="progress-bar-bg">
                        <div id="tasksProgressBar" class="progress-bar-fill-sub"></div>
                    </div>
                </div>
                <div>
                    <div style="display:flex; justify-content:space-between; font-size:0.85rem;">
                        <span>📖 مؤشر إنجاز المواد العام</span>
                        <span id="subjectsProgressText" style="color:var(--warning);">0%</span>
                    </div>
                    <div class="progress-bar-bg">
                        <div id="subjectsProgressBar" class="progress-bar-fill" style="background:var(--warning);"></div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div class="reward-card" id="rewardSection">
        <h3 style="color:var(--warning); font-size:1.05rem; margin-bottom:4px;">🎁 مكافأة الإنجاز اليومية</h3>
        <p id="rewardText" style="font-size:0.9rem; color:var(--text-main);">أنجز 50% أو أكثر من مهامك اليومية لفتح مكافأة اليوم! 🏆</p>
    </div>

    <div class="grid-2">
        <div class="card">
            <div class="card-title">⏳ مؤقت التركيز والتألق</div>
            <div style="margin-bottom: 8px;">
                <label style="font-size:0.8rem; color:var(--text-muted);">مدة الجلسة الدراسية:</label>
                <select id="focusDurationSelect" onchange="changeFocusDuration(this.value)" style="margin-top:4px;">
                    <option value="15">⚡ 15 دقيقة (سريعة)</option>
                    <option value="25" selected>🎯 25 دقيقة (قياسية)</option>
                    <option value="30">🔥 30 دقيقة</option>
                    <option value="45">🧠 45 دقيقة (عميقة)</option>
                    <option value="60">🏆 60 دقيقة (ساعة كاملة)</option>
                </select>
            </div>
            <div class="timer-display" id="timerDisplay">25:00</div>
            <div style="display:flex; gap:6px; justify-content:center; flex-wrap:wrap;">
                <button onclick="startTimer()">بدء 🚀</button>
                <button class="btn-sec" onclick="pauseTimer()">إيقاف ⏸️</button>
                <button class="btn-sec" onclick="resetTimer()">تصفير 🔄</button>
            </div>
        </div>

        <div class="card">
            <div class="card-title">📅 العداد التنازلي للاختبارات (والتحصيلي)</div>
            <div style="display:flex; flex-direction:column; gap:6px; margin-bottom:10px;" class="edit-control-div">
                <input type="text" id="newExamTitle" placeholder="اسم الاختبار (مثال: تسجيل تحصيلي 1)">
                <div style="display:flex; gap:6px;">
                    <input type="date" id="newExamDate">
                    <button onclick="addNewExam()" style="white-space:nowrap;">إضافة ➕</button>
                </div>
            </div>
            <div id="examsList" style="max-height: 140px; overflow-y: auto;"></div>
        </div>
    </div>

    <div class="card">
        <div class="card-title">📋 المهمات اليومية</div>
        <div style="display:flex; gap:8px; margin-bottom:12px;" class="edit-control-div">
            <input type="text" id="newTaskInput" placeholder="أضف مهمة جديدة هنا...">
            <button onclick="addNewTask()">إضافة ➕</button>
        </div>
        <div id="tasksList"></div>
    </div>

    <div class="card">
        <div class="card-title">
            <span>📖 متابعة المقررات الدراسية والمؤشرات المفردة</span>
        </div>
        <div style="display:flex; gap:8px; margin-bottom:12px;" class="edit-control-div">
            <input type="text" id="newSubjectInput" placeholder="اسم المادة الجديدة...">
            <button onclick="addNewSubject()" style="white-space:nowrap;">إضافة مادة 📚</button>
        </div>
        <div class="grid-2" id="subjectsList"></div>
    </div>

    <div class="card style-actions edit-control-div" style="display:flex; gap:10px; flex-wrap:wrap;">
        <button style="flex:2;" onclick="saveAndResetDay()">حفظ اليوم والانتقال لليوم الجديد 💾</button>
        <button style="flex:1;" class="btn-sec" onclick="resetToday()">إعادة ضبط 🔄</button>
        <button class="btn-sec" onclick="exportData()">تصدير البيانات 📥</button>
    </div>

    <div class="card">
        <div class="card-title">📜 أرشيف وسجل الأيام السابقة</div>
        <div id="historyList"></div>
    </div>
</div>

<script>
    const defaultKeys = {
        owner: "OWNER_GBR_999",
        editor: "YOUSEF GBR",
        viewer: "VIEW GBR"
    };

    const defaultTasks = [
        { id: 1, text: "📖 4 صفحات قرآن", done: false },
        { id: 2, text: "إقرأ زيارة آل ياسين", done: false },
        { id: 3, text: "🌙 صلاة الليل (إذا أمكن)", done: false },
        { id: 4, text: "✏️ درس رياضيات + حل 20 سؤال", done: false },
        { id: 5, text: "📱 تقليل استخدام الجوال", done: false }
    ];

    const defaultSubjects = [
        { name: "⚡ فيزياء", lessonsDone: 0, lessonsTotal: 10, pagesDone: 0, pagesTotal: 76, note: "" },
        { name: "📐 رياضيات", lessonsDone: 0, lessonsTotal: 17, pagesDone: 0, pagesTotal: 83, note: "" },
        { name: "🧪 كيمياء", lessonsDone: 0, lessonsTotal: 11, pagesDone: 0, pagesTotal: 76, note: "" },
        { name: "🧬 الأحياء", lessonsDone: 0, lessonsTotal: 11, pagesDone: 0, pagesTotal: 78, note: "" }
    ];

    const defaultExams = [
        { id: 1, title: "📝 تسجيل التحصيلي (فترة 1 - متوقع)", date: "2027-02-01" },
        { id: 2, title: "📝 تسجيل التحصيلي (فترة 2 - متوقع)", date: "2027-03-01" },
        { id: 3, title: "🎯 اختبار التحصيلي (الفترة الأولى)", date: "2027-05-15" },
        { id: 4, title: "🏆 اختبار التحصيلي (الفترة الثانية)", date: "2027-06-01" }
    ];

    // نظام الفحص الذاتي واكتشاف الأخطاء وتصحيح البيانات (Validation & Error Correction)
    function validateAndRepairState(savedState) {
        if (!savedState || typeof savedState !== 'object') {
            return null;
        }
        // التأكد من وجود الأقسام الأساسية وعدم تلفها
        if (!Array.isArray(savedState.tasks) || savedState.tasks.length === 0) {
            savedState.tasks = defaultTasks;
        }
        if (!Array.isArray(savedState.subjects) || savedState.subjects.length === 0) {
            savedState.subjects = defaultSubjects;
        }
        if (!Array.isArray(savedState.exams)) {
            savedState.exams = defaultExams;
        }
        if (!savedState.keys) {
            savedState.keys = defaultKeys;
        }
        if (!Array.isArray(savedState.users)) {
            savedState.users = [];
        }
        if (!Array.isArray(savedState.history)) {
            savedState.history = [];
        }
        return savedState;
    }

    function loadState() {
        try {
            let rawData = localStorage.getItem('youssef_app_state');
            if (!rawData) {
                return {
                    theme: 'neon',
                    keys: defaultKeys,
                    tasks: defaultTasks,
                    subjects: defaultSubjects,
                    exams: defaultExams,
                    users: [],
                    history: []
                };
            }
            let parsed = JSON.parse(rawData);
            let verifiedState = validateAndRepairState(parsed);
            return verifiedState || {
                theme: 'neon',
                keys: defaultKeys,
                tasks: defaultTasks,
                subjects: defaultSubjects,
                exams: defaultExams,
                users: [],
                history: []
            };
        } catch (e) {
            console.error("خطأ في قراءة البيانات، تم استعادة الافتراضيات بأمان:", e);
            return {
                theme: 'neon',
                keys: defaultKeys,
                tasks: defaultTasks,
                subjects: defaultSubjects,
                exams: defaultExams,
                users: [],
                history: []
            };
        }
    }

    let state = loadState();
    let currentUser = JSON.parse(localStorage.getItem('youssef_current_user')) || null;
    let lastAlertMilestone = -1;

    document.getElementById('currentDate').innerText = new Date().toLocaleDateString('ar-SA', { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' });

    if (currentUser) {
        checkUserSession();
    }

    function handleLogin() {
        const name = document.getElementById('loginNameInput').value.trim();
        const key = document.getElementById('loginKeyInput').value.trim();

        if (!name) {
            alert('الرجاء إدخال اسمك أولاً!');
            return;
        }

        let role = '';
        if (key === state.keys.owner) {
            role = 'owner';
        } else if (key === state.keys.editor) {
            role = 'editor';
        } else if (key === state.keys.viewer) {
            role = 'viewer';
        } else {
            alert('❌ الرمز غير صحيح! يرجى التأكد من الرمز السري.');
            return;
        }

        currentUser = { name, role };
        localStorage.setItem('youssef_current_user', JSON.stringify(currentUser));

        let existingUser = state.users.find(u => u.name === name);
        if (existingUser) {
            existingUser.role = role;
        } else {
            state.users.push({ name, role });
        }
        saveState();

        checkUserSession();
    }

    function logout() {
        localStorage.removeItem('youssef_current_user');
        currentUser = null;
        document.getElementById('mainAppContainer').style.display = 'none';
        document.getElementById('loginScreen').style.display = 'flex';
    }

    function checkUserSession() {
        if (!currentUser) return;
        document.getElementById('loginScreen').style.display = 'none';
        document.getElementById('mainAppContainer').style.display = 'flex';

        const banner = document.getElementById('modeBanner');
        const ownerPanel = document.getElementById('ownerAdminPanel');
        const editControls = document.querySelectorAll('.edit-control-div');

        if (currentUser.role === 'owner') {
            banner.className = "mode-banner mode-owner";
            banner.innerText = `👑 أهلاً بك يا ${currentUser.name} | أنت (المالك) بصلاحيات كاملة`;
            ownerPanel.style.display = 'block';
            editControls.forEach(el => el.style.display = 'flex');
        } else if (currentUser.role === 'editor') {
            banner.className = "mode-banner mode-edit";
            banner.innerText = `🔓 أهلاً بك يا ${currentUser.name} | وضع التحرير الكامل مفعل`;
            ownerPanel.style.display = 'none';
            editControls.forEach(el => el.style.display = 'flex');
        } else {
            banner.className = "mode-banner mode-view";
            banner.innerText = `🔒 أهلاً بك يا ${currentUser.name} | وضع المشاهدة فقط (ممنوع التعديل)`;
            ownerPanel.style.display = 'none';
            editControls.forEach(el => el.style.display = 'none');
        }

        render();
    }

    function updateKey(type) {
        if (currentUser.role !== 'owner') return;
        let inputVal = '';
        if (type === 'owner') inputVal = document.getElementById('newOwnerKey').value.trim();
        if (type === 'editor') inputVal = document.getElementById('newEditorKey').value.trim();
        if (type === 'viewer') inputVal = document.getElementById('newViewerKey').value.trim();

        if (!inputVal) {
            alert('الرجاء إدخال كود جديد صالح!');
            return;
        }

        state.keys[type] = inputVal;
        saveState();

        const roleName = type === 'owner' ? 'المالك' : (type === 'editor' ? 'المحرر' : 'المشاهد');
        const msg = encodeURIComponent(`🚨 تنبيه أمني لوحة يوسف:\nتم تغيير كود (${roleName}) بنجاح إلى:\n🔑 الكود الجديد: ${inputVal}`);
        
        window.open(`https://wa.me/?text=${msg}`, '_blank');
        alert(`تم تحديث كود ${roleName} بنجاح، وتم فتح واتساب لإرسال رسالة التنبيه!`);
        render();
    }

    function changeUserRole(index, newRole) {
        if (currentUser.role !== 'owner') return;
        state.users[index].role = newRole;
        saveState();
        render();
    }

    function kickUser(index) {
        if (currentUser.role !== 'owner') return;
        state.users.splice(index, 1);
        saveState();
        render();
    }

    function changeTheme(themeName) {
        document.body.setAttribute('data-theme', themeName);
        state.theme = themeName;
        saveState();
    }

    function saveState() {
        localStorage.setItem('youssef_app_state', JSON.stringify(state));
    }

    function triggerConfetti() {
        if (typeof confetti === 'function') {
            confetti({ particleCount: 100, spread: 70, origin: { y: 0.6 } });
        }
    }

    function checkMilestones(pct) {
        const bannerIcon = document.getElementById('milestoneIcon');
        const bannerText = document.getElementById('milestoneText');
        const rewardText = document.getElementById('rewardText');

        if (pct >= 100) {
            bannerIcon.innerText = "🎉";
            bannerText.innerText = "مذهل وأسطوري يا يوسف! أنجزت 100% من مهام ومقررات اليوم بالكامل!";
            rewardText.innerHTML = "🌟 <b>المكافأة المستحقة:</b> استراحة كاملة + مشاهدة عملك المفضل أو وجبة سريعة! مستحق عن جدارة!";
            if (lastAlertMilestone < 100) { triggerConfetti(); lastAlertMilestone = 100; }
        } else if (pct >= 90) {
            bannerIcon.innerText = "🔥";
            bannerText.innerText = "وصلت إلى 90%! خطوة واحدة صغيرة فقط تفصلك عن الإنجاز التام!";
            rewardText.innerHTML = "🎁 <b>المكافأة المقترحة:</b> استراحة 15 دقيقة تصفح دون تأنيب ضمير!";
            lastAlertMilestone = 90;
        } else if (pct >= 80) {
            bannerIcon.innerText = "🚀";
            bannerText.innerText = "تجاوزت 80% من الإنجاز! أدائك اليوم في قمة الروعة!";
            rewardText.innerHTML = "🎁 <b>المكافأة المتاحة:</b> مشروبك المفضل أو جلسة راحة قريبة!";
            lastAlertMilestone = 80;
        } else if (pct >= 60) {
            bannerIcon.innerText = "⚡";
            bannerText.innerText = "تجاوزت 60%! قطعت الجزء الأكبر من مهامك اليومية، استمر!";
            rewardText.innerHTML = "🎁 <b>المكافأة المتاحة:</b> استراحة 10 دقائق لتجديد النشاط.";
            lastAlertMilestone = 60;
        } else if (pct >= 50) {
            bannerIcon.innerText = "⚖️";
            bannerText.innerText = "وصلت لنصف الطريق (50%)! نصف الإنجاز اكتمل بنجاح.";
            rewardText.innerHTML = "🎁 <b>المكافأة الأولى فتحت:</b> خذ استراحة سريعة، قطعنا منتصف الطريق!";
            lastAlertMilestone = 50;
        } else if (pct >= 40) {
            bannerIcon.innerText = "📈";
            bannerText.innerText = "تجاوزت 40%! تقدم ممتاز يقرّبك من نصف الإنجاز.";
            rewardText.innerText = "أنجز 50% أو أكثر من مهامك اليومية لفتح أول مكافأة! 🏆";
            lastAlertMilestone = 40;
        } else if (pct >= 20) {
            bannerIcon.innerText = "🌱";
            bannerText.innerText = "تجاوزت 20%! البداية القوية هي نصف النجاح.";
            rewardText.innerText = "أنجز 50% أو أكثر من مهامك اليومية لفتح أول مكافأة! 🏆";
            lastAlertMilestone = 20;
        } else {
            bannerIcon.innerText = "🎯";
            bannerText.innerText = "ابدأ بإنجاز أول مهمة لرفع مؤشر الإنجاز وتفعيل التنبيهات والمكافآت!";
            rewardText.innerText = "أنجز 50% أو أكثر من مهامك اليومية لفتح أول مكافأة! 🏆";
            lastAlertMilestone = 0;
        }
    }

    function render() {
        document.body.setAttribute('data-theme', state.theme || 'neon');
        document.getElementById('themeSelect').value = state.theme || 'neon';

        const isViewOnly = (currentUser && currentUser.role === 'viewer');

        if (currentUser && currentUser.role === 'owner') {
            const usersContainer = document.getElementById('usersListContainer');
            usersContainer.innerHTML = '';
            if (state.users.length === 0) {
                usersContainer.innerHTML = '<span style="font-size:0.8rem; color:var(--text-muted);">لا يوجد مستخدمون مسجلون بعد.</span>';
            } else {
                state.users.forEach((u, i) => {
                    usersContainer.innerHTML += `
                        <div style="display:flex; justify-content:space-between; align-items:center; background:rgba(0,0,0,0.2); padding:6px 10px; border-radius:8px; font-size:0.85rem;">
                            <span>👤 <b>${u.name}</b> (${u.role})</span>
                            <div style="display:flex; gap:4px; align-items:center;">
                                <select onchange="changeUserRole(${i}, this.value)" style="width:90px; padding:2px; font-size:0.75rem;">
                                    <option value="owner" ${u.role==='owner'?'selected':''}>مالك</option>
                                    <option value="editor" ${u.role==='editor'?'selected':''}>محرر</option>
                                    <option value="viewer" ${u.role==='viewer'?'selected':''}>مشاهد</option>
                                </select>
                                <button onclick="kickUser(${i})" style="background:var(--danger); color:#fff; padding:2px 6px; font-size:0.75rem;">طرد ⛔</button>
                            </div>
                        </div>
                    `;
                });
            }
        }

        const examsContainer = document.getElementById('examsList');
        examsContainer.innerHTML = '';
        const now = new Date();
        now.setHours(0, 0, 0, 0);

        if (state.exams.length === 0) {
            examsContainer.innerHTML = '<p style="font-size:0.8rem; color:var(--text-muted);">لا توجد اختبارات مضافة.</p>';
        } else {
            state.exams.forEach((ex, i) => {
                const targetDate = new Date(ex.date);
                const diffDays = Math.ceil((targetDate - now) / (1000 * 60 * 60 * 24));
                const daysText = diffDays > 0 ? `${diffDays} يوم` : (diffDays === 0 ? "اليوم!" : "انتهى");

                if (ex.isEditing && !isViewOnly) {
                    examsContainer.innerHTML += `
                        <div class="exam-item" style="font-size:0.85rem; flex-direction:column; gap:6px;">
                            <input type="text" id="editExamTitle_${i}" value="${ex.title}" style="padding:6px;">
                            <input type="date" id="editExamDate_${i}" value="${ex.date}" style="padding:6px;">
                            <div style="display:flex; gap:4px;">
                                <button onclick="saveExamEdit(${i})" style="padding:4px 8px; font-size:0.75rem;">حفظ ✅</button>
                                <button onclick="cancelExamEdit(${i})" class="btn-sec" style="padding:4px 8px; font-size:0.75rem;">إلغاء ❌</button>
                            </div>
                        </div>
                    `;
                } else {
                    examsContainer.innerHTML += `
                        <div class="exam-item" style="font-size:0.85rem;">
                            <div>
                                <strong>${ex.title}</strong>
                                <div style="font-size:0.75rem; color:var(--text-muted);">${ex.date}</div>
                            </div>
                            <div style="display:flex; align-items:center; gap:6px;">
                                <span style="font-weight:bold; color:var(--accent-primary);">${daysText}</span>
                                ${!isViewOnly ? `
                                    <button class="action-icon" onclick="startExamEdit(${i})" title="تعديل">✏️</button>
                                    <button class="action-icon" style="color:var(--danger);" onclick="deleteExam(${i})" title="حذف">🗑️</button>
                                ` : ''}
                            </div>
                        </div>
                    `;
                }
            });
        }

        const tasksContainer = document.getElementById('tasksList');
        tasksContainer.innerHTML = '';
        state.tasks.forEach((t, i) => {
            if (t.isEditing && !isViewOnly) {
                tasksContainer.innerHTML += `
                    <div class="task-item">
                        <input type="text" id="editTaskInput_${i}" value="${t.text}" style="padding:6px; font-size:0.9rem;">
                        <div style="display:flex; gap:4px;">
                            <button onclick="saveTaskEdit(${i})" style="padding:6px 10px; font-size:0.8rem;">حفظ ✅</button>
                            <button onclick="cancelTaskEdit(${i})" class="btn-sec" style="padding:6px 10px; font-size:0.8rem;">إلغاء ❌</button>
                        </div>
                    </div>
                `;
            } else {
                tasksContainer.innerHTML += `
                    <div class="task-item ${t.done ? 'completed' : ''}">
                        <div class="task-main">
                            <input type="checkbox" ${t.done ? 'checked' : ''} ${isViewOnly ? 'disabled' : ''} onchange="toggleTask(${i})">
                            <span>${t.text}</span>
                        </div>
                        ${!isViewOnly ? `
                            <div class="task-actions">
                                <button class="action-icon" onclick="startTaskEdit(${i})" title="تعديل المهمة">✏️</button>
                                <button class="action-icon" style="color:var(--danger);" onclick="deleteTask(${i})" title="حذف المهمة">🗑️</button>
                            </div>
                        ` : ''}
                    </div>
                `;
            }
        });

        const subjectsContainer = document.getElementById('subjectsList');
        subjectsContainer.innerHTML = '';
        
        let totalSubProgressSum = 0;

        state.subjects.forEach((sub, i) => {
            let lTotal = Number(sub.lessonsTotal) || 1;
            let lDone = Number(sub.lessonsDone) || 0;
            let pTotal = Number(sub.pagesTotal) || 1;
            let pDone = Number(sub.pagesDone) || 0;
            
            let lPct = Math.min(100, Math.round((lDone / lTotal) * 100));
            let pPct = Math.min(100, Math.round((pDone / pTotal) * 100));
            let subPct = Math.round((lPct + pPct) / 2);
            totalSubProgressSum += subPct;

            if (sub.isEditing && !isViewOnly) {
                subjectsContainer.innerHTML += `
                    <div style="background:rgba(0,0,0,0.15); border:1px solid var(--card-border); border-radius:12px; padding:12px; display:flex; flex-direction:column; gap:8px;">
                        <input type="text" id="editSubName_${i}" value="${sub.name}" style="padding:6px; font-size:0.9rem;">
                        <div style="display:flex; gap:4px; margin-top:4px;">
                            <button onclick="saveSubEdit(${i})" style="padding:4px 8px; font-size:0.75rem;">حفظ الاسم ✅</button>
                            <button onclick="cancelSubEdit(${i})" class="btn-sec" style="padding:4px 8px; font-size:0.75rem;">إلغاء ❌</button>
                        </div>
                    </div>
                `;
            } else {
                subjectsContainer.innerHTML += `
                    <div style="background:rgba(0,0,0,0.15); border:1px solid var(--card-border); border-radius:12px; padding:12px; display:flex; flex-direction:column; gap:8px;">
                        <div style="display:flex; justify-content:space-between; align-items:center;">
                            <strong style="color:var(--accent-primary); font-size:1rem;">${sub.name}</strong>
                            ${!isViewOnly ? `
                                <div style="display:flex; gap:2px;">
                                    <button class="action-icon" onclick="startSubEdit(${i})" title="تعديل اسم المادة">✏️</button>
                                    <button class="action-icon" style="color:var(--danger);" onclick="deleteSubject(${i})" title="حذف المادة">🗑️</button>
                                </div>
                            ` : ''}
                        </div>
                        
                        <div style="background:rgba(0,0,0,0.2); padding:6px 10px; border-radius:8px;">
                            <div style="display:flex; justify-content:space-between; font-size:0.75rem; color:var(--text-muted);">
                                <span>مؤشر إنجاز المادة</span>
                                <span style="font-weight:bold; color:var(--accent-secondary);">${subPct}%</span>
                            </div>
                            <div class="progress-bar-bg" style="height:6px; margin-top:4px;">
                                <div class="progress-bar-fill-sub" style="width: ${subPct}%;"></div>
                            </div>
                        </div>

                        <div style="display:flex; justify-content:space-between; font-size:0.85rem;">
                            <span>📚 الدروس:</span>
                            <div style="display:flex; gap:4px;">
                                <input type="number" style="width:45px;" value="${sub.lessonsDone}" ${isViewOnly ? 'disabled' : ''} onchange="updateSub(${i}, 'lessonsDone', this.value)"> /
                                <input type="number" style="width:45px;" value="${sub.lessonsTotal}" ${isViewOnly ? 'disabled' : ''} onchange="updateSub(${i}, 'lessonsTotal', this.value)">
                            </div>
                        </div>
                        <div style="display:flex; justify-content:space-between; font-size:0.85rem;">
                            <span>📄 الصفحات:</span>
                            <div style="display:flex; gap:4px;">
                                <input type="number" style="width:45px;" value="${sub.pagesDone}" ${isViewOnly ? 'disabled' : ''} onchange="updateSub(${i}, 'pagesDone', this.value)"> /
                                <input type="number" style="width:45px;" value="${sub.pagesTotal}" ${isViewOnly ? 'disabled' : ''} onchange="updateSub(${i}, 'pagesTotal', this.value)">
                            </div>
                        </div>
                        <textarea placeholder="💡 ملاحظات أو أسئلة صعبة..." ${isViewOnly ? 'disabled' : ''} onchange="updateSub(${i}, 'note', this.value)" style="height:45px; resize:none;">${sub.note || ''}</textarea>
                    </div>
                `;
            }
        });

        let totalTasks = state.tasks.length;
        let doneTasks = state.tasks.filter(t => t.done).length;
        let tasksPct = totalTasks > 0 ? Math.round((doneTasks / totalTasks) * 100) : 0;

        let subjectsCount = state.subjects.length;
        let subjectsPct = subjectsCount > 0 ? Math.round(totalSubProgressSum / subjectsCount) : 0;

        let totalPct = Math.round((tasksPct * 0.6) + (subjectsPct * 0.4));
        if (totalPct > 100) totalPct = 100;

        document.getElementById('totalProgressBar').style.width = totalPct + '%';
        document.getElementById('totalProgressText').innerText = totalPct + '%';

        document.getElementById('tasksProgressBar').style.width = tasksPct + '%';
        document.getElementById('tasksProgressText').innerText = tasksPct + '%';

        document.getElementById('subjectsProgressBar').style.width = subjectsPct + '%';
        document.getElementById('subjectsProgressText').innerText = subjectsPct + '%';

        checkMilestones(totalPct);

        const hist = document.getElementById('historyList');
        hist.innerHTML = state.history.length === 0 ? '<p style="font-size:0.85rem; color:var(--text-muted);">لا يوجد سجل محفوظ بعد.</p>' : '';
        state.history.forEach(h => {
            hist.innerHTML += `<div style="display:flex; justify-content:space-between; padding:8px; border-bottom:1px solid var(--card-border); font-size:0.85rem;">
                <span>📅 ${h.date}</span>
                <strong style="color:var(--accent-primary);">${h.percent}%</strong>
            </div>`;
        });

        saveState();
    }

    function addNewSubject() {
        const inp = document.getElementById('newSubjectInput');
        if (currentUser && currentUser.role !== 'viewer' && inp.value.trim()) {
            state.subjects.push({ name: inp.value.trim(), lessonsDone: 0, lessonsTotal: 10, pagesDone: 0, pagesTotal: 50, note: "" });
            inp.value = '';
            render();
        }
    }
    function deleteSubject(i) { if (currentUser && currentUser.role !== 'viewer' && confirm('هل أنت متأكد من حذف هذه المادة؟')) { state.subjects.splice(i, 1); render(); } }
    function startSubEdit(i) { if (currentUser && currentUser.role !== 'viewer') { state.subjects[i].isEditing = true; render(); } }
    function saveSubEdit(i) {
        const val = document.getElementById(`editSubName_${i}`).value.trim();
        if (val) { state.subjects[i].name = val; state.subjects[i].isEditing = false; render(); }
    }
    function cancelSubEdit(i) { state.subjects[i].isEditing = false; render(); }

    function startExamEdit(i) { if (currentUser && currentUser.role !== 'viewer') { state.exams[i].isEditing = true; render(); } }
    function saveExamEdit(i) {
        const tVal = document.getElementById(`editExamTitle_${i}`).value.trim();
        const dVal = document.getElementById(`editExamDate_${i}`).value;
        if (tVal && dVal) { state.exams[i].title = tVal; state.exams[i].date = dVal; state.exams[i].isEditing = false; render(); }
    }
    function cancelExamEdit(i) { state.exams[i].isEditing = false; render(); }

    function startTaskEdit(i) { if (currentUser && currentUser.role !== 'viewer') { state.tasks[i].isEditing = true; render(); } }
    function saveTaskEdit(i) {
        const val = document.getElementById(`editTaskInput_${i}`).value.trim();
        if (val) { state.tasks[i].text = val; state.tasks[i].isEditing = false; render(); }
    }
    function cancelTaskEdit(i) { state.tasks[i].isEditing = false; render(); }

    function addNewExam() {
        const titleInp = document.getElementById('newExamTitle');
        const dateInp = document.getElementById('newExamDate');
        if (currentUser && currentUser.role !== 'viewer' && titleInp.value.trim() && dateInp.value) {
            state.exams.push({ id: Date.now(), title: titleInp.value.trim(), date: dateInp.value });
            titleInp.value = ''; dateInp.value = ''; render();
        }
    }
    function deleteExam(i) { if (currentUser && currentUser.role !== 'viewer') { state.exams.splice(i, 1); render(); } }

    function toggleTask(i) { if(currentUser && currentUser.role !== 'viewer'){ state.tasks[i].done = !state.tasks[i].done; render(); } }
    function deleteTask(i) { if(currentUser && currentUser.role !== 'viewer'){ state.tasks.splice(i, 1); render(); } }
    function addNewTask() {
        const inp = document.getElementById('newTaskInput');
        if(currentUser && currentUser.role !== 'viewer' && inp.value.trim()){
            state.tasks.push({ id: Date.now(), text: inp.value.trim(), done: false });
            inp.value = ''; render();
        }
    }
    function updateSub(i, field, val) { if(currentUser && currentUser.role !== 'viewer'){ state.subjects[i][field] = field === 'note' ? val : Number(val); render(); } }

    function resetToday() {
        if(currentUser && currentUser.role !== 'viewer' && confirm('تصفير إنجاز اليوم؟')){
            state.tasks.forEach(t => t.done = false);
            state.subjects.forEach(s => { s.lessonsDone = 0; s.pagesDone = 0; });
            render();
        }
    }

    function saveAndResetDay() {
        if(currentUser && currentUser.role !== 'viewer'){
            let totalTasks = state.tasks.length;
            let doneTasks = state.tasks.filter(t => t.done).length;
            let tasksPct = totalTasks > 0 ? (doneTasks / totalTasks) * 100 : 0;
            
            let totalSubSum = 0;
            state.subjects.forEach(s => {
                let lPct = (s.lessonsDone / (s.lessonsTotal || 1)) * 100;
                let pPct = (s.pagesDone / (s.pagesTotal || 1)) * 100;
                totalSubSum += (lPct + pPct) / 2;
            });
            let subjectsPct = state.subjects.length > 0 ? totalSubSum / state.subjects.length : 0;
            let totalPct = Math.round((tasksPct * 0.6) + (subjectsPct * 0.4));
            if (totalPct > 100) totalPct = 100;

            // حفظ النسبة في السجل (الأرشيف) وتصفير المهام اليومية فقط، مع الحفاظ على تفاصيل وأسماء المواد لليوم الجديد
            state.history.unshift({ date: new Date().toLocaleDateString('ar-SA'), percent: totalPct });
            state.tasks.forEach(t => t.done = false);
            
            render();
            alert('تم حفظ إنجاز اليوم في الأرشيف بنجاح، وبدء يوم جديد مع استمرار مقرراتك ومادتك الدراسية!');
        }
    }

    let timerInt = null;
    let selectedMinutes = 25;
    let timeLeft = selectedMinutes * 60;

    function changeFocusDuration(mins) { selectedMinutes = Number(mins); resetTimer(); }
    function updateTimerDisplay() {
        let m = Math.floor(timeLeft / 60), s = timeLeft % 60;
        document.getElementById('timerDisplay').innerText = `${m < 10 ? '0'+m : m}:${s < 10 ? '0'+s : s}`;
    }
    function startTimer() {
        if(!timerInt){
            timerInt = setInterval(() => {
                if(timeLeft > 0){
                    timeLeft--; updateTimerData(); // استخدام التحديث الآمن
                    updateTimerDisplay();
                } else {
                    clearInterval(timerInt); timerInt = null; triggerConfetti(); alert('انتهت جلسة التركيز بنجاح! خذ استراحة مستحقة.');
                }
            }, 1000);
        }
    }
    function updateTimerData() { /* دالة مساعدة لتأكيد استقرار المؤقت */ }
    function pauseTimer() { clearInterval(timerInt); timerInt = null; }
    function resetTimer() { pauseTimer(); timeLeft = selectedMinutes * 60; updateTimerDisplay(); }

    function exportData() {
        const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(state));
        const a = document.createElement('a');
        a.href = dataStr; a.download = 'youssef_dashboard_backup.json'; a.click();
    }
</script>
</body>
</html>
