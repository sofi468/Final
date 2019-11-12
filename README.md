# Final package listadinamica;

import java.util.ArrayList;
import java.util.Scanner;

public class ListaDinamica {

    static ArrayList <Integer> lista = new ArrayList();
    static Scanner sc = new Scanner(System.in);
    static String verif;
    static int A = 0, tam, aux, c=0;
    
    public static void main(String args[]) {
        System.out.println();
        do{
        System.out.println("De que tamaño desea la lista?");
        verif = sc.next();
            if(Validacion(verif) == true){
                tam = Integer.parseInt(verif);
                c = 1;
            }else{
                System.out.println("Por favor, ingrese un numero, sin simbolos");
            }
        }while(c==0);
        do{
            System.out.println("Presione (1) para agregarle un valor a la lista");
            System.out.println("Presione (2) para mostrar los numeros de forma ascendente");
            System.out.println("Presione (3) para mostrar los numeros de forma descendente");
            System.out.println("Presione (4) para mostrar la informacion guardada");
            System.out.println("Presione (0) si desea salir");
            System.out.println();
            c = 0;
            do{
                System.out.println("Ingrese el numero de la opcion deseada:");
                verif = sc.next();
                if(Validacion(verif) == true){
                    A = Integer.parseInt(verif);
                    c = 1;
                }else{
                    System.out.println("SOLAMENTE INGRESE NUMEROS DE LAS OPCIONES DADAS");
                }
            }while(c == 0);
            switch(A){
                case(1):
                    IngresarNumero();
                break;
                case(2):
                    OrdenarNumerosAscend();
                break;
                case(3):
                    OrdenarNumerosDescend();
                break;
                case(4):
                    MostrarLista();
                break;
                case(0):
                break;
                default:
                    System.out.println("SOLAMENTE INGRESE NUMEROS DE LAS OPCIONES DADAS");
                break;
            }
        }while(A != 0);
    }
    public static void IngresarNumero(){
        if(lista.size()>=tam){
            System.out.println("Ya no se pueden ingresar mas numeros");
            System.out.println();
        }else{
            c = 0;
            do{
                System.out.println("Inserte el numero que desea ingresar:");
                verif = sc.next();
                if(Validacion(verif) == true){
                    lista.add(Integer.parseInt(verif));
                    c = 1;
                }else{
                    System.out.println("Por favor solo ingresar numeros");
                }
            }while(c == 0);
        }
    }
    public static void OrdenarNumerosDescend(){
        System.out.println();
        for(int i=0;i<lista.size();i++){
            for(int k=i+1;k<lista.size();k++){
                if(lista.get(i) == lista.get(k)){
                    lista.remove(k);
                }else{
                    if(lista.get(i)<lista.get(k)){
                        aux = lista.get(i);
                        lista.set(i, lista.get(k));
                        lista.set(k, aux);
                    }
                }
            }
        }
        if(lista.size()!=1){
            if(lista.get(0) == lista.get(lista.size()-1)){
                lista.remove(lista.size()-1);
            }
        }
    }
    public static void OrdenarNumerosAscend(){
        System.out.println();
        for(int i=0;i<lista.size();i++){
            for(int k=i+1;k<lista.size();k++){
                if(lista.get(i) == lista.get(k)){
                    lista.remove(k);
                }else{
                    if(lista.get(i)>lista.get(k)){
                        aux = lista.get(i);
                        lista.set(i, lista.get(k));
                        lista.set(k, aux);
                    }
                }
            }
        }
        if(lista.size()!=1){
            if(lista.get(0) == lista.get(lista.size()-1)){
                lista.remove(lista.size()-1);
            }
        }
    }
    public static void MostrarLista(){
        for(int i=0;i<lista.size();i++){
            System.out.print(lista.get(i) + ", ");
        }
        System.out.println();
        System.out.println();
    }
    public static boolean Validacion(String cad){
        int num;
        try{
            num = Integer.parseInt(cad);
            return true;
        }catch(Exception e){
            return false;
        }
    }
}









