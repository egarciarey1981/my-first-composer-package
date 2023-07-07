# my-first-composer-package

En PHP se usa Composer para utilizar bibliotecas de terceros.

Me he preguntado si sería capaz de crear una biblioteca PHP, y he sido capaz.

He utilizado este tutorial: https://dev-daglab.pantheonsite.io/composer-how-to-use-git-repositories/

## Creación

Lo primero que he hecho ha siso crear una carpeta src y dentro una clase Add (no olvidar el namespace) que suma dos números.

Para que todo el código que hagamos se considere una biblioteca, hay que crear un fichero <var>composer.json</var> y establecer como tipo <var>library</var>.

```
{
    "name": "egarciarey1981/math",
    "description": "My first Composer Package",
    "type": "library",
    "autoload": {
        "psr-4": {
            "Egarciarey1981\\Math\\": "src/"
        }
    }
}
```

NOTA

El repositorio (<var>egarciarey1981/my-first-composer-package</var>) y la bibliteca (<var>egarciarey1981/math</var>) se llaman distinto. Para utilizar la biblioteca hay que utilizar su namespace (<var>Egarciarey1981\Math</var>).



## Instalación

En el archivo <var>composer.json</var> del proyecto en el que queramos usar la biblioteca, hay que añadir el repositorio:

```
"repositories": [
    {
        "type": "git",
        "url": "https://github.com/egarciarey1981/my-first-composer-package"
    }
],
```

Ya podemos instalar la biblioteca:

```
composer require egarciarey1981/math
```

> ¡PROBLEMAS!
>
> He tenido problemas para instalar la biblioteca con Composer porque no estaba
versionada (no he puesto en qué versión está, por ejemplo la 0.1.0).
>
> La versión de una biblioteca se establece mediante tags. Puedes crear los tags a mano o utilizar una herramienta como Commitizen (por eso hay un fichero <var>.cz.json</var>).
>
> Una vez hecho esto, se instaló sin problemas.

Comprueba la carpeta que en la carpeta <var>vendor</var> se emcuentra la biblioteca.
## Uso

Ya cualquier otra biblioteca de terceros, podemos usarla importando la biblioteca.

```
use Egarciarey\Math;

$add = new Math\Add();
$result = $add(2, 3);
```
