
import java.util.Scanner;

public class ValidaSenhaForte {

    public static String avaliarSenha(String senha) {

        // 1. Verificar o comprimento da senha
        if (senha.length() < 8) {
            return "DICA: A senha deve ter no mínimo 8 caracteres.";
        }

        // 2. Verificar se existe pelo menos um número
        boolean temNumero = false;

        for (int i = 0; i < senha.length(); i++) {
            char caractere = senha.charAt(i);

            if (Character.isDigit(caractere)) {
                temNumero = true;
                break;
            }
        }

        if (!temNumero) {
            return "DICA: Adicione pelo menos um número à sua senha.";
        }

        // 3. Verificar se a senha é óbvia
        String[] senhasObvias = {
            "12345678",
            "senha123",
            "admin123"
        };

        for (int i = 0; i < senhasObvias.length; i++) {
            if (senha.equals(senhasObvias[i])) {
                return "ALERTA: Esta senha é muito comum ou óbvia.";
            }
        }

        // 4. Verificar se existe pelo menos uma letra maiúscula
        boolean temMaiuscula = false;

        for (int i = 0; i < senha.length(); i++) {
            char caractere = senha.charAt(i);

            if (Character.isUpperCase(caractere)) {
                temMaiuscula = true;
                break;
            }
        }

        if (!temMaiuscula) {
            return "DICA: Adicione pelo menos uma letra maiúscula à sua senha.";
        }

        // 5. Se todas as regras forem atendidas
        return "SUCESSO: Sua senha passou nos critérios básicos!";
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        while (true) {

            System.out.print("Digite uma senha fictícia: ");
            String senha = sc.nextLine();

            String resultado = avaliarSenha(senha);

            System.out.println(resultado);

            if (resultado.startsWith("SUCESSO:")) {
                break;
            }
        }

        sc.close();
    }
}
