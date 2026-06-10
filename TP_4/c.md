Axioma = translation-unit

No Terminales = {
    translation-unit,
    declaration-seq,
    declaration,
    function-definition,
    compound-statement,
    statement-seq,
    statement,
    selection-statement,
    condition,
    expression
}

Terminales = {
    if,
    else,
    int,
    main,
    {,
    },
    (,
    ),
    ;
}

Producciones de GIC =
translation-unit -> declaration-seq
declaration-seq -> declaration
declaration-seq -> declaration declaration-seq

declaration -> function-definition
function-definition -> int main ( ) compound-statement

compound-statement -> { statement-seq }
compound-statement -> { }

statement-seq -> statement
statement-seq -> statement statement-seq

statement -> selection-statement
statement -> compound-statement
statement -> ;

selection-statement -> if ( condition ) statement
selection-statement -> if ( condition ) statement else statement

condition -> expression

