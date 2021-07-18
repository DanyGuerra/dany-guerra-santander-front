# 8. Email development / Deploy de un sitio estático (Email de Bienvenida)

En esta sección se aprenderá como se puede crear un email de bienvenida con una plantilla utilizando HTML y CSS asi como las limitantes que se tienen al realizar la misma. Además se hará Deploy del proyecto realizado a lo largo de las sesiones en un sitio estático.
## Limitaciones de emails

En esta sección aprende sobre las limitaciones que existen al hacer código para emails. Si bien los emails se diseñan con HTML y CSS, el flujo de desarrollo y las características más recientes de estos lenguajes no están disponibles para la creación de emails.

La mayoría de clientes de correo electrónico no son compatibles con todos los tipos de contenido HTML que se ve en la Web. Los navegadores Web pueden mostrar secuencias de comandos, animaciones y menús de navegación complejos, mientras que tu bandeja de entrada normal no está creada para gestionar este tipo de contenido.

| Seguro de usar | Utilizar con precaución | No usar |
|--------|-----------|-------------|
| -Diseños estáticos basados ​​en tablas <br>-HTML y tablas anidadas <br>- Anchura de la plantilla de 600-800px <br>-Simple, CSS en línea <br> -Fuentes seguras para Web |-Imágenes de fondo <br>-fuentes personalizadas para Web <br>-Diseños anchos <br>-Mapas de imagen <br>-CSS incrustado | -JavaScript <br>-`<iframe>` <br>-Flash <br>-Audio incrustado <br>-vídeo incrustado <br>-formularios <br>-estratificación `<div>`|

- Seguro de usar: ampliamente compatible con la mayoría de clientes de correo electrónico

- Utilizar con precaución: compatibilidad limitada con la mayoría de clientes de correo electrónico

- No usar: no es compatible con la mayoría de clientes de correo electrónico

[Como crear el HTML de un email para una platilla responsive](http://blog.fidelizador.com/2020/01/22/html-email-plantilla-responsive/)

### Correo de bienvenida

Para agregar la funcionalidad del correo de bienvenida se agrega el codigo de Javascript siguiente.

```
$("[data-toggle=popover]").popover();

// Crear proyecto de node

// npm init -> agregar la configuración

// npm i sass -> instalar dependencia de sass desde https://www.npmjs.com/package/sass

// crear .gitignore y agregar texto de la pagina -> https://www.toptal.com/developers/gitignore/api/node

// ejecutar comando -> ./node_modules/sass/sass.js --watch ./scss/main.scss output.css

// Si es desde windows -> node ./node_modules/sass/sass.js --watch ./scss/main.scss output.css


// Variables -----------------------------------------------------------

// const x = 5
// let y = 5

// console.log(y);

// y = 6

// var z = 6
// z = 8

// console.log(z);
// ------------------------------------------------------------



const forms = document.querySelectorAll(".signup-form")

// console.log(forms);

// function suma(a, b) {
//   return a + b
// }

const getTemplate = () => {
  return fetch("./template.html")
    .then((response) => response.text())
}

const sendEmailToApi = (address, template) => {
  fetch(`https://bedu-email-sender-api.herokuapp.com/send?id`, {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
    },
    body: JSON.stringify({
      address: address,
      template: template,
    }),
  })
    .then((results) => {
      console.log(results.status);
      if (results.status == 200) {
        alert("E-mail send!!!")
      } else {
        alert("Send failed")
      }
      document.getElementById("email").value = ""
    })
    .catch((error) => {
      console.error(error);
      document.getElementById("email").value = ""
      alert("Send failed")
    });
};

function sendEmail(miVariable) {
  miVariable.preventDefault()
  const email = miVariable.target.querySelector("input").value
  getTemplate()
    .then((template) => {
      sendEmailToApi(email, template)
    })
    .catch((error) => {
      console.log(error, "error al obtener el template");
    })
}

// const sendEmail = (miVariable) => {
//   miVariable.preventDefault()
//   console.log(miVariable);
// }

for (let i = 0; i < forms.length; i++) {
  // console.log(forms[i]);
  forms[i].addEventListener("submit", sendEmail)
}


```

Ademas se agrega la plantilla HTML del correo el cual se mandara:

```
<table
  style="width: 100%; max-width: 600px; text-align: center; margin: 0 auto; background-color: #fffbf7; color: #025157;">
  <tr>
    <td>
      <a href="https://fervent-almeida-b80b1e.netlify.com/" target="_blank" style="display:block;">
        <img style="width: 50px; margin-top: 15px; margin-bottom: 15px;"
          src="https://getmatcha.com/wp-content/uploads/2020/01/Icon-green.png" alt="Matcha" />
      </a>
    </td>
  </tr>
  <tr>
    <!-- Aquí irá la imagen descriptiva de Matcha -->
    <td>
      <img style="width: 100%;" src="https://getmatcha.com/wp-content/themes/getmatcha/css/../img/home_people.png"
        alt="People at Matcha" />
    </td>
  </tr>
  <tr>
    <!-- Aquí irá el texto de bienvenida y el cta -->
    <td>
      <main class="container">
        <header class="header">
          <h1>Hi, there</h1>
          <p style="font-size: 18px; padding: 0px 20px 0px 20px; color: #000000;">
            Thanks for cheking out Marcha, Instantly publish articles, drive more traffic, grow
            your email list, and see your blog's impact on sales.
          </p>
          <a href="https://getmatcha.com/">
            <button style="
            background-color: #025157;
            padding: 15px;
            font-weight: 600;
            margin-bottom: 20px;
            color: #ffffff;">EXPLORE MATCHA</button>
            </button>
      </main>
    </td>
  </tr>
  <tr>
    <!-- Aquí irá las características que Matcha provee -->
    <td style="
        border-top: 1px solid #999999d1;
        border-bottom: 1px solid #999999d1;
        padding-top: 35px;
        padding-bottom: 35px;
      ">
      <table style="
          text-align: center;
          width: 100%;
          color: #025157;
          font-family: Arial, Helvetica, sans-serif;
        ">
        <tr>
          <td style="width: 50%">
            <img style="height: 300px;" src="https://getmatcha.com/wp-content/themes/getmatcha/img/ill-publish.png"
              alt="Publish" />
            <h2>Publish</h2>
          </td>
          <td style="width: 50%">
            <img style="height: 300px;" src="https://getmatcha.com/wp-content/themes/getmatcha/img/ill-promote.png"
              alt="Promote" />
            <h2>Promote</h2>
          </td>
        </tr>
        <tr>
          <td>
            <img style="height: 300px;" src="https://getmatcha.com/wp-content/themes/getmatcha/img/ill-capture.png"
              alt="Capture" />
            <h2>Capture</h2>
          </td>
          <td>
            <img style="height: 300px;" src="https://getmatcha.com/wp-content/themes/getmatcha/img/ill-measure.png"
              alt="Measure" />
            <h2>Measure</h2>
          </td>
        </tr>
      </table>
    </td>
  </tr>
  <tr>
    <!-- Aquí irá el pie de página con enlaces a redes sociales -->
    <td style="
      padding-top: 20px;
      padding-bottom: 20px;
      font-family: 'Times New Roman', Times, serif;
      color: #46484c;
      font-size: 16px;
    ">
      <p>Follow us on:</p>
      <div>
        <a href="https://www.instagram.com/matchacontent" style="display: inline-block; width: 50px; height: 50px;">
          <img style="width: 100%;"
            src="https://images.vexels.com/media/users/3/137380/isolated/preview/1b2ca367caa7eff8b45c09ec09b44c16-icono-de-instagram-logo-by-vexels.png"
            alt="Instagram" />
        </a>
        <a href="https://www.facebook.com/matchacontent/" style="display: inline-block; width: 50px; height: 50px;">
          <img style="width: 100%;"
            src="https://images.vexels.com/media/users/3/137253/isolated/preview/90dd9f12fdd1eefb8c8976903944c026-icono-de-facebook-logo-by-vexels.png"
            alt="Facebook" />
        </a>
        <a href="https://twitter.com/matchacontent" style="display: inline-block; width: 50px; height: 50px;">
          <img style="width: 100%;"
            src="https://images.vexels.com/media/users/3/137419/isolated/preview/b1a3fab214230557053ed1c4bf17b46c-icono-de-twitter-logo-by-vexels.png"
            alt="Twitter" />
        </a>
        <a href="https://linkedin.com/company/matchacontent" style="display: inline-block; width: 50px; height: 50px;">
          <img style="width: 100%;"
            src="https://images.vexels.com/media/users/3/140687/isolated/preview/f705441ceeb70b9920ce6c37d80f5603-linkedin-distorsionado-icono-redondo-by-vexels.png"
            alt="LinkedIn" />
        </a>
      </div>
      <p>
        © 2021 Matcha. All Rights Reserved
      </p>
    </td>
  </tr>
</table>

```


## Deploy de un sitio estático

Un hosting es un servicio en línea que te permite publicar un sitio o aplicación web en Internet. Cuando te registras en un servicio de alojamiento, básicamente alquilas un espacio en un servidor donde puedes almacenar todos los archivos y datos necesarios para que tu sitio web funcione correctamente.

Existen varios servicios de alojamiento en la Web gratuitos entre ellos tenemos los siguientes.

- GitHub Pages

- Firebase de Google

- Netlify

- Heroku

- Zeit

En este proyecto se usará Netlify para alojar nuestra página.




### [Regresar](../sesion7)

### [Menu](../README.md)