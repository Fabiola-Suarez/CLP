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
    Condition,
    Expression
}

Terminales = {
    if,
    else,
    int,
    main,
    true,
    false,
    {,
    },
    (,
    ),
    ;
}

Producciones de GIC =
TranslationUnit -> DeclarationSeq -> Declaration -> FunctionDefinition -> int main ( ) CompoundStatement
CompoundStatement -> { StatementSeq }
CompoundStatement -> { }

StatementSeq -> Statement
StatementSeq -> Statement StatementSeq

Statement -> SelectionStatement
Statement -> CompoundStatement
Statement -> ;

SelectionStatement -> if ( Condition ) Statement
SelectionStatement -> if ( Condition ) Statement else Statement

Condition -> Expression


