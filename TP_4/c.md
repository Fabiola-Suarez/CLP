Axioma: translation-unit

translation-unit = external-declaration { external-declaration } .

external-declaration = function-definition | declaration .

function-definition = declaration-specifiers declarator compound-statement .

compound-statement = "{" [ block-item-list ] "}" .

block-item-list = block-item { block-item } .

block-item = declaration | statement .

statement = labeled-statement | compound-statement | expression-statement |
            selection-statement | iteration-statement | jump-statement .

selection-statement = "if" "(" expression ")" statement |
                      "if" "(" expression ")" statement "else" statement |
                      "switch" "(" expression ")" statement .
