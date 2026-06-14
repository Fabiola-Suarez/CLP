Axioma:kotlinFile 

kotlinFile = [ shebangLine ] { fileAnnotation } [ packageHeader ]
             { importList } { topLevelObject } .

topLevelObject = declaration | statement .

declaration = classDeclaration | objectDeclaration | functionDeclaration |
              propertyDeclaration | typeAlias .

functionDeclaration = [ functionModifier ] "fun" [ typeParameters ]
                      [ receiverType "." ] simpleIdentifier
                      functionValueParameters [ ":" type ]
                      [ typeConstraints ] [ functionBody ] .

functionBody = block | "=" expression .

block = "{" statements "}" .

statements = { statement ";" } .

statement = declaration | assignment | loopStatement | expression .

controlStructureBody = block | statement .

expression = disjunction .

disjunction = conjunction { "||" conjunction } .

conjunction = equality { "&&" equality } .

equality = comparison { equalityOperator comparison } .

comparison = genericCallLikeComparison { comparisonOperator genericCallLikeComparison } .

genericCallLikeComparison = infixOperation .

infixOperation = elvisExpression { infixFunctionCall } .

elvisExpression = infixFunctionCall { "?:" infixFunctionCall } .

infixFunctionCall = rangeExpression { simpleIdentifier rangeExpression } .

rangeExpression = additiveExpression { rangeOperator additiveExpression } .

additiveExpression = multiplicativeExpression { additiveOperator multiplicativeExpression } .

multiplicativeExpression = asExpression { multiplicativeOperator asExpression } .

asExpression = prefixUnaryExpression { asOperator type } .

prefixUnaryExpression = [ prefixUnaryOperator ] postfixUnaryExpression .

postfixUnaryExpression = primaryExpression { postfixUnarySuffix } .

primaryExpression = parenthesizedExpression | simpleIdentifier |
                    literalConstant | stringLiteral |
                    callableReference | functionLiteral |
                    objectLiteral | collectionLiteral |
                    thisExpression | superExpression |
                    ifExpression | whenExpression |
                    tryExpression | jumpExpression .

ifExpression = "if" "(" expression ")" controlStructureBody
               [ "else" controlStructureBody ] .
