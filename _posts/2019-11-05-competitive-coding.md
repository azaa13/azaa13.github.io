---
layout: post
title:  "Competitive programming: Task 1 - Easy (хялбар)түвшин"
date:   2019-11-5 20:49:00 0000
categories: competitive coding 
---

Сайн байцгаана уу уншигчдаа! ByteAcad coding энэ удаа competitive programming сурж байгаа болон бичиж байгаа хүмүүст зориулж кодинг даалгавар сонгон авч түүнийг хэрхэн бодож бүтэн оноо авах талаар бичихээр боллоо.
Манай бичвэр доорх хэсгүүдээс бүрдсэн байна.
1. Даалгавар буюу бодлого уншиж ойлгох хэсэг
2. Бодлогоо хэрхэн бодох тухай энгийн алгоритм зохиох хэсэг
3. Бодолтын хэсэг буюу алгоритмээ код болгон бичих
Бодлогоо Hackerrank-аас сонгон авсан бөгөөд хэрвээ өөрөө бодох сонирхолтой байгаа бол энд линкийг нь оруулая. https://www.hackerrank.com/challenges/designer-pdf-viewer/problem 
Task 1: Designer PDF viewer - Хялбар (easy) түвшний бодлого

1. Бодлого уншиж ойлгох хэсэг (өгөгдөл болон үр дүн)
PDF viewer дээр үгээ тодотгох(highlight)үед цэнхэр өнгөөр ялгарч харагддаг. Жишээ нь тодотгосон үг доорх байдлаар харагдана. 
Энэхүү даалгаварт англи хэлний цагаан толгойн үсэг бүрийн өндөр болон нэг үг өгөгдөнө. Тэдгээр үсэг бүрийн уртыг харгалзан тодотгосон үгийн mm2 area-г тооцох юм.
Жишээ нь: torn гэдэг үг өгөгдөж үсэг бүрийн урт нь t=2 o=1 r=1 n=1. Үүнээс хамгийн урт үсэг болох t=2, үгэнд нийт 4 үсэг орсон тул тодотгосон үгийн area нь 2*4=8mm2 болох юм.
Даалгавар:  designerPdfViewer(h, word) функц бичих. Тодотгосон үгийн area-г тоон утга (integer)буцаах

2. Энгийн алгоритм зохиох хэсэг
3. Алгоритмээ код болгон бичих

алгоритм-н кодоо python3 бичээд ```compile``` хийнэ.
{% highlight ruby %}
#!/bin/python3

import math
import os
import random
import re
import sys
import string

# Complete the designerPdfViewer function below.
def designerPdfViewer(h, word):
    alpha = list(string.ascii_lowercase)
    mapping_dict = dict()
    for i in range(len(alpha)):
        mapping_dict[alpha[i]] = h[i]
    #return mapping_dict

    values = []
    for i in range(len(word)):
        values.append(mapping_dict[word[i]])
    return max(values) * len(word)

{% endhighlight %}