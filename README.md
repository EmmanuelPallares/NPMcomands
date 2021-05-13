# Actualizar paquetes

Revisar que paquetes disponen de nuevas versiones.
    npm outdate

Para ver un output más detallado.

    npm outdate --dd

Actualizar los paquetes que no están en la ultima versión.

    npm update

Actualizar un paquete específico.

    npm install json-server@latest

# Eliminar paquetes

Eliminar un paquete de node_modules y del archivo package.json.

     npm uninstall json-server

Desinstalar un paquete de todo node_modules pero no del archivo package.json.
        npm uninstall webpack --no-save

# Solución de errores

En caso de que nuestros archivos de node_module no estén bien instalados o tengamos una versión anterior lo que podemos hacer es lo siguiente:

    npm cache clear --force
#Para verificar que verdaderamente se borro podemos usar
    npm cache clear --force
    #Para verificar que verdaderamente se borro podemos usar
    npm cache verify

Uno de los errores que podemos tener es tener algún valor corrupto en node_module, o tambien que la instalación no este completa de los paquetes que hemos instalado, para ello podemos eliminar el paquete con el siguiente comando:

    rm -rf node_modules  #este comando eliminar la carpeta 


Otra alternativa para eliminar de forma segura una carpeta es instalando el siguiente paquete:

    sudo npm install -g rimraf

Ahora podemos ejecutar el siguiente comando para eliminar node_module.

    rimraf node_modules 
    #Ahora podemos volver a instalar nuestro paquetes
    npm install


# Seguridad 

Para ver las vulnerabilidades que tenemos en nuestro proyecto.

    npm audit

Nos genera un json con información un poco mas detallada de lo que esta pasando con estos paquetes que instalamos.

    npm audit --json

Una vez sepamos cual es la vulnerabilidad podemos proceder a actualizar cualquiera de los paquetes e instalar todas sus dependencias con un nivel 2 ejemplo:

    npm update eslint-utils --depth 2


Solucionar las vulnerabilidades que tengamos en nuestro proyecto básicamente, actualiza a la ultima version nuestros paquetes con las dependencias que requieren.
    npm audit fix

Despues volvemos a ejecutar npm audit para ver el nuevo estado y ver que no tengamos vulnerabilidades.

# Crear un paquete para npm

Crear la carpeta y archivos básicos

    pwd
    mkdir packageTest
    cd packageTest
    git init
    npm init

Se crea el archivo index.js en la carpeta src.
```javascript
// Se declara el arreglo
const messages = [
    "David",
    "Diana",
    "Ana Maria",
    "Isabela",
    "Antonio",
    "Norma"
]

//Crear función para enviar aleatoriamente  los nombres del arreglo
const randomMsg = () => {
    const message = messages[Math.floor(Math.random()*messages.length)]
    console.log(message)
}

// Exportar como un módulo

module.exports = { randomMsg }
```

Se debe crear una carpeta bin donde se crea el archivo global.js (Configuración que se necesita).

```javascript
#!/usr/bin/env node
// se va ejecutar dentro de bash

//Variable que llama la funcion que exportamos
let random = require('../src/index.js')

//Ejecuto la funcion
random.randomMsg()
```
Modifico el package.json y coloco la configuración de bin que necesito.
```javascript
  "bin": {
    "random-msg": "./bin/global.js"
  },
  "preferGlobal": true
```

Primero se debe probar de forma local.

    pwd
    npm link
    #Se ejecuta la función
    random-msg

Otra forma de instalar el paquete.

    npm i -g C:\Users\Emmanuel\random-messages

Crear cuenta para poder subir el paquete
- Npm.js https://www.npmjs.com/
- Verificar la cuenta que llega al correo electrónico registrado.

Se loguea a la cuenta creada por consola y se publica el paquete

    npm adduser
    npm publish
