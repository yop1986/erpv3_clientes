# ERPv3 - Clientes

## Desarrollo

### Configuración del Ambiente

Esta aplicacion depende del [Modulo de usuarios](https://github.com/yop1986/erpv3_usuarios) 
por lo que es necesario instalar este y sus dependencias previamente.

Desde la consola de Git se procede a clonar este repositorio, en la raiz del 
proyecto.

    $ git clone https://github.com/yop1986/erpv3_clientes.git clientes

#### Settings

Es necesario modificar el archivo **settings.py** del proyecto general con la
siguiente informacion:

    INSTALLED_APPS = [
        ...
        'clientes',
    ]

    INFORMACION_APLICACIONES = {
        'clientes': {
            'nombre':       'Clientes',
            'descripcion':  _('Aplicación para el control base de clientes.'),
            'url':          reverse_lazy('cliente:index'),
            'imagen':       'clientes_cliente.png',
        },
    }

#### Urls

Posterior a esta configuracion es necesario agregar las urls al proyecto base __< Base >/urls.py__

    path('clientes/', include('clientes.urls')),

#### Configuracion

Se incluira la siguiente sección en __static/configuraciones.cfg__ si fuera necesaria alguna parametrización
general para el proyecto.

    [clientes]
    # configuraciones generales para la aplicación     

#### Comandos adicionales de Django

    (venv) ERPv3> python manage.py check
    (venv) ERPv3> python manage.py migrate clientes


## Funcionalidades

### Clientes

La busqueda de clientes se puede realizar de cuatro formas diferentes, utilizando palabras reservadas que serviran para filtrar resultados o sin palabras reservadas:

- nit: validará el nit ingresado entre los clientes registrados
- dpi: validará el dpi ingresado entre los clientes registrados
- nombre: validará las palabras ingresadas y devolvera todas las posibles combinaciones que surjan
- Sin palabra reservada, será una busqueda exacta la que se intentará devolver.
