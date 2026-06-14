Axioma = file

file = [ statements ] ENDMARKER .

statements = statement { statement } .

statement = compound_stmt | simple_stmts .

compound_stmt = function_def | if_stmt | class_def |
                with_stmt | for_stmt | try_stmt |
                while_stmt | match_stmt .

block = NEWLINE INDENT statements DEDENT | simple_stmts .

if_stmt = "if" named_expression ":" block elif_stmt |
          "if" named_expression ":" block [ else_block ] .

elif_stmt = "elif" named_expression ":" block elif_stmt |
            "elif" named_expression ":" block [ else_block ] .

else_block = "else" ":" block .
