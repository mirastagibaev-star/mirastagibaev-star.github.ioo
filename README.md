<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GT Car Service - Профессиональный автосервис в Алматы</title>
    <!-- Firebase SDK -->
    <script type="module">
        // Import the functions you need from the SDKs you need
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-app.js";
        import { getFirestore } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-firestore.js";
        
        // Your web app's Firebase configuration
        const firebaseConfig = {
            apiKey: "AIzaSyDl7y8eCZ6whgfcEE5y5Wmd3zXfSdCjgK0",
            authDomain: "gt-car-service.firebaseapp.com",
            projectId: "gt-car-service",
            storageBucket: "gt-car-service.firebasestorage.app",
            messagingSenderId: "9989551998",
            appId: "1:9989551998:web:e4ba23be8259acb24f252f",
            measurementId: "G-BGBXVGC007"
        };

        // Initialize Firebase
        const app = initializeApp(firebaseConfig);
        const db = getFirestore(app);
        
        // Делаем db глобально доступной
        window.db = db;
    </script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            color: #333;
            background-color: #f4f4f4;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        header {
            background: linear-gradient(135deg, #1e3c72, #2a5298);
            color: white;
            padding: 1rem 0;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 2rem;
            font-weight: bold;
            color: #ffd700;
        }

        .logo span {
            color: white;
        }

        nav ul {
            display: flex;
            list-style: none;
        }

        nav ul li {
            margin-left: 2rem;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
        }

        nav ul li a:hover {
            color: #ffd700;
        }

        /* Hero Section */
        .hero {
            background: url('https://images.unsplash.com/photo-1503376780353-7e6692767b70?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80') no-repeat center center/cover;
            height: 80vh;
            display: flex;
            align-items: center;
            text-align: center;
            color: white;
            position: relative;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.6);
        }

        .hero-content {
            position: relative;
            z-index: 1;
            max-width: 800px;
            margin: 0 auto;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }

        .hero p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.5);
        }

        .btn {
            display: inline-block;
            background: #ff6b35;
            color: white;
            padding: 12px 30px;
            text-decoration: none;
            border-radius: 5px;
            font-weight: bold;
            transition: background 0.3s;
            border: none;
            cursor: pointer;
            font-size: 1rem;
        }

        .btn:hover {
            background: #e55a2b;
        }

        .btn:disabled {
            background: #cccccc;
            cursor: not-allowed;
        }

        /* Services */
        .services {
            padding: 5rem 0;
            background: white;
        }

        .section-title {
            text-align: center;
            margin-bottom: 3rem;
        }

        .section-title h2 {
            font-size: 2.5rem;
            color: #2a5298;
            margin-bottom: 1rem;
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .service-card {
            background: white;
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            text-align: center;
            transition: transform 0.3s;
        }

        .service-card:hover {
            transform: translateY(-5px);
        }

        .service-icon {
            font-size: 3rem;
            color: #2a5298;
            margin-bottom: 1rem;
        }

        .service-card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: #333;
        }

        /* About */
        .about {
            padding: 5rem 0;
            background: #f8f9fa;
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .about-text h2 {
            font-size: 2.5rem;
            color: #2a5298;
            margin-bottom: 1.5rem;
        }

        .about-text p {
            margin-bottom: 1.5rem;
            font-size: 1.1rem;
        }

        .about-image img {
            width: 100%;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        /* Contacts */
        .contacts {
            padding: 5rem 0;
            background: white;
        }

        .contacts-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
        }

        .contact-info {
            background: #2a5298;
            color: white;
            padding: 3rem;
            border-radius: 10px;
        }

        .contact-info h3 {
            font-size: 2rem;
            margin-bottom: 2rem;
            color: #ffd700;
        }

        .contact-item {
            margin-bottom: 1.5rem;
            display: flex;
            align-items: center;
        }

        .contact-item i {
            font-size: 1.5rem;
            margin-right: 1rem;
            color: #ffd700;
        }

        .contact-form {
            background: #f8f9fa;
            padding: 3rem;
            border-radius: 10px;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: bold;
        }

        .form-group input,
        .form-group textarea,
        .form-group select {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 1rem;
        }

        .form-group textarea {
            height: 120px;
            resize: vertical;
        }

        .form-group select {
            background-color: white;
            cursor: pointer;
        }

        /* Success Message */
        .success-message {
            display: none;
            color: #2e7d32;
            background-color: #e8f5e8;
            padding: 15px;
            border-radius: 5px;
            margin-top: 20px;
            border: 1px solid #c8e6c9;
            text-align: center;
        }

        .error-message {
            display: none;
            color: #d32f2f;
            background-color: #ffebee;
            padding: 15px;
            border-radius: 5px;
            margin-top: 20px;
            border: 1px solid #ffcdd2;
            text-align: center;
        }

        /* Loading */
        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid #f3f3f3;
            border-top: 3px solid #3498db;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Footer */
        footer {
            background: #333;
            color: white;
            text-align: center;
            padding: 2rem 0;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                text-align: center;
            }

            nav ul {
                margin-top: 1rem;
                flex-direction: column;
            }

            nav ul li {
                margin: 0.5rem 0;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .about-content,
            .contacts-grid {
                grid-template-columns: 1fr;
            }

            .hero {
                height: 60vh;
            }
        }
    </style>
</head>

<body>

    <!-- Header -->
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">GT<span>CarService</span></div>
                <nav>
                    <ul>
                        <li><a href="#services">Услуги</a></li>
                        <li><a href="#about">О нас</a></li>
                        <li><a href="#contacts">Контакты</a></li>
                        <li><a href="#booking">Запись</a></li>
                    </ul>
                </nav>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="container">
            <div class="hero-content">
                <h1>Профессиональный автосервис в Алматы</h1>
                <p>Качественный ремонт и обслуживание автомобилей любой сложности. Работаем с 2025 года.</p>
                <a href="#contacts" class="btn">Записаться на обслуживание</a>
            </div>
        </div>
    </section>

    <!-- Services -->
    <section id="services" class="services">
        <div class="container">
            <div class="section-title">
                <h2>Наши услуги</h2>
                <p>Полный спектр услуг по ремонту и обслуживанию автомобилей</p>
            </div>

            <div class="services-grid">
                <div class="service-card">
                    <div class="service-icon">🔧</div>
                    <h3>Диагностика</h3>
                    <p>Компьютерная диагностика двигателя, ходовой части и электронных систем</p>
                </div>

                <div class="service-card">
                    <div class="service-icon">🛢️</div>
                    <h3>Техобслуживание</h3>
                    <p>Регулярное техническое обслуживание и замена расходных материалов</p>
                </div>

                <div class="service-card">
                    <div class="service-icon">🚗</div>
                    <h3>Ремонт двигателя</h3>
                    <p>Капитальный и текущий ремонт двигателей любой сложности</p>
                </div>

                <div class="service-card">
                    <div class="service-icon">⚡</div>
                    <h3>Электрика</h3>
                    <p>Диагностика и ремонт электрооборудования автомобиля</p>
                </div>

                <div class="service-card">
                    <div class="service-icon">🛞</div>
                    <h3>Шиномонтаж</h3>
                    <p>Сезонная замена шин, балансировка и ремонт колес</p>
                </div>

                <div class="service-card">
                    <div class="service-icon">🎛️</div>
                    <h3>Чип-тюнинг</h3>
                    <p>Настройка ЭБУ для улучшения характеристик</p>
                </div>
            </div>
        </div>
    </section>

    <!-- About -->
    <section id="about" class="about">
        <div class="container">
            <div class="about-content">
                <div class="about-text">
                    <h2>О нашем сервисе</h2>
                    <p>GT Car Service - это современный автосервис в Алматы, оснащенный передовым оборудованием и укомплектованный опытными специалистами.</p>
                    <p>Мы работаем с 2025 года и за это время заслужили немало хороших отзывов о нас.</p>
                    <p>Наши мастера регулярно проходят обучение и повышают квалификацию.</p>
                    <a href="#contacts" class="btn">Связаться с нами</a>
                </div>

                <div class="about-image">
                    <img src="https://images.unsplash.com/photo-1621461133947-f63381c2f7f8?ixlib=rb-4.0.3&auto=format&fit=crop&w=1974&q=80" alt="Наш автосервис">
                </div>
            </div>
        </div>
    </section>

    <!-- Contacts -->
    <section id="contacts" class="contacts">
        <div class="container">
            <div class="section-title">
                <h2>Контакты</h2>
                <p>Свяжитесь с нами удобным для вас способом</p>
            </div>

            <div class="contacts-grid">

                <!-- Left Info -->
                <div class="contact-info">
                    <h3>Наши контакты</h3>

                    <div class="contact-item">
                        <i>📍</i>
                        <div>
                            <strong>Адрес:</strong><br>
                            Алматы, ул. Ауэзова 126
                        </div>
                    </div>

                    <div class="contact-item">
                        <i>📞</i>
                        <div>
                            <strong>Телефоны:</strong><br>
                            <a href="tel:+77006461728" style="color: white;">+7 700 646 17 28 (Miras)</a><br>
                            <a href="tel:+77472627236" style="color: white;">+7 747 262 7236 (Alexander)</a><br>
                            <a href="tel:+77078333058" style="color: white;">+7 707 833 3058 (Rukhaniat)</a>
                        </div>
                    </div>

                    <div class="contact-item">
                        <i>🕒</i>
                        <div>
                            <strong>График работы:</strong><br>
                            Пн-Пт: 9:00 - 19:00<br>
                            Сб-Вс: 10:00 - 17:00
                        </div>
                    </div>

                    <div class="contact-item">
                        <i>✉️</i>
                        <div>
                            <strong>Email:</strong><br>
                            mirastagibaev@gmail.com
                        </div>
                    </div>
                </div>

                <!-- Form -->
                <div class="contact-form">
                    <h3>Форма обратной связи</h3>

                    <!-- НОВАЯ ФОРМА С БАЗОЙ ДАННЫХ -->
                    <form id="contact-form">
                        <div class="form-group">
                            <label for="name">Ваше имя *</label>
                            <input type="text" id="name" name="name" required>
                        </div>

                        <div class="form-group">
                            <label for="phone">Телефон *</label>
                            <input type="tel" id="phone" name="phone" required placeholder="+7 777 123 45 67">
                        </div>

                        <div class="form-group">
                            <label for="car">Марка автомобиля</label>
                            <input type="text" id="car" name="car" placeholder="Toyota Camry">
                        </div>

                        <div class="form-group">
                            <label for="service">Услуга</label>
                            <select id="service" name="service">
                                <option value="">Выберите услугу</option>
                                <option value="Диагностика">Диагностика</option>
                                <option value="Техобслуживание">Техобслуживание</option>
                                <option value="Ремонт двигателя">Ремонт двигателя</option>
                                <option value="Электрика">Электрика</option>
                                <option value="Шиномонтаж">Шиномонтаж</option>
                                <option value="Чип-тюнинг">Чип-тюнинг</option>
                                <option value="Другое">Другое</option>
                            </select>
                        </div>

                        <div class="form-group">
                            <label for="message">Сообщение</label>
                            <textarea id="message" name="message" placeholder="Опишите проблему или задайте вопрос..."></textarea>
                        </div>

                        <button type="submit" class="btn" id="submit-btn">
                            <span id="btn-text">Отправить заявку</span>
                            <span id="btn-loading" class="loading" style="display: none;"></span>
                        </button>
                    </form>

                    <div id="success-message" class="success-message">
                        ✅ Заявка успешно отправлена! Мы свяжемся с вами в ближайшее время.
                    </div>
                    
                    <div id="error-message" class="error-message">
                        ❌ Произошла ошибка при отправке. Попробуйте позже или позвоните нам.
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <p>&copy; 2025 GT Car Service. Проект созданный студентами IITU.</p>
            <p>Автосервис в Алматы | Ремонт и обслуживание автомобилей</p>
        </div>
    </footer>

    <script>
        // Импортируем функции Firestore
        import { collection, addDoc, serverTimestamp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-firestore.js";

        // Обработка формы
        document.getElementById('contact-form').addEventListener('submit', async (e) => {
            e.preventDefault();
            
            // Получаем элементы
            const submitBtn = document.getElementById('submit-btn');
            const btnText = document.getElementById('btn-text');
            const btnLoading = document.getElementById('btn-loading');
            const successMessage = document.getElementById('success-message');
            const errorMessage = document.getElementById('error-message');
            const form = e.target;
            
            // Скрываем предыдущие сообщения
            successMessage.style.display = 'none';
            errorMessage.style.display = 'none';
            
            // Показываем загрузку
            btnText.textContent = 'Отправка...';
            btnLoading.style.display = 'inline-block';
            submitBtn.disabled = true;
            
            // Собираем данные
            const formData = {
                name: document.getElementById('name').value,
                phone: document.getElementById('phone').value,
                car: document.getElementById('car').value,
                service: document.getElementById('service').value,
                message: document.getElementById('message').value,
                date: new Date().toLocaleString('ru-RU'),
                timestamp: serverTimestamp(),
                status: 'новая'
            };
            
            try {
                // 1. Сохраняем в Firebase Firestore
                const docRef = await addDoc(collection(window.db, 'requests'), formData);
                console.log('✅ Данные сохранены в Firebase, ID документа:', docRef.id);
                
                // 2. Отправляем на FormSubmit (для получения email)
                const formSubmitURL = 'https://formsubmit.co/ajax/mirastagibaev@gmail.com';
                const formSubmitData = new FormData();
                
                formSubmitData.append('_subject', 'Новая заявка с сайта GT Car Service');
                formSubmitData.append('Имя', formData.name);
                formSubmitData.append('Телефон', formData.phone);
                formSubmitData.append('Автомобиль', formData.car);
                formSubmitData.append('Услуга', formData.service);
                formSubmitData.append('Сообщение', formData.message);
                formSubmitData.append('_captcha', 'false');
                formSubmitData.append('_template', 'table');
                
                await fetch(formSubmitURL, {
                    method: 'POST',
                    body: formSubmitData
                });
                
                // 3. Показываем успешное сообщение
                successMessage.style.display = 'block';
                form.reset();
                
                // 4. Прячем сообщение через 5 секунд
                setTimeout(() => {
                    successMessage.style.display = 'none';
                }, 5000);
                
            } catch (error) {
                console.error('❌ Ошибка при отправке:', error);
                errorMessage.style.display = 'block';
                
                // Прячем сообщение об ошибке через 5 секунд
                setTimeout(() => {
                    errorMessage.style.display = 'none';
                }, 5000);
                
            } finally {
                // Восстанавливаем кнопку
                btnText.textContent = 'Отправить заявку';
                btnLoading.style.display = 'none';
                submitBtn.disabled = false;
            }
        });
        
        // Плавная прокрутка
        document.querySelectorAll('nav a').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    targetElement.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });
    </script>

</body>
</html>
