![](https://alumni.utpl.edu.ec/sites/default/files/logo.png)

# Programación Orientada a Objetos

# Código fuente de los archivos creados(Videojuego, Inventario, Main).

import pickle

class Videojuego:
            
    def __init__(self, titulo, plataforma, anioLanzamiento, precio):
        self.__titulo = titulo
        self.__plataforma = plataforma
        self.__anioLanzamiento = anioLanzamiento
        self.__precio = precio

    @property
    def titulo(self):
        return self.__titulo
    @property
    def plataforma(self):
        return self.__plataforma
    
    @titulo.setter
    def titulo(self, nuevo_titulo):
        self.__titulo = nuevo_titulo

    @property
    def precio(self):
        return self.__precio

    @precio.setter
    def precio(self, nuevo_precio):
        if nuevo_precio >= 0:
            self.__precio = nuevo_precio
        else:
            print("¡Error! El precio no puede ser negativo")

    def mostrar_info(self):
        print(f"Juego: {self.__titulo} | Consola: {self.__plataforma} | Precio: ${self.__precio}")

class Inventario:
    def __init__(self):
        self.__lista_videojuegos = []

    def agregar_videojuego(self, juego):
        self.__lista_videojuegos.append(juego)
          
    def listar_inventario(self):
             if not self.__lista_videojuegos:
                print("El inventario esta vacio")
                return
             for juego in self.__lista_videojuegos:
                juego.mostrar_info()
    def buscar_por_plataforma(self, plataforma_buscada):
                print(f"\n--- Buscando juegos de: {plataforma_buscada}---")
                encontrado= False

                for juego in self.__lista_videojuegos:
                    if juego.plataforma.lower()== plataforma_buscada.lower():
                       juego.mostrar_info()
                    encontrado = True
                    if not encontrado:
                     print(f"No se encontraron juegos para la consola {plataforma_buscada}.")
    def guardar_datos(self, nombre_archivos):
        try:
            with open(nombre_archivos,"wb")as archivo:
                 pickle.dump(self.__lista_videojuegos, archivo)
            print(f"[SISTEMA] Datos guardados con éxito en {nombre_archivos}")
        except Exception as e:
            print(f"[ERROR] No se pudo guardar: {e}")
    def cargar_datos(self, nombre_archivo):
        try:
            
            with open(nombre_archivo, "rb") as archivo:
                # pickle.load lee el archivo y reconstruye la lista original
                self.__lista_videojuegos = pickle.load(archivo)
            print(f"[SISTEMA] Datos cargados con éxito desde {nombre_archivo}")
        except FileNotFoundError:
            print(f"[AVISO] No se encontró el archivo {nombre_archivo}. Iniciando vacío.")
        except Exception as e:
            print(f"[ERROR] Error al cargar: {e}")

        
if __name__ == "__main__":
    print("=== PASO 1: Creando el inventario original ===")
    inventario_original = Inventario()

    print("\n=== PASO 2: Ingresar datos del videojuego por teclado ===")
    
    # 1. Capturamos los datos desde la consola
    print("Por favor, ingrese los datos del nuevo videojuego:")
    titulo_usuario = input("-> Título: ")
    plataforma_usuario = input("-> Plataforma (ej: NES, SEGA): ")
    
    anio_usuario = int(input("-> Año de lanzamiento: "))
    
    precio_usuario = float(input("-> Precio: "))

    juego_usuario = Videojuego(titulo_usuario, plataforma_usuario, anio_usuario, precio_usuario)

    print("\n=== PASO 3: Agregando el juego al inventario ===")
    inventario_original.agregar_videojuego(juego_usuario)

    print("\n=== PASO 4: Mostrando el inventario inicial ===")
    inventario_original.listar_inventario()

    print("\n=== PASO 5: Guardando en 'inventario.dat' ===")
    inventario_original.guardar_datos(r"C:\Users\ASUS\Desktop\POO\inventario.dat")

    print("\n" + "="*50)
    print("=== PASO 6: Simulando reinicio (Nuevo inventario vacío) ===")
    print("="*50)
    nuevo_inventario = Inventario()
    
    print("\nVerificando que el nuevo inventario está vacío:")
    nuevo_inventario.listar_inventario()

    print("\n=== PASO 7: Cargando datos desde 'inventario.dat' ===")
    nuevo_inventario.cargar_datos(r"C:\Users\ASUS\Desktop\POO\inventario.dat")

    print("\n=== PASO 8: Listando el nuevo inventario recuperado ===")
    nuevo_inventario.listar_inventario()

### El archivo binario generado por el programa (inventario.dat).
El archivo binario generado por el programa es `inventario.dat`.
<img width="1412" height="821" alt="image" src="https://github.com/user-attachments/assets/3acd9bc5-ae72-4ae8-a032-f39f8d580d87" />
### Un reporte en formato PDF o markdown que incluya capturas de pantalla de la consola demostrando el proceso de guardado y posterior carga de los datos.


[Reporte_Taller_POO_LuisMiguel_v2.docx](https://github.com/user-attachments/files/28114101/Reporte_Taller_POO_LuisMiguel_v2.docx)

    
    
