<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mini Surtidito - Huautla de Jiménez</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #ff4e50;
            --secondary: #f9d423;
            --dark: #1a1a2e;
            --success: #25d366;
            --info: #3498db;
            --oferta: #e74c3c;
            --altura-imagen: 230px; 
        }

        body { font-family: 'Poppins', sans-serif; margin: 0; padding: 0; background: #f4f7f6; color: var(--dark); padding-bottom: 120px; }

        .promo-bar { background: var(--dark); color: var(--secondary); text-align: center; padding: 10px; font-weight: bold; font-size: 0.9em; letter-spacing: 1px; }

        header { 
            background: linear-gradient(135deg, var(--primary), var(--secondary)); 
            color: white; padding: 40px 20px; text-align: center; 
            border-bottom-left-radius: 40px; border-bottom-right-radius: 40px;
        }

        .delivery-highlight {
            max-width: 800px; margin: 20px auto; background: white;
            border-left: 8px solid var(--success); padding: 20px;
            border-radius: 15px; display: flex; align-items: center;
            gap: 15px; box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        .delivery-text h4 { margin: 0; color: var(--success); text-transform: uppercase; font-size: 1.1em; }
        .delivery-text p { margin: 5px 0 0; font-size: 0.95em; font-weight: 500; }

        .search-container { max-width: 600px; margin: -25px auto 10px; padding: 0 20px; }
        .search-box { display: flex; background: white; padding: 10px 20px; border-radius: 50px; box-shadow: 0 10px 25px rgba(0,0,0,0.1); }
        .search-box input { border: none; width: 100%; padding: 10px; outline: none; font-size: 1em; }

        .container { max-width: 1200px; margin: auto; padding: 20px; }
        h2.section-title { text-align: center; margin: 40px 0 20px; color: var(--dark); text-transform: uppercase; letter-spacing: 2px; }

        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 25px; }
        
        .card { 
            background: white; border-radius: 20px; overflow: hidden; 
            box-shadow: 0 5px 15px rgba(0,0,0,0.05); transition: 0.3s;
            display: flex; flex-direction: column; position: relative;
        }

        .img-box { 
            width: 100%; height: var(--altura-imagen);
            background: #ffffff; display: flex; align-items: center;
            justify-content: center; padding: 15px; box-sizing: border-box;
            border-bottom: 1px solid #eee; cursor: zoom-in;
        }
        .img-box img { max-width: 100%; max-height: 100%; object-fit: contain; }

        .card.oferta-especial { border: 3px solid var(--oferta); }
        .badge-oferta { position: absolute; top: 10px; right: 10px; background: var(--oferta); color: white; padding: 5px 15px; border-radius: 50px; font-size: 0.8em; font-weight: bold; z-index: 10; animation: pulse 1.5s infinite; }
        @keyframes pulse { 0% { transform: scale(1); } 50% { transform: scale(1.1); } 100% { transform: scale(1); } }

        .card-info { padding: 15px; text-align: center; flex-grow: 1; }
        .card-info h3 { margin: 0; color: var(--primary); font-size: 1.1em; }
        .card-info p { font-size: 0.85em; color: #666; margin-top: 5px; }

        .btn-add { background: var(--dark); color: white; border: none; padding: 12px; width: 85%; margin: 0 auto 15px; border-radius: 50px; cursor: pointer; font-weight: bold; transition: 0.3s; }
        .btn-add:hover { background: var(--primary); transform: scale(1.05); }

        .info-section { background: white; border-radius: 30px; padding: 30px; margin-top: 50px; display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px; }
        .map-container { border-radius: 20px; overflow: hidden; height: 350px; border: 4px solid #f4f7f6; }

        #zoomModal { display: none; position: fixed; z-index: 5000; padding-top: 50px; left: 0; top: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); text-align: center; }
        #zoomModal img { max-width: 90%; max-height: 80%; border-radius: 10px; margin-top: 20px; }
        .close-zoom { position: absolute; top: 20px; right: 35px; color: white; font-size: 40px; cursor: pointer; }

        #cart-bar { position: fixed; bottom: 20px; left: 50%; transform: translateX(-50%); width: 90%; max-width: 500px; background: var(--dark); color: white; padding: 15px 25px; border-radius: 50px; display: none; z-index: 2000; box-shadow: 0 10px 30px rgba(0,0,0,0.4); }
        .btn-wp { background: var(--success); color: white; padding: 10px 20px; border-radius: 50px; text-decoration: none; font-weight: bold; }
    </style>
</head>
<body>

<div class="promo-bar">🚚 ENVÍO A DOMICILIO SIN COSTO EXTRA EN HUAUTLA 📦</div>

<header>
    <h1>MINI SURTIDITO</h1>
    <p>Tecnología y Accesorios</p>
</header>

<div class="search-container">
    <div class="search-box">
        <input type="text" id="searchInput" onkeyup="filterProducts()" placeholder="🔍 Busca bocinas, audífonos, memorias...">
    </div>
</div>

<div class="container">
    <div class="delivery-highlight">
        <div style="font-size: 30px;">🏠</div>
        <div class="delivery-text">
            <h4>¿Quieres verlo antes de comprar?</h4>
            <p>Pídelo por WhatsApp y <b>lo llevamos a tu domicilio para mostrártelo sin compromiso.</b></p>
        </div>
    </div>

    <h2 class="section-title">🔥 Ofertas del Mes 🔥</h2>
    <div class="grid">
        <div class="card oferta-especial" data-name="audinos de diadema wireless headphones p47">
            <div class="badge-oferta">OFERTA</div>
            <div class="img-box" onclick="zoomImg(this)"><img src="https://i.ebayimg.com/images/g/ChIAAeSw-Ixo45lW/s-l960.webp"></div>
            <div class="card-info">
                <h3>Audífonos P47</h3>
                <p>Antes: <del>$250</del><br><b style="color:var(--oferta); font-size: 1.2em;">Hoy: $100.00</b></p>
            </div>
            <button class="btn-add" onclick="add('OFERTA: Audífonos P47 ($100)')">Añadir al Carrito</button>
        </div>

        <div class="card oferta-especial" data-name="oferta electronica bocina chica link bits">
            <div class="badge-oferta">OFERTA</div>
            <div class="img-box" onclick="zoomImg(this)"><img src="bocina chica.jpg"></div>
            <div class="card-info">
                <h3>Bocina Link Bits 3"</h3>
                <p>Antes: <del>$200</del><br><b style="color:var(--oferta); font-size: 1.2em;">Hoy: $120.00</b></p>
            </div>
            <button class="btn-add" onclick="add('OFERTA: Bocina Link Bits ($120)')">Añadir al Carrito</button>
        </div>
    </div>

    <h2 class="section-title">Todos los Productos</h2>
    <div class="grid">
        <div class="card" data-name="electronica bocina link bits 3 pulgadas naranja">
            <div class="img-box" onclick="zoomImg(this)"><img src="bocina naranja.jpg"></div>
            <div class="card-info"><h3>Bocina Naranja 3"</h3><p>Precio: $150.00</p></div>
            <button class="btn-add" onclick="add('Bocina Naranja ($150)')">Añadir</button>
        </div>
        
        <div class="card" data-name="electronica bocina azul link bits 6 pulgadas">
            <div class="img-box" onclick="zoomImg(this)"><img src="https://http2.mlstatic.com/D_NQ_NP_738539-MLM83975346537_042025-O.webp"></div>
            <div class="card-info"><h3>Bocina Link Bits 6"</h3><p>Precio: $300.00</p></div>
            <button class="btn-add" onclick="add('Bocina Azul 6p ($300)')">Añadir</button>
        </div>

        <div class="card" data-name="electronica memoria usb kingston 64gb">
            <div class="img-box" onclick="zoomImg(this)"><img src="memoria usb.jpg"></div>
            <div class="card-info"><h3>USB Kingston 64GB</h3><p>Precio: $250.00</p></div>
            <button class="btn-add" onclick="add('USB 64GB ($250)')">Añadir</button>
        </div>

        <div class="card" data-name="electronica audifonos in Pods 12">
            <div class="img-box" onclick="zoomImg(this)"><img src="inpods 12.jpg"></div>
            <div class="card-info"><h3>Audífonos InPods 12</h3><p>Precio: $110.00</p></div>
            <button class="btn-add" onclick="add('inpods 12 ($110)')">Añadir</button>
        </div>

        <div class="card" data-name="electronica audifonos samsung con power bank">
            <div class="img-box" onclick="zoomImg(this)"><img src="audifonos samsung.jpg"></div>
            <div class="card-info"><h3>Samsung TWS + Power Bank</h3><p>Precio: $300.00</p></div>
            <button class="btn-add" onclick="add('Samsung TWS PowerBank ($300)')">Añadir</button>
        </div>

        <div class="card" data-name="electronica bocina con lampara y carga solar">
            <div class="img-box" onclick="zoomImg(this)"><img src="https://joinet-images-bucket.s3.us-east-1.amazonaws.com/wp-content/uploads/2025/08/KTS-1437-1.webp"></div>
            <div class="card-info"><h3>Bocina Lámpara Solar</h3><p>Precio: $300.00</p></div>
            <button class="btn-add" onclick="add('Bocina Solar ($300)')">Añadir</button>
        </div>

        <div class="card" data-name="electronica mini lampara de escritorio con forma de conejo, color azul">
            <div class="img-box" onclick="zoomImg(this)"><img src="https://joinet-images-bucket.s3.us-east-1.amazonaws.com/wp-content/uploads/2025/07/FAN-712B.webp"></div>
            <div class="card-info"><h3>Mini Lámpara Conejo</h3><p>Precio: $130.00</p></div>
            <button class="btn-add" onclick="add('Lámpara Conejo ($130)')">Añadir</button>
        </div>

        <div class="card" data-name="electronica termo, color negro y azul">
            <div class="img-box" onclick="zoomImg(this)"><img src="https://dcdn-us.mitiendanube.com/stores/002/059/290/products/028-048-foto11-73e4523875c89cf7bf16753833223016-1024-1024.webp"></div>
            <div class="card-info"><h3>Termo Negro/Azul</h3><p>Precio: $90.00</p></div>
            <button class="btn-add" onclick="add('Termo ($90)')">Añadir</button>
        </div>

        <div class="card" data-name="electronica rasuradora portatil, recargable">
            <div class="img-box" onclick="zoomImg(this)"><img src="https://http2.mlstatic.com/D_NQ_NP_2X_659678-MLM97460602227_112025-F.webp"></div>
            <div class="card-info"><h3>Rasuradora Portátil</h3><p>Precio: $90.00</p></div>
            <button class="btn-add" onclick="add('Rasuradora ($90)')">Añadir</button>
        </div>

        <div class="card" data-name="electronica reloj de kuromi mini">
            <div class="img-box" onclick="zoomImg(this)"><img src="https://ae-pic-a1.aliexpress-media.com/kf/Sfbf5b63328be40768196fe1059101ae57.jpg_640x640q75.jpg_.avif"></div>
            <div class="card-info"><h3>Reloj Kuromi Mini</h3><p>Precio: $70.00</p></div>
            <button class="btn-add" onclick="add('Reloj Kuromi ($70)')">Añadir</button>
        </div>

        <div class="card" data-name="electronica audifonos de diadema color azul,con bluetooth,memoria sd y auxiliares">
            <div class="img-box" onclick="zoomImg(this)"><img src="audifonos azul cielo.jpg"></div>
            <div class="card-info"><h3>Audífonos Azul Cielo</h3><p>Precio: $120.00</p></div>
            <button class="btn-add" onclick="add('Diadema Azul Cielo ($120)')">Añadir</button>
        </div>

        <div class="card" data-name="electronica audifonos de diadema de oreja,con bluetooth,memoria sd y auxiliares">
            <div class="img-box" onclick="zoomImg(this)"><img src="https://http2.mlstatic.com/D_NQ_NP_2X_710150-MLM96364257947_102025-F.webp"></div>
            <div class="card-info"><h3>Audífonos Azul Marino</h3><p>Precio: $120.00</p></div>
            <button class="btn-add" onclick="add('Diadema Azul Marino ($120)')">Añadir</button>
        </div>

        <div class="card" data-name="electronica audifonos marca hora">
            <div class="img-box" onclick="zoomImg(this)"><img src="audifonos marca hora.jpeg"></div>
            <div class="card-info"><h3>Audífonos MARCA HORA</h3><p>Precio: $90.00</p></div>
            <button class="btn-add" onclick="add('Audífonos HORA ($90)')">Añadir</button>
        </div>

        <div class="card" data-name="electronica cargador v8, marca hora">
            <div class="img-box" onclick="zoomImg(this)"><img src="cargador v8.jpg"></div>
            <div class="card-info"><h3>Cargador V8,MARCA HORA</h3><p>Precio: $100.00</p></div>
            <button class="btn-add" onclick="add('Cargador V8 ($100)')">Añadir</button>
        </div>

        <div class="card" data-name="electronica cargador de c a c, marca hora">
            <div class="img-box" onclick="zoomImg(this)"><img src="https://http2.mlstatic.com/D_NQ_NP_2X_613434-MLM92661186777_092025-F.webp"></div>
            <div class="card-info"><h3>Cargador C a C, MARCA HORA</h3><p>Precio: $150.00</p></div>
            <button class="btn-add" onclick="add('Cargador C a C ($150)')">Añadir</button>
        </div>

 <div class="card" data-name="electronica cargador tipo c, marca hora">
            <div class="img-box" onclick="zoomImg(this)"><img src="https://papeleriadelahorro.mx/cdn/shop/files/1719014.jpg?v=1751741811"></div>
            <div class="card-info"><h3>Cargador tipo C, MARCA HORA</h3><p>Precio: $100.00</p></div>
            <button class="btn-add" onclick="add('Cargador tipo C($100)')">Añadir</button>
        </div>

<div class="card" data-name="electronica VENTA DE CHIT BAIT">
            <div class="img-box" onclick="zoomImg(this)"><img src="chit bait.png"></div>
            <div class="card-info"><h3>Venta de chip BAIT,Con $100 DE SALDO</h3><p>Precio: $80.00</p></div>
            <button class="btn-add" onclick="add('CHIP BAIT($80)')">Añadir</button>
        </div>

<div class="card" data-name="electronica VENTA DE CHIP telcel">
            <div class="img-box" onclick="zoomImg(this)"><img src="chip telcel.jpg"></div>
            <div class="card-info"><h3>Venta de chiP telcel</h3><p>Precio: $50.00</p></div>
            <button class="btn-add" onclick="add('CHIP TELCEL($50)')">Añadir</button>
        </div>

<div class="card" data-name="electronica TIMBRE INALAMBRICO">
            <div class="img-box" onclick="zoomImg(this)"><img src="https://http2.mlstatic.com/D_NQ_NP_789025-MLM40074442597_122019-O.webp"></div>
            <div class="card-info"><h3>TIMBRE INALAMBRICO</h3><p>Precio: $150.00</p></div>
            <button class="btn-add" onclick="add('TIMBRE INALAMBRICO($150)')">Añadir</button>
        </div>

<div class="card" data-name="electronica TIMBRE con SENSOR de movimiento">
            <div class="img-box" onclick="zoomImg(this)"><img src="censor de movimiento.jpg"></div>
            <div class="card-info"><h3>TIMBRE con SENSOR de movimiento</h3><p>Precio: $150.00</p></div>
            <button class="btn-add" onclick="add('TIMBRE con SENSOR de movimiento($150)')">Añadir</button>
        </div>

<div class="card" data-name="electronica SOPORTE PARA CELULAR EN MOTO">
            <div class="img-box" onclick="zoomImg(this)"><img src="soporte celular.jpg"></div>
            <div class="card-info"><h3>SOPORTE PARA CELULAR EN MOTO</h3><p>Precio: $150.00</p></div>
            <button class="btn-add" onclick="add('SOPORTE PARA CELULAR EN MOTO($150)')">Añadir</button>
        </div>

<div class="card" data-name="electronica LUZ LED PARA BICICLETA">
            <div class="img-box" onclick="zoomImg(this)"><img src="https://http2.mlstatic.com/D_NQ_NP_2X_823668-MLU72126742088_102023-F.webp"></div>
            <div class="card-info"><h3>LUZ LED PARA BICICLETA</h3><p>Precio: $90.00</p></div>
            <button class="btn-add" onclick="add('LUZ LED PARA BICICLETA($90)')">Añadir</button>
        </div>

<div class="card" data-name="electronica AUDIFONOS SONY">
            <div class="img-box" onclick="zoomImg(this)"><img src="sony.jpg"></div>
            <div class="card-info"><h3>AUDIFONOS SONY, DIADEMA</h3><p>Precio: $350.00</p></div>
            <button class="btn-add" onclick="add('AUDIFONOS SONY($350)')">Añadir</button>
        </div>

<div class="card" data-name="electronica LAMPARA TACTICA,BUENA ILUMINACION,RECARGABLE">
            <div class="img-box" onclick="zoomImg(this)"><img src="https://http2.mlstatic.com/D_NQ_NP_949921-MLM80373882847_112024-O-lampara-tactica-ultra-potente-recargable-p50-15000-lumenes.webp"></div>
            <div class="card-info"><h3>LAMPARA TACTICA,BUENA ILUMINACION,RECARGABLE</h3><p>Precio: $150.00</p></div>
            <button class="btn-add" onclick="add('LAMPARA TACTICA,BUENA ILUMINACION,RECARGABLE($150)')">Añadir</button>
        </div>

<div class="card" data-name="electronica CARGADOR DE CONTROL XBOX 360">
            <div class="img-box" onclick="zoomImg(this)"><img src="https://http2.mlstatic.com/D_NQ_NP_2X_966217-MLM90133406251_082025-F-10x-kit-carga-y-juega-cable-cargador-pila-para-xbox-360.webp"></div>
            <div class="card-info"><h3>CARGADOR DE CONTROL XBOX 360</h3><p>Precio: $180.00</p></div>
            <button class="btn-add" onclick="add('CARGADOR DE CONTROL XBOX 360($180)')">Añadir</button>
        </div>

    </div> <div class="info-section">
        <div class="details">
            <h2>📍 Ubicación</h2>
            <p>Av. de los Constituyentes #100, Huautla de Jiménez.</p>
            <p><b>WhatsApp:</b> 236 123 1236</p>
            <a href="#" target="_blank" style="background:var(--info); color:white; padding:10px 20px; border-radius:50px; text-decoration:none; display:inline-block; font-weight:bold; margin-top:10px;">Ver Mapa</a>
        </div>
        <div class="map-container">
            <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3774.2!2d-96.8415!3d18.1341!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zMTjCsDA4JzAyLjgiTiA5Niw0OCcyOS40Ilc!5e0!3m2!1ses!2smx!4v1620000000000!5m2!1ses!2smx" width="100%" height="100%" style="border:0;" allowfullscreen=""></iframe>
        </div>
    </div>
</div>

<div id="zoomModal">
    <span class="close-zoom" onclick="closeZoom()">×</span>
    <img id="imgAmpliada">
</div>

<div id="cart-bar">
    <div style="display:flex; justify-content:space-between; align-items:center;">
        <span>🛒 <b id="cart-count">0</b> productos</span>
        <a href="#" class="btn-wp" onclick="send()">PEDIR A DOMICILIO</a>
    </div>
</div>

<script>
    let cart = [];
    const WHATSAPP = "522361231236"; 

    function zoomImg(elemento) {
        document.getElementById("imgAmpliada").src = elemento.querySelector("img").src;
        document.getElementById("zoomModal").style.display = "block";
    }
    function closeZoom() { document.getElementById("zoomModal").style.display = "none"; }
    window.onclick = function(e) { if (e.target == document.getElementById("zoomModal")) closeZoom(); }

    function add(item) { 
        cart.push(item); 
        document.getElementById('cart-bar').style.display = 'block'; 
        document.getElementById('cart-count').innerText = cart.length; 
    }

    function filterProducts() {
        let input = document.getElementById('searchInput').value.toLowerCase();
        let cards = document.getElementsByClassName('card');
        for (let i = 0; i < cards.length; i++) {
            let name = cards[i].getAttribute('data-name') || "";
            cards[i].style.display = name.includes(input) ? "flex" : "none";
        }
    }

    function send() {
        if(cart.length === 0) return;
        const msg = encodeURIComponent("¡Hola! Me interesan estos productos para verlos en mi domicilio sin compromiso:\n\n" + cart.join('\n'));
        window.open(`https://wa.me/${WHATSAPP}?text=${msg}`, '_blank');
    }
</script>

</body>
</html>
