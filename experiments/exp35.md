В данном опыте проводились запуски с Фурье слоями, которые состоят из последовательного прямого преобразования Фурье, линейного комплексного преобразования, обратного преобразования Фурье и нелинейного преобразования.  
<https://colab.research.google.com/drive/1T22LG48MTiQxZf76erV38-ymx3irT6ZE?usp=sharing>  
Результаты получились следующие:  
При правильном сочетании Фурье слоёв с обычнымим слоями точность получится немного выше, чем без этого. Но обычно получается так, что время обучения модели увеличивается, а точность ухудшается. Более того, добавление Фурье слоёв не решает проблемы падения точности с ростом `k` и не устраняет распыления солитонов при увеличении `alpha`(но есть основания полагать, что падение точности слабее на ~30%).  
Ноутбук можно скачать тут: <https://github.com/mikhakuv/PINNs/blob/main/notebooks/exp35.ipynb>  
