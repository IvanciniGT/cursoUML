
# Qué es eso del UML?

Unified Modeling Language. 
Nos ayuda a modelar sistemas de forma visual. Creando gráficos que representan:
- la estructura (gráficos estáticos)
- el comportamiento de un sistema (gráficos dinámicos)

Esto tiene más años que Maricastaña! (1995)
Se usa mucho? Se usa pero que muy poco desgraciadamente

## Por qué no se usa mucho?

Es malo? NO, ni mucho menos... es muy bueno.
Es complejo? No tanto, pero si que es verdad que hay que aprenderlo.
Es poco práctico? Ni mucho menos... Sirve para hacer gráfos explicando conceptos de forma visual.
                  Y al final el hecho es que muchas veces tiramos de gráficos para representar conceptos. 
                  Y un problema es que al final, cada persona monta, pinta esos gráficos a su bola!
                  Inventando su propio lenguaje visual. Y eso es un problema, porque al final,
                  esos gráficos los entiendo yo, y mi primo que entre cañas se lo he contao.
UML pone coherencia en esos gráficos. Y eso es bueno.
Nos ofrece una forma de crear gráficos de distinta naturaleza, que se complementan entre sí.
Una forma estandarizada. De hecho es una norma ISO.
Es un lenguaje... y es gratis... los lenguajes es muy complejo ponerles precio.

## Dónde está el problema ? dónde está el truco?

Los problemas son que: 
1. Es un rollo pintar todo esto a manita con los entornos gráficos que hay.
2. Hay programas que les paso un código y me generan el gráfico en automático.. Ah pues entonces?
   Pues entonces me interesa más lo contrario.. primero el diseño... y ahí es donde me vienen bien los gráficos. Si desde ellos se genera el código GUAY... Al revés... uff... Me puede venir bien para mantener el gráfico actualizado. Si ya controlo el sistema... y llevamos 2 años trabajando en él... el gráfico me lo paso por el peiro!
3. Mal uso... Al final, muchas empresas / jefes de proyecto... etc... han obligado a su uso de forma indiscriminada. ABSURDO... y la gente al final, lo aborrece!

Pensad en UML de forma distinta... Simplemente como un lenguaje para unificar criterios visuales.
Cuando quiera pintar algo, lo pintaré usando ese lenguaje.
Y si no quiero pintar nada.. porque no tengo la necesidad... pues no pinto nada.

## Qué pienso yo al respecto? (SUBJETIVO)

La gente, poco a poco va a ir recuperando UML -> CHATGPT y amigos!

ChatGPT me ayuda a montar estos gráficos en automático. Y eso es una pasada.
Con esto consigo tener gráficos estandarizados y no tardo en montarlos ni 5 minutos.

Vamos a usar chatgpt aquí en el curso: NO

En el curso queremos entender y aprender el lenguaje UML: Qué tipo de gráficos hay, cómo se montan, qué significan, etc. No queremos usar ninguna herramienta de generación de gráficos... por qué? A las pruebas me remito... no valen pa' na'!

Cómo vamos a montar entonces gráficos?? Y como chatGPT nos ayuda con ellos?
ChatGTP es bueno generando imágenes? NO ... se las inventan... no son reales. No saben ( y no se las enseña) ni a escribir textos en las imágenes.

Este tipo de herramientas son buenas generando: TEXTOS
Y si además son texto en lenguajes FORMALES mejor que mejor.

## Lenguajes formales vs Lenguajes Naturales:

- Lenguajes naturales: Español, Inglés, etc.
- Lenguajes formales: UML, SQL, JAVA, MATEMATICO (tienen reglas gramaticales MUY ESTRICTAS).

Vamos a usar una herramienta llamada MERMAID... integrado con MarkDown.

## Markdown

Es un lenguaje para documentar. Un lenguaje formal, muy sencillo de utilizar, que se ha impuesto en el mercado, especialmente en el mundo de la programación. Es el estandar hoy en día para documentar proyectos de software. Por defecto es el lenguaje soportado en **Github**, **Gitlab**, **Bitbucket**, etc.

Nos permite escribir un documento de texto plano, y luego convertirlo/visualizarlo a HTML, PDF, etc de forma automática.

Y además, tiene una ventaja GIGANTE por la que nos encanta, frente a opciones como WORD y similares: NO HACE FALTA COGER EL RATÓN PARA NADA. Odiamos el ratón... nos hace ir muy lentos al trabajar.

### En markdown podemos escribir bloques de código... con resaltado de sintaxis:

```adabas
* Sample CHECKSUM to compare contents of two data base files
*   - same file on two databases
*
* Customization:
*   1 Provide DBIDs
*   2 Provide file name in #FILE
*   3 Provide file name in VIEW
*   4 Provide a full DDM definition following VIEW
*   5 Provide LRECL in #DDM - try (A50000) - Natural will correct you
*   6 Following testing, remove the limit
*   7 Specify a unique key - records must be in the same sequence
*   8 Consistent sign nibble across platforms
*
DEFINE DATA LOCAL
1 #DB1 (N5)        INIT <001>               /* <<<<< 1
1 #DB2 (N5)        INIT <002>               /* <<<<< 1
1 #FILE (A32)      INIT <"EMPLOYEES">       /* <<<<< 2
1 DDM   VIEW EMPLOYEES                      /* <<<<< 3
  2 PERSONNEL-ID                            /* <<<<< 4
  2 FIRST-NAME
  2 MIDDLE-I
  2 NAME
  2 MIDDLE-NAME
  2 MAR-STAT
  2 SEX
  2 BIRTH
  2 ADDRESS-LINE (5)
  2 CITY
  2 ZIP
  2 POST-CODE
  2 COUNTRY
  2 AREA-CODE
  2 PHONE
  2 DEPT
  2 JOB-TITLE
  2 CURR-CODE (10)
  2 SALARY (10)
  2 BONUS (10, 10)
  2 LEAVE-DUE
  2 LEAVE-TAKEN
  2 LEAVE-START (20)
  2 LEAVE-END (20)
  2 LANG (5)
                   1 REDEFINE DDM
  2 #DDM (A1189)                            /* <<<<< 5
1 #1023
  2 FUNC (A1)      INIT <"M">
  2 RC (N4)
  2 TIME (T)
  2 DATE (D)
  2 TS (B8)
  2 MS (P19)
1 #1040
  2 OP (A1)        INIT <'S'>
  2 DB (N5)
  2 RC (I4)
1 #4011
  2 FUNC (I4)
  2 CTX (B156)
  2 TEXT (A) DYNAMIC
  2 HASH (B20)
1 #HASH (B20)
1 #COUNT (P10)
1 #ELAPSED (N7)
END-DEFINE
*
FORMAT SG=F
*
DEFINE SUBROUTINE HASH-RTN
CALLNAT "USR1040N" #1040
ASSIGN #4011.FUNC = 1
CALLNAT "USR4011N" #4011
ASSIGN #4011.FUNC = 2
ASSIGN #1023.MS   = *CPU-TIME
E.
SET TIME
R.
LIMIT (100)                                 /* <<<<< 6
READ MULTI-FETCH ON
                          DDM BY ISN        /* <<<<< 7
  ADD 0 TO DDM.BIRTH                        /* <<<<< 8
  ADD 0 TO DDM.SALARY (*)                   /* <<<<< 8
  ADD 0 TO DDM.BONUS  (*, *)                /* <<<<< 8
  ASSIGN #4011.TEXT = #DDM
  CALLNAT "USR4011N" #4011
END-READ
ASSIGN #4011.FUNC = 3
CALLNAT "USR4011N" #4011
ASSIGN #1023.MS = *CPU-TIME - #1023.MS
CALLNAT "USR1023N" #1023
ASSIGN #ELAPSED = *TIMD (E.)
DISPLAY 'DBID'     #1040.DB
        'Records'  *COUNTER (R.)
        'Checksum' #4011.HASH
        'CPU Time' #1023.TIME (EM=HH:II:SS.T)
        'Elapsed'  #ELAPSED (EM=99':'99':'99'.'9)
END-SUBROUTINE
*
*
ASSIGN #1040.DB = #DB1
PERFORM HASH-RTN
ASSIGN #HASH  = #4011.HASH
ASSIGN #COUNT = *COUNTER (R.)
*
ASSIGN #1040.DB = #DB2
PERFORM HASH-RTN
*
IF  *COUNTER (R.) = #COUNT
  THEN
    WRITE / T**COUNTER (R.) 'Counters match' (GRI)
  ELSE
    WRITE / T**COUNTER (R.) '>>>>>  Counters do not match  <<<<<' (REI)
END-IF
IF  #4011.HASH = #HASH
  THEN
    WRITE / T*#4011.HASH 'Checksums match' (GRI)
  ELSE
    WRITE / T*#4011.HASH '>>>>>  Checksums do not match  <<<<<' (REI)
END-IF
*
WRITE TITLE LEFT
          *PROGRAM
      10T 'Checksum Comparison'
      62T *DAT4U
          *TIME (AL=5)
    / 10T 'File' #FILE
    /
END            
```

```sql
SELECT * FROM EMPLOYEES;
```
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!"); 
    }
}
```

### Hay una extensión de markdown, que esta soportada por Github, Gitlab, visual studio code, etc, que se llama Mermaid:

De hecho mermaid es una librería JS para la renderización de gráficos (entre otros muchos: UML)

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

# Gráficos dinámicos: DE COMPORTAMIENTO

## Diagrama de secuencia

Nos viene bien cuando queremos entender, contar las distintas interacciones entre los distintos componentes/actores de un sistema.

## Diagramas de actividad

Habéis visto por ahí los típicos diagramas de flujo (algoritmos)

Aquí no me centro en los componentes, ni en sus interacciones, sino en el flujo de control / en el proceso.