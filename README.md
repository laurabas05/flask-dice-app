# Practica: Flask Dice Roller

## Comandos utilizados

1. **Para crear la imagen**

`docker build -t flask-dice-app`

3. **Para ejecutarla**
- `docker run --rm -p 8888:5000 flask-dice-app` sin la variable
- `docker run --rm -p 8888:5000 -e DICE_SIDES=20 flask-dice-app` con la variable

## Página funcionando en http://localhost:8888

<img width="1012" height="612" alt="image" src="https://github.com/user-attachments/assets/e86fffe7-12be-4845-90c9-72ca41967df0" />

## ¿Qué cambia al usar `-e DICE_SIDES=...`
Al ejecutar la imagen proporcionándole un valor a la variable, se cambia tanto el número de caras que tiene el dado como la cantidad de números random que nos pueden aparecer al rerollear el dado. Esto es así porque en nuestra app hemos implementado una función que, según el valor que le damos al número de la variable, le asignamos un determinado número de caras. En caso de que no introduzcamos la variable, el valor por defecto sería 6.

# Versión 2 Flask Dice Roller: compose y archivo .env

## ¿Qué hemos hecho en esta versión?

Hemos creado un archivo `.env` para almacenar las variables de entorno. En este caso, una variable llamada `DICE_SIDES` que define el número de cara de los dados (en este caso yo le he puesto 10).

```
DICE_SIDES=10
```

También hemos creado un archivo `compose.yml` definiendo un servicio `web` para que construya la imagen a partir del `Dockerfile`, que la sirva en el puerto `8080:5000` y que utilice la variable de entorno que hemos definido.

En caso de que no hayamos definido esa variable de entorno, se utilizará como valor por defecto '6'. Este es el código completo de `compose.yml`.

```
services:
  web:
    build: .
    ports:
      - "8080:5000"
    environment:
      - DICE_SIDES=${DICE_SIDES:-6}
```