# Entornos-ejercicio-5

### Josep Lluis: Hola que tal

Josep Lluis: uaikgsuwgqowa

Josep Lluis: uawgdiuqñod8iwady

Josep Lluis: ysikrpñy

## Josep Lluis: Adios

Paso 1 Creo mi rama 
![Paso 1](https://raw.githubusercontent.com/JoseBallesta/Entornos-ejercicio-5/josep-features/Entornos/Paso1.PNG)

Paso 2 Abrimos la rama
![Paso 2](https://raw.githubusercontent.com/JoseBallesta/Entornos-ejercicio-5/josep-features/Entornos/Paso2.PNG)

Paso 3 Ponemos nuestro email y nombre
![Paso 3](https://raw.githubusercontent.com/JoseBallesta/Entornos-ejercicio-5/josep-features/Entornos/Paso3.PNG)
![Paso 4](https://raw.githubusercontent.com/JoseBallesta/Entornos-ejercicio-5/josep-features/Entornos/Paso4.PNG)

Paso 4 Ahora lo comitamos
![Paso 5](https://raw.githubusercontent.com/JoseBallesta/Entornos-ejercicio-5/josep-features/Entornos/Paso5.PNG)

Paso 5 Hacemos un push
![Paso 6](https://raw.githubusercontent.com/JoseBallesta/Entornos-ejercicio-5/josep-features/Entornos/Paso6.PNG)

Paso 6 Hacemos un pull
![Paso 7](https://raw.githubusercontent.com/JoseBallesta/Entornos-ejercicio-5/josep-features/Entornos/Paso7.PNG)

Paso 7 Editamos el readme
![Paso 8](https://raw.githubusercontent.com/JoseBallesta/Entornos-ejercicio-5/josep-features/Entornos/Paso8.PNG)

Paso 8 Ahora lo comitamos
![Paso 9](https://raw.githubusercontent.com/JoseBallesta/Entornos-ejercicio-5/josep-features/Entornos/Paso9.PNG)

Paso 9 Hacemos un push
![Paso 10](https://raw.githubusercontent.com/JoseBallesta/Entornos-ejercicio-5/josep-features/Entornos/Paso10.PNG)

static Scanner sc=new Scanner(System.in);
    public static void main(String[] args) throws InterruptedException {
        int max=13;
        int min=1;
        
        int valorCarta;
        String nombreCarta;
        String seguir = "n";
        int saldo;
        int apuesta;
        
        System.out.println("Cuanta pasta llevas?");
        saldo=Integer.parseInt(sc.nextLine());
        
        
        
        
        do {
            int totalJugador = 0;
            int totalOrdenador = 0;
            seguir = "n";
            
            
            do {
                System.out.println("Cuanto quieres apostar");
                apuesta=Integer.parseInt(sc.nextLine());
                if (apuesta>saldo) {
                    System.out.println("No tienes suficiente pasta!!");
                }
            } while (apuesta>saldo);
            
            
            
            do {
                valorCarta = (int) (Math.random() * (max - min + 1) + min);
                nombreCarta = valorCarta + "";
                if (valorCarta == 11) {
                    nombreCarta = "J";
                    valorCarta = 10;
                }
                if (valorCarta == 12) {
                    nombreCarta = "Q";
                    valorCarta = 10;
                }
                if (valorCarta == 13) {
                    nombreCarta = "K";
                    valorCarta = 10;
                }
                if (valorCarta == 1) {
                    nombreCarta = "AS";
                    if (totalJugador < 11) {
                        valorCarta = 11;
                    } else {
                        valorCarta = 1;
                    }
                }
                totalJugador += valorCarta;
                System.out.println("Te ha salido un " + nombreCarta);
                System.out.println("Llevas un total de " + totalJugador);
                if (totalJugador > 21) {
                    System.out.println("HAS PERDIDO, Te has pasado!!");
                    saldo-=apuesta;
                } else if (totalJugador < 21) {
                    System.out.println("¿Quieres otra carta (s/n)?");
                    seguir = sc.nextLine();
                }
            } while (seguir.equals("s") && totalJugador < 21);
            if (totalJugador <= 21) {
                System.out.println("Te has plantado con " + totalJugador);
                System.out.println("------------------------------------------\n");

                do {
                    valorCarta = (int) (Math.random() * (max - min + 1) + min);
                    nombreCarta = valorCarta + "";
                    if (valorCarta == 11) {
                        nombreCarta = "J";
                        valorCarta = 10;
                    }
                    if (valorCarta == 12) {
                        nombreCarta = "Q";
                        valorCarta = 10;
                    }
                    if (valorCarta == 13) {
                        nombreCarta = "K";
                        valorCarta = 10;
                    }
                    if (valorCarta == 1) {
                        nombreCarta = "AS";
                        if (totalOrdenador < 11) {
                            valorCarta = 11;
                        } else {
                            valorCarta = 1;
                        }
                    }
                    totalOrdenador += valorCarta;
                    System.out.println("Le ha salido un " + nombreCarta);
                    System.out.println("Lleva un total de " + totalOrdenador);

                    if (totalOrdenador < totalJugador) {
                        System.out.println("Quiere otra\n");
                        Thread.sleep(2000);
                    }
                    if (totalOrdenador >= totalJugador && totalOrdenador <= 21) {
                        System.out.println("HAS PERDIDO!!!!");
                        saldo-=apuesta;
                    }
                    if (totalOrdenador > 21) {
                        System.out.println("HAS GANADO!!!");
                        saldo+=apuesta;
                    }

                } while (totalOrdenador < totalJugador);

            }
            
            System.out.println("------------------------------");
            System.out.println(" SALDO: "+saldo);
            System.out.println("------------------------------");
            
            if (saldo>0) {
                System.out.println("Quieres volver a jugar (s/n)");
                seguir=sc.nextLine();
            }
        } while (seguir.equals("s") );

        
    }
