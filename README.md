# Adinet 2Auth

Adinet 2Auth es una libreria de 2 factor para inicio de sesion segura en plataformas internas.

## Instalacion

puedes instalarlo desde npm 

`$ npm install npm-adinet-2auth`

o tambien puedes clonar el repositorio 

`$ git clone https://github.com/chechooxd/Adinet-2Auth.git`

## Como se usa

### Creacion y envio de Codigo

``` [JS]
const auth = require('npm-adinet-2auth')

const mailConfig = {
  host: "smtp.example.com",
  port: 587,
  secure: false, // upgrade later with STARTTLS
  auth: {
    user: "username",
    pass: "password",
  },
}

const from = 'example@from.com'

auth.addCode(mailConfig, from, 'userName', 'user@email.com')

```
### Validacion de Codigo

``` [JS]
const auth = require('npm-adinet-2auth')

var valid = auth.validateCode('userName', 'code') // return Boolean

```

### Expiracion de Codigo

``` [JS]
const auth = require('npm-adinet-2auth')

var CODES = auth.getCode()

const expire = () => {
    for (const {id, time} of CODES) {
        auth.expireCode(id, time)
    }
} 

setTimeout(expire(), 3000);

```

## Licencia 

MIT
