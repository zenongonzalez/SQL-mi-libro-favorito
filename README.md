
class Libro:

    def __init__(self,titulo,autor,numero_paginas):
        self.titulo = titulo
        self.__calificacion = None
        self.autor = autor
        self.numero_paginas = numero_paginas

    def set_calificacion(self,calificacion):
        if calificacion >= 0 and calificacion <= 10:
            self.__calificacion = calificacion
        else:
            print('Rango de calificacion incorrecto')

    def get_calificacion(self):
        return self.__calificacion

class ConjuntoLibros:

    def __init__(self,capacidad):
        self.capacidad = capacidad
        self.libros = []
        self.mejor = None
        self.peor = None


    def agregar_libro(self,libro):
        if len(self.libros) < self.capacidad:
            self.libros.append(libro)
            print('El libro ha sido agregado con éxito!')
            if self.peor == None or libro.get_calificacion() < self.peor.get_calificacion() : 
                self.peor = libro
            if self.mejor == None or libro.get_calificacion() > self.mejor.get_calificacion() :
                self.mejor = libro
        else:
            print('No hay más espacio')

    def get_peor(self):
        return self.peor

    def get_mejor(self):
        return self.mejor

    def eliminar_libro_por_titulo(self,titulo):
        lista_nueva = []
        for libro in self.libros:
            if libro.titulo != titulo:
                lista_nueva.append(libro)
            else:
                print(f'Se eliminó {libro.titulo}')
        self.libros = lista_nueva

    def eliminar_libro_por_autor(self,autor):
        lista_nueva = []
        for libro in self.libros:
            if libro.autor != autor:
                lista_nueva.append(libro)
            else:
                print(f'Se eliminó {libro.autor}')
        self.libros = lista_nueva

    def mostrar_contenido(self):
        if not self.libros :
            print('No hay libros cargados')
        else:
            for libro in self.libros:
                print(f'Titulo: {libro.titulo}\nAutor: {libro.autor}\nCalificacion: {libro.get_calificacion()}\nCantidad de paginas: {libro.numero_paginas}\n----------------')

libro1 = Libro('It','Stephen King',1300)
libro1.set_calificacion(9.4)
libro2 = Libro('The Hobbit','autor',300)
libro2.set_calificacion(10)
libro3 = Libro('Harry Potter', 'J.K.Rowling', 500)
libro3.set_calificacion(5)

conjunto_libros = ConjuntoLibros(4)
conjunto_libros.agregar_libro(libro1)
conjunto_libros.agregar_libro(libro2)
conjunto_libros.agregar_libro(libro3)

print(conjunto_libros.get_peor().titulo)
print(conjunto_libros.get_mejor().titulo)

conjunto_libros.mostrar_contenido()

# SQL-mi-libro-favorito
prueba de ejercicios
