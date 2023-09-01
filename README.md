# Proyecto
## Proyecto 1 de algoritmos
### Triple de pitagoras en pseudocodigo:

    Algoritmo Triple_de_Pitagoras
    
        Definir limite, lado1, lado2, hipotenusa como Entero
    
        limite = 500
    
        Escribir "Triples de Pitágoras menores o iguales a ", limite, ":"
    
        Para lado1 = 1 Hasta limite Hacer
            Para lado2 = 1 Hasta limite Hacer
                Para hipotenusa = 1 Hasta limite Hacer
                    Si lado1^2 + lado2^2 = hipotenusa^2 Entonces
                        Escribir "Lado1:", lado1, ", Lado2:", lado2, ", Hipotenusa:", hipotenusa
                    FinSi
                FinPara
            FinPara
        FinPara

    FinAlgoritmo

___
### Triple de pitagoras en c++:

    #include <iostream>

    using namespace std;

    int main() {
    
    int limite = 500;
    cout << "Triples de Pitagoras menores o iguales a " << limite << ":" << endl;

    for (int lado1 = 1; lado1 <= limite; lado1++) {
        for (int lado2 = lado1; lado2 <= limite; lado2++) {
            for (int hipotenusa = lado2; hipotenusa <= limite; hipotenusa++) {
                if (lado1 * lado1 + lado2 * lado2 == hipotenusa * hipotenusa) {
                    cout << "Lado1: " << lado1 << ", Lado2: " << lado2 << ", Hipotenusa: " << hipotenusa << endl;
                }
            }
        }
    }

    return 0;
    }
___

### Triple de pitagoras en python:

    limite = 500
    print("Triples de Pitagoras menores o iguales a", limite, ":")

    for lado1 in range(1, limite + 1):
        for lado2 in range(lado1, limite + 1):
            for hipotenusa in range(lado2, limite + 1):
                if lado1 ** 2 + lado2 ** 2 == hipotenusa ** 2:
                    print("Lado1:", lado1, ", Lado2:", lado2, ", Hipotenusa:", hipotenusa)
___

## Juego de ahorcado

### Ahorcado en pseudocodigo:

    Algoritmo juego_del_ahorcado
        PALABRAS_TAMANO <- 23;
        oportunidades <- 6;
        Dimension palabras[PALABRAS_TAMANO];
        palabras[1] <- "Arbol";
        palabras[2] <- "Casa";
        palabras[3] <- "Tener";
        palabras[4] <- "Pared";
        palabras[5] <- "Luces";
        palabras[6] <- "Archivo";
        palabras[7] <- "Personalizar";
        palabras[8] <- "Caminar";
        palabras[9] <- "Enterrado";
        palabras[10] <- "Problema";
        palabras[11] <- "Amarillo";
        palabras[12] <- "Alaska";
        palabras[13] <- "Alas";
        palabras[14] <- "Luna";
        palabras[15] <- "Estacion";
        palabras[16] <- "Funcionamiento";
        palabras[17] <- "Pantalla";
        palabras[18] <- "Noche";
        palabras[19] <- "Amanecer";
        palabras[20] <- "Avion";
        palabras[21] <- "Nieve";
        cabeza <- ' ';
        cuerpo <- ' ';
        mano_izquierda <- ' ';
        mano_derecha <- ' ';
        pie_izquierdo <- ' ';
        pie_derecho <- ' ';
        turnos <- 0;
        aciertos <- 0;
        palabra <- palabras[Azar(PALABRAS_TAMANO)+1];
        n <- Longitud(palabra);
        Dimension casillas(n);
        Para i<-1 Hasta n Con Paso 1 Hacer
            casillas[i] <- '_';
        FinPara
        Repetir
            Escribir "";
            Escribir "Oportunidades restantes: ", oportunidades-turnos;
            Para i<-1 Hasta n Con Paso 1 Hacer
                Escribir Sin Saltar " ", casillas[i];
            FinPara
            Escribir "";
            Escribir Sin Saltar "Escriba una letra: ";
            Leer letra;
            encontrado <- Falso;
            Para i<-1 Hasta n Con Paso 1 Hacer
                chr <- Subcadena(palabra, i, i);
                Si Mayusculas(letra)=Mayusculas(chr) Entonces
                    encontrado <- Verdadero;
                    Si casillas[i]='_' Entonces
                        casillas[i] <- chr;
                        aciertos <- aciertos+1;
                    FinSi
                FinSi
            FinPara
            Si No encontrado Entonces
                turnos <- turnos+1;
                Escribir "Letra no encontrada.";
                Segun turnos Hacer
                    1:
                        cabeza <- 'O';
                    2:
                        cuerpo <- '+';
                    3:
                        mano_derecha <- '/';
                    4:
                        mano_izquierda <- '\';
                    5:
                        pie_derecho <- '/';
                    6:
                        pie_izquierdo <- '\';
                FinSegun
            FinSI
            Escribir "     ", cabeza," ";
            Escribir "    ", mano_derecha, cuerpo, mano_izquierda;
            Escribir "    ", pie_derecho," ", pie_izquierdo;
            Escribir "";
        Hasta Que turnos>=oportunidades O aciertos>=n;
        Si aciertos=n Entonces
            Escribir "Felicidades, has ganado.";
        Sino
            Escribir "Has perdido.";
        FinSi
        Escribir "La palabra secreta es: ", palabra;
    FinAlgoritmo
___

### Juego ahorcado en c++:

    #include <iostream>
    #include <string>
    #include <ctime> 
    #include <cstdlib> 

    using namespace std;

    void LimpiarPantalla();
    void JugarPartida();
    void Dibujar();

    char eleccion;
    string palabras[] = {"armonica","estudio","animacion","computadora","apertura","gato","amarillo","purpura","ventilador","apellido","semana","arandano","camiseta","puerta","telefono","edicion","cielo","timon","dedos","numeros"};
    string palabra, fallidas; 
    int nA;
    int vida;
    bool correcta, completa;

    int main(){
        while(true){
            vida = 6;
            palabra = "";
            fallidas = "";
            LimpiarPantalla();
            cout<<"\t::::MENU::::"<<endl;
            cout<<"1) empezar partida"<<endl;
            cout<<"2) Salir."<<endl;
            cout<<"Eleccion: ";
            cin>>eleccion;
            switch(eleccion){
                case '1':
                    JugarPartida();
                    break;
                case '2':
                    return 0;
            }
        }
    }

    void JugarPartida(){
        srand(static_cast<unsigned>(time(NULL)));
        nA = rand() % 10;
        
        for(int i = 0; i < static_cast<int>(palabras[nA].size()); i++){
            palabra += "-";
        }
        
        while(vida > 0){
            LimpiarPantalla();
            cout<<"\t::: A H O R C A D O :::"<<endl;
            Dibujar();
            cout<<"Fallos: "<<fallidas;
            cout<<"  Progreso: "<<palabra<<endl;
            cout<<"Ingrese una letra(minuscula): ";
            cin>>eleccion;
            
            correcta = false;
            for(int i = 0; i < static_cast<int>(palabras[nA].size()); i++){
                if(palabras[nA][i] == eleccion){
                    palabra[i] = eleccion;
                    correcta = true;    
                }
            }
            if(!correcta){
                vida--;
                fallidas += eleccion;
            }
            
            completa = true;
            for(int i = 0; i < static_cast<int>(palabra.size()); i++){
                if(palabra[i] == '-'){
                    completa = false;
                }
            }
            if(completa){
                LimpiarPantalla();
                cout<<"\t::: A H O R C A D O :::"<<endl;
                Dibujar();
                cout<<"Palabra: "<<palabras[nA]<<endl;
                cout<<"Ganaste. Ingresa un caracter para continuar: ";
                cin>>eleccion;
                return;
            }
        }
        LimpiarPantalla();
        cout<<"\t::: A H O R C A D O :::"<<endl;
        Dibujar();
        cout<<"Palabra: "<<palabras[nA]<<endl;
        cout<<"Perdiste. Ingresa un caracter para continuar: ";
        cin>>eleccion;
    }

    void Dibujar(){
        switch(vida){
            case 6:
            cout<<"  --------"<<endl;
            cout<<"  |      |"<<endl;
            cout<<"  |"<<endl;
            cout<<"  |"<<endl;
            cout<<"  |"<<endl;
            cout<<"  |"<<endl;
            cout<<"  |"<<endl;
            cout<<" ---"<<endl;
            break;
            case 5:
            cout<<"  --------"<<endl;
            cout<<"  |      |"<<endl;
            cout<<"  |      O"<<endl;
            cout<<"  |"<<endl;
            cout<<"  |"<<endl;
            cout<<"  |"<<endl;
            cout<<"  |"<<endl;
            cout<<" ---"<<endl;
            break;
            case 4:
            cout<<"  --------"<<endl;
            cout<<"  |      |"<<endl;
            cout<<"  |      O"<<endl;
            cout<<"  |      |"<<endl;
            cout<<"  |"<<endl;
            cout<<"  |"<<endl;
            cout<<"  |"<<endl;
            cout<<" ---"<<endl;
            break;
            case 3:
            cout<<"  --------"<<endl;
            cout<<"  |      |"<<endl;
            cout<<"  |      O"<<endl;
            cout<<"  |     /|"<<endl;
            cout<<"  |"<<endl;
            cout<<"  |"<<endl;
            cout<<"  |"<<endl;
            cout<<" ---"<<endl;
            break;
            case 2:
            cout<<"  --------"<<endl;
            cout<<"  |      |"<<endl;
            cout<<"  |      O"<<endl;
            cout<<"  |     /|\\"<<endl;
            cout<<"  |"<<endl;
            cout<<"  |"<<endl;
            cout<<"  |"<<endl;
            cout<<" ---"<<endl;
            break;
            case 1:
            cout<<"  --------"<<endl;
            cout<<"  |      |"<<endl;
            cout<<"  |      O"<<endl;
            cout<<"  |     /|\\"<<endl;
            cout<<"  |     /"<<endl;
            cout<<"  |"<<endl;
            cout<<"  |"<<endl;
            cout<<" ---"<<endl;
            break;
            case 0:
            cout<<"  --------"<<endl;
            cout<<"  |      |"<<endl;
            cout<<"  |      O"<<endl;
            cout<<"  |     /|\\"<<endl;
            cout<<"  |     / \\"<<endl;
            cout<<"  |"<<endl;
            cout<<"  |"<<endl;
            cout<<" ---"<<endl;
            break;
        }
    }

    void LimpiarPantalla(){
        if(system("clear") == -1){
            cout<<"Error al borrar la pantalla.";
        }
    }
___

### Juego ahorcado en python:

    import random
    AHORCADO = ['''
        +---+
        |   |
            |
            |
            |
            |
        =========''', '''
        +---+
        |   |
        O   |
            |
            |
            |
        =========''', '''
        +---+
        |   |
        O   |
        |   |
            |
            |
        =========''', '''
        +---+
        |   |
        O   |
        /|   |
            |
            |
        =========''', '''
        +---+
        |   |
        O   |
        /|\  |
            |
            |
        =========''', '''
        +---+
        |   |
        O   |
        /|\  |
        /    |
            |
        =========''', '''
        +---+
        |   |
        O   |
        /|\  |
        / \  |
            |
        =========''']
    palabras = 'celular pato'.split()
    
    def buscarPalabraAleat(listaPalabras):
        palabraAleatoria = random.randint(0, len(listaPalabras) - 1)
        return listaPalabras[palabraAleatoria]
    
    def displayBoard(AHORCADO, letraIncorrecta, letraCorrecta, palabraSecreta):
        print(AHORCADO[len(letraIncorrecta)])
        print ("")
        fin = " "
        print ('Letras incorrectas:', fin)
        for letra in letraIncorrecta:
            print (letra, fin)
        print ("")
        espacio = '_' * len(palabraSecreta)
        for i in range(len(palabraSecreta)): # Remplaza los espacios en blanco por la letra bien escrita
            if palabraSecreta[i] in letraCorrecta:
                espacio = espacio[:i] + palabraSecreta[i] + espacio[i+1:]
        for letra in espacio: # Mostrará la palabra secreta con espacios entre letras
            print (letra, fin)
        print ("")
    
    def elijeLetra(algunaLetra):
        while True:
            print ('Adivina una letra:')
            letra = input()
            letra = letra.lower()
            if len(letra) != 1:
                print ('Introduce una sola letra.') 
            elif letra in algunaLetra:
                print ('Ya has elegido esa letra ¿Qué tal si pruebas con otra?')
            elif letra not in 'abcdefghijklmnopqrstuvwxyz':
                print ('Elije una letra.')
            else:
                return letra
    
    def empezar():
        print ('Quieres jugar de nuevo? (Si o No)')
        return input().lower().startswith('s')
    
    print ('A H O R C A D O')
    letraIncorrecta = ""
    letraCorrecta = ""
    palabraSecreta = buscarPalabraAleat(palabras)
    finJuego = False
    while True:
        displayBoard(AHORCADO, letraIncorrecta, letraCorrecta, palabraSecreta)
        letra = elijeLetra(letraIncorrecta + letraCorrecta)
        if letra in palabraSecreta:
            letraCorrecta = letraCorrecta + letra
            letrasEncontradas = True
            for i in range(len(palabraSecreta)):
                if palabraSecreta[i] not in letraCorrecta:
                    letrasEncontradas = False
                    break
            if letrasEncontradas:
                print ('¡Muy bien! La palabra secreta es "' + palabraSecreta + '"! ¡Has ganado!')
                finJuego = True
        else:
            letraIncorrecta = letraIncorrecta + letra
            if len(letraIncorrecta) == len(AHORCADO) - 1:
                displayBoard(AHORCADO, letraIncorrecta, letraCorrecta, palabraSecreta)
                print ('¡Se ha quedado sin letras!\nDespues de ' + str(len(letraIncorrecta)) + ' letras erroneas y ' + str(len(letraCorrecta)) + ' letras correctas, la palabra era "' + palabraSecreta + '"')
                finJuego = True
        if finJuego:
            if empezar():
                letraIncorrecta = ""
                letraCorrecta = ""
                finJuego = False
                palabraSecreta = buscarPalabraAleat(palabras)
            else:
                break
___
___ 
