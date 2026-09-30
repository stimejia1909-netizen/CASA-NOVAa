# CASA-NOVAa
VENTA AL POR MAYOR Y A EL MINORISTA  CON PRECIOS COMPETITIVOS Y PARA EL HOGAR 
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Casa Nova</title>

    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: Arial, Helvetica, sans-serif;
            background: #080808;
            color: #fff;
            min-height: 100vh;
        }

        header {
            height: 75px;
            background: #0f0f0f;
            border-bottom: 1px solid #2a2419;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 6%;
            position: sticky;
            top: 0;
            z-index: 10;
        }

        .logo {
            font-size: 25px;
            font-weight: bold;
            letter-spacing: 3px;
            color: #d4af37;
        }

        .logo span {
            color: #fff;
        }

        .btn {
            background: linear-gradient(135deg, #d4af37, #aa820a);
            color: #000;
            border: none;
            padding: 11px 18px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
            transition: 0.2s;
        }

        .btn:hover {
            background: linear-gradient(135deg, #e5c158, #c49918);
            box-shadow: 0 0 10px rgba(212, 175, 55, 0.3);
        }

        .container {
            width: 88%;
            max-width: 1200px;
            margin: 35px auto;
        }

        .hero {
            text-align: center;
            padding: 35px 10px;
        }

        .hero h1 {
            font-size: 42px;
            letter-spacing: 5px;
            margin-bottom: 10px;
            color: #d4af37;
            text-shadow: 0 2px 4px rgba(0,0,0,0.5);
        }

        .hero p {
            color: #aaa;
        }

        .search {
            margin: 25px auto 35px;
            max-width: 500px;
        }

        .search input {
            width: 100%;
            padding: 14px;
            background: #121212;
            border: 1px solid #332b1d;
            color: white;
            border-radius: 8px;
            outline: none;
            transition: border-color 0.3s;
        }

        .search input:focus {
            border-color: #d4af37;
        }

        .products {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 22px;
        }

        .product {
            background: #121212;
            border: 1px solid #2a2419;
            border-radius: 10px;
            overflow: hidden;
            transition: 0.25s;
            cursor: pointer;
        }

        .product:hover {
            transform: translateY(-4px);
            border-color: #d4af37;
            box-shadow: 0 4px 15px rgba(212, 175, 55, 0.15);
        }

        .product img {
            width: 100%;
            height: 220px;
            object-fit: cover;
            display: block;
            background: #181818;
        }

        .product-info {
            padding: 17px;
        }

        .product-name {
            font-size: 18px;
            margin-bottom: 10px;
        }

        .price {
            font-size: 19px;
            font-weight: bold;
            margin-bottom: 15px;
            color: #d4af37;
        }

        .delete {
            background: transparent;
            color: #aaa;
            border: 1px solid #333;
            padding: 7px 12px;
            border-radius: 5px;
            cursor: pointer;
            transition: 0.2s;
        }

        .delete:hover {
            color: #ff5555;
            border-color: #ff5555;
        }

        /* MODALES */

        .modal {
            display: none;
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.85);
            z-index: 100;
            align-items: center;
            justify-content: center;
            padding: 20px;
            overflow-y: auto;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: #121212;
            border: 1px solid #332b1d;
            width: 100%;
            max-width: 500px;
            padding: 28px;
            border-radius: 10px;
            max-height: 90vh;
            overflow-y: auto;
        }

        .modal-content h2 {
            margin-bottom: 20px;
            color: #d4af37;
        }

        .form-group {
            margin-bottom: 18px;
        }

        .form-group label {
            display: block;
            margin-bottom: 7px;
            color: #ccc;
            font-size: 14px;
        }

        .form-group input,
        .form-group select {
            width: 100%;
            padding: 12px;
            border: 1px solid #332b1d;
            background: #080808;
            color: white;
            border-radius: 6px;
            outline: none;
        }

        .form-group input:focus,
        .form-group select:focus {
            border-color: #d4af37;
        }

        .form-group select option {
            background: #111;
            color: white;
        }

        .form-buttons {
            display: flex;
            gap: 10px;
            margin-top: 25px;
        }

        .form-buttons button {
            flex: 1;
        }

        .cancel {
            background: transparent;
            color: white;
            border: 1px solid #444;
            padding: 11px;
            border-radius: 6px;
            cursor: pointer;
            transition: 0.2s;
        }

        .cancel:hover {
            border-color: #888;
        }

        .empty {
            text-align: center;
            color: #666;
            padding: 60px 10px;
            grid-column: 1 / -1;
        }

        footer {
            text-align: center;
            color: #666;
            padding: 50px 20px 30px;
            font-size: 13px;
        }

        /* DETALLE DEL PRODUCTO */

        .detalle-img {
            width: 100%;
            height: 280px;
            object-fit: cover;
            border-radius: 8px;
            margin-bottom: 20px;
            border: 1px solid #2a2419;
        }

        .detalle-nombre {
            font-size: 25px;
            margin-bottom: 10px;
        }

        .detalle-precio {
            font-size: 22px;
            font-weight: bold;
            margin-bottom: 25px;
            color: #d4af37;
        }

        .cantidad-control {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 20px;
        }

        .cantidad-control button {
            width: 38px;
            height: 38px;
            background: #1e1e1e;
            color: white;
            border: 1px solid #332b1d;
            border-radius: 6px;
            cursor: pointer;
            font-size: 20px;
        }

        .cantidad-control button:hover {
            background: #d4af37;
            color: black;
        }

        .cantidad-control input {
            width: 80px;
            text-align: center;
            padding: 10px;
            background: #080808;
            color: white;
            border: 1px solid #332b1d;
            border-radius: 6px;
        }

        /* PAGO */

        .pago-box {
            background: #0a0a0a;
            border: 1px solid #332b1d;
            border-radius: 8px;
            padding: 18px;
            margin-top: 20px;
        }

        .pago-box h3 {
            margin-bottom: 15px;
            color: #d4af37;
        }

        .opcion-pago {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 12px;
            background: #141414;
            border: 1px solid #2a2419;
            border-radius: 6px;
            margin-bottom: 10px;
            cursor: pointer;
            transition: 0.2s;
        }

        .opcion-pago:hover {
            border-color: #d4af37;
        }

        .opcion-pago input {
            width: 17px;
            height: 17px;
            cursor: pointer;
            accent-color: #d4af37;
        }

        /* SELECCIÓN DE MESES */

        .credito-opciones {
            display: none;
            margin-top: 15px;
        }

        .credito-opciones.active {
            display: block;
        }

        .credito-opciones label {
            display: block;
            margin-bottom: 7px;
            color: #bbb;
            font-size: 14px;
        }

        .credito-opciones select {
            width: 100%;
            padding: 12px;
            background: #080808;
            color: white;
            border: 1px solid #332b1d;
            border-radius: 6px;
            outline: none;
            cursor: pointer;
        }

        .credito-info {
            display: none;
            background: #151515;
            border: 1px solid #332b1d;
            padding: 15px;
            border-radius: 7px;
            margin-top: 12px;
        }

        .credito-info.active {
            display: block;
        }

        .credito-info p {
            margin-bottom: 7px;
            color: #bbb;
        }

        .resumen {
            margin-top: 20px;
            padding-top: 20px;
            border-top: 1px solid #2a2419;
        }

        .fila {
            display: flex;
            justify-content: space-between;
            gap: 15px;
            margin-bottom: 10px;
            color: #aaa;
        }

        .fila.total {
            color: #d4af37;
            font-size: 20px;
            font-weight: bold;
            margin-top: 15px;
        }

        .fila.cuota {
            color: #fff;
            font-size: 18px;
            font-weight: bold;
            margin-top: 10px;
        }

        .comprar {
            width: 100%;
            margin-top: 20px;
            padding: 14px;
            background: linear-gradient(135deg, #d4af37, #aa820a);
            color: black;
            border: none;
            border-radius: 7px;
            cursor: pointer;
            font-weight: bold;
            font-size: 16px;
            transition: 0.2s;
        }

        .comprar:hover {
            background: linear-gradient(135deg, #e5c158, #c49918);
            box-shadow: 0 0 12px rgba(212, 175, 55, 0.4);
        }

        @media (max-width: 600px) {

            header {
                padding: 0 20px;
            }

            .logo {
                font-size: 20px;
            }

            .hero h1 {
                font-size: 32px;
            }

            .products {
                grid-template-columns: repeat(2, 1fr);
                gap: 12px;
            }

            .product img {
                height: 170px;
            }

            .product-info {
                padding: 12px;
            }

            .product-name {
                font-size: 15px;
            }

            .price {
                font-size: 16px;
            }
        }

        @media (max-width: 400px) {

            .products {
                grid-template-columns: 1fr;
            }

            .product img {
                height: 230px;
            }
        }
    </style>
</head>

<body>

<header>

    <div class="logo">
        CASA <span>NOVA</span>
    </div>

    <button class="btn" onclick="abrirModal()">
        + Agregar
    </button>

</header>


<main class="container">

    <section class="hero">

        <h1>CASA NOVA</h1>

        <p>
            Productos seleccionados para tu hogar
        </p>

    </section>


    <div class="search">

        <input
            type="text"
            id="buscador"
            placeholder="Buscar producto..."
            oninput="buscarProductos()"
        >

    </div>


    <section class="products" id="productos"></section>

</main>


<footer>

    © 2026 Casa Nova — Todos los derechos reservados

</footer>


<!-- ==========================
     MODAL AGREGAR PRODUCTO
========================== -->

<div class="modal" id="modal">

    <div class="modal-content">

        <h2>Agregar producto</h2>

        <div class="form-group">

            <label>
                Nombre del producto
            </label>

            <input
                type="text"
                id="nombre"
                placeholder="Ej: Mesa de comedor"
            >

        </div>


        <div class="form-group">

            <label>
                Precio
            </label>

            <input
                type="number"
                id="precio"
                placeholder="Ej: 250000"
                min="1"
            >

        </div>


        <div class="form-group">

            <label>
                Foto del producto
            </label>

            <input
                type="file"
                id="foto"
                accept="image/*"
            >

        </div>


        <div class="form-buttons">

            <button
                class="cancel"
                onclick="cerrarModal()"
            >
                Cancelar
            </button>

            <button
                class="btn"
                onclick="agregarProducto()"
            >
                Guardar
            </button>

        </div>

    </div>

</div>


<!-- ==========================
     MODAL COMPRA
========================== -->

<div class="modal" id="modalCompra">

    <div class="modal-content">

        <h2>Detalle del producto</h2>


        <img
            id="detalleImagen"
            class="detalle-img"
            src=""
            alt="Producto"
        >


        <div
            id="detalleNombre"
            class="detalle-nombre"
        ></div>


        <div
            id="detallePrecio"
            class="detalle-precio"
        ></div>


        <!-- CANTIDAD -->

        <div class="form-group">

            <label>
                Cantidad
            </label>

            <div class="cantidad-control">

                <button onclick="cambiarCantidad(-1)">
                    −
                </button>

                <input
                    type="number"
                    id="cantidad"
                    value="1"
                    min="1"
                    oninput="actualizarCompra()"
                >

                <button onclick="cambiarCantidad(1)">
                    +
                </button>

            </div>

        </div>


        <!-- MÉTODO DE PAGO -->

        <div class="pago-box">

            <h3>
                Método de pago
            </h3>


            <!-- CONTADO -->

            <label class="opcion-pago">

                <input
                    type="radio"
                    name="metodoPago"
                    value="contado"
                    checked
                    onchange="actualizarCompra()"
                >

                <span>
                    Pago de contado
                </span>

            </label>


            <!-- CRÉDITO -->

            <label class="opcion-pago">

                <input
                    type="radio"
                    name="metodoPago"
                    value="credito"
                    onchange="actualizarCompra()"
                >

                <span>
                    Crédito
                </span>

            </label>


            <!-- SELECCIÓN DE MESES -->

            <div
                class="credito-opciones"
                id="creditoOpciones"
            >

                <label>
                    ¿A cuántos meses desea financiarlo?
                </label>

                <select
                    id="mesesCredito"
                    onchange="actualizarCompra()"
                >

                    <option value="1">
                        1 mes
                    </option>

                    <option value="2">
                        2 meses
                    </option>

                    <option value="3">
                        3 meses
                    </option>

                    <option value="4">
                        4 meses
                    </option>

                    <option value="5">
                        5 meses
                    </option>

                    <option value="6">
                        6 meses
                    </option>

                    <option value="7">
                        7 meses
                    </option>

                    <option value="8">
                        8 meses
                    </option>

                    <option value="9">
                        9 meses
                    </option>

                    <option value="10">
                        10 meses
                    </option>

                    <option value="11">
                        11 meses
                    </option>

                    <option value="12" selected>
                        12 meses
                    </option>

                </select>

            </div>


            <!-- INFORMACIÓN CRÉDITO -->

            <div
                class="credito-info"
                id="creditoInfo"
            >

                <p>
                    <strong>Recargo del crédito:</strong>
                    5%
                </p>

                <p id="textoMeses"></p>

                <p id="cuotaMensual"></p>

            </div>


            <!-- RESUMEN -->

            <div class="resumen">

                <div class="fila">

                    <span>
                        Precio unitario:
                    </span>

                    <span id="resumenPrecio">
                        $0
                    </span>

                </div>


                <div class="fila">

                    <span>
                        Cantidad:
                    </span>

                    <span id="resumenCantidad">
                        1
                    </span>

                </div>


                <div class="fila">

                    <span>
                        Subtotal:
                    </span>

                    <span id="resumenSubtotal">
                        $0
                    </span>

                </div>


                <div
                    class="fila"
                    id="filaInteres"
                    style="display:none;"
                >

                    <span>
                        Recargo 5%:
                    </span>

                    <span id="resumenInteres">
                        $0
                    </span>

                </div>


                <div class="fila total">

                    <span>
                        TOTAL:
                    </span>

                    <span id="resumenTotal">
                        $0
                    </span>

                </div>


                <div
                    class="fila cuota"
                    id="filaCuota"
                    style="display:none;"
                >

                    <span>
                        Cuota mensual:
                    </span>

                    <span id="resumenCuota">
                        $0
                    </span>

                </div>

            </div>

        </div>


        <button
            class="comprar"
            onclick="simularCompra()"
        >
            Comprar ahora
        </button>


        <button
            class="cancel"
            style="width:100%; margin-top:10px;"
            onclick="cerrarCompra()"
        >
            Cerrar
        </button>

    </div>

</div>


<script>

    /* ==========================
       PRODUCTOS
    ========================== */

    let productos =
        JSON.parse(
            localStorage.getItem(
                "casaNovaProductos"
            )
        ) || [];


    let productoSeleccionado = null;


    /* ==========================
       GUARDAR
    ========================== */

    function guardarProductos() {

        localStorage.setItem(
            "casaNovaProductos",
            JSON.stringify(productos)
        );

    }


    /* ==========================
       FORMATO DE PRECIO
    ========================== */

    function formatoPrecio(valor) {

        return Number(valor)
            .toLocaleString("es-CO");

    }


    /* ==========================
       MOSTRAR PRODUCTOS
    ========================== */

    function mostrarProductos(
        lista = productos
    ) {

        const contenedor =
            document.getElementById(
                "productos"
            );


        contenedor.innerHTML = "";


        if (lista.length === 0) {

            contenedor.innerHTML = `
                <div class="empty">
                    No hay productos disponibles.
                </div>
            `;

            return;

        }


        lista.forEach(
            producto => {

                const tarjeta =
                    document.createElement(
                        "div"
                    );


                tarjeta.className =
                    "product";


                tarjeta.innerHTML = `

                    <img
                        src="${producto.foto}"
                        alt="${producto.nombre}"
                    >

                    <div class="product-info">

                        <div class="product-name">
                            ${producto.nombre}
                        </div>

                        <div class="price">
                            $${formatoPrecio(
                                producto.precio
                            )}
                        </div>

                        <button
                            class="delete"
                            onclick="
                                event.stopPropagation();
                                eliminarProducto('${producto.id}')
                            "
                        >
                            Eliminar
                        </button>

                    </div>

                `;


                tarjeta.onclick =
                    function() {

                        abrirCompra(
                            producto.id
                        );

                    };


                contenedor.appendChild(
                    tarjeta
                );

            }
        );

    }


    /* ==========================
       ABRIR AGREGAR
    ========================== */

    function abrirModal() {

        document
            .getElementById("modal")
            .classList.add("active");

    }


    /* ==========================
       CERRAR AGREGAR
    ========================== */

    function cerrarModal() {

        document
            .getElementById("modal")
            .classList.remove(
                "active"
            );


        document.getElementById(
            "nombre"
        ).value = "";


        document.getElementById(
            "precio"
        ).value = "";


        document.getElementById(
            "foto"
        ).value = "";

    }


    /* ==========================
       AGREGAR PRODUCTO
    ========================== */

    function agregarProducto() {

        const nombre =
            document.getElementById(
                "nombre"
            ).value.trim();


        const precio =
            document.getElementById(
                "precio"
            ).value;


        const archivo =
            document.getElementById(
                "foto"
            ).files[0];


        if (
            !nombre ||
            !precio ||
            !archivo
        ) {

            alert(
                "Completa todos los campos."
            );

            return;

        }


        if (
            Number(precio) <= 0
        ) {

            alert(
                "El precio debe ser mayor que cero."
            );

            return;

        }


        const lector =
            new FileReader();


        lector.onload =
            function(e) {

                const nuevoProducto = {

                    id:
                        Date.now().toString(),

                    nombre:
                        nombre,

                    precio:
                        Number(precio),

                    foto:
                        e.target.result

                };


                productos.push(
                    nuevoProducto
                );


                guardarProductos();

                mostrarProductos();

                cerrarModal();

            };


        lector.readAsDataURL(
            archivo
        );

    }


    /* ==========================
       ELIMINAR PRODUCTO
    ========================== */

    function eliminarProducto(id) {

        const confirmar =
            confirm(
                "¿Quieres eliminar este producto?"
            );


        if (!confirmar)
            return;


        productos =
            productos.filter(
                producto =>
                    producto.id !== id
            );


        guardarProductos();

        mostrarProductos();

    }


    /* ==========================
       BUSCAR
    ========================== */

    function buscarProductos() {

        const texto =
            document
                .getElementById(
                    "buscador"
                )
                .value
                .toLowerCase()
                .trim();


        const filtrados =
            productos.filter(
                producto =>
                    producto.nombre
                        .toLowerCase()
                        .includes(texto)
            );


        mostrarProductos(
            filtrados
        );

    }


    /* ==========================
       ABRIR COMPRA
    ========================== */

    function abrirCompra(id) {

        const producto =
            productos.find(
                p => p.id === id
            );


        if (!producto)
            return;


        productoSeleccionado =
            producto;


        document.getElementById(
            "detalleImagen"
        ).src =
            producto.foto;


        document.getElementById(
            "detalleNombre"
        ).textContent =
            producto.nombre;


        document.getElementById(
            "detallePrecio"
        ).textContent =
            "$" +
            formatoPrecio(
                producto.precio
            );


        document.getElementById(
            "cantidad"
        ).value = 1;


        document.querySelector(
            'input[value="contado"]'
        ).checked = true;


        document.getElementById(
            "mesesCredito"
        ).value = 12;


        document
            .getElementById(
                "modalCompra"
            )
            .classList.add(
                "active"
            );


        actualizarCompra();

    }


    /* ==========================
       CERRAR COMPRA
    ========================== */

    function cerrarCompra() {

        document
            .getElementById(
                "modalCompra"
            )
            .classList.remove(
                "active"
            );


        productoSeleccionado =
            null;

    }


    /* ==========================
       CAMBIAR CANTIDAD
    ========================== */

    function cambiarCantidad(
        valor
    ) {

        const input =
            document.getElementById(
                "cantidad"
            );


        let cantidad =
            Number(
                input.value
            ) || 1;


        cantidad += valor;


        if (cantidad < 1) {

            cantidad = 1;

        }


        input.value =
            cantidad;


        actualizarCompra();

    }


    /* ==========================
       ACTUALIZAR COMPRA
    ========================== */

    function actualizarCompra() {

        if (
            !productoSeleccionado
        )
            return;


        let cantidad =
            Number(
                document.getElementById(
                    "cantidad"
                ).value
            );


        if (
            cantidad < 1 ||
            isNaN(cantidad)
        ) {

            cantidad = 1;

            document.getElementById(
                "cantidad"
            ).value = 1;

        }


        const precio =
            Number(
                productoSeleccionado
                    .precio
            );


        const subtotal =
            precio * cantidad;


        const metodo =
            document.querySelector(
                'input[name="metodoPago"]:checked'
            ).value;


        let recargo = 0;

        let total =
            subtotal;


        let meses = 1;

        let cuota = 0;


        /* CONTADO */

        if (
            metodo === "contado"
        ) {

            document
                .getElementById(
                    "creditoOpciones"
                )
                .classList.remove(
                    "active"
                );


            document
                .getElementById(
                    "creditoInfo"
                )
                .classList.remove(
                    "active"
                );


            document.getElementById(
                "filaInteres"
            ).style.display =
                "none";


            document.getElementById(
                "filaCuota"
            ).style.display =
                "none";

        }


        /* CRÉDITO */

        else {

            document
                .getElementById(
                    "creditoOpciones"
                )
                .classList.add(
                    "active"
                );


            recargo =
                subtotal * 0.05;


            total =
                subtotal +
                recargo;


            meses =
                Number(
                    document.getElementById(
                        "mesesCredito"
                    ).value
                );


            cuota =
                total / meses;


            document
                .getElementById(
                    "creditoInfo"
                )
                .classList.add(
                    "active"
                );


            document.getElementById(
                "filaInteres"
            ).style.display =
                "flex";


            document.getElementById(
                "filaCuota"
            ).style.display =
                "flex";


            document.getElementById(
                "textoMeses"
            ).innerHTML =
                "<strong>Plazo:</strong> " +
                meses +
                (
                    meses === 1
                        ? " mes"
                        : " meses"
                );


            document.getElementById(
                "cuotaMensual"
            ).innerHTML =
                "<strong>Cuota mensual:</strong> $" +
                formatoPrecio(
                    cuota
                );

        }


        /* RESUMEN */

        document.getElementById(
            "resumenPrecio"
        ).textContent =
            "$" +
            formatoPrecio(
                precio
            );


        document.getElementById(
            "resumenCantidad"
        ).textContent =
            cantidad;


        document.getElementById(
            "resumenSubtotal"
        ).textContent =
            "$" +
            formatoPrecio(
                subtotal
            );


        document.getElementById(
            "resumenInteres"
        ).textContent =
            "$" +
            formatoPrecio(
                recargo
            );


        document.getElementById(
            "resumenTotal"
        ).textContent =
            "$" +
            formatoPrecio(
                total
            );


        document.getElementById(
            "resumenCuota"
        ).textContent =
            "$" +
            formatoPrecio(
                cuota
            );

    }


    /* ==========================
       SIMULAR COMPRA
    ========================== */

    function simularCompra() {

        if (
            !productoSeleccionado
        )
            return;


        const cantidad =
            Number(
                document.getElementById(
                    "cantidad"
                ).value
            );


        const precio =
            Number(
                productoSeleccionado
                    .precio
            );


        const subtotal =
            precio * cantidad;


        const metodo =
            document.querySelector(
                'input[name="metodoPago"]:checked'
            ).value;


        let mensaje;


        if (
            metodo === "credito"
        ) {

            const meses =
                Number(
                    document.getElementById(
                        "mesesCredito"
                    ).value
                );


            const recargo =
                subtotal * 0.05;


            const total =
                subtotal +
                recargo;


            const cuota =
                total / meses;


            mensaje =
                "COMPRA SIMULADA\n\n" +

                "Producto: " +
                productoSeleccionado
                    .nombre +

                "\nCantidad: " +
                cantidad +

                "\n\nMétodo: Crédito" +

                "\nPlazo: " +
                meses +
                (
                    meses === 1
                        ? " mes"
                        : " meses"
                ) +

                "\nRecargo: 5%" +

                "\nValor recargo: $" +
                formatoPrecio(
                    recargo
                ) +

                "\n\nTOTAL A PAGAR: $" +
                formatoPrecio(
                    total
                ) +

                "\n\nCUOTA MENSUAL: $" +
                formatoPrecio(
                    cuota
                );

        }


        else {

            mensaje =
                "COMPRA SIMULADA\n\n" +

                "Producto: " +
                productoSeleccionado
                    .nombre +

                "\nCantidad: " +
                cantidad +

                "\n\nMétodo: Pago de contado" +

                "\n\nTOTAL A PAGAR: $" +
                formatoPrecio(
                    subtotal
                );

        }


        alert(
            mensaje
        );

    }


    /* ==========================
       INICIAR
    ========================== */

    mostrarProductos();

</script>

</body>
</html>
