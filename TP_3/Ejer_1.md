# PARADIGMA IMPERATIVO
```py
numeros = [30, 10, 50, 20, 40]
def buscar_elemento(coleccion, elemento):
    for i in range(len(coleccion)):
        if coleccion[i] == elemento:
            return i
    return -1
posicion = buscar_elemento(numeros, 20)

if posicion != -1:
    print("El elemento fue encontrado en la posición:", posicion)
else:
    print("El elemento no fue encontrado")

# 2. Ordenar elementos en una colección
def ordenar_elementos(coleccion):
    return sorted(coleccion)

numeros_ordenados = ordenar_elementos(numeros)
print("Números ordenados:", numeros_ordenados)
```

# PARADIGMA ORIENTADO A OBJETOS
```py
class ColeccionNumeros:
    def __init__(self, numeros):
        self.numeros = numeros

    def buscar(self, elemento):
        if elemento in self.numeros:
            return self.numeros.index(elemento)
        return -1

    # 2. Ordenar elementos en una colección
    def ordenar(self):
        return sorted(self.numeros)

coleccion = ColeccionNumeros([30, 10, 50, 20, 40])
posicion = coleccion.buscar(20)
if posicion != -1:
    print("El elemento fue encontrado en la posición:", posicion)
else:
    print("El elemento no fue encontrado")

print("Números ordenados:", coleccion.ordenar())


```

# PARADIGMA FUNCIONAL
```py
def buscar_elemento(coleccion, elemento):
    posiciones = list(filter(lambda i: coleccion[i] == elemento, range(len(coleccion))))

    if len(posiciones) > 0:
        return posiciones[0]
    return -1

# 2. Ordenar elementos en una colección
def ordenar_elementos(coleccion):
    return sorted(coleccion)

posicion = buscar_elemento(numeros, 20)

if posicion != -1:
    print("El elemento fue encontrado en la posición:", posicion)
else:
    print("El elemento no fue encontrado")

print("Números ordenados:", ordenar_elementos(numeros))

```
# PARADIGMA LOGICO
```prolog
% Colección de números
numero(30).
numero(10).
numero(50).
numero(20).
numero(40).

buscar(X) :- elemento(X)

?- buscar(20).
% Respuesta esperada:
% true.

% 2. Ordenar elementos en una colección
% ?- findall(X, numero(X), Lista), sort(Lista, Ordenada).
% Resultado:
% Lista = [30, 10, 50, 20, 40],
% Ordenada = [10, 20, 30, 40, 50].

```


