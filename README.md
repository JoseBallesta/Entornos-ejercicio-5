# Entornos-ejercicio-5
<<<<<<< HEAD
public class Main {

	static Scanner sc=new Scanner(System.in);
	public static void main(String[] args) {
		SimpleDateFormat formato1=new SimpleDateFormat("dd/MM/yyyy");
		SimpleDateFormat formato2=new SimpleDateFormat("yyyy");
		SimpleDateFormat formato3=new SimpleDateFormat("d");
		SimpleDateFormat formato4=new SimpleDateFormat("M");
		SimpleDateFormat formato5=new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");
	
		
		Date fechaHoy = null;
		try {
			fechaHoy = formato5.parse(formato1.format(new Date())+" 23:59:59");
		} catch (ParseException e1) {

		}
		
		
		Date miFecha = null;
		boolean error=true;
		do {
			System.out.println("Fecha de nacimiento?");
			try {
				miFecha = formato1.parse(sc.nextLine());
				error=false;
			} catch (ParseException e) {
				System.out.println("Formato incorrecto");
			} 
		} while (error);
		
		
		int dia=Integer.parseInt(formato3.format(miFecha));
		int mes=Integer.parseInt(formato4.format(miFecha));
		int ano=Integer.parseInt(formato2.format(miFecha))+18;

		Date miFechamas = null;
		try {
			miFechamas=formato1.parse(dia+"/"+mes+"/"+ano);
		} catch (ParseException e) {

		}
		if (miFechamas.before(fechaHoy)) {
			System.out.println("Es mayor de edad");
		} else {
			System.out.println("No es mayor de edad");
		} 

		
		/*GregorianCalendar cal=new GregorianCalendar();
		
		
		cal.setTime(miFecha);
		
		cal.add(Calendar.YEAR, 18);
		
		
		Date tope=cal.getTime();
		
		System.out.println(formato2.format(tope));*/

	}

=======


static Scanner sc=new Scanner(System.in);
Freddy Garcés
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
>>>>>>> dace1130c5d49ee0b4ef729e76bd6d8a34dedf99
