#Python

import csv


month_and_code = []
count_month = [0] * 12
with open('rocket.csv', encoding='utf8',) as file:
    reader = list(csv.DictReader(file))
    for row in reader:
        month_and_code.append([row['date'][5:7], row['code']])
    for el in month_and_code:
        count_month[int(el[0]) - 1] += 1
    """Создание списка месяцев с количеством шифров, полученных в данный месяц
    row - сторка в .csv файле
    month_and_code - список месяцев и шифров из файла .csv
    count_month - список содержащий 12 чисел - количество шифров в соответствующий месяц"""

with open('rocket_part.txt', 'w', encoding='utf8') as f:
    writer = csv.writer(f)
    k = 1
    for i in count_month:
        m = str(k)
        if len(m) == 1: m = '0' + m
        writer.writerow(f'В {m} было получено - {i} шифров')
        k += 1

        """
        writer.writerow - функция, записывающая ответ в новый .txt файл
        m - номер месяца
        k - счётчик
        """

