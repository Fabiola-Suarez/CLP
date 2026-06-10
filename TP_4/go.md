Axioma = SourceFile

No Terminales = {
    SourceFile,
    PackageClause,
    TopLevelDecl,
    FunctionDecl,
    FunctionBody,
    Block,
    StatementList,
    Statement,
    IfStmt,
    Condition,
    Expression
}

Terminales = {
    package,
    main,
    func,
    if,
    else,
    {,
    },
    (,
    ),
    ;
}

Producciones de GIC =
SourceFile -> PackageClause TopLevelDecl
PackageClause -> package main

TopLevelDecl -> FunctionDecl
FunctionDecl -> func main ( ) FunctionBody
FunctionBody -> Block

Block -> { StatementList }
Block -> { }

StatementList -> Statement
StatementList -> Statement StatementList

Statement -> IfStmt
Statement -> Block
Statement -> ;

IfStmt -> if Condition Block
IfStmt -> if Condition Block else Block
IfStmt -> if Condition Block else IfStmt

Condition -> Expression


