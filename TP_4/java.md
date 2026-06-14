Axioma: CompilationUnit

CompilationUnit = OrdinaryCompilationUnit | ModularCompilationUnit .

OrdinaryCompilationUnit = [ PackageDeclaration ] { ImportDeclaration } { TypeDeclaration } .

TypeDeclaration = ClassDeclaration | InterfaceDeclaration | ";" .

ClassDeclaration = NormalClassDeclaration | EnumDeclaration |
                   RecordDeclaration .

NormalClassDeclaration = { ClassModifier } "class" TypeIdentifier
                         [ TypeParameters ] [ ClassExtends ]
                         [ ClassImplements ] [ ClassPermits ] ClassBody .

ClassBody = "{" { ClassBodyDeclaration } "}" .

ClassBodyDeclaration = ClassMemberDeclaration |
                       InstanceInitializer |
                       StaticInitializer |
                       ConstructorDeclaration .

InstanceInitializer = Block .

Block = "{" [ BlockStatements ] "}" .

BlockStatements = BlockStatement { BlockStatement } .

BlockStatement = LocalClassOrInterfaceDeclaration |
                 LocalVariableDeclarationStatement |
                 Statement .

Statement = StatementWithoutTrailingSubstatement |
            LabeledStatement |
            IfThenStatement |
            IfThenElseStatement |
            WhileStatement |
            ForStatement .

IfThenStatement = "if" "(" Expression ")" Statement .

IfThenElseStatement = "if" "(" Expression ")" StatementNoShortIf "else" Statement .
