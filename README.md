# Entornos-ejercicio-5
## hey
### Dennis Hector: Hola que tal


Paso 1 clono el repositorio
![Paso 1](https://github.com/JoseBallesta/Entornos-ejercicio-5/blob/dennis2-features/imagenes/Captura1.PNG)

Paso 2 creamos la rama
![Paso 2](https://github.com/JoseBallesta/Entornos-ejercicio-5/blob/dennis2-features/imagenes/Captura2.PNG)

Paso 3 entramos a la rama
![Paso 3](https://github.com/JoseBallesta/Entornos-ejercicio-5/blob/dennis2-features/imagenes/Captura3.PNG)
hacemos un push
![Paso 4](https://github.com/JoseBallesta/Entornos-ejercicio-5/blob/dennis2-features/imagenes/Captura4.PNG)

Paso 4 accedo a mi cuenta
![Paso 5](https://github.com/JoseBallesta/Entornos-ejercicio-5/blob/dennis2-features/imagenes/Captura5.PNG)

Paso 5 hacemos un git add a los cambios y git commit
![Paso 6](https://github.com/JoseBallesta/Entornos-ejercicio-5/blob/dennis2-features/imagenes/Captura6.PNG)
![paso7](https://github.com/JoseBallesta/Entornos-ejercicio-5/blob/dennis2-features/imagenes/Captura7.PNG)
hacemos un git pull
![paso 8](https://github.com/JoseBallesta/Entornos-ejercicio-5/blob/dennis2-features/Captura8.PNG)








static Scanner sc=new Scanner(System.in);
    public static void main(String[] args) throws InterruptedException {
        int max=13;
        int min=1;
        int dennis;
        
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
