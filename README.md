### Задание: Реализация очереди задач

Цель этого задания - создать программу для управления задачами с использованием структуры данных "очередь". Задачи будут представлены в виде объектов, и программа должна поддерживать операции добавления задачи в очередь, извлечения задачи из очереди и проверки состояния очереди.

#### Требования:

1. Создайте класс TaskQueue, который будет представлять очередь задач. Этот класс должен иметь следующие методы:
- add_task(task): Добавляет задачу task в конец очереди.
- get_next_task(): Извлекает и возвращает задачу из начала очереди. Если очередь пуста, вернуть None.
- is_empty(): Проверяет, пуста ли очередь. Возвращает True, если очередь пуста, и False в противном случае.
2. Создайте класс Task, который будет представлять задачу. Этот класс должен иметь атрибут:
- name: Название задачи (строка).
3. Реализуйте логику работы с задачами в соответствии с их добавлением и извлечением из очереди.

### Код решения задачи:

````
    class Task:
    def __init__(self, name):
        self.name = name

    def __repr__(self):
        return f"Task('{self.name}')"


class TaskQueue:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        if not isinstance(task, Task):
            raise TypeError("Можно добавлять только через объект")
        self.tasks.append(task)

    def get_next_task(self):
        if self.is_empty():
            return None
        return self.tasks.pop(0)

    def is_empty(self):
        return len(self.tasks) == 0
````

### Примеры тестовых данных и ожидаемых результатов:
```` 
   queue = TaskQueue()

task1 = Task("Задача 1")
task2 = Task("Задача 2")
task3 = Task("Задача 3")

queue.add_task(task1)
queue.add_task(task2)
queue.add_task(task3)

next_task = queue.get_next_task()
print(f"Следующая задача: {next_task.name if next_task else 'Нет задач'}")

queue.get_next_task()

print(f"Очередь пуста: {queue.is_empty()}")
````