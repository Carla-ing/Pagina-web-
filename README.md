<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema de Regularización de Transporte - Nueva Tarjeta Digital</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        header {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            padding: 1rem 0;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            transition: all 0.3s ease;
        }

        header.scrolled {
            background: rgba(255, 255, 255, 0.95);
            box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            color: white;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo::before {
            content: "🚌";
            font-size: 2rem;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            transition: all 0.3s ease;
            padding: 0.5rem 1rem;
            border-radius: 25px;
        }

        .nav-links a:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
        }

        .hero {
            margin-top: 80px;
            padding: 4rem 0;
            text-align: center;
            color: white;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            animation: fadeInUp 1s ease;
        }

        .hero p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            animation: fadeInUp 1s ease 0.2s both;
        }

        .cta-button {
            background: linear-gradient(45deg, #ff6b6b, #feca57);
            color: white;
            padding: 1rem 2rem;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
            animation: fadeInUp 1s ease 0.4s both;
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
        }

        .card-demo {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 2rem;
            margin: 2rem auto;
            max-width: 400px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            animation: float 3s ease-in-out infinite;
        }

        .card {
            background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
            border-radius: 15px;
            padding: 1.5rem;
            color: white;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -50%;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            transform: rotate(45deg);
            animation: cardShine 2s infinite;
        }

        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
        }

        .card-number {
            font-size: 1.2rem;
            font-family: 'Courier New', monospace;
            letter-spacing: 2px;
        }

        .features {
            background: white;
            padding: 4rem 0;
            margin: 2rem 0;
            border-radius: 30px;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .feature-card {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
            padding: 2rem;
            border-radius: 20px;
            text-align: center;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
        }

        .feature-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: left 0.5s;
        }

        .feature-card:hover::before {
            left: 100%;
        }

        .feature-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .process {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 30px;
            padding: 3rem;
            margin: 2rem 0;
            color: white;
        }

        .process-steps {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .step {
            text-align: center;
            padding: 1.5rem;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            transition: all 0.3s ease;
        }

        .step:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: scale(1.05);
        }

        .step-number {
            background: linear-gradient(45deg, #ff9a9e, #fecfef);
            color: #333;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 1.2rem;
            margin: 0 auto 1rem;
        }

        /* Estilos para el registro actualizado */
        .registro {
            background: rgba(255, 255, 255, 0.95);
            padding: 4rem 0;
            margin: 2rem 0;
            border-radius: 30px;
            color: #333;
        }

        .registro-container {
            max-width: 800px;
            margin: 0 auto;
            padding: 0 20px;
            text-align: center;
        }

        .info-box {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 2rem;
            border-radius: 15px;
            margin: 2rem 0;
            text-align: left;
        }

        .info-box h3 {
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .info-box ul {
            list-style: none;
            margin-top: 1rem;
        }

        .info-box li {
            margin: 0.5rem 0;
            padding-left: 1.5rem;
            position: relative;
        }

        .info-box li::before {
            content: "✓";
            position: absolute;
            left: 0;
            color: #28a745;
            font-weight: bold;
        }

        .form-redirect {
            background: white;
            padding: 3rem;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            margin-top: 2rem;
        }

        .form-redirect-icon {
            font-size: 4rem;
            margin-bottom: 1rem;
        }

        .form-redirect h3 {
            color: #333;
            margin-bottom: 1rem;
            font-size: 1.8rem;
        }

        .form-redirect p {
            color: #666;
            margin-bottom: 2rem;
            font-size: 1.1rem;
        }

        .google-form-btn {
            background: linear-gradient(45deg, #4285f4, #34a853);
            color: white;
            padding: 1.2rem 2.5rem;
            border: none;
            border-radius: 50px;
            font-size: 1.2rem;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            margin: 0.5rem;
        }

        .google-form-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 30px rgba(66, 133, 244, 0.3);
        }

        .google-form-btn::before {
            content: "📝";
            font-size: 1.2rem;
        }

        .alternative-info {
            background: #f8f9fa;
            padding: 2rem;
            border-radius: 15px;
            margin-top: 2rem;
            border-left: 4px solid #667eea;
        }

        .alternative-info h4 {
            color: #333;
            margin-bottom: 1rem;
            font-size: 1.2rem;
        }

        .alternative-info p {
            color: #666;
            margin-bottom: 0.5rem;
        }

        footer {
            background: rgba(0, 0, 0, 0.8);
            color: white;
            text-align: center;
            padding: 2rem 0;
            margin-top: 2rem;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }

        @keyframes cardShine {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        .pulse {
            animation: pulse 2s infinite;
        }

        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }
            
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .hero p {
                font-size: 1.1rem;
            }

            .form-redirect {
                padding: 2rem;
            }

            .google-form-btn {
                padding: 1rem 2rem;
                font-size: 1.1rem;
            }
        }
    </style>
</head>
<body>
    <header id="header">
        <nav class="container">
            <div class="logo">TransCard</div>
            <ul class="nav-links">
                <li><a href="#inicio">Inicio</a></li>
                <li><a href="#caracteristicas">Características</a></li>
                <li><a href="#proceso">Proceso</a></li>
                <li><a href="#registro">Registro</a></li>
                <li><a href="#contacto">Contacto</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section class="hero" id="inicio">
            <div class="container">
                <h1>Sistema de Regularización de Transporte</h1>
                <p>La nueva tarjeta digital que revoluciona el transporte público</p>
                <a href="#registro" class="cta-button">Registrarse Ahora</a>
                
                <div class="card-demo">
                    <div class="card">
                        <div class="card-header">
                            <div>
                                <div style="font-weight: bold;">TRANSCARD</div>
                                <div style="font-size: 0.9rem; opacity: 0.8;">Transporte Digital</div>
                            </div>
                            <div style="font-size: 2rem;">💳</div>
                        </div>
                        <div class="card-number">**** **** **** 1234</div>
                        <div style="display: flex; justify-content: space-between; margin-top: 1rem;">
                            <div>
                                <div style="font-size: 0.8rem; opacity: 0.7;">USUARIO</div>
                                <div style="font-size: 0.9rem;">MARÍA GONZÁLEZ</div>
                            </div>
                            <div>
                                <div style="font-size: 0.8rem; opacity: 0.7;">VÁLIDA</div>
                                <div style="font-size: 0.9rem;">12/28</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section class="features" id="caracteristicas">
            <div class="container">
                <h2 style="text-align: center; font-size: 2.5rem; color: #333; margin-bottom: 1rem;">Características Principales</h2>
                <div class="features-grid">
                    <div class="feature-card">
                        <div class="feature-icon">📱</div>
                        <h3>Tecnología NFC</h3>
                        <p>Pago sin contacto rápido y seguro. Solo acerca la tarjeta al lector y listo.</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">💰</div>
                        <h3>Tarifas Diferenciadas</h3>
                        <p>Precios especiales para estudiantes, adultos mayores y usuarios frecuentes.</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">📊</div>
                        <h3>Control Inteligente</h3>
                        <p>Seguimiento en tiempo real de rutas, horarios y patrones de uso del transporte.</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">🛡️</div>
                        <h3>Seguridad Avanzada</h3>
                        <p>Protección de datos personales y transacciones con cifrado de última generación.</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">🌐</div>
                        <h3>Recarga Online</h3>
                        <p>Recarga tu tarjeta desde cualquier lugar usando nuestra aplicación móvil.</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">📈</div>
                        <h3>Reportes Detallados</h3>
                        <p>Consulta tu historial de viajes y gastos en transporte en tiempo real.</p>
                    </div>
                </div>
            </div>
        </section>

        <section class="process" id="proceso">
            <div class="container">
                <h2 style="text-align: center; font-size: 2.5rem; margin-bottom: 1rem;">¿Cómo Funciona?</h2>
                <div class="process-steps">
                    <div class="step">
                        <div class="step-number">1</div>
                        <h3>Registro</h3>
                        <p>Registra tus datos personales y obtén tu tarjeta TransCard en puntos autorizados.</p>
                    </div>
                    <div class="step">
                        <div class="step-number">2</div>
                        <h3>Recarga</h3>
                        <p>Añade saldo a tu tarjeta en línea, puntos de recarga o a través de la app móvil.</p>
                    </div>
                    <div class="step">
                        <div class="step-number">3</div>
                        <h3>Viaja</h3>
                        <p>Acerca tu tarjeta al lector al subir al autobús. El sistema descontará automáticamente.</p>
                    </div>
                    <div class="step">
                        <div class="step-number">4</div>
                        <h3>Controla</h3>
                        <p>Revisa tu historial de viajes y saldo disponible desde la aplicación móvil.</p>
                    </div>
                </div>
            </div>
        </section>

        <section class="registro" id="registro">
            <div class="registro-container">
                <h2 style="font-size: 2.5rem; margin-bottom: 1rem;">Registro de Usuario</h2>
                <p style="font-size: 1.2rem; margin-bottom: 2rem;">Completa tu registro a través de nuestro formulario en línea</p>
                
                <div class="info-box">
                    <h3>📋 Información Importante</h3>
                    <ul>
                        <li>El registro es completamente gratuito</li>
                        <li>Recibirás tu tarjeta en 3-5 días hábiles</li>
                        <li>Puedes recoger tu tarjeta en cualquier punto autorizado</li>
                        <li>Tarifa especial para estudiantes y adultos mayores</li>
                    </ul>
                </div>

                <div class="form-redirect">
                    <div class="form-redirect-icon">🚀</div>
                    <h3>¡Registrate Ahora!</h3>
                    <p>Te redirigiremos a nuestro formulario de registro seguro donde podrás completar todos tus datos de manera rápida y sencilla.</p>
                    
                    <a href="https://docs.google.com/forms/d/1XBmOtqDQX_CRxkFxvp3es55dRHjBdlttp92-P5ZrZUU/viewform" 
                       target="_blank" 
                       class="google-form-btn pulse">
                        Ir al Formulario de Registro
                    </a>
                    
                    <div class="alternative-info">
                        <h4>¿Tienes problemas para acceder?</h4>
                        <p>📞 Llámanos al: 904 510 446</p>
                        <p>📧 Escríbenos a: proyectopagoportarjetaunfv@gmail.com</p>
                        <p>🏢 Visítanos en cualquiera de nuestras oficinas</p>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <footer id="contacto">
        <div class="container">
            <h3>¿Necesitas más información?</h3>
            <p>Contacta con nuestro equipo de soporte</p>
            <p>📧 proyectopagoportarjetaunfv@gmail.com | 📞 904 510 446</p>
            <p style="margin-top: 1rem; opacity: 0.7;">&copy; 2025 TransCard - Sistema de Regularización de Transporte</p>
        </div>
    </footer>

    <script>
        // Header scroll effect
        window.addEventListener('scroll', function() {
            const header = document.getElementById('header');
            if (window.scrollY > 100) {
                header.classList.add('scrolled');
            } else {
                header.classList.remove('scrolled');
            }
        });

        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Add animation on scroll
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver(function(entries) {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.animation = 'fadeInUp 0.6s ease forwards';
                }
            });
        }, observerOptions);

        // Observe all feature cards and steps
        document.querySelectorAll('.feature-card, .step').forEach(el => {
            observer.observe(el);
        });

        // Track form button clicks
        document.querySelector('.google-form-btn').addEventListener('click', function() {
            console.log('User clicked registration form button');
            // Here you could add analytics tracking if needed
        });
    </script>
</body>
</html>
