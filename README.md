#------------------------------------Задача 36---------------------------------
: Напишите функцию print_operation_table(operation, num_rows=6, num_columns=6),
#которая принимает в качестве аргумента функцию, вычисляющую элемент по номеру строки и столбца.
#Аргументы num_rows и num_columns указывают число строк и столбцов таблицы, которые должны быть распечатаны.
#Нумерация строк и столбцов идет с единицы (подумайте, почему не с нуля).
#Примечание: бинарной операцией называется любая операция, у которой ровно два аргумента, как, например,
#у операции умножения.
#Пример:
#Ввод:`print_operation_table(lambda x, y: x * y) `
#Вывод:
#1 2 3 4 5 6
#2 4 6 8 10 12
#3 6 9 12 15 18
#4 8 12 16 20 24
#5 10 15 20 25 30
#6 12 18 24 30 36

def print_operation_table(operation, num_rows=6, num_columns=6):
 
    header = "   |" + "|".join(f" {i:2}" for i in range(1, num_columns + 1)) + " "
    separator = "---+" + "+".join("---" for i in range(num_columns)) + "-"
    
    print(header)
    print(separator)
    
    for i in range(1, num_rows + 1):
        row = f" {i:2}|"
        for j in range(1, num_columns + 1):
            row += f"{operation(i, j):3}|"
        print(row)
        print(separator)
def multiply(x, y):
    return x * y
print_operation_table(multiply, num_rows=6, num_columns=6)

#------------------------------------Задача 34---------------------------------
:  Винни-Пух попросил Вас посмотреть, есть ли в его стихах ритм. 
#Поскольку разобраться в его кричалках не настолько просто, насколько легко 
#он их придумывает, Вам стоит написать программу. Винни-Пух считает, что ритм есть, 
#если число слогов (т.е. число гласных букв) в каждой фразе стихотворения одинаковое. 
#Фраза может состоять из одного слова, если во фразе несколько слов, то они разделяются 
#дефисами. Фразы отделяются друг от друга пробелами. Стихотворение  Винни-Пух вбивает в 
#программу с клавиатуры. В ответе напишите “Парам пам-пам”, если с ритмом все в порядке и
# “Пам парам”, если с ритмом все не в порядке
#**Ввод:** пара-ра-рам рам-пам-папам па-ра-па-да    
#**Вывод:** Парам пам-пам

print("Ввод: пара-ра-рам рам-пам-папам па-ра-па-да Вывод: Парам пам-пам")
line = input("Введите строку :")
lines = line.split()
 
print(lines)
 
lst = [sum(x in 'уеыаоэяию' for x in lin)
 for lin in lines]
 
if len(set(lst)) == 1 :
    res = "Парам пам-пам"  
else: 
    res = "Пам парам"
 
print(res)

-----------------------------------чат бот----------------
from random import *
import json 

als=[]

def save():
    with open("als.joson", "w", encoding="utf-8")as fh:
        fh.write(json.dumps(als,ensure_ascii=False))#выгружает все садержимое
        print("Сохранен  в фаиле als.joson")

def load():
    with open("als.joson", "r", encoding="utf-8")as fh:
        als=json.load(fh)
    print("Бибилиотека загружена ")

try:
    with open("als.joson", "r", encoding="utf-8")as fh:
         als=json.load(fh)
    print("Бибилиотека загружена ")

except:
    als.append("Собрать документы", )
    als.append("Командираовка", )


print("!ALS IS WORK! ")
while True:
    print("Паланируем на сегодня или на дату ?")
    command=input("ВВедите команду :")
    if command=="старт":
        print("Бот начал свою работу")
    elif command=="стоп":
        save()
        print("Бот end свою работу")
        break
    elif command=="список":
        print(als)
    elif command=="дату":
        f=input("Что делаем и когда ? :")
        als.append(f)
        print("Запись добавлен ")
    elif command == "сегодня":
        a=input("Что делаем :")
        als.append(a)
        print("Запись добавлен ")
    elif command=="уд":
        print("Список : ", als)
        f=input("ВВедите запись для удоления  :")
        try:
            als.remove(f)
            print("Запись удален ")
        except:
            print("нет такой записи")

    elif command=="сох":
        save()
    elif command=="/load":
       with open("als.joson", "r", encoding="utf-8")as fh:
           als=json.load(fh)
           print("Бибилиотека загружена ")
    elif command=="кол":
        print("Запланирова дел :", len(als))
    else:
        print("Команда не верная")



