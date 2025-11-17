<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>מש"א 7000 - הנדסת העתיד</title>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Heebo:wght@300;400;700;900&display=swap" rel="stylesheet">

    <style>
        /* --- משתני עיצוב גלובליים --- */
        :root {
            --primary-color: #0d47a1; /* כחול איכותי ועמוק */
            --secondary-color: #f5f5f5; /* אפור בהיר */
            --dark-color: #212121;
            --light-color: #ffffff;
            --font-main: 'Heebo', sans-serif;
            --transition-speed: 0.3s;
        }

        /* --- איפוס ועיצוב בסיסי --- */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: var(--font-main);
            line-height: 1.6;
            color: var(--dark-color);
            background-color: var(--light-color);
        }

        html {
            scroll-behavior: smooth;
        }

        h1, h2, h3 {
            font-weight: 900;
            line-height: 1.2;
        }
        
        h2 {
            font-size: 2.5rem;
            margin-bottom: 40px;
            text-align: center;
        }

        p {
            font-weight: 300;
            font-size: 1.1rem;
            margin-bottom: 20px;
        }

        a {
            text-decoration: none;
            color: var(--primary-color);
            transition: color var(--transition-speed);
        }

        img {
            max-width: 100%;
            height: auto;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 25px;
        }

        .section {
            padding: 100px 0;
        }

        /* --- כותרת עליונה (Header) עם תפריט נייד --- */
        .main-header {
            background: rgba(var(--dark-color), 0.85); /* רקע כהה שקוף */
            padding: 15px 0;
            position: fixed;
            width: 100%;
            z-index: 1000;
            backdrop-filter: blur(5px);
        }

        .main-header .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .main-header .logo {
            font-size: 2rem;
            font-weight: 900;
            color: var(--light-color);
        }

        /* ניווט רגיל */
        .main-nav a {
            color: var(--light-color);
            margin-right: 30px;
            font-weight: 400;
            position: relative;
        }
        
        .main-nav a:after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            display: block;
            margin-top: 5px;
            right: 0;
            background: var(--primary-color);
            transition: width var(--transition-speed) ease;
        }
        
        .main-nav a:hover:after {
            width: 100%;
        }

        /* כפתור המבורגר (מוסתר ב-Desktop) */
        .menu-toggle {
            display: none;
            flex-direction: column;
            cursor: pointer;
            gap: 5px;
            padding: 10px;
        }
        
        .menu-toggle .bar {
            width: 30px;
            height: 3px;
            background-color: var(--light-color);
            transition: all var(--transition-speed) ease;
        }

        /* תפריט נייד פתוח (מוסתר כברירת מחדל) */
        .main-nav.active {
            display: flex;
            flex-direction: column;
            position: absolute;
            top: 100%;
            right: 0;
            width: 100%;
            background: var(--dark-color);
            padding: 20px 0;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .main-nav.active a {
            margin: 10px 0;
        }

        /* --- אזור כותרת ראשית (Hero) עם אנימציה --- */
        .hero {
            height: 100vh;
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
            color: var(--light-color);
            overflow: hidden;
            background: var(--dark-color); /* רקע שחור כשאין תמונות */
        }

        /* האלמנט שמכיל את תמונות הרקע המתחלפות */
        .hero-background {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-size: cover;
            background-position: center;
            z-index: 1;
            animation: changeBackground 24s infinite linear;
            opacity: 0.7; /* שקיפות קלה לרקע */
        }

        /* ----- אנימציית הרקע ----- */
        @keyframes changeBackground {
            0%, 100% { background-image: url('https://images.unsplash.com/photo-1504955322921-b3b34381c810?auto=format&fit=crop&w=1920&q=80'); }
            25% { background-image: url('https://images.unsplash.com/photo-1581090444101-f3c0b4f8f4c3?auto=format&fit=crop&w=1920&q=80'); }
            50% { background-image: url('https://images.unsplash.com/photo-1552519507-da3b142c6e3d?auto=format&fit=crop&w=1920&q=80'); }
            75% { background-image: url('https://images.unsplash.com/photo-1543349931-98b6710b379e?auto=format&fit=crop&w=1920&q=80'); }
        }

        .hero-content {
            z-index: 5;
            padding: 40px;
            background: rgba(0, 0, 0, 0.65); /* שכבה כהה חזקה יותר */
            border-radius: 10px;
            max-width: 800px;
        }

        .hero-content h1 {
            font-size: 5rem;
            margin-bottom: 10px;
            color: var(--primary-color);
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }

        .hero-content p {
            font-size: 1.8rem;
            font-weight: 300;
            margin-bottom: 40px;
            color: var(--light-color);
        }

        .btn {
            display: inline-block;
            background: var(--primary-color);
            color: var(--light-color);
            padding: 15px 40px;
            border-radius: 50px; /* כפתור עגול ומודרני */
            font-size: 1.2rem;
            font-weight: 700;
            transition: all var(--transition-speed) ease;
            border: none;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(var(--primary-color), 0.4);
        }

        .btn:hover {
            background: #083c74;
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(var(--primary-color), 0.6);
        }

        /* --- אזור 'אודות' --- */
        #about {
            background: var(--light-color);
            text-align: center;
        }
        
        #about p {
            max-width: 800px;
            margin: 0 auto 20px auto;
        }

        /* --- דבר המנכ"ל --- */
        #ceo {
            background: var(--secondary-color);
        }
        
        .ceo-wrapper {
            display: flex;
            align-items: center;
            gap: 80px;
            direction: ltr; /* מחליף כיוון לסידור תמונה/טקסט נוח */
            text-align: left;
        }
        
        .ceo-img {
            flex-basis: 300px;
            flex-shrink: 0;
            position: relative;
            z-index: 2;
        }

        .ceo-img img {
            width: 300px;
            height: 300px;
            object-fit: cover;
            border-radius: 8px; /* קווים נקיים */
            box-shadow: 10px 10px 0px 0px var(--primary-color); /* אפקט עומק עיצובי */
        }
        
        .ceo-text {
            flex-grow: 1;
            direction: rtl; /* מחזיר את הטקסט לעברית תקינה */
            text-align: right;
        }

        .ceo-text blockquote {
            font-size: 1.6rem;
            font-style: italic;
            font-weight: 300;
            color: var(--dark-color);
            border-right: 5px solid var(--primary-color);
            padding-right: 30px;
            margin: 0 0 20px 0;
        }
        
        .ceo-text strong {
            display: block;
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--primary-color);
        }

        /* --- טופס יצירת קשר --- */
        #contact {
            background: var(--light-color);
        }

        .contact-form {
            max-width: 600px;
            margin: 0 auto;
            padding: 40px;
            border: 1px solid #ddd;
            border-radius: 12px;
            box-shadow: 0 5px 25px rgba(0, 0, 0, 0.08);
        }
        
        .form-group {
            margin-bottom: 25px;
        }
        
        .form-control {
            width: 100%;
            padding: 15px;
            font-size: 1rem;
            font-family: var(--font-main);
            border: 1px solid #ccc;
            border-radius: 8px;
            transition: border-color var(--transition-speed);
        }
        
        .form-control:focus {
            border-color: var(--primary-color);
            outline: none;
            box-shadow: 0 0 0 2px rgba(var(--primary-color), 0.2);
        }
        
        textarea.form-control {
            height: 180px;
            resize: vertical;
        }
        
        .contact-form .btn {
            width: 100%;
        }

        /* --- פוטר --- */
        .main-footer {
            background: var(--dark-color);
            color: var(--light-color);
            text-align: center;
            padding: 40px 0;
        }
        
        .main-footer p {
            margin: 0;
            font-weight: 300;
        }

        /* --- רספונסיביות למובייל (Mobile First) --- */
        @media (max-width: 900px) {
            .ceo-wrapper {
                flex-direction: column;
                align-items: center;
                gap: 40px;
                direction: rtl; /* מחזיר הכל לעברית */
                text-align: center;
            }
            
            .ceo-img {
                order: 1; /* שם את התמונה למעלה */
            }
            
            .ceo-text {
                order: 2;
                text-align: center;
            }
            
            .ceo-text blockquote {
                border-right: none;
                border-top: 5px solid var(--primary-color);
                padding-right: 0;
                padding-top: 20px;
                margin-top: 20px;
            }
        }

        @media (max-width: 768px) {
            .section {
                padding: 60px 0;
            }
            
            h2 {
                font-size: 2rem;
            }
            
            .hero-content h1 {
                font-size: 3rem;
            }

            .hero-content p {
                font-size: 1.3rem;
            }
            
            /* תפריט המבורגר מופעל */
            .main-nav {
                display: none;
            }
            
            .menu-toggle {
                display: flex;
            }
            
            .main-nav.active {
                display: flex;
            }

            /* שינוי תצוגת ההמבורגר כשהתפריט פתוח */
            .menu-toggle.active .bar:nth-child(2) {
                opacity: 0;
            }
            .menu-toggle.active .bar:nth-child(1) {
                transform: translateY(8px) rotate(45deg);
            }
            .menu-toggle.active .bar:nth-child(3) {
                transform: translateY(-8px) rotate(-45deg);
            }
        }
    </style>
</head>
<body>

    <header class="main-header">
        <div class="container">
            <a href="#" class="logo">מש"א 7000</a>
            <nav class="main-nav" id="main-nav">
                <a href="#about">אודות</a>
                <a href="#ceo">דבר המנכ"ל</a>
                <a href="#contact" class="btn">צור קשר</a>
            </nav>
            <div class="menu-toggle" id="menu-toggle">
                <div class="bar"></div>
                <div class="bar"></div>
                <div class="bar"></div>
            </div>
        </div>
    </header>

    <main>
        <section class="hero">
            <div class="hero-background"></div> 
            <div class="hero-content">
                <h1>מש"א 7000</h1>
                <p>הנדסת עתיד התחבורה. דיוק. חדשנות. איכות.</p>
                <a href="#contact" class="btn">צור קשר עכשיו</a>
            </div>
        </section>

        <section id="about" class="section">
            <div class="container">
                <h2>אודות מש"א 7000: הדיוק שמאחורי המכונה</h2>
                <p>
                    מש"א 7000 אינו רק מפעל לייצור מכוניות; זהו מרכז חדשנות והנדסה מהמתקדמים בעולם. מאז הקמתנו, חרטנו על דגלנו את ערכי המצוינות, הדיוק והבטיחות. אנו משלבים טכנולוגיות ייצור רובוטיות מתקדמות עם עבודת אומן אנושית, כדי ליצור כלי רכב שהם לא רק אמצעי תחבורה, אלא יצירת אמנות הנדסית. פס הייצור שלנו פועל בסנכרון מושלם 24/7.
                </p>
                <p>
                    אנו מתמחים בייצור רכבים חשמליים (EV) פורצי דרך, תוך שימוש בחומרים ברי קיימא והתמקדות בצמצום טביעת הרגל הפחמנית. החזון שלנו הוא להוביל את מהפכת התחבורה הנקייה, רכב אחד בכל פעם, תוך שמירה על סטנדרטים בלתי מתפשרים של איכות ואמינות.
                </p>
            </div>
        </section>

        <section id="ceo" class="section">
            <div class="container">
                <h2>מנהיגות שמובילה לחדשנות</h2>
                <div class="ceo-wrapper">
                    <div class="ceo-img">
                        <img src="https://images.unsplash.com/photo-1568602471122-7832951cc4c5?auto=format&fit=crop&w=300&q=80" alt="מנכ'ל מש'א 7000">
                    </div>
                    <div class="ceo-text">
                        <blockquote>
                            "במש"א 7000, אנחנו לא בונים רק מכוניות – אנחנו בונים את העתיד. כל בורג, כל שבב וכל קו עיצובי הם עדות למחויבות הבלתי מתפשרת שלנו לאיכות. האנשים שלנו הם המנוע האמיתי מאחורי ההצלחה הזו, ואני גאה להוביל צוות שדוחף את גבולות האפשרי מדי יום."
                        </blockquote>
                        <strong>יצחק כהן, מנכ"ל מש"א 7000</strong>
                    </div>
                </div>
            </div>
        </section>

        <section id="contact" class="section">
            <div class="container">
                <h2>צרו איתנו קשר</h2>
                <p style="text-align: center; max-width: 600px; margin: 0 auto 30px auto; font-weight: 300;">
                    יש לכם שאלה? מעוניינים בשיתוף פעולה? השאירו פרטים ונציג שלנו יחזור אליכם בהקדם.
                </p>
                
                <form name="contact" class="contact-form" method="POST" data-netlify="true">
                    <input type="hidden" name="form-name" value="contact" /> 
                    <div class="form-group">
                        <label for="name">שם מלא</label>
                        <input type="text" name="name" id="name" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="email">דוא"ל</label>
                        <input type="email" name="email" id="email" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="phone">טלפון (אופציונלי)</label>
                        <input type="tel" name="phone" id="phone" class="form-control">
                    </div>
                    <div class="form-group">
                        <label for="message">הודעה</label>
                        <textarea name="message" id="message" class="form-control" required></textarea>
                    </div>
                    <button type="submit" class="btn">שלח הודעה</button>
                </form>
            </div>
        </section>
    </main>

    <footer class="main-footer">
        <p>כל הזכויות שמורות © <span id="year"></span> מש"א 7000 | הנדסת עתיד.</p>
    </footer>

    <script>
        // --- JavaScript לאלמנטים אינטראקטיביים ---
        
        // 1. עדכון שנת זכויות יוצרים אוטומטית
        document.getElementById('year').textContent = new Date().getFullYear();

        // 2. לוגיקה לתפריט הנייד (המבורגר)
        const nav = document.getElementById('main-nav');
        const toggle = document.getElementById('menu-toggle');
        
        toggle.addEventListener('click', () => {
            nav.classList.toggle('active');
            toggle.classList.toggle('active');
        });

        // סגור את התפריט בלחיצה על קישור (במובייל)
        document.querySelectorAll('.main-nav a').forEach(link => {
            link.addEventListener('click', () => {
                if (window.innerWidth <= 768) {
                    nav.classList.remove('active');
                    toggle.classList.remove('active');
                }
            });
        });

    </script>

</body>
</html>
