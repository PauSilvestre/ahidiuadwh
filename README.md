import java.util.Scanner;
import java.util.Random;

public class Main { public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        System.out.println("Selecciona el tamaño del mapa (ejemplo: 10 10 para un tablero de 10x10)");

        System.out.println("Columnas:");
        int columnas = scanner.nextInt();

        System.out.println("Filas:");
        int filas = scanner.nextInt();

        int[][] mapa = new int[columnas][filas];

        System.out.println("Indica cuantos bárcos quieres tener");
        int barcos = scanner.nextInt();

        System.out.println("Indica el número de disparos");
        int disparos = scanner.nextInt();

        //generación de barcos
        int direccion_barco_x = 0;
        int direccion_barco_y = 0;

        for (int i = 0; i < barcos; i++) {
            int mitad_tablero = (filas/2);
            int x_o_y = random.nextInt(0,1); // 0 es horizontal 1 es vertical
            direccion_barco_x = random.nextInt(0,1);
            direccion_barco_y = random.nextInt(0,1);
            int posi_x = random.nextInt(0, filas);
            int posi_y = random.nextInt(0, filas);
            mapa[posi_x][posi_y] = 1;

            // 0 izquierda, 1 derecha
            if(posi_x > mitad_tablero){
                direccion_barco_x = 0;
            } else if (posi_y > mitad_tablero) {
                direccion_barco_y = 0;
            } else if (posi_x < mitad_tablero) {
                direccion_barco_x = 1;
            } else if (posi_y < mitad_tablero) {
                direccion_barco_y = 1;
            } else{
                direccion_barco_x = 1;
                direccion_barco_y = 1;
            }
            int size_barco = random.nextInt(1, mitad_tablero);

            for (int j = 0; j < size_barco; j++) {
                int cont_x = 1;
                int cont_y = 1;
                if (direccion_barco_x == 0){
                    cont_x = -1;
                    if (x_o_y == 0){
                        mapa[posi_x][posi_y + cont_y] = 1;
                        cont_y--;
                    } else{
                        mapa[posi_x + cont_x][posi_y] = 1;
                        cont_x--;
                    }
                } else if (direccion_barco_x == 1) {
                    cont_x = 1;
                    if (x_o_y == 0){
                        mapa[posi_x][posi_y + cont_y] = 1;
                        cont_y++;
                    } else{
                        mapa[posi_x + cont_x][posi_y] = 1;
                        cont_x++;
                    }
                } else if (direccion_barco_y == 0){
                    cont_y = -1;
                    if (x_o_y == 0){
                        mapa[posi_x][posi_y + cont_y] = 1;
                        cont_y--;
                    } else{
                        mapa[posi_x + cont_x][posi_y] = 1;
                        cont_x--;
                    }
                } else{
                    cont_y = 1;
                    if (x_o_y == 0){
                        mapa[posi_x][posi_y + cont_y] = 1;
                        cont_y--;
                    } else{
                        mapa[posi_x + cont_x][posi_y] = 1;
                        cont_x--;
                    }
                }
            }
        }
        for (int i = 0; i < mapa.length; i++) {
            for (int j = 0; j < mapa[i].length; j++) {
                System.out.print(mapa[i][j] + "  ");
            }
            System.out.println();
        }

    }
}
