#1
class Task:
    def __init__(self, title, description, deadline):
        self.title = title
        self.description = description
        self.deadline = deadline
        self.completed = False

    def mark_completed(self):
        self.completed = True

    def __str__(self):
        status = "Зделано" if self.completed else "не зделано"
        return f"{self.title} - {self.description} (Дедлайн: {self.deadline}) [{status}]"

class TaskManager:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append(task)

    def remove_task(self, title):
        self.tasks = [task for task in self.tasks if task.title != title]

    def mark_tasl_completed(self, title):
        for task in self.tasks:
            if task.title == title:
                task.mark_completed()
                return True
            return False

    def list_tasks(self):
        if not self.tasks:
            print("Список порожній ;(")
        for task in self.tasks:
            print(task)

task_manager = TaskManager()
task1 = Task("Прибрати дім", "Пропилососити і помити підлогу", "2025-02-25")
task2 = Task("Написати код", "Закінчити проект", "2025-02-26")

task_manager.add_task(task1)
task_manager.add_task(task2)
task_manager.mark_tasl_completed("Прибрати дім")
task_manager.list_tasks()


#2
print(10 * "--------------------")




class Product:
    def __init__(self, name, price, stock):
        self.name = name
        self.price = price
        self.stock = stock

    def __str__(self):
        return f"{self.name}: {self.price} грн (в наявності: {self.stock})"


class Cart:
    def __init__(self):
        self.items = {}

    def add_product(self, product, quantity):
        if product.stock >= quantity:
            self.items[product] = self.items.get(product, 0) + quantity
            product.stock -= quantity
        else:
            print(f"Недостатньо товару: {product.name}")

    def remove_product(self, product):
        if product in self.items:
            product.stock += self.items[product]
            del self.items[product]

    def total_price(self):
        return sum(product.price * qty for product, qty in self.items.items())

    def show_cart(self):
        if not self.items:
            print("Кошик порожній.")
        else:
            for product, qty in self.items.items():
                print(f"{product.name} - {qty} шт.")

##############
p1 = Product("часи", 1400, 7)
p2 = Product("nokia3310", 15000, 5)

cart = Cart()
cart.add_product(p1, 1)
cart.add_product(p2, 2)
cart.show_cart()
print(f"Загальна вартість: {cart.total_price()} грн")
print(10 * "--------------------")
#ну тут должно бить 3 но тут технические неполадки ми запутались если в краце
#месяц назад 3 начал и не закончил шас даже не понял ни одной строчки там а их там 217
# так што вот вам 4
print(10 * "---------------")
# 4                ###############################

class Employee:
    def __init__(self, name, position, salary):
        self.name = name
        self.position = position
        self.salary = salary


    def __str__(self):
        return f"{self.name} - {self.position}, Зарплата: {self.salary} грн"

class Departement:
    def __init__(self, name):
        self.name = name
        self.employees = []

    def add_employe(self, employe):
        self.employees.append(employe)

    def remove_employee(self, name):
        self.employees = [emp for emp in self.employees if emp.name != name]

    def total_salary(self):
        return sum(emp.salary for emp in self.employees)

    def list_employees(self):
        if not self.employees:
            print("Тут никого нет ;(")
        for emp in self.employees:
            print(emp)

dep = Departement("IT Відділ")
emp1 = Employee("Максим", "Програміст", 31000)
emp2 = Employee("Іван", "Тестувальник", 27000)

dep.add_employe(emp1)
dep.add_employe(emp2)
dep.list_employees()
print(f"Загальна зарплата відділу: {dep.total_salary()} грн")
