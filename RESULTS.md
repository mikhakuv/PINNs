### Итоги:
* Проблема с z0 была в функции активации(была tanh, теперь будет sin)(см [exp3](https://github.com/mikhakuv/PINNs/blob/main/exp3.md)), остальные изменения заметных положительных эффектов не дали(cм [exp4](https://github.com/mikhakuv/PINNs/blob/main/exp4.md), [exp5](https://github.com/mikhakuv/PINNs/blob/main/exp5.md)).
* Решение всё ещё плохо продолжается на большие t, а если и продолжается, то почему-то идёт ниже, чем нужно(см [exp6](https://github.com/mikhakuv/PINNs/blob/main/exp6.md)).
* Soft Adapt тоже не очень помог, коэффициенты просто постепенно приравниваются(см [exp7](https://github.com/mikhakuv/PINNs/blob/main/exp7.md)).
* Что интересно, при lr=1e-4 и ниже сеть вроде учится, loss уменьшается, но на выходе получается какая-то странная фигня, не похожая ни на константу ни на аналитическое решение(см [exp8](https://github.com/mikhakuv/PINNs/blob/main/exp8.md)).
---
* Чтобы получить хорошие результаты нужно было поправить процесс обучения и использовать 100000 итераций оптимизатора ADAM с убывающим lr(см [exp9](https://github.com/mikhakuv/PINNs/blob/main/exp9.md))
* Использование балансировки весов замедляет обучение, но в то же время улучшает стабильность уменьшения mse_q. Чем сильнее разбиение loss на части, тем сильнее эффект(см [exp10](https://github.com/mikhakuv/PINNs/blob/main/exp10.md), [exp11](https://github.com/mikhakuv/PINNs/blob/main/exp11.md),  [exp12](https://github.com/mikhakuv/PINNs/blob/main/exp12.md))
---
Статистику обучения в exp9-exp12 и сравнительные графики можно найти в файле: [stats.xlsx](https://github.com/mikhakuv/PINNs/blob/main/stats.xlsx)   
Результаты всех успешных экспериментов можно найти в таблице: [performance_table.xlsx](https://docs.google.com/spreadsheets/d/1EAHA_UamNzLTHufkJSFcJTIRn0lpgeh28o-bcWYOjjE/edit?usp=sharing)
