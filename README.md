```assembly
using System;

class Program
{
    const int MaxAlumnos = 100;
    string[] codigos = new string[MaxAlumnos];
    string[] nombres = new string[MaxAlumnos];
    DateTime[] fechasNacimiento = new DateTime[MaxAlumnos];
    string[] grados = new string[MaxAlumnos];
    int[] aniosRegistro = new int[MaxAlumnos];
    int cantidadAlumnos = 0;

    static void Main(string[] args)
    {
        int opcion;
        Program programa = new Program();

        do
        {
            Console.WriteLine("Menú Principal");
            Console.WriteLine("1. Agregar un alumno");
            Console.WriteLine("2. Mostrar listado de alumnos");
            Console.WriteLine("3. Buscar alumno por código");
            Console.WriteLine("4. Editar información de un alumno por código");
            Console.WriteLine("5. Salir");
            Console.Write("Elija una opción: ");
            opcion = int.Parse(Console.ReadLine());

            switch (opcion)
            {
                case 1:
                    programa.AgregarAlumno();
                    break;
                case 2:
                    programa.MostrarListadoAlumnos();
                    break;
                case 3:
                    programa.BuscarAlumnoPorCodigo();
                    break;
                case 4:
                    programa.EditarAlumnoPorCodigo();
                    break;
                case 5:
                    Console.WriteLine("Saliendo del programa.");
                    break;
                default:
                    Console.WriteLine("Opción no válida. Intente de nuevo.");
                    break;
            }

        } while (opcion != 5);
    }

    void AgregarAlumno()
    {
        if (cantidadAlumnos < MaxAlumnos)
        {
            Console.Write("Código del alumno: ");
            codigos[cantidadAlumnos] = Console.ReadLine();

            Console.Write("Nombre completo del alumno: ");
            nombres[cantidadAlumnos] = Console.ReadLine();

            Console.Write("Fecha de nacimiento (yyyy-MM-dd): ");
            fechasNacimiento[cantidadAlumnos] = DateTime.Parse(Console.ReadLine());

            Console.Write("Grado del alumno: ");
            grados[cantidadAlumnos] = Console.ReadLine();

            Console.Write("Año de registro: ");
            aniosRegistro[cantidadAlumnos] = int.Parse(Console.ReadLine());

            cantidadAlumnos++;
        }
        else
        {
            Console.WriteLine("Se ha alcanzado el límite de alumnos (100).");
        }
    }

    void MostrarListadoAlumnos()
    {
        Console.WriteLine("Listado de Alumnos:");
        Console.WriteLine("Código | Nombre | Fecha Nacimiento | Grado | Año de Registro");
        for (int i = 0; i < cantidadAlumnos; i++)
        {
            Console.WriteLine($"{codigos[i]} | {nombres[i]} | {fechasNacimiento[i]:yyyy-MM-dd} | {grados[i]} | {aniosRegistro[i]}");
        }
    }

    void BuscarAlumnoPorCodigo()
    {
        Console.Write("Ingrese el código del alumno a buscar: ");
        string codigoBuscado = Console.ReadLine();
        bool encontrado = false;

        for (int i = 0; i < cantidadAlumnos; i++)
        {
            if (codigos[i] == codigoBuscado)
            {
                Console.WriteLine("Alumno encontrado:");
                Console.WriteLine($"Código: {codigos[i]}");
                Console.WriteLine($"Nombre: {nombres[i]}");
                Console.WriteLine($"Fecha de Nacimiento: {fechasNacimiento[i]:yyyy-MM-dd}");
                Console.WriteLine($"Grado: {grados[i]}");
                Console.WriteLine($"Año de Registro: {aniosRegistro[i]}");
                encontrado = true;
                break;
            }
        }

        if (!encontrado)
        {
            Console.WriteLine("Alumno no encontrado.");
        }
    }

    void EditarAlumnoPorCodigo()
    {
        Console.Write("Ingrese el código del alumno a editar: ");
        string codigoBuscado = Console.ReadLine();
        bool encontrado = false;

        for (int i = 0; i < cantidadAlumnos; i++)
        {
            if (codigos[i] == codigoBuscado)
            {
                Console.WriteLine("Editar información del alumno:");
                Console.Write("Nuevo Nombre: ");
                nombres[i] = Console.ReadLine();

                Console.Write("Nueva Fecha de Nacimiento (yyyy-MM-dd): ");
                fechasNacimiento[i] = DateTime.Parse(Console.ReadLine());

                Console.Write("Nuevo Grado: ");
                grados[i] = Console.ReadLine();

                Console.Write("Nuevo Año de Registro: ");
                aniosRegistro[i] = int.Parse(Console.ReadLine());

                Console.WriteLine("Información del alumno actualizada.");
                encontrado = true;
                break;
            }
        }

        if (!encontrado)
        {
            Console.WriteLine("Alumno no encontrado.");
        }
    }
}

```
