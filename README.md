<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Vida Salud IPS</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f2f2f2;
      margin: 0;
      padding: 0;
    }
    header, footer {
      background: #005F73;
      color: white;
      padding: 1rem;
      text-align: center;
    }
    nav {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      background: #94d2bd;
      padding: 1rem;
    }
    nav button {
      margin: 0.5rem;
      padding: 0.8rem 1.2rem;
      border: none;
      border-radius: 8px;
      background: #0A9396;
      color: white;
      font-size: 1rem;
      cursor: pointer;
    }
    section {
      padding: 2rem;
    }
    form input, form textarea, form select {
      width: 100%;
      margin: 0.5rem 0;
      padding: 0.5rem;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    form button {
      background: #005F73;
      color: white;
      border: none;
      padding: 0.7rem 1.2rem;
      border-radius: 6px;
      font-weight: bold;
      cursor: pointer;
    }
    .footer-info {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-around;
      text-align: left;
    }
    .footer-info div {
      margin: 1rem;
    }
    .pdf-viewer {
      width: 100%;
      height: 800px;
      border: none;
    }
    .login-container {
      max-width: 400px;
      margin: 2rem auto;
      background: white;
      padding: 2rem;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    .login-container h2 {
      text-align: center;
    }
    .search-bar {
      margin: 1rem auto;
      text-align: center;
    }
    .search-bar input {
      width: 60%;
      padding: 0.5rem;
      border-radius: 5px;
      border: 1px solid #ccc;
      font-size: 1rem;
    }
    .logout-btn {
      background-color: #bb3e03;
      margin-left: 1rem;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 1rem;
    }
    table, th, td {
      border: 1px solid #ccc;
    }
    th, td {
      padding: 0.75rem;
      text-align: left;
    }
    th {
      background-color: #0A9396;
      color: white;
    }
  </style>
</head>
<body>
  <header>
    <h1>Vida Salud IPS</h1>
    <p>Sistema desarrollado por el Ingeniero de Sistemas Full Stack Jorge Adolfo Cerón | jorgeadolfceron@gmail.com</p>
  </header>

  <section class="login-container" id="login">
    <h2>Iniciar Sesión</h2>
    <form onsubmit="return iniciarSesion()">
      <input type="text" id="usuario" placeholder="Usuario" required>
      <input type="password" id="clave" placeholder="Contraseña" required>
      <button type="submit">Entrar</button>
    </form>
  </section>

  <nav id="navegacion" style="display:none">
    <button onclick="mostrarFormulario('agendamiento')">Agendamiento de Citas</button>
    <button onclick="mostrarFormulario('confirmacion')">Confirmación de Asistencia</button>
    <button onclick="mostrarFormulario('cobranza')">Gestión de Cobranza</button>
    <button onclick="mostrarFormulario('espera')">Lista de Espera</button>
    <button onclick="mostrarFormulario('leads')">Gestión de Leads</button>
    <button onclick="mostrarFormulario('encuestas')">Encuestas</button>
    <button onclick="mostrarFormulario('cliente')">Servicio al Cliente</button>
    <button onclick="mostrarFormulario('faq')">Preguntas Frecuentes</button>
    <button onclick="mostrarFormulario('documentos')">Documentos en PDF</button>
    <button onclick="mostrarFormulario('buscador')">Buscador de Google</button>
    <button onclick="mostrarFormulario('chatbot')">Chatbot Soporte</button>
    <button onclick="mostrarFormulario('directorio')">Directorio Médico</button>
    <button class="logout-btn" onclick="cerrarSesion()">Cerrar Sesión</button>
  </nav>

  <div class="search-bar" id="searchBar" style="display:none">
    <input type="text" placeholder="Buscar en el sistema...">
  </div>

  <section id="contenido">
    <p>Selecciona una opción para iniciar.</p>
  </section>

  <footer>
    <div class="footer-info">
      <div>
        <h3>Líneas de atención al usuario</h3>
        <p>Régimen subsidiado:<br>018000 93 04 22<br>WhatsApp: +57 300 912 6625<br>COVID: +57 300 912 6639</p>
      </div>
      <div>
        <h3>Régimen contributivo</h3>
        <p>Línea nacional: 018000 93 04 22<br>Afiliados: +57 300 912 6625 opc. 1-3<br>Empleadores: +57 300 912 6625 opc. 2</p>
      </div>
      <div>
        <h3>Oficinas y redes</h3>
        <p>Nariño, Putumayo, Valle del Cauca, Cauca<br>Microredes, puntos de atención, empleo, documentos.</p>
      </div>
    </div>
    <div>
      <p>Versión: 1.0.0 | Última actualización: 30 de mayo de 2025</p>
      <p>Desarrollado con ❤️ por Jorge Adolfo Calambás Cerón - 3160675159 - jorgeadolfoceron@gmail.com</p>
    </div>
  </footer>

  <script>
    function iniciarSesion() {
      const user = document.getElementById('usuario').value;
      const pass = document.getElementById('clave').value;
      if (user === "admin" && pass === "1234") {
        document.getElementById('login').style.display = 'none';
        document.getElementById('navegacion').style.display = 'flex';
        document.getElementById('searchBar').style.display = 'block';
        document.getElementById('contenido').innerHTML = '<p>Bienvenido al sistema Vida Salud IPS.</p>';
        return false;
      } else {
        alert("Credenciales incorrectas");
        return false;
      }
    }

    function cerrarSesion() {
      document.getElementById('login').style.display = 'block';
      document.getElementById('navegacion').style.display = 'none';
      document.getElementById('searchBar').style.display = 'none';
      document.getElementById('contenido').innerHTML = '<p>Selecciona una opción para iniciar.</p>';
    }

    function mostrarFormulario(tipo) {
      const formularios = {
        agendamiento: `<h2>Agendamiento de Citas</h2><form><input type="text" placeholder="Nombre completo"><input type="email" placeholder="Correo electrónico"><input type="date"><textarea placeholder="Motivo de la cita"></textarea><button type="submit">Agendar</button></form>`,
        confirmacion: `<h2>Confirmación de Asistencia</h2><form><input type="text" placeholder="Número de documento"><input type="date"><select><option>Confirmo</option><option>No Confirmo</option></select><button type="submit">Enviar</button></form>`,
        cobranza: `<h2>Gestión de Cobranza</h2><form><input type="text" placeholder="Nombre del paciente"><input type="text" placeholder="Factura N°"><textarea placeholder="Comentarios sobre el estado de pago"></textarea><button type="submit">Registrar</button></form>`,
        espera: `<h2>Gestión de Lista de Espera</h2><form><input type="text" placeholder="Nombre"><input type="text" placeholder="Servicio requerido"><input type="tel" placeholder="Teléfono de contacto"><button type="submit">Agregar a lista</button></form>`,
        leads: `<h2>Gestión de Leads</h2><form><input type="text" placeholder="Nombre del contacto"><input type="email" placeholder="Correo electrónico"><input type="text" placeholder="Interés o servicio de interés"><button type="submit">Guardar Lead</button></form>`,
        encuestas: `<h2>Encuesta de Satisfacción</h2><form><label>¿Cómo califica nuestro servicio?</label><br><select><option>Excelente</option><option>Bueno</option><option>Regular</option><option>Malo</option></select><textarea placeholder="Comentarios adicionales"></textarea><button type="submit">Enviar Encuesta</button></form>`,
        cliente: `<h2>Servicio al Cliente</h2><form><input type="text" placeholder="Nombre completo"><input type="email" placeholder="Correo electrónico"><textarea placeholder="Describe tu solicitud"></textarea><button type="submit">Enviar</button></form>`,
        faq: `<h2>Preguntas Frecuentes</h2><ul><li>¿Cómo afiliarme?</li><li>¿Dónde solicito una cita?</li><li>¿Cómo obtener mi historia clínica?</li><li>¿Qué hacer si tengo una urgencia?</li></ul>`,
        documentos: `<h2>Documentos en PDF</h2><iframe class="pdf-viewer" src="https://drive.google.com/file/d/1mAQeG7IUtBkFVPCBiUqqMwEi-5u0kxOa/preview" allow="autoplay"></iframe>`,
        buscador: `<h2>Buscador de Google</h2><form action="https://www.google.com/search" method="get" target="_blank"><input type="text" name="q" placeholder="Buscar en Google"><button type="submit">Buscar</button></form>`,
        chatbot: `<h2>Chatbot de Soporte</h2><p>Hola, soy tu asistente virtual. ¿En qué puedo ayudarte hoy?</p><div id="chatbot-widget"></div><script src="https://cdn.botpress.cloud/webchat/v0/inject.js"></script><script>window.botpressWebChat.init({ host: "https://cdn.botpress.cloud/webchat/v0", botId: "your-bot-id" });</script>`,
        directorio: `<h2>Directorio Médico</h2><table><thead><tr><th>Nombre</th><th>Especialidad</th><th>Teléfono</th><th>Correo</th><th>Sede</th></tr></thead><tbody><tr><td>Dra. Laura Martínez</td><td>Medicina General</td><td>3011234567</td><td>laura@vidasalud.com</td><td>Popayán</td></tr><tr><td>Dr. Carlos Pérez</td><td>Pediatría</td><td>3019876543</td><td>carlos@vidasalud.com</td><td>Cali</td></tr><tr><td>Dra. Ana Gómez</td><td>Ginecología</td><td>3023456789</td><td>ana@vidasalud.com</td><td>Pasto</td></tr><tr><td>Dr. Andrés Díaz</td><td>Odontología</td><td>3009988776</td><td>andres@vidasalud.com</td><td>Popayán</td></tr></tbody></table>`
      };
      document.getElementById('contenido').innerHTML = formularios[tipo] || '<p>Opción no disponible.</p>';
    }
  </script>
</body>
</html>
# vidasaludips-web-app
