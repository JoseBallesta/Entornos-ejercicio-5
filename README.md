# Entornos-ejercicio-5
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

