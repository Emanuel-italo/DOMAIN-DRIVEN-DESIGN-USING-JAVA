//Escreva um programa para ler 2 valores (considere que não serão informados valores iguais) e escrever o maior deles.

import java.util.Scanner;

public class IntensivoJava1 {
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);

        System.out.println("Digite o primeiro valor: ");
        int valor = scanner.nextInt();

        System.out.println("Digite o segundo valor: ");
        int valor2 = scanner.nextInt();

        if (valor > valor2) {
            System.out.println("O valor maior eh: " + valor);
        } else {
            System.out.println("O valor maior eh: " + valor2);
        }


        scanner.close();
    }
}