# Tkach_Anna
* Импортирование библиотеки pymorphy2
* Считывание текста
* Разделение
* Морфологический анализ
  * Простой разбор
  * Норма
  * Склонение
  * Лексемы
* Запись в файл
Определяет слово "потом"(существительное в твор. падеже) как  **потом(наречие)**.
Вместо род.падежа выводит *None*
![alt text](http://illustrators.ru/uploads/illustration/image/1001658/main_вино_из_одуванчиков.jpg)


[Читать](https://www.litmir.me/br/?b=85288&p=1)

:+1:  :blossom: :honeybee:


import pymorphy2

text = """Они сидели на траве, уплетали сандвичи с ветчиной, свежую клубнику и яркие, блестящие, точно восковые, апельсины,
 и Тридден рассказывал, как много лет назад тут по вечерам на разукрашенной эстраде играл оркестр:
  музыканты изо всех сил трубили в медные трубы, толстенький дирижер, обливаясь потом, усердно размахивал палочкой;
в высокой траве гонялись друг за другом ребятишки и мелькали светлячки, а по дощатым мосткам, постукивая каблуками,
 будто играя на ксилофоне, расхаживали дамы в длинных платьях с высокими стоячими воротниками
 и мужчины в таких тесных накрахмаленных воротничках, что того и гляди задохнутся.
Вот они, остатки этих мостков, только за долгие годы доски сгнили и превратились в какое – то деревянное месиво
Озеро лежало молчаливое, голубое и безмятежное, рыба медленно плескалась в блестящих камышах, а вагоновожатый все говорил и говорил,
 и детям казалось, что они перенеслись в какое – то иное время, и мистер Тридден стал вдруг на диво молодой, а глаза у него горят,
  как голубые электрические лампочки.
День проплывал сонно, бестревожно, никто никуда не спешил, со всех сторон их обступал лес,
 и даже солнце словно остановилось на одном месте, а голос Триддена поднимался и падал,
 и стрекозы сновали в воздухе, рисуя золотые невидимые узоры.
Пчела забралась в цветок и жужжит, жужжит…
Трамвай стоял молчаливый, точно заколдованный орган, поблескивая в солнечных лучах.
Ребята ели спелые вишни, а на руках у них все еще держался медный запах трамвая.
И когда теплый ветерок шевелил на них одежду, от нее тоже остро пахло трамваем.
"""

text_split = text.split(" ")

morphy = pymorphy2.MorphAnalyzer()

for i in text_split:

    parse = morphy.parse(i) [0]
    
    result = parse.normalized
    
    sklon = parse.inflect({"gent"})
    
    lex = parse.lexeme
   
    print("Простой разбор: ", parse)
    
    print("Нормализовано: ", result)
    
    print("Склонение в родительном: ", sklon)
    
    print("Лексемы: ", lex)
    
file = open ("itog.txt", "w")

file.write(str(parse))
