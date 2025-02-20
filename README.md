// Interfaz IAsignatura
interface IAsignatura {
    double CalcularNotaFinal();
    double CalcularNotaFinal(int n1, int n2, int n3);
    String MensajeNotaFinal(double notaFinal);
    void Imprimir();
}

// Clase Alumno
class Alumno {
    protected String NombreAlumno;
    protected String NumeroCuenta;
    protected String Email;
}

// Clase Asignatura que hereda de Alumno e implementa IAsignatura
class Asignatura extends Alumno implements IAsignatura {
    private int N1, N2, N3;
    private String NombreAsignatura;
    private String Horario;
    private String NombreDocente;

    public Asignatura(String nombreAlumno, String numeroCuenta, String email, String nombreAsignatura, String horario, String nombreDocente, int n1, int n2, int n3) {
        this.NombreAlumno = nombreAlumno;
        this.NumeroCuenta = numeroCuenta;
        this.Email = email;
        this.NombreAsignatura = nombreAsignatura;
        this.Horario = horario;
        this.NombreDocente = nombreDocente;
        this.N1 = n1;
        this.N2 = n2;
        this.N3 = n3;
    }

    @Override
    public double CalcularNotaFinal() {
        return N1 + N2 + N3;
    }

    @Override
    public double CalcularNotaFinal(int n1, int n2, int n3) {
        return n1 + n2 + n3;
    }

    @Override
    public String MensajeNotaFinal(double notaFinal) {
        if (notaFinal < 60) return "Reprobado";
        else if (notaFinal < 80) return "Bueno";
        else if (notaFinal < 90) return "Muy Bueno";
        else return "Sobresaliente";
    }

    @Override
    public void Imprimir() {
        double notaFinal1 = CalcularNotaFinal();
        double notaFinal2 = CalcularNotaFinal(N1, N2, N3);
        String mensaje = MensajeNotaFinal(notaFinal1);
        
        System.out.println("Nombre del Alumno: " + NombreAlumno);
        System.out.println("Número de Cuenta: " + NumeroCuenta);
        System.out.println("Email: " + Email);
        System.out.println("Asignatura: " + NombreAsignatura);
        System.out.println("Horario: " + Horario);
        System.out.println("Docente: " + NombreDocente);
        System.out.println("Nota Final (Método 1): " + notaFinal1 + " - " + mensaje);
        System.out.println("Nota Final (Método 2): " + notaFinal2 + " - " + mensaje);
    }
}

// Main
public class Examen {
    public static void main(String[] args) {
        java.util.Scanner scanner = new java.util.Scanner(System.in);
        try {
            System.out.print("Ingrese nombre del alumno: ");
            String nombreAlumno = scanner.nextLine();
            System.out.print("Ingrese número de cuenta: ");
            String numeroCuenta = scanner.nextLine();
            System.out.print("Ingrese email: ");
            String email = scanner.nextLine();
            System.out.print("Ingrese nombre de la asignatura: ");
            String nombreAsignatura = scanner.nextLine();
            System.out.print("Ingrese horario: ");
            String horario = scanner.nextLine();
            System.out.print("Ingrese nombre del docente: ");
            String nombreDocente = scanner.nextLine();

            int n1, n2, n3;
            while (true) {
                System.out.print("Ingrese nota del primer parcial (máx 30%): ");
                n1 = scanner.nextInt();
                if (n1 <= 30) break;
                System.out.println("Error: La nota no puede superar el 30%.");
            }
            while (true) {
                System.out.print("Ingrese nota del segundo parcial (máx 30%): ");
                n2 = scanner.nextInt();
                if (n2 <= 30) break;
                System.out.println("Error: La nota no puede superar el 30%.");
            }
            while (true) {
                System.out.print("Ingrese nota del tercer parcial (máx 40%): ");
                n3 = scanner.nextInt();
                if (n3 <= 40) break;
                System.out.println("Error: La nota no puede superar el 40%.");
            }
            
            Asignatura asignatura = new Asignatura(nombreAlumno, numeroCuenta, email, nombreAsignatura, horario, nombreDocente, n1, n2, n3);
            asignatura.Imprimir();
        } catch (Exception e) {
            System.out.println("Error al ingresar los datos: " + e.getMessage());
        }
    }
}
