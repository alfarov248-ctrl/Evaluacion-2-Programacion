class Empleado:
    def __init__(self, id_empleado: str, cargo: str, nombre: str, direccion: str, telefono: str, correo: str, fecha_inicio: str, salario: float):
        self.__id_empleado: str = id_empleado
        self.__cargo: str = cargo
        self.__nombre: str = nombre
        self.__direccion: str = direccion
        self.__telefono: str = telefono
        self.__correo: str = correo
        self.__fecha_inicio: str = fecha_inicio
        self.__salario: float = salario

    def CalcularSueldoLiquido(): float

    def RegistrarTiempo(proyecto: Proyecto, horas: float, descripcion: str):


class Proyecto:
    def __init__(self, id_proyecto: str, nombre_proyecto: str, descripcion: str, fecha_inicio: str, presupuesto: float):
        self.__id_proyecto: str = id_proyecto
        self.__nombre_proyecto: str = nombre_proyecto
        self.__descripcion: str = descripcion
        self.__fecha_inicio: str = fecha_inicio
        self.__presupuesto: float = presupuesto

    def CalcularPresupuesto():

    def AsignarEmpleado(Empleado):

class Departamento:
    def __init__(self, id_departamento: int, nombre: str, gerente_asociado: str):
        self.__id_departamento: int = id_departamento
        self.__nombre: str = nombre
        self.__gerente_asociado: str = gerente_asociado

    def CrearDepartamento():
        
    def AsignarEmpleado(Empleado):

    def ObtenerEmpleado(): list<Empleado>

class RegistrarTiempo:
    def __init__(self, id_registro: int, fecha: str, horas_trabajadas: float, descripcion_tarea: str):
        self.__id_registro: int = id_registro
        self.__fecha: str = fecha
        self.__horas_trabajadas: float = horas_trabajadas
        self.__descripcion_tarea: float = descripcion_tarea
