# login-lecc42

Sprint V:

- En este proyecto hemos creado un Log In de Laboratoria, uno se puede logear normal o mediante la cuenta de Facebook.

Ver el proyecto terminado https://rosariofelix.github.io/login-lecc42/

## Hemos Utilizado

- HTML
- CSS
- JS
- jQuery
- API de facebook (crear tu propia app)
- Serve  ( para que levante un serve al proyecto )

## Componentes

- Script para cargar el SDK de Facebook

``` sh
(function(thisdocument,scriptelement,id){
    var js, fjs = thisdocument.getElementsByTagName(scriptelement)[0];
    if(thisdocument.getElementById(id)) return;

    js = thisdocument.createElement(scriptelement); js.id = id;
    js.src = "//connect.facebook.net/en_US/sdk.js";
    fjs.parentNode.insertBefore(js, fjs);
  }(document, 'script', 'facebook-jssdk'));
```
- Se ha cargo los componentes de HTML mediante JS:
  - Header
  - Dashboard
  - login
  
``` sh
const Login = () =>{
  const login       = $('<div class = "login"></div>');
  const title       = $('<h1>Log into Laboratoria</h1>');
  const email       = $('<input type = "email" class = "username" placeholder= "Correo electronico"/>');
  const password    = $('<input type = "password" class = "password" placeholder= "Contraseña"/>');
```
- Obtener informacion del usuario nombre y email

``` sh


function loginHandler(response){
  if(response.status === 'connected'){
    state.status = "Conectado";
    FB.api('/me?fields=email,name', user =>{
      state.user = user;
      state.doRender();
    })
  }else if( response.status === 'not_authorized'){
    state.user = null;
    state.status = "Aplicación no autorizada"
    state.doRender();
  }
};

function doLogin(){
  FB.login(loginHandler, {scope: 'email'});
}
```
