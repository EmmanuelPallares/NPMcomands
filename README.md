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
