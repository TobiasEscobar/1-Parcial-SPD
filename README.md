# 1° Parcial Sistema de Procesamiento de datos

## Alumno:
- Tobías Fabricio Escobar

### División:
1-D

## Proyecto: Montacargas
![1°Parcial - SPD - Escobar Tobías Fabricio](https://github.com/TobiasEscobar/1-Parcial-SPD/assets/98720272/f8601d56-680c-4ed3-9772-7074802cf30e)


## Descripción
Se nos pide armar un modelo de montacarga funcional como maqueta para un hospital. El
objetivo es que implementes un sistema que pueda recibir ordenes de subir, bajar o pausar
desde diferentes pisos y muestre el estado actual del montacargas en el display 7
segmentos.

# Documentación del Código de Control de Montacargas

## Variables y DEFINE
- BOTON_SUBIR: define el pin del botón de subir.
- BOTON_PAUSAR: define el pin del botón de pausar.
- BOTON_BAJAR: define el pin del botón de bajar.
- LED_ROJO: define el pin del LED rojo.
- LED_VERDE: define el pin del LED verde.
- LED_A a LED_G: definen los pines de los LEDs A a G y del display 7 segmentos.
- estadoBoton: Variable que almacena el estado actual del botón.
- ultimoEstadoBoton: Variable que almacena el último estado del botón.
- contador: Variable que lleva la cuenta del piso actual.
- contadorAuxiliar: Variable auxiliar utilizada para almacenar el valor del contador.

## Funciones
### void setup()
Esta función se ejecuta una vez al iniciar el programa y se encarga de configurar los pines como entradas o salidas, estableciendo los modos necesarios para los botones y los LEDs.

### void loop()
Esta función se ejecuta de forma repetitiva y controla el flujo principal del programa. En cada ciclo, se enciende el LED rojo y se llama a la función subirBajar() para verificar si se debe iniciar la secuencia de subida o bajada del montacargas.

### void prenderLed(int led, int duracion)
Esta función recibe como parámetros el número de pin de un LED y la duración en milisegundos durante la cual se debe mantener encendido. Enciende el LED durante el tiempo especificado y luego lo apaga.

### void prenderDisplay(int a, int b, int c, int d, int e, int f, int g, int led, int duracion)
Esta función se encarga de encender o apagar cada segmento del display de acuerdo a los valores de las variables "A" a "G". También enciende un LED adicional durante la duración especificada utilizando la función prenderLed(). Se utiliza para mostrar un número en el display y resaltar el piso actual del montacargas.

### void apagarDisplay()
Esta función apaga todos los segmentos del display, asegurándose de que no quede ningún segmento encendido.

### void display(int led, int duracion)
Esta función muestra en el display el número correspondiente al piso actual del montacargas utilizando la función prenderDisplay(). Dependiendo del valor de la variable contador, se encienden los segmentos del display correspondientes al número del piso.

### void empezarSecuenciaSubida(int led, int duracion, bool flagSubir)
Esta función inicia la secuencia de subida del montacargas. Recibe como parámetros el número de pin del LED y la duración del encendido. Si flagSubir es verdadero, se ejectará un bucle for que incrementa el contador desde el valor almacenado en contadorAuxiliar hasta 9. En cada iteración, se llama a la función display() para mostrar en el display el número del piso actual. También se verifica si se mantiene presionado el botón de pausar utilizando la función pausarSecuencia() para detener la secuencia si es necesario.

### void empezarSecuenciaBajada(int led, int duracion, bool flagBajar)
Esta función inicia la secuencia de bajada del montacargas. Recibe como parámetros el número de pin del LED y la duración del encendido. Si flagBajar es verdadero, se ejecutará un bucle for que decrementa el contador desde el valor almacenado en contadorAuxiliar hasta 0. En cada iteración, se llama a la función display() para mostrar en el display el número del piso actual. También se verifica si se mantiene presionado el botón de pausar utilizando la función pausarSecuencia() para detener la secuencia si es necesario.

### void pausarSecuencia(int valorDeCorte)
Esta función se encarga de pausar o reanudar la secuencia del montacargas en función del estado del botón de pausar. Recibe como parámetro valorDeCorte, que indica el valor al que se debe asignar el contador en caso de pausar la secuencia. Si se detecta un cambio en el estado del botón, se verifica si se ha presionado el botón de pausar. Si es así, se muestra un mensaje en el monitor serial, se enciende el LED rojo durante 3 segundos y se asigna a contador el valor de valorDeCorte. Si se suelta el botón de pausar, se muestra un mensaje de reanudación y se vuelve a llamar a la función subirBajar() para continuar la secuencia.

### void subirBajar()
Esta función verifica si se ha presionado el botón de subir o el botón de bajar. Si se detecta que el botón de subir está presionado, se llama a la función empezarSecuenciaSubida() con los parámetros adecuados para iniciar la secuencia de subida. Si se detecta que el botón de bajar está presionado, se llama a la función empezarSecuenciaBajada() con los parámetros adecuados para iniciar la secuencia de bajada.

## Uso del Código
1. Conecte los componentes necesarios (botones y LEDs) a los pines especificados en el código.
2. Compile y cargue el código en su placa Arduino utilizando el entorno de desarrollo de Arduino.
3. Una vez cargado el código, el montacargas estará listo para funcionar.
4. Al presionar el botón de subir, el montacargas iniciará la secuencia de subida, mostrando en el display cada piso a medida que asciende.
5. Al presionar el botón de bajar, el montacargas iniciará la secuencia de bajada, mostrando en el display cada piso a medida que desciende.
6. Si se mantiene presionado el botón de pausar, se detendrá la secuencia y se mostrará un mensaje en el monitor serial. Al soltar el botón de pausar, la secuencia se reanudará.

## Diagrama esquemático: 
![diagrama-esquematico](https://github.com/TobiasEscobar/1-Parcial-SPD/assets/98720272/bc67099c-8643-472a-90ae-42cb964ded89)

## :robot: Link al proyecto 
[Proyecto-Parcial](https://www.tinkercad.com/things/0VUXdhJp14X-1parcial-spd-escobar-tobias-fabricio/editel?sharecode=VjpCkzpbkIJkHSVWQhmTBHnWZeh9Q9fcdaGzutt19uQ)
