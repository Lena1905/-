"""
Задание 1.

Реализовать класс «Дата», конструктор которого должен принимать дату
в виде строки формата «день-месяц-год».

В рамках класса реализовать два метода.

Первый, с декоратором @classmethod, должен извлекать число, месяц,
год и преобразовывать их тип к типу «Число».

Второй, с декоратором @staticmethod, должен проводить валидацию числа, месяца
и года (например, месяц — от 1 до 12). Проверить работу полученной структуры на реальных данных.
"""


class Data:

    day_month_year = "11 - 1 - 2020"

    @classmethod
    def extract(cls):
        my_date = [int(el) for el in cls.day_month_year.split() if el != '-']
        cls.day, cls.month, cls.year = my_date

    @staticmethod
    def valid():

        if 1 <= Data.day <= 31:
            if 1 <= Data.month <= 12:
                if 2020 >= Data.year >= 0:
                    return f"Все в порядке"
                else:
                    return f"Неправильный год"
            else:
                return f"Неправильный месяц"
        else:
            return f"Неправильный день"


Data.extract()
print(Data.valid())

class ComplexNumber:

    def __init__(self, real, imaginary):
        self.real = real
        self.imaginary = imaginary

    def __add__(self, other):
        return ComplexNumber(self.real + other.real, self.imaginary + other.imaginary)

    def __mul__(self, other):
        return ComplexNumber((self.real * other.real - self.imaginary * other.imaginary),
                             (self.real * other.imaginary + other.real * self.imaginary))

    def __str__(self):
        return f'{self.real}{"+" if self.imaginary > 0 else ""}{self.imaginary}i'


cn_1 = ComplexNumber(1, -2)
cn_2 = ComplexNumber(3, 4)

print(cn_1 + cn_2)
print(cn_1 * cn_2)


class MyOwnExc(Exception):
    def __init__(self, txt):
        self.txt = txt


num_lst = []
while True:
    try:
        elem = input("Введите число или stop для завершения: ")
        if elem == 'stop':
            break
        elif elem.isdigit():
            num_lst.append(int(elem))
        else:
            raise MyOwnExc("Вы ввели не число")
    except MyOwnExc as e:
        print(e.txt)

print(num_lst)


class MyOwnExc(Exception):
    def __init__(self, txt):
        self.txt = txt


class OfficeEquipment:
    def __init__(self, name, price, quantity, number_of_lists):
        self.name = name
        self.price = price
        self.numb = number_of_lists
        try:
            if isinstance(quantity, int):

                self.quantity = quantity

                self.my_unit = {
                    'Модель устройства': self.name,
                    'Цена за ед': self.price,
                    'Количество': self.quantity}
            else:
                self.my_unit = {}
                raise MyOwnExc("Вы ввели не число, словарь будем пустым")

        except MyOwnExc as e:
            print(e.txt)


class Warehouse:
    goods = []

    @classmethod
    def reception(cls, obj):
        cls.goods.append(obj.my_unit)

    @classmethod
    def put_to_div(cls, obj, div):
        pass


class Printer(OfficeEquipment):
    def to_print(self):
        return f'to print smth {self.numb} times'


class Scanner(OfficeEquipment):
    def to_scan(self):
        return f'to scan smth {self.numb} times'


class Copier(OfficeEquipment):
    def to_copier(self):
        return f'to copier smth  {self.numb} times'


unit_1 = Printer('hp', 2000, 5, 10)
unit_2 = Scanner('Canon', 1200, 5, 10)
Warehouse.reception(unit_1)
Warehouse.reception(unit_2)

print(Warehouse.goods)

print(unit_2.to_scan())

class ComplexNumber:

    def __init__(self, real, imaginary):
        self.real = real
        self.imaginary = imaginary

    def __add__(self, other):
        return ComplexNumber(self.real + other.real, self.imaginary + other.imaginary)

    def __mul__(self, other):
        return ComplexNumber((self.real * other.real - self.imaginary * other.imaginary),
                             (self.real * other.imaginary + other.real * self.imaginary))

    def __str__(self):
        return f'{self.real}{"+" if self.imaginary > 0 else ""}{self.imaginary}i'


cn_1 = ComplexNumber(1, -2)
cn_2 = ComplexNumber(3, 4)

print(cn_1 + cn_2)
print(cn_1 * cn_2)# -
