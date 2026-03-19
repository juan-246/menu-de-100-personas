# menu-de-100-personas
import java.util.Scanner;

public class Main {

    int nroUsuarios = 0;
    Persona[] usuarios = new Persona[100];
    Scanner input = new Scanner(System.in);

    public static void main(String[] args) {
        Main sistema = new Main();
        sistema.iniciar();
    }

    public void iniciar() {

        int opcion = 0;

        while (opcion != 5) {

            opcion = menu();

            switch (opcion) {

                case 1:
                    agregar();
                    break;

                case 2:
                    editar();
                    break;

                case 3:
                    verUsuarios();
                    break;

                case 4:
                    eliminar();
                    break;

                case 5:
                    System.out.println("Gracias por usar el sistema");
                    break;

                default:
                    System.out.println("Opcion incorrecta");
                    break;
            }
        }
    }

   
    public void agregar() {

        if (nroUsuarios >= 100) {
            System.out.println("Memoria llena");
            return;
        }

        System.out.println("---- NUEVO USUARIO ----");

        System.out.print("Nombre: ");
        String nombre = input.nextLine();

        System.out.print("Edad: ");
        int edad = input.nextInt();

        System.out.print("Documento: ");
        int documento = input.nextInt();
        input.nextLine();

        usuarios[nroUsuarios] = new Persona(nombre, edad, documento);
        nroUsuarios++;

        System.out.println("Usuario agregado");
    }

  
    public void editar() {

        System.out.print("Indice del usuario: ");
        int pos = input.nextInt();
        input.nextLine();

        if (pos >= nroUsuarios) {
            System.out.println("No existe");
            return;
        }

        System.out.print("Nuevo nombre: ");
        usuarios[pos].setNombre(input.nextLine());

        System.out.print("Nueva edad: ");
        usuarios[pos].setEdad(input.nextInt());

        System.out.print("Nuevo documento: ");
        usuarios[pos].setDocumento(input.nextInt());
        input.nextLine();

        System.out.println("Actualizado");
    }


    public void verUsuarios() {

        System.out.println("---- LISTA ----");

        for (int i = 0; i < nroUsuarios; i++) {
            System.out.println("Indice: " + i);
            System.out.println("Nombre: " + usuarios[i].getNombre());
            System.out.println("Edad: " + usuarios[i].getEdad());
            System.out.println("Documento: " + usuarios[i].getDocumento());
            System.out.println("----------------");
        }
    }

   
    public void eliminar() {

        System.out.print("Indice a eliminar: ");
        int pos = input.nextInt();
        input.nextLine();

        if (pos >= nroUsuarios) {
            System.out.println("No existe");
            return;
        }

        for (int i = pos; i < nroUsuarios - 1; i++) {
            usuarios[i] = usuarios[i + 1];
        }

        nroUsuarios--;

        System.out.println("Eliminado");
    }

    
    public int menu() {

        System.out.println("\nMENU");
        System.out.println("1. Crear usuario");
        System.out.println("2. Editar usuario");
        System.out.println("3. Ver usuarios");
        System.out.println("4. Eliminar usuario");
        System.out.println("5. Salir");
        System.out.print("Opcion: ");

        int opcion = input.nextInt();
        input.nextLine();

        return opcion;
    }
}




        public class Persona {

    private String nombre;
    private int edad;
    private int documento;

    public Persona(String nombre, int edad, int documento) {
        this.nombre = nombre;
        this.edad = edad;
        this.documento = documento;
    }

    // SETTERS
    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public void setEdad(int edad) {
        this.edad = edad;
    }

    public void setDocumento(int documento) {
        this.documento = documento;
    }

    // GETTERS
    public String getNombre() {
        return nombre;
    }

    public int getEdad() {
        return edad;
    }

    public int getDocumento() {
        return documento;
    }
}

        return opcion;
    }
}
