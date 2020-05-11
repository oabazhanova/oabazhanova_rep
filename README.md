# oabazhanova_rep

import numpy as np

def game_core_my(number):
    '''Устанавливаем число в середине диапазона поиска, смещаем диапазон в зависимости от того, больше наше число или меньше нужного.
       Функция принимает загаданное число и возвращает число попыток'''
    count = 1
    minimum = 1                              #задаем начальный минимум диапазона 
    maximum = 100                            #задаем начальный максимум диапазона
    predict = (minimum + maximum)//2         #начальное число в середине диапазона
    while number != predict:
        count+=1
        if number > predict:                 #если искомое число больше нашего
            minimum = predict                #меняем минимум диапазона поиска на наше число 
        elif number < predict:               #если искомое число меньше нашего
            maximum = predict                #меняем максимум диапазона поиска на наше число
        predict = (minimum + maximum)//2     #новое число устанавливаем в середину нового диапазона
    return(count)                            #выход из цикла, если угадали
                
def score_game(game_core):
    '''Запускаем игру 1000 раз, чтобы узнать, как быстро игра угадывает число'''
    count_ls = []
    np.random.seed(1)
    random_array = np.random.randint(1,101, size=(10))
    for number in random_array:
        count_ls.append(game_core(number))
    score = int(np.mean(count_ls))
    return(print(f"Ваш алгоритм угадывает число в среднем за {score} попыток"))

score_game(game_core_my)

#Ваш алгоритм угадывает число в среднем за 5 попыток
