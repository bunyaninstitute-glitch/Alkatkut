<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تطبيق الكتكوت - تعليم الحروف العربية</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* أنماط CSS - مع الألوان القديمة */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: #fff;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1200px;
            width: 100%;
            text-align: center;
        }
        
        /* شاشة إدخال الاسم */
        .name-input-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 10000;
            transition: opacity 0.5s;
        }
        
        .name-input-box {
            background: rgba(255, 255, 255, 0.95);
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
            text-align: center;
            max-width: 500px;
            width: 90%;
            border: 5px solid #FFD700;
        }
        
        .name-input-box h2 {
            color: #667eea;
            margin-bottom: 20px;
            font-size: 2.2rem;
        }
        
        .name-input-box p {
            color: #666;
            margin-bottom: 30px;
            font-size: 1.2rem;
        }
        
        #child-name-input {
            width: 100%;
            padding: 15px;
            font-size: 1.5rem;
            border: 3px solid #FFD700;
            border-radius: 10px;
            text-align: center;
            margin-bottom: 20px;
            color: #333;
        }
        
        #start-learning {
            background: #4CAF50;
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 1.3rem;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 10px;
            margin: 0 auto;
        }
        
        #start-learning:hover {
            background: #45a049;
            transform: translateY(-3px);
        }
        
        .hidden {
            display: none !important;
        }
        
        header {
            margin-bottom: 30px;
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 20px;
            backdrop-filter: blur(10px);
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
            position: relative;
            overflow: hidden;
            width: 100%;
        }
        
        .header-top {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            flex-wrap: wrap;
            gap: 15px;
        }
        
        .child-name-display {
            background: rgba(255, 215, 0, 0.2);
            padding: 10px 20px;
            border-radius: 50px;
            font-size: 1.2rem;
            font-weight: bold;
            border: 2px solid #FFD700;
            flex-grow: 1;
            text-align: center;
        }
        
        .whatsapp-btn {
            background: #25D366;
            color: white;
            padding: 10px 20px;
            border-radius: 50px;
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 8px;
            font-weight: bold;
            transition: all 0.3s;
            white-space: nowrap;
        }
        
        .whatsapp-btn:hover {
            background: #128C7E;
            transform: translateY(-2px);
        }
        
        .chick-title {
            font-size: 3.5rem;
            margin-bottom: 10px;
            color: #FFD700;
            text-shadow: 3px 3px 0 rgba(0, 0, 0, 0.3);
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
        }
        
        .chick-icon {
            color: #FFD700;
            font-size: 3rem;
            animation: bounce 2s infinite;
        }
        
        .subtitle {
            font-size: 1.4rem;
            margin-bottom: 20px;
            opacity: 0.9;
        }
        
        .tabs {
            display: flex;
            justify-content: center;
            margin-bottom: 20px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50px;
            padding: 5px;
            width: fit-content;
            margin: 0 auto 30px;
            flex-wrap: wrap;
        }
        
        .tab {
            padding: 12px 25px;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: bold;
            flex-grow: 1;
            text-align: center;
            min-width: 120px;
        }
        
        .tab.active {
            background: #FF5722;
            box-shadow: 0 4px 15px rgba(255, 87, 34, 0.4);
        }
        
        .content-section {
            display: none;
        }
        
        .content-section.active {
            display: block;
            animation: fadeIn 0.5s;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .main-content {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .letter-section {
            background-color: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 25px;
            width: 100%;
            max-width: 700px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
        }
        
        .letter-display {
            font-size: 10rem;
            margin: 20px 0;
            text-shadow: 4px 4px 8px rgba(0, 0, 0, 0.3);
            transition: transform 0.3s;
            color: #FFD700;
        }
        
        .letter-display:hover {
            transform: scale(1.1);
        }
        
        .letter-info {
            margin-bottom: 20px;
        }
        
        .letter-name {
            font-size: 2.5rem;
            margin-bottom: 10px;
            color: #4FC3F7;
        }
        
        .letter-example {
            font-size: 2rem;
            color: #FFEB3B;
            margin-bottom: 5px;
        }
        
        .letter-position {
            font-size: 1.3rem;
            color: #B388FF;
            margin-bottom: 20px;
        }
        
        .video-preview {
            width: 100%;
            max-width: 560px;
            margin: 0 auto 20px;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            background: #000;
            position: relative;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .video-preview:hover {
            transform: scale(1.02);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
        }
        
        .video-preview img {
            width: 100%;
            height: 315px;
            object-fit: cover;
            background: #222; /* خلفية سوداء للصور التي لا تحمل */
        }
        
        .video-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            transition: background 0.3s;
        }
        
        .video-preview:hover .video-overlay {
            background: rgba(0, 0, 0, 0.3);
        }
        
        .play-button {
            background: #FF0000;
            width: 80px;
            height: 80px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 15px;
            animation: pulse 2s infinite;
        }
        
        .play-button i {
            font-size: 2.5rem;
            color: white;
            margin-left: 5px;
        }
        
        .video-title {
            font-size: 1.3rem;
            font-weight: bold;
            color: white;
            text-align: center;
            padding: 0 20px;
        }
        
        .youtube-note {
            font-size: 0.9rem;
            color: #FFD700;
            margin-top: 10px;
            font-style: italic;
        }
        
        .controls {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 20px;
        }
        
        button {
            background-color: #FF5722;
            color: white;
            border: none;
            padding: 14px 28px;
            border-radius: 50px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            display: flex;
            align-items: center;
            gap: 8px;
            font-weight: bold;
        }
        
        button:hover {
            background-color: #FF7043;
            transform: translateY(-3px);
        }
        
        button:active {
            transform: translateY(1px);
        }
        
        .play-sound {
            background-color: #4CAF50;
        }
        
        .watch-video {
            background-color: #FF0000;
        }
        
        .nav-buttons {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            justify-content: center;
        }
        
        .game-section {
            background-color: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 25px;
            width: 100%;
            max-width: 700px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
            position: relative;
            overflow: hidden;
        }
        
        .game-section h2 {
            margin-bottom: 20px;
            font-size: 2.2rem;
            color: #4FC3F7;
        }
        
        .game-question {
            font-size: 1.8rem;
            margin-bottom: 25px;
            color: #FFEB3B;
            min-height: 60px;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 15px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
        }
        
        .game-options {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin-bottom: 25px;
        }
        
        .game-option {
            background-color: rgba(255, 255, 255, 0.2);
            border: none;
            border-radius: 15px;
            padding: 25px;
            font-size: 3rem;
            cursor: pointer;
            transition: all 0.3s;
            min-height: 120px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
        }
        
        .game-option:hover {
            background-color: rgba(255, 255, 255, 0.3);
            transform: scale(1.05);
        }
        
        .game-option.correct {
            background-color: #4CAF50;
            animation: pulse 0.5s;
        }
        
        .game-option.incorrect {
            background-color: #F44336;
        }
        
        .game-feedback {
            font-size: 1.8rem;
            margin: 15px 0;
            min-height: 40px;
            font-weight: bold;
            padding: 15px;
            border-radius: 15px;
        }
        
        .game-stats {
            display: flex;
            justify-content: space-around;
            margin-top: 20px;
            background: rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 15px;
            flex-wrap: wrap;
            gap: 15px;
        }
        
        .stat {
            display: flex;
            flex-direction: column;
            align-items: center;
            flex-grow: 1;
            min-width: 100px;
        }
        
        .stat-value {
            font-size: 2.5rem;
            font-weight: bold;
            color: #FFD700;
        }
        
        .stat-label {
            font-size: 1.1rem;
            opacity: 0.8;
        }
        
        .game-controls {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 20px;
            flex-wrap: wrap;
        }
        
        .ask-letter-game {
            background-color: #9C27B0;
        }
        
        .progress {
            margin-top: 20px;
            width: 100%;
            background-color: rgba(255, 255, 255, 0.2);
            border-radius: 10px;
            overflow: hidden;
        }
        
        .progress-bar {
            height: 25px;
            background: linear-gradient(90deg, #4CAF50, #8BC34A);
            width: 10%;
            transition: width 0.5s;
        }
        
        .progress-text {
            margin-top: 10px;
            font-size: 1.2rem;
        }
        
        .all-letters {
            display: grid;
            grid-template-columns: repeat(6, 1fr);
            gap: 15px;
            margin-top: 20px;
        }
        
        .letter-card {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 20px 10px;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        
        .letter-card:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-5px);
        }
        
        .letter-card.active {
            background: rgba(255, 87, 34, 0.3);
            box-shadow: 0 5px 15px rgba(255, 87, 34, 0.4);
        }
        
        .letter-card .char {
            font-size: 2.8rem;
            margin-bottom: 5px;
            color: #FFD700;
            font-weight: bold;
        }
        
        .letter-card .name {
            font-size: 1rem;
            opacity: 0.8;
        }
        
        footer {
            margin-top: 30px;
            padding: 20px;
            text-align: center;
            width: 100%;
            background-color: rgba(0, 0, 0, 0.2);
            border-radius: 15px;
            font-size: 1.1rem;
        }
        
        .footer-content {
            display: flex;
            flex-direction: column;
            gap: 20px;
            align-items: center;
        }
        
        .developer-info {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 15px;
            flex-wrap: wrap;
        }
        
        .bunyan-link {
            background: #FF0000;
            color: white;
            text-decoration: none;
            font-weight: bold;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 8px;
            padding: 10px 20px;
            border-radius: 50px;
        }
        
        .bunyan-link:hover {
            background: #CC0000;
            transform: translateY(-2px);
        }
        
        .footer-whatsapp {
            display: flex;
            justify-content: center;
        }
        
        .footer-whatsapp .whatsapp-btn {
            padding: 12px 25px;
            font-size: 1.1rem;
        }
        
        /* تأثيرات الرسوم المتحركة */
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
        
        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        
        @keyframes float {
            0% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(10deg); }
            100% { transform: translateY(0px) rotate(0deg); }
        }
        
        @keyframes fireworks {
            0% { transform: translateY(0) scale(0); opacity: 1; }
            100% { transform: translateY(-100px) scale(1); opacity: 0; }
        }
        
        .celebration {
            animation: pulse 0.5s;
        }
        
        /* تأثيرات القلوب الطائرة والألعاب النارية */
        .heart {
            position: absolute;
            color: #FF6B6B;
            font-size: 1.5rem;
            animation: float 3s linear forwards;
            pointer-events: none;
            z-index: 1000;
        }
        
        .firework {
            position: absolute;
            width: 10px;
            height: 10px;
            border-radius: 50%;
            animation: fireworks 1s linear forwards;
            pointer-events: none;
            z-index: 1000;
        }
        
        /* تصميم متجاوب */
        @media (max-width: 768px) {
            .chick-title {
                font-size: 2.5rem;
            }
            
            .letter-display {
                font-size: 8rem;
            }
            
            .main-content {
                flex-direction: column;
                align-items: center;
            }
            
            .letter-section, .game-section {
                width: 100%;
            }
            
            .game-options {
                grid-template-columns: 1fr;
            }
            
            .video-preview img {
                height: 250px;
            }
            
            .all-letters {
                grid-template-columns: repeat(4, 1fr);
            }
            
            .controls {
                flex-direction: column;
                align-items: center;
            }
            
            .nav-buttons {
                width: 100%;
            }
            
            .header-top {
                flex-direction: column;
                align-items: center;
                text-align: center;
            }
            
            .whatsapp-btn {
                width: 100%;
                justify-content: center;
            }
            
            .tabs {
                width: 100%;
            }
            
            .tab {
                min-width: 100px;
                padding: 10px 15px;
                font-size: 1rem;
            }
        }
        
        @media (max-width: 480px) {
            .all-letters {
                grid-template-columns: repeat(3, 1fr);
            }
            
            .letter-display {
                font-size: 6rem;
            }
            
            .game-option {
                font-size: 2.5rem;
                min-height: 100px;
                padding: 15px;
            }
            
            .chick-title {
                font-size: 2rem;
            }
            
            .play-button {
                width: 60px;
                height: 60px;
            }
            
            .play-button i {
                font-size: 2rem;
            }
            
            .name-input-box {
                padding: 20px;
            }
            
            .name-input-box h2 {
                font-size: 1.8rem;
            }
            
            .footer-content {
                gap: 15px;
            }
            
            .developer-info {
                flex-direction: column;
                gap: 10px;
            }
        }
    </style>
</head>
<body>
    <!-- شاشة إدخال اسم الطفل -->
    <div class="name-input-screen" id="name-input-screen">
        <div class="name-input-box">
            <h2><i class="fas fa-child"></i> مرحباً يا صغيري!</h2>
            <p>ما اسمك الجميل؟ سأستخدمه لتشجيعك أثناء تعلم الحروف</p>
            <input type="text" id="child-name-input" placeholder="اكتب اسمك هنا..." maxlength="20">
            <button id="start-learning">
                <i class="fas fa-rocket"></i> ابدأ التعلم
            </button>
        </div>
    </div>
    
    <!-- التطبيق الرئيسي -->
    <div class="container hidden" id="main-app">
        <header>
            <div class="header-top">
                <div class="child-name-display" id="child-name-display">
                    <i class="fas fa-user"></i> مرحباً <span id="child-name">صغيري</span>
                </div>
                <a href="https://wa.me/+201096317712" class="whatsapp-btn" target="_blank">
                    <i class="fab fa-whatsapp"></i> تواصل مع المعلم
                </a>
            </div>
            
            <h1 class="chick-title">
                <i class="fas fa-dove chick-icon"></i>
                تطبيق الكتكوت
                <i class="fas fa-dove chick-icon"></i>
            </h1>
            <p class="subtitle">هيا نتعلم الحروف العربية معاً بطريقة ممتعة</p>
            
            <div class="tabs">
                <div class="tab active" data-tab="learn">التعلم</div>
                <div class="tab" data-tab="game">اللعبة</div>
                <div class="tab" data-tab="all-letters">كل الحروف</div>
            </div>
        </header>
        
        <section class="content-section active" id="learn-section">
            <div class="main-content">
                <div class="letter-section">
                    <h2>الحرف اليوم</h2>
                    <div class="letter-display" id="current-letter">أ</div>
                    
                    <div class="letter-info">
                        <div class="letter-name" id="letter-name">حرف الألف</div>
                        <div class="letter-example" id="letter-example">أَسَد</div>
                        <div class="letter-position" id="letter-position">الحرف الأول في الأبجدية العربية</div>
                    </div>
                    
                    <div class="video-preview" id="video-preview">
                        <img src="https://img.youtube.com/vi/stJeoh3ty1E/maxresdefault.jpg" alt="فيديو تعليمي لحرف الألف" id="video-thumbnail" onerror="this.src='https://img.youtube.com/vi/stJeoh3ty1E/hqdefault.jpg'">
                        <div class="video-overlay">
                            <div class="play-button">
                                <i class="fab fa-youtube"></i>
                            </div>
                            <div class="video-title" id="video-title">مشاهدة فيديو تعليمي لحرف الألف على يوتيوب</div>
                            <div class="youtube-note">سيتم فتح الفيديو في موقع YouTube</div>
                        </div>
                    </div>
                    
                    <div class="controls">
                        <button class="play-sound" id="play-sound">
                            <i class="fas fa-volume-up"></i> اسمع الصوت
                        </button>
                        <button class="watch-video" id="watch-video">
                            <i class="fab fa-youtube"></i> شاهد الفيديو
                        </button>
                        <div class="nav-buttons">
                            <button id="prev-letter">
                                <i class="fas fa-arrow-right"></i> السابق
                            </button>
                            <button id="next-letter">
                                التالي <i class="fas fa-arrow-left"></i>
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
        <section class="content-section" id="game-section">
            <div class="main-content">
                <div class="game-section">
                    <h2><i class="fas fa-gamepad"></i> لعبة اختيار الحرف الصحيح</h2>
                    <div class="game-question" id="game-question">ما هو هذا الحرف؟</div>
                    
                    <div class="game-options" id="game-options">
                        <!-- سيتم ملؤها بالخيارات عبر JavaScript -->
                    </div>
                    
                    <div class="game-feedback" id="game-feedback"></div>
                    
                    <div class="game-stats">
                        <div class="stat">
                            <div class="stat-value" id="game-score">0</div>
                            <div class="stat-label">النقاط</div>
                        </div>
                        <div class="stat">
                            <div class="stat-value" id="correct-answers">0</div>
                            <div class="stat-label">الإجابات الصحيحة</div>
                        </div>
                        <div class="stat">
                            <div class="stat-value" id="questions-answered">0</div>
                            <div class="stat-label">الأسئلة المجابة</div>
                        </div>
                    </div>
                    
                    <div class="game-controls">
                        <button class="ask-letter-game" id="ask-letter-game">
                            <i class="fas fa-question-circle"></i> أين حرف؟
                        </button>
                        <button id="new-game">
                            <i class="fas fa-redo"></i> لعبة جديدة
                        </button>
                    </div>
                </div>
            </div>
        </section>
        
        <section class="content-section" id="all-letters-section">
            <div class="main-content">
                <div class="letter-section">
                    <h2><i class="fas fa-font"></i> جميع الحروف العربية</h2>
                    <p>إضغط على أي حرف لتعلمه</p>
                    
                    <div class="all-letters" id="all-letters">
                        <!-- سيتم ملؤها بالحروف عبر JavaScript -->
                    </div>
                    
                    <div class="progress">
                        <div class="progress-bar" id="progress-bar"></div>
                    </div>
                    <div class="progress-text" id="progress-text">تعلمت 1 من 28 حرفاً</div>
                </div>
            </div>
        </section>
        
        <footer>
            <div class="footer-content">
                <div class="developer-info">
                    <span>قام بتطويره:</span>
                    <a href="https://youtube.com/@bunyan--m5q" class="bunyan-link" target="_blank">
                        <i class="fab fa-youtube"></i> Bunyan Institute
                    </a>
                </div>
                <div class="footer-whatsapp">
                    <a href="https://wa.me/+201096317712" class="whatsapp-btn" target="_blank">
                        <i class="fab fa-whatsapp"></i> تواصل مع المعلم
                    </a>
                </div>
            </div>
        </footer>
    </div>

    <script>
        // بيانات الحروف العربية الكاملة مع مقاطع الفيديو المحددة
        const arabicLetters = [
            { 
                letter: 'أ', 
                name: 'الألف', 
                example: 'أَسَد', 
                video: 'https://www.youtube.com/watch?v=stJeoh3ty1E',
                thumbnail: 'https://img.youtube.com/vi/stJeoh3ty1E/maxresdefault.jpg',
                sound: 'أَلِف',
                position: 'الحرف الأول في الأبجدية العربية'
            },
            { 
                letter: 'ب', 
                name: 'الباء', 
                example: 'بَطَّة', 
                video: 'https://www.youtube.com/watch?v=gJgAMzMEfIA',
                thumbnail: 'https://img.youtube.com/vi/gJgAMzMEfIA/maxresdefault.jpg',
                sound: 'بَاء',
                position: 'الحرف الثاني في الأبجدية العربية'
            },
            { 
                letter: 'ت', 
                name: 'التاء', 
                example: 'تِفَّاح', 
                video: 'https://www.youtube.com/watch?v=t3EGi1JdIto',
                thumbnail: 'https://img.youtube.com/vi/t3EGi1JdIto/maxresdefault.jpg',
                sound: 'تَاء',
                position: 'الحرف الثالث في الأبجدية العربية'
            },
            { 
                letter: 'ث', 
                name: 'الثاء', 
                example: 'ثَوْر', 
                video: 'https://www.youtube.com/watch?v=8RAb2ViqFmI',
                thumbnail: 'https://img.youtube.com/vi/8RAb2ViqFmI/maxresdefault.jpg',
                sound: 'ثَاء',
                position: 'الحرف الرابع في الأبجدية العربية'
            },
            { 
                letter: 'ج', 
                name: 'الجيم', 
                example: 'جَمَل', 
                video: 'https://www.youtube.com/watch?v=ijGXqQ8vl3I',
                thumbnail: 'https://img.youtube.com/vi/ijGXqQ8vl3I/maxresdefault.jpg',
                sound: 'جِيم',
                position: 'الحرف الخامس في الأبجدية العربية'
            },
            { 
                letter: 'ح', 
                name: 'الحاء', 
                example: 'حِصَان', 
                video: 'https://www.youtube.com/watch?v=_OIJRJv25Cc',
                thumbnail: 'https://img.youtube.com/vi/_OIJRJv25Cc/maxresdefault.jpg',
                sound: 'حَاء',
                position: 'الحرف السادس في الأبجدية العربية'
            },
            { 
                letter: 'خ', 
                name: 'الخاء', 
                example: 'خُرُوف', 
                video: 'https://www.youtube.com/watch?v=-LHyjqYYY60',
                thumbnail: 'https://img.youtube.com/vi/-LHyjqYYY60/maxresdefault.jpg',
                sound: 'خَاء',
                position: 'الحرف السابع في الأبجدية العربية'
            },
            { 
                letter: 'د', 
                name: 'الدال', 
                example: 'دُب', 
                video: 'https://www.youtube.com/watch?v=fBDbJ37uJy8',
                thumbnail: 'https://img.youtube.com/vi/fBDbJ37uJy8/maxresdefault.jpg',
                sound: 'دَال',
                position: 'الحرف الثامن في الأبجدية العربية'
            },
            { 
                letter: 'ذ', 
                name: 'الذال', 
                example: 'ذِئْب', 
                video: 'https://www.youtube.com/watch?v=b2YiJmm4K3s',
                thumbnail: 'https://img.youtube.com/vi/b2YiJmm4K3s/maxresdefault.jpg',
                sound: 'ذَال',
                position: 'الحرف التاسع في الأبجدية العربية'
            },
            { 
                letter: 'ر', 
                name: 'الراء', 
                example: 'رُمح', 
                video: 'https://www.youtube.com/watch?v=WGkjzWP7obI',
                thumbnail: 'https://img.youtube.com/vi/WGkjzWP7obI/maxresdefault.jpg',
                sound: 'رَاء',
                position: 'الحرف العاشر في الأبجدية العربية'
            },
            { 
                letter: 'ز', 
                name: 'الزاي', 
                example: 'زَرَافَة', 
                video: 'https://www.youtube.com/watch?v=UXdyRqaYcpw',
                thumbnail: 'https://img.youtube.com/vi/UXdyRqaYcpw/maxresdefault.jpg',
                sound: 'زَاي',
                position: 'الحرف الحادي عشر في الأبجدية العربية'
            },
            { 
                letter: 'س', 
                name: 'السين', 
                example: 'سَمَك', 
                video: 'https://www.youtube.com/watch?v=W-faLFUfZ7k',
                thumbnail: 'https://img.youtube.com/vi/W-faLFUfZ7k/maxresdefault.jpg',
                sound: 'سِين',
                position: 'الحرف الثاني عشر في الأبجدية العربية'
            },
            { 
                letter: 'ش', 
                name: 'الشين', 
                example: 'شَمْس', 
                video: 'https://www.youtube.com/watch?v=JKikUoH5S8U',
                thumbnail: 'https://img.youtube.com/vi/JKikUoH5S8U/maxresdefault.jpg',
                sound: 'شِين',
                position: 'الحرف الثالث عشر في الأبجدية العربية'
            },
            { 
                letter: 'ص', 
                name: 'الصاد', 
                example: 'صَقْر', 
                video: 'https://www.youtube.com/watch?v=L1Xdg3AhtRE',
                thumbnail: 'https://img.youtube.com/vi/L1Xdg3AhtRE/maxresdefault.jpg',
                sound: 'صَاد',
                position: 'الحرف الرابع عشر في الأبجدية العربية'
            },
            { 
                letter: 'ض', 
                name: 'الضاد', 
                example: 'ضِفْدَع', 
                video: 'https://www.youtube.com/watch?v=S7AdeEdyxUs',
                thumbnail: 'https://img.youtube.com/vi/S7AdeEdyxUs/maxresdefault.jpg',
                sound: 'ضَاد',
                position: 'الحرف الخامس عشر في الأبجدية العربية'
            },
            { 
                letter: 'ط', 
                name: 'الطاء', 
                example: 'طَائِر', 
                video: 'https://www.youtube.com/watch?v=pBic4A2roHU',
                thumbnail: 'https://img.youtube.com/vi/pBic4A2roHU/maxresdefault.jpg',
                sound: 'طَاء',
                position: 'الحرف السادس عشر في الأبجدية العربية'
            },
            { 
                letter: 'ظ', 
                name: 'الظاء', 
                example: 'ظَبْي', 
                video: 'https://www.youtube.com/watch?v=SSdm_kddhWM',
                thumbnail: 'https://img.youtube.com/vi/SSdm_kddhWM/maxresdefault.jpg',
                sound: 'ظَاء',
                position: 'الحرف السابع عشر في الأبجدية العربية'
            },
            { 
                letter: 'ع', 
                name: 'العين', 
                example: 'عُصْفُور', 
                video: 'https://www.youtube.com/watch?v=JPqKTovWwS8',
                thumbnail: 'https://img.youtube.com/vi/JPqKTovWwS8/maxresdefault.jpg',
                sound: 'عَيْن',
                position: 'الحرف الثامن عشر في الأبجدية العربية'
            },
            { 
                letter: 'غ', 
                name: 'الغين', 
                example: 'غَزَال', 
                video: 'https://www.youtube.com/watch?v=qvHpNdNGROc',
                thumbnail: 'https://img.youtube.com/vi/qvHpNdNGROc/maxresdefault.jpg',
                sound: 'غَيْن',
                position: 'الحرف التاسع عشر في الأبجدية العربية'
            },
            { 
                letter: 'ف', 
                name: 'الفاء', 
                example: 'فَأْر', 
                video: 'https://www.youtube.com/watch?v=JdP_S28KkzM',
                thumbnail: 'https://img.youtube.com/vi/JdP_S28KkzM/maxresdefault.jpg',
                sound: 'فَاء',
                position: 'الحرف العشرون في الأبجدية العربية'
            },
            { 
                letter: 'ق', 
                name: 'القاف', 
                example: 'قِرْد', 
                video: 'https://www.youtube.com/watch?v=xM1U6AD6yqU',
                thumbnail: 'https://img.youtube.com/vi/xM1U6AD6yqU/maxresdefault.jpg',
                sound: 'قَاف',
                position: 'الحرف الحادي والعشرون في الأبجدية العربية'
            },
            { 
                letter: 'ك', 
                name: 'الكاف', 
                example: 'كَلْب', 
                video: 'https://www.youtube.com/watch?v=2sa9RJweb6I',
                thumbnail: 'https://img.youtube.com/vi/2sa9RJweb6I/maxresdefault.jpg',
                sound: 'كَاف',
                position: 'الحرف الثاني والعشرون في الأبجدية العربية'
            },
            { 
                letter: 'ل', 
                name: 'اللام', 
                example: 'لِيمُون', 
                video: 'https://www.youtube.com/watch?v=0BqZdP9vnd4',
                thumbnail: 'https://img.youtube.com/vi/0BqZdP9vnd4/maxresdefault.jpg',
                sound: 'لاَم',
                position: 'الحرف الثالث والعشرون في الأبجدية العربية'
            },
            { 
                letter: 'م', 
                name: 'الميم', 
                example: 'مُوْز', 
                video: 'https://www.youtube.com/watch?v=pJ8LlxHdyoI',
                thumbnail: 'https://img.youtube.com/vi/pJ8LlxHdyoI/hqdefault.jpg',
                sound: 'مِيم',
                position: 'الحرف الرابع والعشرون في الأبجدية العربية'
            },
            { 
                letter: 'ن', 
                name: 'النون', 
                example: 'نَمْل', 
                video: 'https://www.youtube.com/watch?v=HHXxef8YeHc',
                thumbnail: 'https://img.youtube.com/vi/HHXxef8YeHc/maxresdefault.jpg',
                sound: 'نُون',
                position: 'الحرف الخامس والعشرون في الأبجدية العربية'
            },
            { 
                letter: 'ه', 
                name: 'الهاء', 
                example: 'هُدْهُد', 
                video: 'https://www.youtube.com/watch?v=r8FDQNtpcTs',
                thumbnail: 'https://img.youtube.com/vi/r8FDQNtpcTs/hqdefault.jpg',
                sound: 'هَاء',
                position: 'الحرف السادس والعشرون في الأبجدية العربية'
            },
            { 
                letter: 'و', 
                name: 'الواو', 
                example: 'وَرْد', 
                video: 'https://www.youtube.com/watch?v=PykAMHq30Js',
                thumbnail: 'https://img.youtube.com/vi/PykAMHq30Js/maxresdefault.jpg',
                sound: 'وَاو',
                position: 'الحرف السابع والعشرون في الأبجدية العربية'
            },
            { 
                letter: 'ي', 
                name: 'الياء', 
                example: 'يَخْت', 
                video: 'https://www.youtube.com/watch?v=As4XH5DP0Ck',
                thumbnail: 'https://img.youtube.com/vi/As4XH5DP0Ck/maxresdefault.jpg',
                sound: 'يَاء',
                position: 'الحرف الثامن والعشرون في الأبجدية العربية'
            }
        ];
        
        let currentLetterIndex = 0;
        let gameScore = 0;
        let correctAnswers = 0;
        let questionsAnswered = 0;
        let correctAnswer = '';
        let learnedLetters = new Set(['أ']);
        let childName = "صغيري";
        
        // عناصر DOM
        const nameInputScreen = document.getElementById('name-input-screen');
        const childNameInput = document.getElementById('child-name-input');
        const startLearningButton = document.getElementById('start-learning');
        const mainApp = document.getElementById('main-app');
        const childNameDisplay = document.getElementById('child-name');
        
        const currentLetterElement = document.getElementById('current-letter');
        const letterNameElement = document.getElementById('letter-name');
        const letterExampleElement = document.getElementById('letter-example');
        const letterPositionElement = document.getElementById('letter-position');
        const videoPreviewElement = document.getElementById('video-preview');
        const videoThumbnailElement = document.getElementById('video-thumbnail');
        const videoTitleElement = document.getElementById('video-title');
        const playSoundButton = document.getElementById('play-sound');
        const watchVideoButton = document.getElementById('watch-video');
        const prevLetterButton = document.getElementById('prev-letter');
        const nextLetterButton = document.getElementById('next-letter');
        
        const gameQuestionElement = document.getElementById('game-question');
        const gameOptionsElement = document.getElementById('game-options');
        const gameFeedbackElement = document.getElementById('game-feedback');
        const gameScoreElement = document.getElementById('game-score');
        const correctAnswersElement = document.getElementById('correct-answers');
        const questionsAnsweredElement = document.getElementById('questions-answered');
        const newGameButton = document.getElementById('new-game');
        const askLetterGameButton = document.getElementById('ask-letter-game');
        
        const progressBar = document.getElementById('progress-bar');
        const progressText = document.getElementById('progress-text');
        const allLettersContainer = document.getElementById('all-letters');
        const tabs = document.querySelectorAll('.tab');
        const contentSections = document.querySelectorAll('.content-section');
        
        // بدء التطبيق عند إدخال الاسم
        startLearningButton.addEventListener('click', () => {
            const name = childNameInput.value.trim();
            if (name) {
                childName = name;
                childNameDisplay.textContent = childName;
                
                // إضافة تأثير انتقالي
                nameInputScreen.style.opacity = '0';
                setTimeout(() => {
                    nameInputScreen.classList.add('hidden');
                    mainApp.classList.remove('hidden');
                    
                    // ترحيب صوتي بالطفل
                    speakText(`مرحباً ${childName}، أنا سعيد بلقائك! هيا نتعلم الحروف العربية معاً.`);
                }, 500);
            } else {
                alert('من فضلك أدخل اسمك أولاً!');
                childNameInput.focus();
            }
        });
        
        // السماح بالبدء بالضغط على Enter
        childNameInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                startLearningButton.click();
            }
        });
        
        // تحديث واجهة الحرف
        function updateLetter() {
            const currentLetter = arabicLetters[currentLetterIndex];
            currentLetterElement.textContent = currentLetter.letter;
            letterNameElement.textContent = `حرف ${currentLetter.name}`;
            letterExampleElement.textContent = currentLetter.example;
            letterPositionElement.textContent = currentLetter.position;
            
            // تحديث صورة الفيديو وعنوانه
            videoThumbnailElement.src = currentLetter.thumbnail;
            videoThumbnailElement.alt = `فيديو تعليمي لحرف ${currentLetter.name}`;
            videoTitleElement.textContent = `مشاهدة فيديو تعليمي لحرف ${currentLetter.name} على يوتيوب`;
            
            // تحديث شريط التقدم
            const progress = (learnedLetters.size / arabicLetters.length) * 100;
            progressBar.style.width = `${progress}%`;
            progressText.textContent = `تعلمت ${learnedLetters.size} من ${arabicLetters.length} حرفاً`;
            
            // تحديث الحروف المتعلمة في لوحة كل الحروف
            updateAllLettersDisplay();
            
            // إنشاء لعبة جديدة
            if (document.getElementById('game-section').classList.contains('active')) {
                generateGame();
            }
        }
        
        // تحديث عرض كل الحروف
        function updateAllLettersDisplay() {
            allLettersContainer.innerHTML = '';
            arabicLetters.forEach((letter, index) => {
                const letterCard = document.createElement('div');
                letterCard.className = `letter-card ${learnedLetters.has(letter.letter) ? 'active' : ''}`;
                letterCard.innerHTML = `
                    <div class="char">${letter.letter}</div>
                    <div class="name">${letter.name}</div>
                `;
                letterCard.addEventListener('click', () => {
                    currentLetterIndex = index;
                    updateLetter();
                    switchTab('learn');
                });
                allLettersContainer.appendChild(letterCard);
            });
        }
        
        // دالة النطق
        function speakText(text, lang = 'ar-SA') {
            const utterance = new SpeechSynthesisUtterance(text);
            utterance.lang = lang;
            utterance.rate = 0.8;
            utterance.pitch = 1.2;
            utterance.volume = 1.0;
            speechSynthesis.speak(utterance);
        }
        
        // تشغيل صوت الحرف
        function playLetterSound() {
            const currentLetter = arabicLetters[currentLetterIndex];
            
            // نطق الحرف مع أمثلة
            const soundText = `${currentLetter.sound}... مثل ${currentLetter.example}`;
            speakText(soundText);
            
            // تأثير مرئي عند النقر
            currentLetterElement.classList.add('celebration');
            setTimeout(() => {
                currentLetterElement.classList.remove('celebration');
            }, 500);
            
            // إضافة الحرف إلى الحروف المتعلمة
            learnedLetters.add(currentLetter.letter);
            updateLetter();
        }
        
        // فتح فيديو الحرف في YouTube
        function openYouTubeVideo() {
            const currentLetter = arabicLetters[currentLetterIndex];
            window.open(currentLetter.video, '_blank');
            
            // إضافة الحرف إلى الحروف المتعلمة
            learnedLetters.add(currentLetter.letter);
            updateLetter();
        }
        
        // الانتقال للحرف السابق
        function prevLetter() {
            currentLetterIndex = (currentLetterIndex - 1 + arabicLetters.length) % arabicLetters.length;
            updateLetter();
        }
        
        // الانتقال للحرف التالي
        function nextLetter() {
            currentLetterIndex = (currentLetterIndex + 1) % arabicLetters.length;
            updateLetter();
        }
        
        // سؤال "أين حرف؟" في اللعبة
        function askAboutLetterInGame() {
            const randomIndex = Math.floor(Math.random() * arabicLetters.length);
            const randomLetter = arabicLetters[randomIndex];
            
            speakText(`يا ${childName}، أين حرف ${randomLetter.name}؟`);
            
            // إبراز الحرف في اللعبة
            gameQuestionElement.textContent = `أين حرف ${randomLetter.name}؟`;
            correctAnswer = randomLetter.letter;
            
            // إنشاء خيارات جديدة
            const options = [randomLetter.letter];
            
            // إضافة 3 حروف عشوائية أخرى كخيارات خاطئة
            while (options.length < 4) {
                const randomIndex = Math.floor(Math.random() * arabicLetters.length);
                const randomLetter = arabicLetters[randomIndex].letter;
                if (!options.includes(randomLetter)) {
                    options.push(randomLetter);
                }
            }
            
            // خلط الخيارات عشوائياً
            shuffleArray(options);
            
            // إضافة الخيارات إلى واجهة اللعبة
            gameOptionsElement.innerHTML = '';
            options.forEach(option => {
                const button = document.createElement('button');
                button.className = 'game-option';
                button.textContent = option;
                button.addEventListener('click', () => checkAnswer(option, button));
                gameOptionsElement.appendChild(button);
            });
            
            gameFeedbackElement.textContent = '';
            gameFeedbackElement.style.color = '';
        }
        
        // إنشاء تأثيرات القلوب الطائرة
        function createFlyingHearts(count) {
            const colors = ['#FF6B6B', '#FFD700', '#4CAF50', '#9C27B0', '#2196F3'];
            
            for (let i = 0; i < count; i++) {
                const heart = document.createElement('div');
                heart.className = 'heart';
                heart.innerHTML = '❤️';
                heart.style.left = `${Math.random() * 100}vw`;
                heart.style.top = `${Math.random() * 50 + 50}vh`;
                heart.style.fontSize = `${Math.random() * 2 + 1.5}rem`;
                heart.style.color = colors[Math.floor(Math.random() * colors.length)];
                heart.style.animationDuration = `${Math.random() * 2 + 2}s`;
                
                document.body.appendChild(heart);
                
                // إزالة القلب بعد انتهاء الرسوم المتحركة
                setTimeout(() => {
                    heart.remove();
                }, 3000);
            }
        }
        
        // إنشاء تأثيرات الألعاب النارية
        function createFireworks(count) {
            const colors = ['#FF6B6B', '#FFD700', '#4CAF50', '#9C27B0', '#2196F3'];
            
            for (let i = 0; i < count; i++) {
                const firework = document.createElement('div');
                firework.className = 'firework';
                firework.style.left = `${Math.random() * 100}vw`;
                firework.style.top = `${Math.random() * 50 + 50}vh`;
                firework.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                firework.style.boxShadow = `0 0 10px ${colors[Math.floor(Math.random() * colors.length)]}`;
                firework.style.animationDuration = `${Math.random() * 0.5 + 0.5}s`;
                
                document.body.appendChild(firework);
                
                // إزالة الألعاب النارية بعد انتهاء الرسوم المتحركة
                setTimeout(() => {
                    firework.remove();
                }, 1000);
            }
        }
        
        // إنشاء لعبة اختيار الحرف
        function generateGame() {
            // اختيار حرف عشوائي للحصول على سؤال متنوع
            const randomIndex = Math.floor(Math.random() * arabicLetters.length);
            const questionLetter = arabicLetters[randomIndex];
            correctAnswer = questionLetter.letter;
            
            // إنشاء سؤال
            const questionTypes = [
                `ما هو حرف "${questionLetter.name}"؟`,
                `إختر الحرف "${questionLetter.name}"`,
                `أي من هذه الحروف هو "${questionLetter.name}"؟`,
                `ما هو الحرف الذي ينطق "${questionLetter.sound}"؟`
            ];
            const randomQuestion = questionTypes[Math.floor(Math.random() * questionTypes.length)];
            gameQuestionElement.textContent = randomQuestion;
            
            // إنشاء خيارات عشوائية
            const options = [questionLetter.letter];
            
            // إضافة 3 حروف عشوائية أخرى كخيارات خاطئة
            while (options.length < 4) {
                const randomIndex = Math.floor(Math.random() * arabicLetters.length);
                const randomLetter = arabicLetters[randomIndex].letter;
                if (!options.includes(randomLetter)) {
                    options.push(randomLetter);
                }
            }
            
            // خلط الخيارات عشوائياً
            shuffleArray(options);
            
            // إضافة الخيارات إلى واجهة اللعبة
            gameOptionsElement.innerHTML = '';
            options.forEach(option => {
                const button = document.createElement('button');
                button.className = 'game-option';
                button.textContent = option;
                button.addEventListener('click', () => checkAnswer(option, button));
                gameOptionsElement.appendChild(button);
            });
            
            gameFeedbackElement.textContent = '';
            gameFeedbackElement.style.color = '';
        }
        
        // التحقق من الإجابة
        function checkAnswer(selectedLetter, buttonElement) {
            const options = document.querySelectorAll('.game-option');
            
            // تعطيل جميع الأزرار بعد الاختيار
            options.forEach(option => {
                option.style.pointerEvents = 'none';
            });
            
            questionsAnswered++;
            questionsAnsweredElement.textContent = questionsAnswered;
            
            if (selectedLetter === correctAnswer) {
                // الإجابة صحيحة
                buttonElement.classList.add('correct');
                gameFeedbackElement.textContent = 'إجابة صحيحة! أحسنت!';
                gameFeedbackElement.style.color = '#4CAF50';
                gameScore += 10;
                correctAnswers++;
                
                // تشجيع الطفل باسمه
                setTimeout(() => {
                    const encouragements = [
                        `أحسنت يا ${childName}! أنت ذكي جداً!`,
                        `ممتاز يا ${childName}! إجابة صحيحة!`,
                        `رائع يا ${childName}! أنت تتعلم بسرعة!`,
                        `إجابة صحيحة يا ${childName}! أنت مبدع!`,
                        `عظيم يا ${childName}! أنت تتفوق!`
                    ];
                    const randomEncouragement = encouragements[Math.floor(Math.random() * encouragements.length)];
                    speakText(randomEncouragement);
                }, 500);
                
                // تأثير النجاح
                gameQuestionElement.classList.add('celebration');
                
                // إنشاء تأثيرات القلوب الطائرة والألعاب النارية
                createFlyingHearts(15);
                createFireworks(20);
                
                // تشغيل صوت نجاح
                playSuccessSound();
                
                setTimeout(() => {
                    gameQuestionElement.classList.remove('celebration');
                }, 500);
            } else {
                // الإجابة خاطئة
                buttonElement.classList.add('incorrect');
                gameFeedbackElement.textContent = `ليس صحيح! الإجابة هي: ${correctAnswer}`;
                gameFeedbackElement.style.color = '#F44336';
                
                // تشجيع الطفل للنجاح القادم
                setTimeout(() => {
                    const encouragements = [
                        `لا بأس يا ${childName}! حاول مرة أخرى!`,
                        `أكمل المحاولة يا ${childName}! أنت قادر على النجاح!`,
                        `لا تستسلم يا ${childName}! حاول مرة أخرى!`,
                        `هذه فرصة للتعلم يا ${childName}! ستنجح في المرة القادمة!`,
                        `حاول مرة أخرى يا ${childName}! أنا أثق فيك!`
                    ];
                    const randomEncouragement = encouragements[Math.floor(Math.random() * encouragements.length)];
                    speakText(randomEncouragement);
                }, 500);
                
                // إظهار الإجابة الصحيحة
                options.forEach(option => {
                    if (option.textContent === correctAnswer) {
                        option.classList.add('correct');
                    }
                });
            }
            
            gameScoreElement.textContent = gameScore;
            correctAnswersElement.textContent = correctAnswers;
            
            // إعادة تمكين الأزرار بعد 3 ثوانٍ وإنشاء لعبة جديدة
            setTimeout(() => {
                generateGame();
            }, 3000);
        }
        
        // تشغيل صوت النجاح
        function playSuccessSound() {
            // إنشاء صوت نجاح باستخدام Web Audio API
            try {
                const audioContext = new (window.AudioContext || window.webkitAudioContext)();
                
                // نغمة مرحة للأطفال
                const playNote = (frequency, startTime, duration) => {
                    const oscillator = audioContext.createOscillator();
                    const gainNode = audioContext.createGain();
                    
                    oscillator.connect(gainNode);
                    gainNode.connect(audioContext.destination);
                    
                    oscillator.frequency.setValueAtTime(frequency, audioContext.currentTime + startTime);
                    
                    gainNode.gain.setValueAtTime(0.3, audioContext.currentTime + startTime);
                    gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + startTime + duration);
                    
                    oscillator.start(audioContext.currentTime + startTime);
                    oscillator.stop(audioContext.currentTime + startTime + duration);
                };
                
                // نغمة سعيدة للأطفال
                playNote(523.25, 0, 0.2);  // C5
                playNote(659.25, 0.2, 0.2); // E5
                playNote(783.99, 0.4, 0.3); // G5
                
            } catch (e) {
                console.log('Web Audio API غير مدعوم في هذا المتصفح');
            }
        }
        
        // بدء لعبة جديدة
        function newGame() {
            gameScore = 0;
            correctAnswers = 0;
            questionsAnswered = 0;
            gameScoreElement.textContent = gameScore;
            correctAnswersElement.textContent = correctAnswers;
            questionsAnsweredElement.textContent = questionsAnswered;
            generateGame();
        }
        
        // تبديل التبويبات
        function switchTab(tabName) {
            tabs.forEach(tab => {
                if (tab.dataset.tab === tabName) {
                    tab.classList.add('active');
                } else {
                    tab.classList.remove('active');
                }
            });
            
            contentSections.forEach(section => {
                if (section.id === `${tabName}-section`) {
                    section.classList.add('active');
                } else {
                    section.classList.remove('active');
                }
            });
            
            if (tabName === 'game') {
                generateGame();
            }
        }
        
        // دخل لخلط المصفوفة عشوائياً
        function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
            return array;
        }
        
        // إضافة مستمعي الأحداث
        playSoundButton.addEventListener('click', playLetterSound);
        watchVideoButton.addEventListener('click', openYouTubeVideo);
        videoPreviewElement.addEventListener('click', openYouTubeVideo);
        prevLetterButton.addEventListener('click', prevLetter);
        nextLetterButton.addEventListener('click', nextLetter);
        newGameButton.addEventListener('click', newGame);
        askLetterGameButton.addEventListener('click', askAboutLetterInGame);
        
        // إضافة مستمعي الأحداث للتبويبات
        tabs.forEach(tab => {
            tab.addEventListener('click', () => {
                switchTab(tab.dataset.tab);
            });
        });
        
        // تهيئة التطبيق
        updateLetter();
        updateAllLettersDisplay();
        
        // إضافة تأثيرات تفاعلية إضافية
        currentLetterElement.addEventListener('click', playLetterSound);
        
        // ترتيب النص في حقل الإدخال عند تحميل الصفحة
        childNameInput.focus();
    </script>
</body>
</html>
