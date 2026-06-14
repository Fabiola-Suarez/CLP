Axioma: translation-unit 

translation-unit = [ declaration-seq ] .

declaration-seq = declaration { declaration } .

declaration = block-declaration | nodeclspec-function-declaration |
              function-definition | template-declaration |
              deduction-guide | linkage-specification |
              namespace-definition | empty-declaration |
              attribute-declaration | module-import-declaration .

function-definition = [ attribute-specifier-seq ] [ decl-specifier-seq ]
                      declarator [ virt-specifier-seq ] function-body .

function-body = compound-statement .

compound-statement = "{" [ statement-seq ] "}" .

statement-seq = statement { statement } .

statement = labeled-statement | expression-statement | compound-statement |
            selection-statement | iteration-statement | jump-statement |
            declaration-statement | try-block .

selection-statement = "if" [ "constexpr" ] "(" condition ")" statement |
                      "if" [ "constexpr" ] "(" condition ")" statement "else" statement |
                      "switch" "(" condition ")" statement .
