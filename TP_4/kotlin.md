Axioma =  KotlinFile

No Terminales = {
    KotlinFile,
    Script,
    Statement,
    ControlStructureBody,
    Expression,
    PrimaryExpression,
    IfExpression,
}

Terminales = {
     if,
    else,
    (, 
    ),
    {,
    },
}

Producciones de GIC =
KotlinFile -> Script -> { Statement } -> Statement  -> ControlStructureBody -> PrimaryExpression -> IfExpression
IfExpression -> if ( Expression ) ControlStructureBody -> else ->
ControlStructureBody 




