#SE IMPLEMENTAN LISTAS DADA LA FACILIDAD DE ACCEDER A LOS DIGITOS DE LOS JUGADORES
######## Jugador 1 ###########
print("Jugador 1, ingresa tu número secreto (4 dígitos):")
numJ1 = [
    int(input("Dígito 1: ")),
    int(input("Dígito 2: ")),
    int(input("Dígito 3: ")),
    int(input("Dígito 4: "))
]
print("\nNúmero guardado. Turno del Jugador 2.\n")
######## Jugador 2 ###########
print("Jugador 2, ingresa tu número secreto (4 dígitos):")
numJ2 = [
    int(input("Dígito 1: ")),
    int(input("Dígito 2: ")),
    int(input("Dígito 3: ")),
    int(input("Dígito 4: "))
]
print("\n"*50)
print("\nNúmero guardado. Comienza el juego.\n")
################## Función para calcular picas y fijas ################
def picas_fijas(secreto, intento):
    fijas = sum(1 for i in range(4) if secreto[i] == intento[i]) # <- Cuenta el numero de fijas
    picas = sum(1 for i in range(4) if intento[i] in secreto and intento[i] != secreto[i]) # <- Cuenta el numero de picas
    return picas, fijas
############### CICLO DEL JUEGO #############################
while True:  #<- Hace el ciclo hasta que gana un jugador con un f ==4
################ Turno Jugador 1 ###########################
    print("\nTurno del Jugador 1 (adivinar número del Jugador 2)")
    intento1 = [
        int(input("Dígito 1: ")),
        int(input("Dígito 2: ")),
        int(input("Dígito 3: ")),
        int(input("Dígito 4: "))
    ]
    p, f = picas_fijas(numJ2, intento1)
    print(f"Picas: {p} | Fijas: {f}")
    if f == 4:
        print("Jugador 1 gana")
        break #<- Descansa este ciclo para continuar con el del jugador 2 y así similar los turnos
############## Turno Jugador 2 ################
    print("\nTurno del Jugador 2")
    intento2 = [
        int(input("Dígito 1: ")),
        int(input("Dígito 2: ")),
        int(input("Dígito 3: ")),
        int(input("Dígito 4: "))
    ]
    p, f = picas_fijas(numJ1, intento2)# <- Llama a la funcion de picas y fijas, y los resultados p y j ahora son esos valores que contó el for
    print(f"Picas: {p} | Fijas: {f}") #<- {} cuenta el numero de acierto en picas y fijas
    if f == 4:
        print("\nJugador 2 gana")
        break #<- Posterior a este break vuelve a preguntarle al jugador 1 si no adivino
        
