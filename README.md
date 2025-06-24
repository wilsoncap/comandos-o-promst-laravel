# Comandos o Prompts en Laravel

Como todos sabemos, los comandos o prompts son tareas que creamos para que el servidor las ejecute por nosotros. Sin embargo, también podemos crear otras funcionalidades con estos. Este es un claro ejemplo de otros usos de los comandos.

En este caso, creamos un comando que define una ruta en la cual se generará un fichero previamente definido. Para este ejemplo, tenemos una carpeta llamada src dentro de la carpeta App. Esta carpeta también podría ubicarse a nivel del proyecto, pero en ese caso sería necesario realizar una configuración adicional para que Laravel la reconozca. Con la intención de mantener este ejemplo lo más simple posible, colocamos src dentro de App.

Dentro de esta carpeta, organizamos las funcionalidades en subcarpetas por módulos o features. Si bien estructurar el proyecto por módulos puede parecer tedioso, gracias a los comandos podemos automatizar este proceso. Por eso, creamos un comando específico con el propósito de simplificar la creación de esta estructura

### ¿Como funciona?

El uso del comando es muy sencillo. Solo debes escribir el nombre del comando junto con el nombre del módulo que desees crear, ¡y listo!

``php artisan make:module Vehicle``

![Captura de pantalla 2023-05-18 204208](https://github.com/user-attachments/assets/b2daf24d-1cff-40a8-8df4-92c3767db435)



**Nota:**  Para conservar la convención de Laravel, el módulo se crea en singular, ya que también se genera un modelo, el cual por convención debe estar en singular.

### Esto es un ejemplo básico de como puedes crear un comando con esta funcionalidad, sientete libre de personalizarlo como mejor te parezca ó lo necesites

