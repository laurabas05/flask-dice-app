# Practica: Flask Dice Roller

## Comandos utilizados

1. **Para crear la imagen**
docker build -t flask-dice-app

2. **Para ejecutarla**
- `docker run --rm -p 8888:5000 flask-dice-app` sin la variable
- `docker run --rm -p 8888:5000 -e DICE_SIDES=20 flask-dice-app` con la variable

## Página funcionando en http://localhost:8888

<img width="1012" height="612" alt="image" src="https://github.com/user-attachments/assets/e86fffe7-12be-4845-90c9-72ca41967df0" />

## ¿Qué cambia al usar `-e DICE_SIDES=...`
Al ejecutar la imagen proporcionándole un valor a la variable, se cambia tanto el número de caras que tiene el dado como la cantidad de números random que nos pueden aparecer al rerollear el dado. Esto es así porque en nuestra app hemos implementado una función que, según el valor que le damos al número de la variable, le asignamos un determinado número de caras. En caso de que no introduzcamos la variable, el valor por defecto sería 6.
