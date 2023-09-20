### Прогресс:
* Проблема с z0 была в функции активации(была tanh, теперь будет sin)(см [exp3](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp3.md)), остальные изменения заметных положительных эффектов не дали(cм [exp4](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp4.md), [exp5](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp5.md)).
* Решение всё ещё плохо продолжается на большие t, а если и продолжается, то почему-то идёт ниже, чем нужно(см [exp6](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp6.md)).
* Soft Adapt тоже не очень помог, коэффициенты просто постепенно приравниваются(см [exp7](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp7.md)).
* Что интересно, при lr=1e-4 и ниже сеть вроде учится, loss уменьшается, но на выходе получается какая-то странная фигня, не похожая ни на константу ни на аналитическое решение(см [exp8](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp8.md)).
---
* Чтобы получить хорошие результаты нужно было поправить процесс обучения и использовать 100000 итераций оптимизатора ADAM с убывающим lr(см [exp9](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp9.md))
* Использование балансировки весов замедляет обучение, но в то же время улучшает стабильность уменьшения mse_q. Чем сильнее разбиение loss на части, тем сильнее эффект(см [exp10](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp10.md), [exp11](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp11.md),  [exp12](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp12.md),  [exp13](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp13.md))
---
* Память коэффициентов при балансировке весов улучшила результаты, но они всё ещё хуже, чем без балансировки вообще(см [exp14](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp14.md))
* Учёт порядка слагаемых loss при балансировке весов лишь ухудшил результаты(см [exp15](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp15.md))  
* Использование метода балансировки весов ReLoBRaLo дало существенное увеличение качества, но оно всё ещё хуже, чем без балансировки(см [exp16](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp16.md))
---
* Учёт соблюдения законов сохранения при обучении только ухудшает результаты, ведь задача повышения точности их соблюдения не совпадает с задачей понижения mse_q(см [exp17](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp17.md))
* При увеличении числа итераций в обучении до 300000 ReLoBRaLo показывает самые лучшие результаты. Остальные методы балансировки выдают результаты хуже, чем в опыте без балансировки вообще(см. [exp18](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp18.md), [exp19](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp19.md), [exp20](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp20.md),
[exp21](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp21.md), [exp22](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp22.md),
[exp23](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp23.md))
---
* Изучение взаимодействия двух солитонов при alpha=0 дало замечательные результаты: законы сохранения и уравнение выполняются при всех t(см. [exp24](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp24.md))
* Если же alpha=0.1, то начинаются проблемы: после пересечения солитоны распыляются, а законы сохранения перестают выполняться(см. [exp25](https://github.com/mikhakuv/PINNs/blob/main/experiments/exp25.md))  

Статистику обучения во всех успешных экспериментах и сравнительные графики можно найти в файле: [stats.xlsx](https://github.com/mikhakuv/PINNs/blob/main/statistics/stats.xlsx)   
Результаты можно найти в таблице: [performance_table.xlsx](https://github.com/mikhakuv/PINNs/blob/main/statistics/performance_table.xlsx)
