# ToDo List

Creación de aplicación de gestión de tareas para la línea de comandos.

## Background

Proyecto correspondiente a sprint del bootcamp de NodeJS de la IT Academy.

## Usage

Gestión de tareas a través de menú en la línea de comandos.

Se ha realizado en TypeScript utilizando POO. La aplicaciónn principal correspondiente al archivo _/src/index.ts_ gestiona a través de las opciones que escoge el usuario, en el menú de línea de comandos, el _CRUD_ sobre las tareas.

## **Component/Classes**

Archivos de proyecto:

- index.ts \- Punto de entrada para la aplicación. Bucle de ejecución para opciones de menú.
- ToDoConfig.ts \- Importación y exportación de todas las classes y módulos comunes, de esta manera hacer mas limpio el código.

Descripción de las clases utilizadas:

### **Class UI (_User Interface_)**

Encargada de mostrar las interfaces y textos al usuario.

Para realizar el menú con la posibilidad de selección de opciones se ha utilizado el módulo **_inquirer_**, con el que se pueden crear diferentes tipos de _prompts_ dependiendo de las necesidades.

- **ARCHIVO:** **_/UI.ts_**

- **PROPIEDADES GLOBALES**

```TYPESCRIPT
    enum Commands {
        Add = "Añadir una nueva tarea",
        Update = "Actualizar tarea",
        Status = "Cambiar estado",
        ShowAll = "Mostrar todas las tareas",
        GetTask = "Mostrar detalle de tarea",
        Delete = "Borrar tarea",
        Quit = "Salir"
    };

    enum Status {
        pending = "Pendiente",
        executing = "En ejecución",
        finished = "Finalizada"
    };

    private commands = Commands;
    private status = Status;
    private first: boolean = true;
```

- **METODOS**

```TYPESCRIPT
  - async mainMenu(_userName: string): Promise<any>
  - showListTasks(_taskCollection: Array<Task>): void
  - async inputPrompt(_promptType: string, _promptName: string,_promptMessage: string): Promise<any>
  - async listPrompt(_promptType: string, _promptName: string, _promptMessage: string, _taskCollection: Array<Task>): Promise<any>
  - async statusListPrompt(_promptType: string, _promptName: string, _promptMessage: string, _selectedTaskId: number[], _taskCollection: Array<Task>): Promise<any>
  - async showTaskDetail(_task: Task): Promise<any>
  - show(_text: string): void
  - clearScreen(): void
```

### **Class TaskManager**

Encargada del CRUD de las tareas; **_Crear, Leer, Actualizar, Eliminar._**

- **ARCHIVO:** **_/TaskManager.ts_**

- **PROPIEDADES GLOBALES**

```TYPESCRIPT
    private taskCollection: Array<Task> = [];
```

- **METODOS**

```TYPESCRIPT
  - public constructor(_taskCollection: Array<Task>)
  - addTask(_taskName: string, _created_at: Date, _userName: string, _finished_at: Date | null): Array<Task>
  - updateTask(_taskId: number, _newTaskName: string): Array<Task>
  - deleteTask(_selectedTaskId: number[]): Array<Task>
  - getAllTasks(_userName: string): Array<Task>
  - changeStatus(_selectedTasksId: number[], _newStatus: string): Array<Task>
  - getTask(_taskId: number): Task
```

### **Class Task**

Clase de representación del modelo de datos para las tareas.

- **ARCHIVO:** **_/models/Task.ts_**

- **PROPIEDADES GLOBALES**

```TYPESCRIPT
    private id: number;
    private name: string;
    private created_at: Date;
    private status: string;
    private finished_at: Date | null = null;
    private userName: string;
```

- **METODOS**

```TYPESCRIPT
  -  constructor(_id: number, _name: string, _userName: string, _created_at: Date, _status: string, _finished_at: Date | null)
  - getId(): number
  - setName(_name: string): void
  - getName(): string
  - getCreatedDate(): Date
  - getFinishedDate(): Date | null
  - setFinishedDate(_date: Date | null): void
  - setStatus(_status: string): void
  - getStatus(): string
  - getUserName(): string
```

### **Class JSONDAO**

Clase de conexión con el método de persistencia de datos, en este caso un archivo JSON.

- **ARCHIVO:** **_/repository/JSONDAO.ts_**

- **PROPIEDADES GLOBALES**

```TYPESCRIPT
    private file: any;
    private path: string;
```

- **METODOS**

```TYPESCRIPT
  - constructor(_path: string)
  - getData(): Array<any>
  - saveData(_taskCollection: Array<Task>): void
```

## Installation

Para el correcto funcionamiento se requiere de los siguientes tecnologías:

1. NodeJS
2. TypeScript (módulo typescript - tsc)
3. Inquirer
4. Git

### Para poder instalar todo lo necesario hay que seguir los siguientes pasos:

### \# Clonar repositorio

```shell
git clone https://github.com/raulalhena/Todo-list-app.git
```

### \# Instalación modulos y dependencias

```shell
npm install
```

### \# Transpilación de TypeScript a JavaScript

```shell
npm run build
```

### \# Ejecución de la aplicación

```shell
npm run start
```

## Stack

1. NodeJS
2. TypeScript

## Contact info

Contactame a mi email: raul.alhena@gmail.com

## License

GNU General Public License v3.0
[GNU](https://opensource.org/licenses/GPL-3.0)
