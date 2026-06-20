# PARADIGMA IMPERATIVO
```py
tareas = []
def agregar_tarea(titulo, prioridad):
    tarea = {
        "titulo": titulo,
        "prioridad": prioridad,
        "completada": False
    }
    tareas.append(tarea)

def marcar_completada(titulo):
    for tarea in tareas:
        if tarea["titulo"] == titulo:
            tarea["completada"] = True


def mostrar_pendientes():
    pendientes = []

    for tarea in tareas:
        if tarea["completada"] == False:
            pendientes.append(tarea)

    pendientes_ordenadas = sorted(pendientes, key=lambda tarea: tarea["prioridad"])

    for tarea in pendientes_ordenadas:
        print(tarea["titulo"], "- Prioridad:", tarea["prioridad"])


agregar_tarea("Estudiar lenguajes", 2)
agregar_tarea("Hacer el trabajo práctico", 1)
agregar_tarea("Leer apuntes", 3)

marcar_completada("Leer apuntes")

print("Tareas pendientes:")
mostrar_pendientes()
```
# PARADIGMA ORIENTADO A OBJETOS
```py
class Tarea:
    def __init__(self, titulo, prioridad):
        self.titulo = titulo
        self.prioridad = prioridad
        self.completada = False

    def marcar_completada(self):
        self.completada = True

class GestorTareas:
    def __init__(self):
        self.tareas = []

    def agregar_tarea(self, titulo, prioridad):
        nueva_tarea = Tarea(titulo, prioridad)
        self.tareas.append(nueva_tarea)

    def marcar_completada(self, titulo):
        for tarea in self.tareas:
            if tarea.titulo == titulo:
                tarea.marcar_completada()

    def mostrar_pendientes(self):
        pendientes = []

        for tarea in self.tareas:
            if tarea.completada == False:
                pendientes.append(tarea)

        pendientes_ordenadas = sorted(pendientes, key=lambda tarea: tarea.prioridad)

        for tarea in pendientes_ordenadas:
            print(tarea.titulo, "- Prioridad:", tarea.prioridad)
gestor = GestorTareas()

gestor.agregar_tarea("Estudiar lenguajes", 2)
gestor.agregar_tarea("Hacer el trabajo práctico", 1)
gestor.agregar_tarea("Leer apuntes", 3)

gestor.marcar_completada("Leer apuntes")

print("Tareas pendientes:")
gestor.mostrar_pendientes()
```
# PARADIGMA FUNCIONAL
```py
def crear_tarea(titulo, prioridad):
    return {
        "titulo": titulo,
        "prioridad": prioridad,
        "completada": False
    }


def agregar_tarea(tareas, titulo, prioridad):
    nueva_tarea = crear_tarea(titulo, prioridad)
    return tareas + [nueva_tarea]


def marcar_completada(tareas, titulo):
    return list(
        map(
            lambda tarea: {
                "titulo": tarea["titulo"],
                "prioridad": tarea["prioridad"],
                "completada": True
            } if tarea["titulo"] == titulo else tarea,
            tareas
        )
    )

def obtener_pendientes_ordenadas(tareas):
    pendientes = filter(lambda tarea: tarea["completada"] == False, tareas)
    return sorted(pendientes, key=lambda tarea: tarea["prioridad"])

tareas = []

tareas = agregar_tarea(tareas, "Estudiar lenguajes", 2)
tareas = agregar_tarea(tareas, "Hacer el trabajo práctico", 1)
tareas = agregar_tarea(tareas, "Leer apuntes", 3)

tareas = marcar_completada(tareas, "Leer apuntes")

print("Tareas pendientes:")

for tarea in obtener_pendientes_ordenadas(tareas):
    print(tarea["titulo"], "- Prioridad:", tarea["prioridad"])

% -------------------------------
% PARADIGMA LÓGICO
% -------------------------------

% Colección de números
numero(30).
numero(10).
numero(50).
numero(20).
numero(40).


% 1. Buscar elemento en una colección
% Pregunta:
% ?- numero(20).
%
% Respuesta esperada:
% true.


% 2. Ordenar elementos en una colección
% En Prolog se podría consultar:
% ?- findall(X, numero(X), Lista), sort(Lista, Ordenada).
%
% Resultado:
% Lista = [30, 10, 50, 20, 40],
% Ordenada = [10, 20, 30, 40, 50].


% 3. Gestionar una lista de tareas pendientes

% Hechos: tarea(Titulo, Prioridad, Estado)
tarea("Estudiar lenguajes", 2, pendiente).
tarea("Hacer el trabajo practico", 1, pendiente).
tarea("Leer apuntes", 3, completada).


% Regla para saber si una tarea está pendiente
tarea_pendiente(Titulo, Prioridad) :-
    tarea(Titulo, Prioridad, pendiente).


% Consulta:
% ?- tarea_pendiente(Titulo, Prioridad).
%
% Respuesta:
% Titulo = "Estudiar lenguajes",
% Prioridad = 2 ;
% Titulo = "Hacer el trabajo practico",
% Prioridad = 1.


% Para mostrar tareas pendientes ordenadas por prioridad:
% ?- findall(Prioridad-Titulo, tarea_pendiente(Titulo, Prioridad), Lista),
%    sort(Lista, Ordenada).
%
% Resultado:
% Ordenada = [1-"Hacer el trabajo practico", 2-"Estudiar lenguajes"].