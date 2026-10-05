from typing import List
from datetime import date

class RegistrarTiempo:
    # Atributos privados según el diagrama, más las referencias de las multiplicidades (*)
    def __init__(self, id_registro: int, fecha: date, horas_trabajadas: float, descripcion_tarea: str, empleado: 'Empleado', proyecto: 'Proyecto'):
        self.__id_registro: int = id_registro
        self.__fecha: date = fecha
        self.__horas_trabajadas: float = horas_trabajadas
        self.__descripcion_tarea: str = descripcion_tarea
        self.__empleado: 'Empleado' = empleado
        self.__proyecto: 'Proyecto' = proyecto

    def ObtenerDetalleRegistro(self) -> str:
        # Retorna el detalle del registro vinculando al empleado y proyecto
        return f"Registro {self.__id_registro} | Fecha: {self.__fecha} | Horas: {self.__horas_trabajadas} | Tarea: {self.__descripcion_tarea}"


class Proyecto:
    def __init__(self, id_proyecto: str, nombre_proyecto: str, descripcion: str, fecha_inicio: date, presupuesto: float):
        self.__id_proyecto: str = id_proyecto
        self.__nombre_proyecto: str = nombre_proyecto
        self.__descripcion: str = descripcion
        self.__fecha_inicio: date = fecha_inicio
        self.__presupuesto: float = presupuesto
        self.__empleados_asignados: List['Empleado'] = []

    def CalcularPresupuesto(self) -> float:
        # Lógica para devolver el presupuesto
        return self.__presupuesto

    def AsignarEmpleado(self, empleado: 'Empleado') -> None:
        if empleado not in self.__empleados_asignados:
            self.__empleados_asignados.append(empleado)


class Empleado:
    def __init__(self, id_empleado: str, cargo: str, nombre: str, direccion: str, telefono: str, coorreo: str, fecha_inicio: date, salario: float):
        self.__id_empleado: str = id_empleado
        self.__cargo: str = cargo
        self.__nombre: str = nombre
        self.__direccion: str = direccion
        self.__telefono: str = telefono
        self.__coorreo: str = coorreo  # Escrito tal como aparece en el diagrama
        self.__fecha_inicio: date = fecha_inicio
        self.__salario: float = salario
        self.__registros: List[RegistrarTiempo] = []
        self.__proyectos: List[Proyecto] = []

    def CalcularSueldoLiquido(self) -> float:
        # Lógica de ejemplo para el cálculo de sueldo
        return self.__salario * 0.80

    def RegistrarTiempo(self, proyecto: Proyecto, horas: float, descripcion: str) -> None:
        # Instancia la clase RegistrarTiempo conectando el empleado actual (self) y el proyecto
        nuevo_registro = RegistrarTiempo(
            id_registro=len(self.__registros) + 1, 
            fecha=date.today(), 
            horas_trabajadas=horas, 
            descripcion_tarea=descripcion, 
            empleado=self, 
            proyecto=proyecto
        )
        self.__registros.append(nuevo_registro)


class Departamento:
    def __init__(self, id_departamento: int, nombre: str, gerente_asociado: str):
        self.__id_departamento: int = id_departamento
        self.__nombre: str = nombre
        self.__gerente_asociado: str = gerente_asociado
        self.__empleados: List[Empleado] = []

    def CrearDepartamento(self) -> None:
        # Lógica para inicializar/persistir en base de datos
        print(f"Departamento '{self.__nombre}' creado exitosamente.")

    def AsignarEmpleado(self, empleado: Empleado) -> None:
        if empleado not in self.__empleados:
            self.__empleados.append(empleado)

    def ObtenerEmpleado(self) -> List[Empleado]:
        # Devuelve la lista de empleados asignados, respetando el nombre singular del método en el diagrama
        return self.__empleados
