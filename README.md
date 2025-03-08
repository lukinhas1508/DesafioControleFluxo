# DesafioControleFluxo
 📁 DesafioControleFluxo
 ┣ 📄 Contador.java (Classe principal que executa a lógica)
 ┗ 📄 ParametrosInvalidosException.java (Classe para exceção personalizada)
 
CLASSE PRINCIPAL

    package DesafioControleFluxo;
    import java.util.Scanner;

    public class Contador {  
    public static void main(String[] args) {
       
        try (Scanner terminal = new Scanner(System.in)) {
            System.out.println("Digite o primeiro parâmetro:");
            if (!terminal.hasNextInt()) {
                throw new IllegalArgumentException("Entrada inválida! Digite um número inteiro.");
            }
            int parametroUm = terminal.nextInt();

            System.out.println("Digite o segundo parâmetro:");
            if (!terminal.hasNextInt()) {
                throw new IllegalArgumentException("Entrada inválida! Digite um número inteiro.");
            }
            int parametroDois = terminal.nextInt();

            
            contar(parametroUm, parametroDois);
        } catch (ParametrosInvalidosException | IllegalArgumentException exception) {
            System.out.println("Erro: " + exception.getMessage());
        } catch (Exception e) {
            System.out.println("Erro inesperado: " + e.getMessage());
        }
    }

    static void contar(int parametroUm, int parametroDois) throws ParametrosInvalidosException {
    
        if (parametroUm > parametroDois) {
            throw new ParametrosInvalidosException("O segundo parâmetro deve ser maior que o primeiro.");
        }

        
        int contagem = parametroDois - parametroUm;

       
        for (int i = 1; i <= contagem; i++) {
            System.out.println("Imprimindo o número " + i);
        }
    }


  CLASSE 
  
    package DesafioControleFluxo;

    public class ParametrosInvalidosException extends Exception {
      public ParametrosInvalidosException(String mensagem) {
        super(mensagem);
    }
