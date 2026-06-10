Axioma = File

No terminales = {
    File,
    Statements,
    Statement,
    Compound_stmt,
    Simple_stmts,
    Simple_stmt,
    If_stmt,
    Elif_stmt,
    Try_stmt
    Else_block,
    Block,
    Named_expression
}

Terminales = {  
    'if',
    'elif',
    'else',
    ':',
    NEWLINE,
    INDENT,
    DEDENT
}
  
Producciones de GIC = 
File -> Statements -> Statement -> Compound_stmt ->
Statement -> Simple_stmts -> Simple_stmt 
Compound_stmt -> If_stmt
If_stmt -> 'if' Named_expression ':' Block Elif_stmt
If_stmt -> 'if' Named_expression ':' Block Else_block
If_stmt -> 'if' Named_expression ':' Block

Elif_stmt -> 'elif' Named_expression ':' Block Elif_stmt
Elif_stmt -> 'elif' Named_expression ':' Block Else_block
Elif_stmt -> 'elif' Named_expression ':' Block

Else_block -> 'else' ':' Block

Block -> NEWLINE INDENT Statements DEDENT
Block -> Simple_stmts



