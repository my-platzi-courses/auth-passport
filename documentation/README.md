# Curso de Autenticación con Passport.js

## Autenticación de Usuarios de PlatziVideo

Añade la capa de autenticación y comunicación con una API de forma segura. Usando Passport.js implementa el sign in y el sign up de la aplicación de PlatziVideo.

# Arquitectura del proyecto Platzi Video

En este curso vamos agregar unos endpoints para hacer signin - es decir para autenticar un usuario - y un endpoint para hacer signup - es decir para crear nuevos usuarios.

Para poder consumir este endpoint de signin, los clientes en este caso el Admin Client que es el que esta debajo de nuestro API Server, y el Render Server que es el que esta a la izquierda, necesitan un API Token, un API Token es muy diferente a un Access Token.

Este API Token, nos permite definir los permisos que van a tener estos clientes.

Admin Client -> API Token -> Permiso Administrativo
        - Leer 
        - Actualizar
        - Crear
        - Eliminar

Render Server -> API Token -> Permiso Publico
        - Leer

Cuando el Render Server o el Admin Client haciendo uso de estos diferentes API Token hagan autenticación, toda nuestra estrategia de autenticación va generar un Access Token, este Access Token va ser un JSON Web Token, que va tener la información del usuario que hace autenticación y los permisos determinados por el API Token.
De esta manera en las peticiones siguientes nuestro Render Server o Admin Client con el Access Token que fue generado, va poder consumir los recursos de API Token.

La SPA, se va comunicar por medio del Render Server que va ser de Proxy. Para esta arquitectura es muy importante que la SPA tenga un servidor, por que toda la comunicación que sucede de los Access Token mediante el API Server debe ocurrir dentro del servidor.

La manera en que la SPA se va comunicar el API Server, es mediante una Cookie que va tener el Access Token del Render Server.