# SupremeWaddle
School work and personal projects that I have done in the course of my life as a developer.. 
class Sistema_Alumnos:

	def __init__(self):
		self.alumnos=[]
#_______________________________________________________________________________________________________________________
	def menu(self):
		print("____________________________________________________________")
		menu=[["\n\tREGISTRO ALUMNOS I-SOFT-2"], ["\n\t[1] Registrar Alumno"], ["\t[2] Lista de Alumnos"], ["\t[3] Consultar"], ["\t[4] Editar Info"], ["\t[5] Calificaciones"], ["\t[6] Cerrar progrma"]]
		
		for q in range(7):
			print(menu[q][0])
		opcion=int(input("\nIntroduzca la opción deseada: "))
		if opcion==1:
			self.add()
		elif opcion==2:
			self.list()
		elif opcion==3:
			self.search()
		elif opcion==4:
			self.edit()
		elif opcion==5:
			self.cali()
		elif opcion==6:
			self.showc()
		elif opcion==7:
			print("Saliendo del programa ...")
			exit()
		else:
			print("\nOpcion incorrecta")
		self.menu()
#________________________________________________________________________________________________________________________
	def add(self):
		print("=====================\n  |Registro Alumno|\n======================")
		matri=int(input("Ingresa la matricula :I-SOFT-"))
		name=str(input("Ingresa el nombre(s): ")).title()
		apellidoP=str(input("Ingresa el Apellido Paterno: ")).title()
		apellidoM=str(input("Ingresa el Apellido Materno: ")).title()
		phone=int(input("Ingresa el teléfono: "))
		email=input("Ingresa el email: ")
		self.alumnos.append({'nombre':name, 'apellidoP':apellidoP, 'apellidoM':apellidoM,'matricula':matri, 'telefono':phone,'email':email})
		print("Alumno registrado correctamente")
#________________________________________________________________________________________________________________________
	def list(self):
		print("=====================\nLista de alumnos\n======================")
		if len(self.alumnos) == 0:
			print("No existe ningún alumno registrado en la agenda")
		else:
			for x in range(len(self.alumnos)):
				print(f"{self.alumnos[x]['nombre']} {self.alumnos[x]['apellidoP']} {self.alumnos[x]['apellidoM']}")
#__________________________________________________________________________________________________________________________				
	def search(self):
		print("Consultar alumno")
		name=input("Introduzca el nombre del Alumno: ").title()
		for y in range(len(self.alumnos)):
			if name == self.alumnos[y]['nombre']:
				print("\nDatos del Alumno")
				print(f"Nombre: {self.alumnos[y]['nombre']}\nNo. matricula: I-SOFT-{self.alumnos[y]['matricula']}\nTeléfono: {self.alumnos[y]['telefono']}\nE-mail: {self.alumnos[y]['email']}")
				return y
			else:
				print("Alumno inexiste")
#________________________________________________________________________________________________________________
	def edit(self):
		print("======================\n  Editar Info \n======================")
		dato=self.search()
		condition=False
		while condition==False:
			print("->Opciones para editar: \n1. Nombre\n2.Apellido P\n3.Apellido M\n4.No matricula\n5.Teléfono\n6.E-mail\n7.Volver")
			option=int(input("Ingresa la opción deseada: "))
			if option==1:
				name=input("Introduzca el nuevo nombre: ").title()
				self.alumnos[dato]['nombre']=name
			elif option==2:
				apellidoP=input("Introduzca el nuevo apellido P: ").title()
				self.alumnos[dato]['apellidoP']=apellidoP
			elif option==3:
				apellidoM=input("Introduzca el nuevo apellido M: ").title()
				self.alumnos[dato]['apellidoM']=apellidoM
			elif option==4:
				matricula=input("Introduzca el nueva matricula: I-SOFT-")
				self.alumnos[dato]['matricula']=matricula	
			elif option==5:
				phone=input("Introduzca el nuevo teléfono: ")
				self.alumnos[dato]['telefono']=phone
			elif option==6:
				email=input("Introduzca el nuevo email: ")
				self.alumnos[dato]['email']=email
			elif option==7:
				condition=True
			else:
				print("Opcion incorrecta")
#________________________________________________________________________________________________________________________
	def cali(self):
		print("======================\n  Agregar Calificaciones  \n======================")
		materias = ('Calculo Diferencial', 'Ingeniería de Software Asistida por Computadora (ISAC)', 'Desarrollo Humano y Valores', 'Programación Orientada a Objetos (POO)', 'Proceso de Desarrollo de Software', 'Estructura de Datos', 'Ingles')	
		calificaciones=()
		name=input("Introduzca el nombre del Alumno: ").title()
		for y in range(len(self.alumnos)):
			if name == self.alumnos[y]['nombre']:
				condition=False
				while condition==False:
					print("->Opciones de calificaciones: \n1. Agregar calificaciones\n2.Mostrar calificaciones\n3.Volver")
					option=int(input("Ingresa la opción deseada: "))
					if option==1:
						print(f"Escribe las calificaciones de las siguientes materias del alumno {name}")
						for materia in materias:
							calificacion = int(input(f'{materia:} '))
							calificaciones +=(calificacion,)
					elif option==2:
						print(f"\nCalificaciones  del Alumno {name}")
						for i in range(len(materias)):
							print(f"{i+1}.- {materias[i]}: {calificaciones[i]}")
					elif option==3:
						condition=True
					else:
						print("Opcion incorrecta")
			else:
				print("Alumno no registrado")
#-----------------------------------------------------------------------------------------------
# it doesn't working right in show califications from list self.calificaiones

#________________________________________________________________________________________________________________________

agenda=Sistema_Alumnos()
agenda.menu()
