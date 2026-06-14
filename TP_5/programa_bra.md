### GIC, BNF, EBNF, ABNF

PP presenta un LP que denomina BRA. Es un lenguaje muy simple que está diseñado, específicamente, para poseer un LP concreto sobre el que se pueda analizar la construcción de un compilador básico. Informalmente se define de esta manera:

- El único tipo de datos es entero.
- Todos los identificadores son declarados implícitamente y con una longitud máxima de 4 caracteres.
- Los identificadores deben comenzar con una letra y están compuestos de letras, dígitos y guiones bajos. No pueden terminar con guion bajo ni tener dos guiones bajos seguidos.
- Las constantes son secuencias de dígitos, es decir, números enteros.
- Hay dos tipos de sentencias:
  - Asignación: `ID ::= Expresión;`
  - Entrada/Salida: `ler(lista de IDs);` y `escrever(lista de Expresiones);`
- La expresión es infija y se construye con identificadores, constantes y los operadores `+` y `-`; los paréntesis están permitidos.
- Cada sentencia termina con punto y coma (`;`).
- El cuerpo de un programa está delimitado por `começo` y `final`.
- `começo`, `final`, `ler`, `escrever` son palabras reservadas y deben escribirse en minúsculas.

El siguiente es un programa fuente en BRA:

```bra
começo
    ler(a,b);
    cc ::= a + (b - 2);
    escrever(cc, a+4);
final
```

## GIC

```txt
Programa -> começo Sentencias final

Sentencias -> Sentencia | Sentencia Sentencias

Sentencia -> Asignacion | Entrada | Salida

Asignacion -> Identificador ::= Expresion ;

Entrada -> ler ( Identificadores ) ;

Salida -> escrever ( Expresiones ) ;

Identificadores -> Identificador | 
                Identificador , Identificadores

Expresiones -> Expresion | 
                Expresion , Expresiones

Expresion -> Identificador | Constante | ( Expresion ) | 
            Expresion OperadorSuma Identificador | 
            Expresion OperadorSuma Constante | 
            Expresion OperadorSuma ( Expresion ) | 
            Expresion OperadorResta Identificador | 
            Expresion OperadorResta Constante | 
            Expresion OperadorResta ( Expresion )

Constante -> Digito | Digito Constante

Identificador -> Letra | Letra CaracterFinal | 
                Letra CaracterFinal CaracterFinal | 
                Letra _ CaracterFinal | 
                Letra CaracterFinal CaracterFinal CaracterFinal | 
                Letra _ CaracterFinal CaracterFinal | 
                Letra CaracterFinal _ CaracterFinal

CaracterFinal -> Letra | Digito

Letra -> a | ... | z | A | ... | Z

Digito -> 0 | ... | 9

OperadorSuma -> +

OperadorResta -> -
```

## BNF

```txt
<programa> ::= começo <sentencias> final

<sentencias> ::= <sentencia> | <sentencia> <sentencias>

<sentencia> ::= <asignacion> | <entrada> | <salida>

<asignacion> ::= <identificador> ::= <expresion> ;

<entrada> ::= ler ( <identificadores> ) ;

<salida> ::= escrever ( <expresiones> ) ;

<identificadores> ::= <identificador> | <identificador> , <identificadores>

<expresiones> ::= <expresion> | <expresion> , <expresiones>

<expresion> ::= <identificador> | <constante> | ( <expresion> ) | <expresion> <operadorSuma> <identificador> | <expresion> <operadorSuma> <constante> | <expresion> <operadorSuma> ( <expresion> ) | <expresion> <operadorResta> <identificador> | <expresion> <operadorResta> <constante> | <expresion> <operadorResta> ( <expresion> )

<constante> ::= <digito> | <digito> <constante>

<identificador> ::= <letra> | <letra> <caracterFinal> | <letra> <caracterFinal> <caracterFinal> | <letra> _ <caracterFinal> | <letra> <caracterFinal> <caracterFinal> <caracterFinal> | <letra> _ <caracterFinal> <caracterFinal> | <letra> <caracterFinal> _ <caracterFinal>

<caracterFinal> ::= <letra> | <digito>

<letra> ::= a | ... | z | A | ... | Z

<digito> ::= 0 | ... | 9

<operadorSuma> ::= +

<operadorResta> ::= -
```

## EBNF

```txt
<programa> ::= começo <sentencias> final

<sentencias> ::= <sentencia> { <sentencia> }*

<sentencia> ::= <asignacion> | <entrada> | <salida>

<asignacion> ::= <identificador> ::= <expresion> ;

<entrada> ::= ler ( <identificadores> ) ;

<salida> ::= escrever ( <expresiones> ) ;

<identificadores> ::= <identificador> { , <identificador> }*

<expresiones> ::= <expresion> { , <expresion> }*

<expresion> ::= ( <identificador> | <constante> | ( <expresion> ) ) { ( <operadorSuma> | <operadorResta> ) ( <identificador> | <constante> | ( <expresion> ) ) }*

<constante> ::= <digito> { <digito> }*

<identificador> ::= <letra> [ <restoIdentificador> ]

<restoIdentificador> ::= <caracterFinal> [ <caracterFinal> [ <caracterFinal> ] ] | _ <caracterFinal> [ <caracterFinal> ] | <caracterFinal> _ <caracterFinal>

<caracterFinal> ::= <letra> | <digito>

<letra> ::= a | ... | z | A | ... | Z

<digito> ::= 0 | ... | 9

<operadorSuma> ::= +

<operadorResta> ::= -
```

## ABNF

```txt
programa: começo sentencias final

sentencias: sentencia { sentencia }

sentencia: una de asignacion entrada salida

asignacion: identificador ::= expresion ;

entrada: ler(identificadores) ;

salida: escrever(expresiones) ;

identificadores: identificador {, identificador}

expresiones: expresion {, expresion}

expresion: una de identificador constante ( expresion )
           expresion operadorSuma identificador
           expresion operadorSuma constante
           expresion operadorSuma ( expresion )
           expresion operadorResta identificador
           expresion operadorResta constante
           expresion operadorResta ( expresion )

constante: digito { digito }

identificador: letra
               letra caracterFinal
               letra caracterFinal caracterFinal
               letra _ caracterFinal
               letra caracterFinal caracterFinal caracterFinal
               letra _ caracterFinal caracterFinal
               letra caracterFinal _ caracterFinal

caracterFinal: una de letra digito

letra: una de a-z A-Z

digito: uno de 0-9

operadorSuma: +

operadorResta: -
```
