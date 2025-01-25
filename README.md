# Angular - Conceptos Basicos

## Componentes

Un componente en Angular representa una parte de una página web más grande. Los componentes están compuestos por los siguientes elementos:

1. Un `@Component` que contiene configuraciones utilizadas por Angular.
2. Una plantilla HTML que controla lo que se presenta en el DOM.
3. Un selector CSS que define cómo se utiliza el componente en el HTML.
4. Una clase en TypeScript con comportamientos, para manejar la entrada del usuario o realizar peticiones a un servidor.
Ejemplo:

![Image](https://github.com/user-attachments/assets/deb6482b-4934-443b-932b-d2b13122d868)

> Separar los archivos HTML y CSS
Ejemplo: 

![Image](https://github.com/user-attachments/assets/4cfd8a29-98d4-475a-8be0-26e13a018ba6)

## Uso de Componentes

Ejemplo de página de perfil de usuario:

![Image](https://github.com/user-attachments/assets/92369b03-dad9-4199-afbd-c37009f16753)

Es decir, que UserProfile componente, utiliza otros componentes para producir la pagina final.

> Para importar:

1. En el archivo TS del componente, agregar un `import` para el componente que desea utilizar.
2. En el `@Component` decorador, agregar una entrada a la `imports` matriz para el componente que desea utilizar.
3. En la plantilla del componentem agrega un elemento que coincida con el selector del componente que desea utilizar.

![Image](https://github.com/user-attachments/assets/cd790e6f-9100-4acb-b43e-ef4abfaefdaf)

##  Señales (Crear y gestionar datos dinamicos)

Estas se usan para crear y gestionar estados, es un contenedor que envuelve un valor.
Use `signal` function para crear un aseñal para mantener el estado local.
Ejemplo:

![image](https://github.com/user-attachments/assets/f27456c1-6194-4129-a2c3-756fd3ae3fbc)

> Expresiones calculadas

Una `computed` es una señal que produce su valor en funcion de otras señales. (Solo lectura)
Ejemplo:

![image](https://github.com/user-attachments/assets/05a637e4-24a9-487f-8686-fb553e05dc7c)

> Signals en componentes

Utilize `signal` y `computed` dentro de sus ocmponentes para crear y administrar el estado:
Ejemplo:

![image](https://github.com/user-attachments/assets/7e8cc585-5414-42e3-b24f-e002a9d83d96)

## Texto dinamico

Un enlace crea una conexion dinamica entre la plantilla de un componente y sus datos, esto asegura que los cambios en los datos del componente, 
tambien actualize automaticamente la plantilla representada.
Ejemplo de enlace para mostrar u texto dinamico en una plantilla, usando llaves dobles:

![image](https://github.com/user-attachments/assets/b077bdf3-6e49-45c3-9b0f-100cabf8e8fc)

Cuando se renderiza el componente:

![image](https://github.com/user-attachments/assets/1df36eac-cc22-4d50-8584-c2815329e6a3)

> Configuracion de propiedades y atributos dinamicos

Angular, admite la vinculacion de valores dinamicos a propiedades del DOM con **corchetes.**

![image](https://github.com/user-attachments/assets/369d73d0-8fa0-447a-8ab5-07bab2ac7645)

Tambien se pueden vincular atributos HTML, anteponiendo el nombre del atributo con `attr.`

![image](https://github.com/user-attachments/assets/359e4966-37e4-4cfb-900b-d2658a63041a)

> Manejo de la interacción del usuario

El framework permite agregar escuchas de eventos a un elemento en la plantilla con `paréntesis`:

![image](https://github.com/user-attachments/assets/0a61d4aa-1768-4e77-ae8b-105e0193ef2d)

Si necesita pasar el objeto de su evento a su oyente, puede usar la variable incorporada `$event` dentro de la llamada de la funcion.

![image](https://github.com/user-attachments/assets/57fc6574-7c3f-4c11-aa1d-db3271bd5791)

> Control de flujo con **if** y **for**

Puede ocultar y mostrar condicionalmente partes de una plantilla con `@ifel` bloque de Angular:

![image](https://github.com/user-attachments/assets/32362777-ce72-43b0-997f-2629da9199c7)

Puedes repetir parte de una plantilla varias veces con `@forel` bloque de Angular:

![image](https://github.com/user-attachments/assets/1e74b3c7-2440-4fc7-8285-8af37af0ed40)

Angular utiliza la trackpalabra clave, que se muestra en el ejemplo anterior, para asociar datos con los elementos DOM creados por `@for`

## Inyección de dependencia

Cuando necesita compartir lógica entre componentes, Angular aprovecha el patrón de diseño de inyección de dependencia que le permite crear un “servicio”.

> Servicios

Son piezas de codigo reutilizables que se pueden inyectar.
Los servicios estan compuestos por:

- Un decorador de TypeScript que declara la clase como un servicio Angular a través de `@Injectable`, le permite definir qué parte de la aplicación puede acceder al servicio a través de la `providedInpropiedad` (que normalmente es 'root') para permitir que se acceda a un servicio en cualquier lugar dentro de la aplicación.
- Una clase TypeScript que define el código deseado que será accesible cuando se inyecte el servicio

![image](https://github.com/user-attachments/assets/9583fc59-296a-4dc7-b558-5f758f37a9eb)

> Para utilizar un servicio

Cuando desee utilizar un servicio en un componente, deberá:

1. Importar el servicio
2. Declarar un campo de clase donde se inyecta el servicio. Asignar el campo de clase al resultado de la llamada de la función incorporada `inject` que crea el servicio.

![image](https://github.com/user-attachments/assets/7dae294b-f0c1-4600-9c7f-bde61b61d827)

# Guia Detallada

### Señales

`Signals` es un contenedor que rodea un valor, y notifica a los consumidores interesados cuando dicho valor cambia.

> Señales escribibles - Tipo: `WritableSignal`

Las señales escribibles proporcionan una API para actualizar sus valores directamente.`git status`

![image](https://github.com/user-attachments/assets/8f736e7f-837a-4427-b1ef-8d2c08936c15)

Para cambiar el valor puede usar `.set()`

![image](https://github.com/user-attachments/assets/9aeefa88-ba10-4713-8c05-e9db7cbca309)

Para calcular un nuevo valor a partir del anterior utilice `.update`

![image](https://github.com/user-attachments/assets/548fb94e-be28-4247-a8db-1ed396dd18e1)

> Señales calculadas 

Signals de solo lectura que derivan su valor de otras señales. 
Se definen con la function `computed`

![image](https://github.com/user-attachments/assets/d913fc72-1e2c-4661-ae87-f7ebfe5636fa)

`doubleCount` depende de `count`, cada vez que `count` se actualiza, `doubleCount` tambien lo hara.

> Las señales calculadas no son señales escribibles

Error de compilacion:

![image](https://github.com/user-attachments/assets/24b936ec-dff5-4f69-95b7-2ed0b9f3ab80)

`dobleCount` no es un `WritableSignal`

> [!NOTE]
> Documentacion de la pagina oficial de Angular.
