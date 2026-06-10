Axioma = CompilationUnit

No Terminales = { CompilationUnit,
    TypeDeclaration,
    ClassOrInterfaceDeclaration,
    ClassDeclaration,
    NormalClassDeclaration,
    ClassBody,
    ClassBodyDeclarations,
    ClassBodyDeclaration,
    Block,
    BlockStatements,
    BlockStatement,
    Statement,
    ParExpression,
    Expression}

Terminales = {class,
    if,
    else,
    {,
    },
    (,
    ),
    ;,
    true,
    false}

Producciones de GIC = 
CompilationUnit -> TypeDeclaration -> ClassOrInterfaceDeclaration -> ClassDeclaration -> NormalClassDeclaration-> class Identifier ClassBody -> { ClassBodyDeclarations }
ClassBodyDeclarations -> ClassBodyDeclaration  -> Block -> { BlockStatements }
BlockStatements -> BlockStatement -> Statement -> if ParExpression Statement -> if ParExpression Statement else Statement -> Block
Statement -> ;
ParExpression -> ( Expression )
Expression -> true
Expression -> false



