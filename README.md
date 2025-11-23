# New
<!DOCTYPE html>
<html lang="ar" dir="rtl">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>شطرنجي - تعلم الشطرنج من الصفر للاحتراف</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/chess.js/0.10.3/chess.min.js"></script>
    <style>
        :root {
            --primary-color: #2c3e50;
            --secondary-color: #3498db;
            --accent-color: #e74c3c;
            --light-color: #ecf0f1;
            --dark-color: #2c3e50;
            --success-color: #2ecc71;
            --warning-color: #f39c12;
            --border-radius: 8px;
            --box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            --transition: all 0.3s ease;
        }

        /* Reset and general styles */
        *,
        *::before,
        *::after {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f5f5f5;
            color: var(--dark-color);
            line-height: 1.6;
            overflow-x: hidden; /* Prevent horizontal scroll */
        }

        a {
            text-decoration: none;
            color: inherit; /* Inherit color from parent */
        }

        ul {
            list-style: none;
        }

        img {
            max-width: 100%;
            height: auto;
            display: block; /* Remove extra space below image */
        }

        /* Reusable components */
        .container {
            width: min(90%, 1200px); /* Use min to ensure responsiveness */
            margin-inline: auto; /* Use inline for LTR/RTL support */
            padding-inline: 15px;
        }

        .btn {
            padding: 0.5rem 1rem;
            border: none;
            border-radius: var(--border-radius);
            cursor: pointer;
            font-weight: 500;
            transition: var(--transition);
            display: inline-block; /* Make buttons consistent */
        }

        .btn-primary {
            background-color: var(--secondary-color);
            color: white;
        }

        .btn-primary:hover {
            background-color: #2980b9;
            transform: translateY(-2px);
        }

        .btn-outline {
            background-color: transparent;
            color: white;
            border: 1px solid white;
        }

        .btn-outline:hover {
            background-color: white;
            color: var(--primary-color);
        }

        .btn-success {
            background-color: var(--success-color);
            color: white;
        }

        .btn-warning {
            background-color: var(--warning-color);
            color: white;
        }

        .btn-danger {
            background-color: var(--accent-color);
            color: white;
        }

        .btn-large {
            padding: 0.75rem 1.5rem;
            font-size: 1.1rem;
        }

        /* Header */
        header {
            background-color: var(--primary-color);
            color: white;
            padding: 1rem 0;
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: var(--box-shadow);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            display: flex;
            align-items: center;
        }

        .logo i {
            margin-left: 0.625rem;
            color: var(--secondary-color);
        }

        nav ul {
            display: flex;
        }

        nav ul li {
            margin-right: 1.25rem;
        }

        nav ul li a {
            color: white;
            font-weight: 500;
            transition: var(--transition);
            padding: 0.3125rem 0.625rem;
            border-radius: var(--border-radius);
            display: block; /* Make links fill the li */
        }

        nav ul li a:hover {
            color: var(--secondary-color);
            background-color: rgba(255, 255, 255, 0.1);
        }

        .auth-buttons {
            display: flex;
            gap: 0.625rem;
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(135deg, var(--primary-color), #1a2530);
            color: white;
            padding: 4rem 0;
            text-align: center;
        }

        .hero-content h1 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        .hero-content p {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            max-width: 700px;
            margin-inline: auto;
        }

        .hero-buttons {
            display: flex;
            justify-content: center;
            gap: 0.9375rem;
            margin-top: 2rem;
        }

        /* General Section Styles */
        section {
            padding: 4rem 0;
        }

        .section-title {
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
        }

        .section-title h2 {
            font-size: 2rem;
            color: var(--primary-color);
            display: inline-block;
            padding-bottom: 0.625rem;
        }

        .section-title h2::after {
            content: '';
            position: absolute;
            width: 80px;
            height: 3px;
            background-color: var(--secondary-color);
            bottom: 0;
            right: 50%;
            transform: translateX(50%);
        }

        /* Levels Section */
        .levels {
            background-color: white;
        }

        .levels-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.875rem;
        }

        .level-card {
            background-color: white;
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: var(--box-shadow);
            transition: var(--transition);
        }

        .level-card:hover {
            transform: translateY(-10px);
        }

        .level-header {
            padding: 1.25rem;
            color: white;
            text-align: center;
        }

        .beginner .level-header {
            background-color: var(--success-color);
        }

        .intermediate .level-header {
            background-color: var(--warning-color);
        }

        .advanced .level-header {
            background-color: var(--secondary-color);
        }

        .expert .level-header {
            background-color: var(--accent-color);
        }

        .level-body {
            padding: 1.25rem;
        }

        .level-body ul {
            margin-bottom: 1.25rem;
        }

        .level-body ul li {
            padding: 0.5rem 0;
            border-bottom: 1px solid #eee;
            position: relative;
            padding-right: 1.5625rem;
        }

        .level-body ul li::before {
            content: '✓';
            position: absolute;
            right: 0;
            color: var(--success-color);
            font-weight: bold;
        }

        /* Features Section */
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.875rem;
        }

        .feature-card {
            background-color: white;
            padding: 1.875rem;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            text-align: center;
            transition: var(--transition);
        }

        .feature-card:hover {
            transform: translateY(-5px);
        }

        .feature-icon {
            font-size: 3rem;
            color: var(--secondary-color);
            margin-bottom: 1.25rem;
        }

        /* Chess Board Section */
        .chess-board-section {
            background-color: white;
        }

        .chess-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 1.875rem;
        }

        .chess-board-container {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .chess-board {
            width: 400px;
            height: 400px;
            display: grid;
            grid-template-columns: repeat(8, 1fr);
            grid-template-rows: repeat(8, 1fr);
            border: 2px solid var(--dark-color);
            box-shadow: var(--box-shadow);
            margin-bottom: 1.25rem;
        }

        .chess-square {
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 30px;
            cursor: pointer;
            transition: var(--transition);
            position: relative;
        }

        .white {
            background-color: #f0d9b5;
        }

        .black {
            background-color: #b58863;
        }

        .chess-square.selected {
            background-color: rgba(52, 152, 219, 0.5);
        }

        .chess-square.valid-move::after {
            content: '';
            position: absolute;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background-color: rgba(46, 204, 113, 0.5);
        }

        .chess-square.capture::after {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            border: 3px solid rgba(231, 76, 60, 0.7);
            border-radius: 50%;
        }

        .chess-controls {
            display: flex;
            flex-wrap: wrap;
            gap: 0.625rem;
            justify-content: center;
            margin-bottom: 1.25rem;
        }

        .chess-info {
            background-color: white;
            padding: 1.25rem;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            width: 400px;
            max-height: 400px;
            overflow-y: auto;
        }

        .move-history {
            margin-bottom: 1.25rem;
        }

        .move-list {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 0.3125rem;
            margin-top: 0.625rem;
        }

        .move-item {
            padding: 0.3125rem;
            border-radius: 4px;
            cursor: pointer;
        }

        .move-item:hover {
            background-color: #f0f0f0;
        }

        .move-item.current {
            background-color: var(--secondary-color);
            color: white;
        }

        .analysis-result {
            background-color: #f8f9fa;
            padding: 0.9375rem;
            border-radius: var(--border-radius);
            margin-top: 0.9375rem;
        }

        /* Interactive Lessons Section */
        .interactive-lessons {
            background-color: #f9f9f9;
        }

        .lessons-container {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 1.875rem;
        }

        .lessons-sidebar {
            background-color: white;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            padding: 1.25rem;
            max-height: 500px;
            overflow-y: auto;
        }

        .lesson-item {
            padding: 0.9375rem;
            border-bottom: 1px solid #eee;
            cursor: pointer;
            transition: var(--transition);
        }

        .lesson-item:hover {
            background-color: #f0f0f0;
        }

        .lesson-item.active {
            background-color: var(--secondary-color);
            color: white;
        }

        .lesson-content {
            background-color: white;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            padding: 1.875rem;
        }

        .lesson-title {
            margin-bottom: 1.25rem;
            color: var(--primary-color);
        }

        .lesson-video {
            width: 100%;
            height: 300px;
            background-color: #ddd;
            border-radius: var(--border-radius);
            margin-bottom: 1.25rem;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #777;
        }

        .lesson-exercises {
            margin-top: 1.875rem;
        }

        .exercise-item {
            background-color: #f8f9fa;
            padding: 0.9375rem;
            border-radius: var(--border-radius);
            margin-bottom: 0.9375rem;
            cursor: pointer;
            transition: var(--transition);
        }

        .exercise-item:hover {
            background-color: #e9ecef;
        }

        /* User System Section */
        .user-system {
            background-color: white;
        }

        .user-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.875rem;
        }

        .user-form {
            background-color: white;
            padding: 1.875rem;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
        }

        .form-group {
            margin-bottom: 1.25rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
        }

        .form-control {
            width: 100%;
            padding: 0.625rem;
            border: 1px solid #ddd;
            border-radius: var(--border-radius);
            font-size: 1rem;
        }

        .user-stats {
            background-color: white;
            padding: 1.875rem;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1.25rem;
            margin-top: 1.25rem;
        }

        .stat-card {
            background-color: #f8f9fa;
            padding: 1.25rem;
            border-radius: var(--border-radius);
            text-align: center;
        }

        .stat-value {
            font-size: 2rem;
            font-weight: bold;
            color: var(--secondary-color);
        }

        .progress-bar {
            height: 10px;
            background-color: #e9ecef;
            border-radius: 5px;
            margin-top: 0.625rem;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background-color: var(--success-color);
            border-radius: 5px;
        }

        /* Blog Preview Section */
        .blog-preview {
            background-color: #f9f9f9;
        }

        .blog-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.875rem;
        }

        .blog-card {
            background-color: white;
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: var(--box-shadow);
        }

        .blog-image {
            height: 200px;
            background-color: #ddd;
            background-size: cover;
            background-position: center;
        }

        .blog-content {
            padding: 1.25rem;
        }

        .blog-content h3 {
            margin-bottom: 0.625rem;
            color: var(--primary-color);
        }

        .blog-meta {
            display: flex;
            justify-content: space-between;
            color: #777;
            font-size: 0.9rem;
            margin-bottom: 0.9375rem;
        }

        /* Footer */
        footer {
            background-color: var(--primary-color);
            color: white;
            padding: 3rem 0 1rem;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1.875rem;
            margin-bottom: 2rem;
        }

        .footer-column h3 {
            margin-bottom: 1.25rem;
            position: relative;
            padding-bottom: 0.625rem;
        }

        .footer-column h3::after {
            content: '';
            position: absolute;
            width: 40px;
            height: 2px;
            background-color: var(--secondary-color);
            bottom: 0;
            right: 0;
        }

        .footer-column ul li {
            margin-bottom: 0.625rem;
        }

        .footer-column ul li a {
            color: #ddd;
            transition: var(--transition);
            display: block; /* Make links fill the li */
        }

        .footer-column ul li a:hover {
            color: var(--secondary-color);
        }

        .footer-bottom {
            text-align: center;
            padding-top: 1.25rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        /* Responsive Design */
        @media (max-width: 992px) {

            .lessons-container,
            .user-container {
                grid-template-columns: 1fr;
            }

            .chess-info {
                width: 100%;
                max-width: 400px;
            }
        }

        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 0.9375rem;
            }

            nav ul {
                flex-wrap: wrap;
                justify-content: center;
            }

            .hero-content h1 {
                font-size: 2rem;
            }

            .hero-buttons {
                flex-direction: column;
                align-items: center;
            }

            .chess-board {
                width: 300px;
                height: 300px;
            }

            .stats-grid {
                grid-template-columns: 1fr;
            }
        }

        /* Notification Style */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 0.9375rem 1.25rem;
            background-color: var(--success-color);
            color: white;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            z-index: 1100;
            transform: translateX(150%);
            transition: transform 0.3s ease;
        }

        .notification.show {
            transform: translateX(0);
        }

        .notification.error {
            background-color: var(--accent-color);
        }

        .notification.warning {
            background-color: var(--warning-color);
        }
    </style>
</head>

<body>
    <!-- Header -->
    <header>
        <div class="container header-content">
            <div class="logo">
                <i class="fas fa-chess-knight"></i>
                <span>شطرنجي</span>
            </div>
            <nav>
                <ul>
                    <li><a href="#home">الرئيسية</a></li>
                    <li><a href="#levels">المستويات</a></li>
                    <li><a href="#lessons">الدروس</a></li>
                    <li><a href="#practice">التدريب</a></li>
                    <li><a href="#user">حسابي</a></li>
                    <li><a href="#blog">المدونة</a></li>
                </ul>
            </nav>
            <div class="auth-buttons">
                <button class="btn btn-outline" id="loginBtn">تسجيل الدخول</button>
                <button class="btn btn-primary" id="registerBtn">إنشاء حساب</button>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="container hero-content">
            <h1>ارتقِ بمهاراتك في الشطرنج من الصفر إلى الاحتراف</h1>
            <p>موقع متكامل لتعلم الشطرنج خطوة بخطوة، مع دروس تفاعلية، تمارين عملية، وتحديات تناسب جميع المستويات.</p>
            <div class="hero-buttons">
                <button class="btn btn-primary btn-large" id="startJourneyBtn">ابدأ رحلتك الآن</button>
                <button class="btn btn-outline btn-large" id="exploreLessonsBtn">استكشاف الدروس</button>
            </div>
        </div>
    </section>

    <!-- Levels Section -->
    <section class="levels" id="levels">
        <div class="container">
            <div class="section-title">
                <h2>مستويات التعلم</h2>
            </div>
            <div class="levels-grid">
                <div class="level-card beginner">
                    <div class="level-header">
                        <h3>المبتدئ</h3>
                    </div>
                    <div class="level-body">
                        <p>ابدأ رحلتك في عالم الشطرنج بتعلم الأساسيات</p>
                        <ul>
                            <li>تعرف على قطع الشطرنج وحركاتها</li>
                            <li>فهم قواعد اللعبة الأساسية</li>
                            <li>مبادئ الافتتاحيات البسيطة</li>
                            <li>تعلم كيفية كش ملك</li>
                            <li>تمارين على المبتدئين</li>
                        </ul>
                        <button class="btn btn-primary" style="width: 100%;">ابدأ المستوى</button>
                    </div>
                </div>
                <div class="level-card intermediate">
                    <div class="level-header">
                        <h3>المتوسط</h3>
                    </div>
                    <div class="level-body">
                        <p>تطوير مهاراتك وفهمك الاستراتيجي للعبة</p>
                        <ul>
                            <li>استراتيجيات الافتتاحيات المتقدمة</li>
                            <li>التكتيكات والهجمات المزدوجة</li>
                            <li>مبادئ وسط اللعبة</li>
                            <li>الأسس الأساسية لنهاية اللعبة</li>
                            <li>تحليل الأخطاء الشائعة</li>
                        </ul>
                        <button class="btn btn-primary" style="width: 100%;">ابدأ المستوى</button>
                    </div>
                </div>
                <div class="level-card advanced">
                    <div class="level-header">
                        <h3>المتقدم</h3>
                    </div>
                    <div class="level-body">
                        <p>احتراف التخطيط الاستراتيجي والتنفيذ التكتيكي</p>
                        <ul>
                            <li>استراتيجيات متقدمة للافتتاحيات</li>
                            <li>التخطيط طويل المدى</li>
                            <li>تقنيات نهاية اللعبة المعقدة</li>
                            <li>دراسة مباريات الأساتذة الكبار</li>
                            <li>تحليل المواقف المعقدة</li>
                        </ul>
                        <button class="btn btn-primary" style="width: 100%;">ابدأ المستوى</button>
                    </div>
                </div>
                <div class="level-card expert">
                    <div class="level-header">
                        <h3>المحترف</h3>
                    </div>
                    <div class="level-body">
                        <p>إتقان فن الشطرنج والمنافسة على أعلى المستويات</p>
                        <ul>
                            <li>إعداد الافتتاحيات الشخصية</li>
                            <li>التكتيكات المتقدمة والتركيبات</li>
                            <li>التحضير للمنافسات</li>
                            <li>علم النفس في الشطرنج</li>
                            <li>تحليل مبارياتك باستخدام المحركات</li>
                        </ul>
                        <button class="btn btn-primary" style="width: 100%;">ابدأ المستوى</button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Interactive Lessons Section -->
    <section class="interactive-lessons" id="lessons">
        <div class="container">
            <div class="section-title">
                <h2>الدروس التفاعلية</h2>
            </div>
            <div class="lessons-container">
                <div class="lessons-sidebar">
                    <div class="lesson-item active" data-lesson="1">
                        <h4>مقدمة في الشطرنج</h4>
                        <p>تعرف على أساسيات اللعبة</p>
                    </div>
                    <div class="lesson-item" data-lesson="2">
                        <h4>حركات القطع</h4>
                        <p>كيف تتحرك كل قطعة على الرقعة</p>
                    </div>
                    <div class="lesson-item" data-lesson="3">
                        <h4>الاستراتيجيات الأساسية</h4>
                        <p>مبادئ التخطيط في الشطرنج</p>
                    </div>
                    <div class="lesson-item" data-lesson="4">
                        <h4>الافتتاحيات الشهيرة</h4>
                        <p>أشهر استراتيجيات بداية اللعبة</p>
                    </div>
                    <div class="lesson-item" data-lesson="5">
                        <h4>نهاية اللعبة</h4>
                        <p>تقنيات إنهاء المباراة بفوز</p>
                    </div>
                </div>
                <div class="lesson-content">
                    <h3 class="lesson-title" id="currentLessonTitle">مقدمة في الشطرنج</h3>
                    <div class="lesson-video" id="lessonVideo">
                        <i class="fas fa-play-circle" style="font-size: 4rem; color: #777;"></i>
                        <p>في النسخة الكاملة، سيكون هنا فيديو تعليمي</p>
                    </div>
                    <div class="lesson-text" id="lessonText">
                        <p>الشطرنج هي لعبة استراتيجية تلعب على رقعة مربعة مقسمة إلى 64 مربعًا بلونين متبادلين. يلعبها لاعبان، يتحكمان بمجموعة من القطع، كل لاعب يملك 16 قطعة: ملك، وزير، قلعتان، حصانان، فيلان، وثمانية جنود.</p>
                        <p>الهدف من اللعبة هو إماتة ملك الخصم، أي وضعه في وضعية لا يستطيع فيها الهروب من التهديد (كش ملك).</p>
                    </div>
                    <div class="lesson-exercises">
                        <h4>تمارين الدرس</h4>
                        <div class="exercise-item" data-exercise="1">
                            <p>تمرين 1: تحديد مواقع القطع على الرقعة</p>
                        </div>
                        <div class="exercise-item" data-exercise="2">
                            <p>تمرين 2: فهم حركات القطع الأساسية</p>
                        </div>
                        <div class="exercise-item" data-exercise="3">
                            <p>تمرين 3: التعرف على وضعية كش ملك</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Chess Board Section -->
    <section class="chess-board-section" id="practice">
        <div class="container">
            <div class="section-title">
                <h2>لوحة شطرنج تفاعلية</h2>
            </div>
            <div class="chess-container">
                <div class="chess-board-container">
                    <div class="chess-controls">
                        <button class="btn btn-primary" id="resetBoard">إعادة الضبط</button>
                        <button class="btn btn-success" id="hintBtn">تلميح</button>
                        <button class="btn btn-warning" id="analyzeBtn">تحليل النقلة</button>
                        <button class="btn btn-danger" id="undoBtn">تراجع</button>
                        <button class="btn btn-outline" id="flipBoard">قلب الرقعة</button>
                    </div>
                    <div class="chess-board" id="chessBoard">
                        <!-- سيتم إنشاء لوحة الشطرنج بالجافاسكريبت -->
                    </div>
                    <div class="game-status" id="gameStatus">
                        <p>حالة اللعبة: <span id="statusText">جاهز للعب</span></p>
                    </div>
                </div>
                <div class="chess-info">
                    <div class="move-history">
                        <h4>سجل النقلات</h4>
                        <div class="move-list" id="moveList">
                            <!-- سجل النقلات سيتم إنشاؤه ديناميكيًا -->
                        </div>
                    </div>
                    <div class="analysis-result" id="analysisResult">
                        <h4>نتيجة التحليل</h4>
                        <p id="analysisText">سيظهر هنا تحليل للنقلة الحالية</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- User System Section -->
    <section class="user-system" id="user">
        <div class="container">
            <div class="section-title">
                <h2>نظام المستخدم</h2>
            </div>
            <div class="user-container">
                <div class="user-form">
                    <h3>إنشاء حساب جديد</h3>
                    <form id="registerForm">
                        <div class="form-group">
                            <label for="username">اسم المستخدم</label>
                            <input type="text" id="username" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="email">البريد الإلكتروني</label>
                            <input type="email" id="email" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="password">كلمة المرور</label>
                            <input type="password" id="password" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="confirmPassword">تأكيد كلمة المرور</label>
                            <input type="password" id="confirmPassword" class="form-control" required>
                        </div>
                        <button type="submit" class="btn btn-primary" style="width: 100%;">إنشاء حساب</button>
                    </form>
                    <div class="login-link" style="margin-top: 20px; text-align: center;">
                        <p>هل لديك حساب بالفعل؟ <a href="#" id="showLoginForm">تسجيل الدخول</a></p>
                    </div>
                </div>
                <div class="user-stats">
                    <h3>إحصائياتك</h3>
                    <p>تابع تقدمك في تعلم الشطرنج</p>
                    <div class="stats-grid">
                        <div class="stat-card">
                            <div class="stat-value" id="completedLessons">0</div>
                            <div class="stat-label">دروس مكتملة</div>
                            <div class="progress-bar">
                                <div class="progress-fill" style="width: 0%;"
