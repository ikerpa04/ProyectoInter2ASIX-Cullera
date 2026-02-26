```
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cullera | Sostenible</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary-green: #871b1b;
            --secondary-green: #871b1b;
            --light-green: #e8f5e9;
            --dark-green: #871b1b;
            --blue: #1976d2;
            --light-blue: #e3f2fd;
            --orange: #ff9800;
            --gray: #757575;
            --light-gray: #f5f5f5;
            --white: #ffffff;
            --shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            --shadow-hover: 0 6px 12px rgba(0, 0, 0, 0.15);
            --border-radius: 10px;
            --transition: all 0.3s ease;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background-color: var(--light-gray);
            background-image: linear-gradient(to bottom, #f8f9fa 0%, #e8f5e9 100%);
        }

        header {
            background: linear-gradient(135deg, var(--dark-green) 0%, var(--primary-green) 100%);
            color: var(--white);
            padding: 1.5rem 0;
            text-align: center;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
            position: relative;
            overflow: hidden;
        }

        header::before {
            content: "";
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, rgba(255,255,255,0) 70%);
            transform: rotate(30deg);
        }

        .header-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
            position: relative;
            z-index: 2;
        }

        h1 {
            font-size: 2.8rem;
            margin-bottom: 0.5rem;
            letter-spacing: -0.5px;
        }

        .subtitle {
            font-size: 1.3rem;
            opacity: 0.9;
            margin-top: 0.5rem;
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
        }

        nav {
            background-color: var(--white);
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: center;
        }

        .nav-container ul {
            display: flex;
            list-style: none;
        }

        .nav-container li a {
            display: block;
            padding: 1rem 1.5rem;
            text-decoration: none;
            color: var(--primary-green);
            font-weight: 600;
            transition: var(--transition);
            position: relative;
        }

        .nav-container li a:hover, 
        .nav-container li a.active {
            color: var(--dark-green);
        }

        .nav-container li a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            width: 0;
            height: 3px;
            background-color: var(--secondary-green);
            transition: var(--transition);
            transform: translateX(-50%);
        }

        .nav-container li a:hover::after,
        .nav-container li a.active::after {
            width: 70%;
        }

        main {
            max-width: 1200px;
            margin: 2.5rem auto;
            padding: 0 1.5rem;
        }

        section {
            background-color: var(--white);
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            padding: 2rem;
            margin-bottom: 2.5rem;
            transition: var(--transition);
        }

        section:hover {
            box-shadow: var(--shadow-hover);
            transform: translateY(-5px);
        }

        h2 {
            color: var(--dark-green);
            margin-bottom: 1.8rem;
            padding-bottom: 0.8rem;
            border-bottom: 3px solid var(--light-green);
            font-size: 2.2rem;
            text-align: center;
        }

        .services-intro {
            text-align: center;
            margin-bottom: 2.5rem;
            padding: 1.5rem;
            background-color: var(--light-green);
            border-radius: var(--border-radius);
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.8rem;
            margin-top: 1.5rem;
        }

        .service-card {
            background: var(--white);
            border-radius: var(--border-radius);
            padding: 1.5rem;
            text-align: center;
            box-shadow: var(--shadow);
            transition: var(--transition);
            border: 1px solid var(--light-green);
        }

        .service-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-hover);
            border-color: var(--secondary-green);
        }

        .service-card h3 {
            color: var(--primary-green);
            margin: 0.8rem 0;
            font-size: 1.5rem;
        }

        .ods-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 1.5rem;
        }

        .ods-card {
            border-left: 5px solid var(--primary-green);
            padding: 1.5rem;
            background-color: var(--light-green);
            border-radius: 0 var(--border-radius) var(--border-radius) 0;
            transition: var(--transition);
        }

        .ods-card:hover {
            transform: translateX(5px);
            background-color: #d4edda;
        }

        .ods-card h3 {
            color: var(--dark-green);
            margin-bottom: 0.8rem;
            display: flex;
            align-items: center;
        }

        .ods-card h3::before {
            content: "ODS";
            display: inline-block;
            background: var(--primary-green);
            color: white;
            width: 36px;
            height: 36px;
            border-radius: 50%;
            text-align: center;
            line-height: 36px;
            margin-right: 10px;
            font-weight: bold;
            flex-shrink: 0;
        }

        .ods-card p {
            margin-bottom: 1.2rem;
            font-size: 0.95rem;
        }

        .campos-container {
            display: grid;
            grid-template-columns: 1fr;
            gap: 0.8rem;
        }

        .campo-group {
            margin-bottom: 1rem;
        }

        .campo-group label {
            display: block;
            margin-bottom: 0.4rem;
            font-weight: 600;
            color: var(--dark-green);
            font-size: 0.9rem;
        }

        textarea {
            width: 100%;
            padding: 0.8rem;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-family: inherit;
            font-size: 0.95rem;
            resize: vertical;
            min-height: 80px;
            transition: var(--transition);
        }

        textarea:focus {
            border-color: var(--secondary-green);
            outline: none;
            box-shadow: 0 0 0 3px rgba(76, 175, 80, 0.2);
        }

        .kpi-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.8rem;
            margin-top: 1.5rem;
        }

        .kpi-card {
            text-align: center;
            padding: 1.8rem 1.5rem;
            border-radius: var(--border-radius);
            background: linear-gradient(135deg, var(--white) 0%, #f8f9fa 100%);
            box-shadow: var(--shadow);
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }

        .kpi-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, rgba(255,255,255,0.1) 0%, rgba(255,255,255,0) 70%);
            transform: rotate(45deg);
            transition: var(--transition);
        }

        .kpi-card:hover {
            transform: translateY(-8px);
            box-shadow: var(--shadow-hover);
        }

        .kpi-card:hover::before {
            top: -30%;
            left: -30%;
            width: 160%;
            height: 160%;
        }

        .kpi-card h3 {
            color: var(--dark-green);
            margin-bottom: 1rem;
            font-size: 1.4rem;
            position: relative;
            z-index: 2;
        }

        .kpi-value {
            font-size: 3.2rem;
            font-weight: 800;
            color: var(--primary-green);
            margin: 0.5rem 0;
            position: relative;
            z-index: 2;
            line-height: 1;
        }

        .kpi-goal {
            color: var(--blue);
            font-weight: 600;
            margin-top: 0.5rem;
            font-size: 1.1rem;
            position: relative;
            z-index: 2;
        }

        .kpi-card:nth-child(1) {
            border-top: 5px solid var(--secondary-green);
        }

        .kpi-card:nth-child(2) {
            border-top: 5px solid var(--blue);
        }

        .kpi-card:nth-child(3) {
            border-top: 5px solid var(--orange);
        }

        .ods-highlight {
            background-color: var(--light-blue);
            border-left: 4px solid var(--blue);
            padding: 1.5rem;
            border-radius: 0 var(--border-radius) var(--border-radius) 0;
            margin: 1.5rem 0;
        }

        .ods-highlight h4 {
            color: var(--blue);
            margin-bottom: 0.5rem;
        }

        footer {
            background: linear-gradient(135deg, var(--dark-green) 0%, #0a3d19 100%);
            color: var(--white);
            text-align: center;
            padding: 2rem;
            margin-top: 2rem;
        }

        .footer-content {
            max-width: 800px;
            margin: 0 auto;
        }

        .footer-logo {
            font-size: 2.2rem;
            font-weight: 700;
            margin-bottom: 1rem;
            display: block;
        }

        .copyright {
            opacity: 0.8;
            margin-top: 0.5rem;
            font-size: 0.95rem;
        }

        @media (max-width: 768px) {
            h1 {
                font-size: 2.3rem;
            }
            
            .subtitle {
                font-size: 1.1rem;
            }
            
            .nav-container ul {
                flex-wrap: wrap;
            }
            
            .nav-container li a {
                padding: 0.8rem 0.7rem;
                font-size: 0.9rem;
            }
            
            main {
                margin: 1.5rem;
            }
            
            section {
                padding: 1.5rem;
            }
            
            h2 {
                font-size: 1.9rem;
            }
            
            .kpi-value {
                font-size: 2.5rem;
            }
        }

        @media (max-width: 480px) {
            h1 {
                font-size: 2rem;
            }
            
            .ods-container, .kpi-container, .services-grid {
                grid-template-columns: 1fr;
            }
            
            .kpi-value {
                font-size: 2.2rem;
            }
            
            .nav-container li a {
                padding: 0.8rem 0.5rem;
                font-size: 0.85rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="header-content">
            <h1>Sede de Cullera</h1>
  
        </div>
    </header>

    <nav>
        <div class="nav-container">
            <ul>
                <li><a href="#servicios">Servicios</a></li>
                <li><a href="#ods">Objetivos ODS</a></li>
                <li><a href="#indicadores">Indicadores</a></li>
            </ul>
        </div>
    </nav>

    <main>
        <section id="servicios">
            <h2>Nuestros Servicios Sostenibles</h2>

            <div class="services-grid">
                <div class="service-card">
                    <h3>Reparación de Equipos</h3>
                    <p>Extendemos la vida útil de dispositivos electrónicos mediante reparaciones profesionales, evitando que terminen en vertederos y reduciendo la necesidad de fabricar nuevos productos.</p>
                </div>
                <div class="service-card">
                    <h3>Configuración de Redes</h3>
                    <p>Implementamos infraestructuras de red eficientes energéticamente, optimizando recursos y reduciendo el consumo eléctrico en entornos corporativos y domésticos.</p>
                </div>
                <div class="service-card">
                    <h3>Recuperación de Datos</h3>
                    <p>Salvamos información valiosa de discos duros dañados, evitando la pérdida de todos tus datos y permitiendo la reutilización de componentes funcionales en lugar de desecharlos.</p>
                </div>
                <div class="service-card">
                    <h3>Montaje de PCs</h3>
                    <p>Ensamblamos equipos personalizados utilizando componentes reacondicionados y nuevos de bajo consumo, creando soluciones tecnológicas con menor huella de carbono.</p>
                </div>
            </div>
        </section>

        <section id="ods">
            <h2>Objetivos de Desarrollo Sostenible</h2>
            <div class="ods-container">
                <div class="ods-card">
                    <h3>12: Producción y consumo responsables</h3>
                    <p>Consiste en garantizar modalidades de consumo y producción sostenibles, desvinculando el crecimiento económico del uso intensivo de recursos y la degradación ambiental.</p>

                </div>
                
                <div class="ods-card">
                    <h3>4: Educación de calidad</h3>
                    <p>Este objetivo busca garantizar una educación inclusiva, equitativa y de calidad, promoviendo oportunidades de aprendizaje durante toda la vida para todos.</p>
                  
                </div>
                
                <div class="ods-card">
                    <h3>9: Industria, innovación e infraestructura</h3>
                    <p>Su meta es construir infraestructuras resilientes, promover una industrialización inclusiva y sostenible, y fomentar la innovación tecnológica.</p>
                   
                </div>
                
                <div class="ods-card">
                    <h3>13: Acción por el clima</h3>
                    <p>Este objetivo urge a adoptar medidas urgentes para combatir el cambio climático y sus efectos, limitando el aumento de la temperatura global.</p>
                </div>

                <div class="ods-card">
                    <h3>11: Ciudades y comunidades sostenibles</h3>
                    <p>Este objetivo busca lograr que las ciudades y los asentamientos humanos sean inclusivos, seguros, resilientes y sostenibles.</p>
                </div>

                <div class="ods-card">
                    <h3>7: Energia asequible y no contaminante</h3>
                    <p>Este objetivo busca garantizar el acceso a una energía de fuentes renovables que sea fiable, sostenible y moderna para todos.</p>
                </div>
            </div>
            
            <div class="ods-highlight">
                <h4>Nuestro Compromiso con los ODS</h4>
                <p>En la sede de Cullera, tratamos de integrar los Objetivos de Desarrollo Sostenible. Cada reparación, configuración o montaje que realizamos contribuye directamente a reducir residuos electrónicos, ahorrar energía y promover una economía circular, para garantizar un futuro tecnológico sostenible.</p>
            </div>
        </section>

        <section id="indicadores">
            <h2>Indicadores de Sostenibilidad</h2>
            <div class="kpi-container">
                <div class="kpi-card">
                    <h3>Trabajadores capacitados en sostenibilidad</h3>
                    <div class="kpi-value">100%</div>
                    <p class="kpi-goal">Objetivo conseguido</p>
                    <p>Todos nuestros técnicos y personal administrativo reciben formación continua en prácticas sostenibles y economía circular.</p>
                </div>
                <div class="kpi-card">
                    <h3>Energía renovable utilizada</h3>
                    <div class="kpi-value">50%</div>
                    <p class="kpi-goal">Objetivo: 80% para 2030</p>
                    <p>Nuestra oficina y taller funcionan con energía solar, con planes de expansión para alcanzar el 80% en 2030.</p>
                </div>
                <div class="kpi-card">
                    <h3>Componentes funcionales reutilizados</h3>
                    <div class="kpi-value">70%</div>
                    <p>El 70% de los componentes recuperados de equipos dañados son reutilizados en reparaciones o donados a programas educativos.</p>
                </div>
            </div>
        </section>
    </main>


</body>
</html>
```