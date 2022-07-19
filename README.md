# Acceso a módulos privados

1) Los módulos son privados, por lo tanto necesitarás de un token para poder instalarlos, pide al equipo de producto dicho accesso.

2) Ya teniendo el acceso, crea un archivo con nombre **.npmrc** al mismo nivel que el archivo **package.json**

3) Pega el acceso y guarda el archivo

``` json
//registry.npmjs.org/:_authToken=npm_XXXXXXXXXXXXXXXXXX
``` 

4) Procede a installar los módulos a ocupar.