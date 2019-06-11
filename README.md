# Tutorial-ensamblador-8086

**TUTORIAL DE ENSAMBLADOR**

**1.	DEFINICIONES BÁSICAS**

**1.2	 ENSAMBLADOR**

Assembler o ensamblador es un lenguaje de programación de bajo nivel el cual consiste en un conjunto de mnemónicos que representan instrucciones básicas para los computadores, microprocesadores, microcontroladores y otros circuitos integrados programables.

```
El lenguaje ensamblador es el sistema alfanumérico para escribir código máquina mediante
expresiones abreviadas (mnemotécnicos).
La compilación es más complicada porque incluye la conversión de operaciones matemáticas
complejas, comandos de lenguaje natural o tipos de comandos complejos.
Cada ordenador tiene su propio lenguaje ensamblador, exclusivo de su CPU; un lenguaje de alto
nivel (LAN) puede ser compilado en distintas máquinas.
Es usado principalmente porque hay aplicaciones o programas que deben tratar directamente con los
registros de la máquina, la memoria, dispositivos de E/S, etc.

```

**1.3	EMU8086**

EMU8086 es un emulador del microprocesador 8086 (Intel o AMD compatible) con assembler integrado, este entorno corre sobre Windows y cuenta con una interfaz gráfica muy amigable e intuitiva que facilita el aprendizaje el lenguaje de programación en assembler.

**LA ESTRUCTURA DEL ENSAMBLADOR:**
En el lenguaje ensamblador las líneas de código constan de dos partes, la primera es el nombre de la
instrucción que se va a ejecutar y la segunda son los parámetros del comando u operando. Por
ejemplo:
ADD ah bh
Aquí "ADD" es el comando a ejecutar (en este caso una adición o suma) y tanto "ah" como "bh" son
los parámetros.
El nombre de las instrucciones en este lenguaje puede estar formado de 2 a 6 letras, a estas
instrucciones también se les llama nombres mnemónicos o códigos de operación, ya que representan
alguna función que habrá de realizar el procesador. Existen algunos comandos que no requieren
parámetros para su operación, así como otros que requieren solo un parámetro.
Algunas veces se utilizarán las instrucciones como sigue:
ADD al,[170]
Los corchetes en el segundo parámetro nos indican que vamos a trabajar con el contenido de la casilla
de memoria número 170 y no con el valor 170, a esto se le conoce como direccionamiento directo (en
la instrucción viene la dirección del objeto).

**2.	DESCARGA E INSTALACION DE EMU8086**

Para descargar el instalador del entorno Emu8086 nos dirigimos al siguiente enlace:
https://download.cnet.com/Emu8086-Microprocessor-Emulator/3000-2069_4-10392690.html
 

Luego seleccionamos el botón “donwload now”. A continuación se iniciará automáticamente la descarga.


 

Obtendremos un archivo comprimido ZIP el cual contiene el instalador (setup.exe) del programa.

Ejecutamos el instalador (setup.exe). En este caso no es necesario modificar ningún parámetro de la instalación por lo que en todas las ventanas seleccionamos el botón “Next”, luego “Install” y finalmente “Finish”.


 

**3.	UTILIZACIÓN DEL ENTORNO EMU8086**

Para iniciar el entorno se deje ejecutar el archivo emu8086.exe que se encuentra en el directorio de instalación (ej. c:\emu8086).

Luego de iniciar el entorno el emu8086 ofrece diferentes opciones:  
```

•	New: permite escribir un nuevo código en lenguaje ensamblador (“Código Fuente” con extensión .ASM) 
•	Code examples: permite acceder a una serie de programas ejemplos muy útiles al momento de aprender a utilizar el entorno y la programación en assembler. 
•	Quick start tutor: llama al browser y permite explorar gran variedad de documentos de ayuda. 
•	Recent file: muestra los últimos archivos con los cuales se estuvo trabajando. 
```



**4.	PROGRAMA “HOLA MUNDO”**

En este ejemplo realizaremos un programa que imprima en pantalla el texto “Hola mundo”.

 

Para ello nos dirigimos a la parte superior izquierda y escogemos el botón new, luego en la ventana que se despliega marcamos la opción “empty workspace”. Finalmente seleccionamos “OK” para aceptar.


A continuación escribimos el siguiente código: 
```
.MODEL SMALL                
.STACK 100h                 
CR EQU 13                   
LF EQU 10
.DATA                       
 TEXTO DB 'Hola Mundo$',CR,LF     
                                                      
.CODE                       
 MOV AX, SEG TEXTO          
                            
 MOV DS,AX                 
 LEA DX,TEXTO               
                            
 MOV AH,9                  
 INT 21h                    
                            
 MOV AH,4ch                 
 INT 21h                    
END                         
```



**Cada una de las líneas de código es explicada a continuación:**
```
.MODEL SMALL                ;modelo pequeño de compilacion (64k como maximo)
.STACK 100h                 ;Segmento de pila: Pila 256 posiciones
CR EQU 13                   ;Declaracion de constantes
LF EQU 10
.DATA                       ;Comienzo del segmento de datos
 TEXTO DB 'Hola Mundo!$',CR,LF     ;Reserva de memoria con retorno de carro e
                            ;Inicio de liena, la variable TEXTO es de tipo
                            ;byte,el simbolo $ es el simbolo de fin de cadena
.CODE                       ;Comienzo del segmento de codigo*/
 MOV AX, SEG TEXTO          ;Mueve a AX la direccion del primer byte del
                            ;segmento de datos
 MOV DS,AX                  ;Mueve dicha direccion al segmento de datos
 LEA DX,TEXTO               ;Cargamos en DX la direccion efectiva del texto
                            ;que vamos a imprimir por pantalla
 MOV AH,9                   ;funcion "Escribir texto por pantalla"
 INT 21h                    ;Llamada a DOS por medio de la interrupcion
                            ;para ejecutar la funcion
 MOV AH,4ch                 ;funcion "Retornar a DOS"
 INT 21h                    ;Interrupcion que llama a DOS para terminar elprograma
END                         ;fin

```



Para ejecutar el programa seleccionamos el botón compile del menú superior.

luego en la ventana que se despliega escogemos la ruta donde deseamos guardar el programa compilado, colocamos un nombre al archivo y escogemos la opción “guardar”. 



En la ventana “assembler status” seleccionamos el botón “run” para ejecutar el programa.


**Finalmente, se nos presenta en pantalla el programa ejecutándose.**
