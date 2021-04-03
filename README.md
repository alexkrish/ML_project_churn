# Описание проекта
Данный проект является финальным соревнованием курса [Введение в Data Science и машинное обучение](https://stepik.org/course/4852) на платформе Stepic.
Известно, исходя из постановки задания соревнования, что за метрику качества модели будет взят ROC_AUC sore.  
В рамках этого соревнования на данный момент разработано 2 решения, которые находятся в папке *notebooks_(lang):*  

1. *baseline_with_full_data_processing* - baseline по признакам, которые были созданы в течении прохождения курса. 
Также в ноутбуке присутсвует поэтапная предобработка данных с анализом признаков. Для выбора оптимальной модели также предоставлены сравнительные характеристики и общая аналитика.  
**ROC_AUC score данной модели = 0.804**    

2. *best_performance_with_new_features* - решение, которое расширяет набор признаков из baseline. Добавлено оценку сложности каждого степа по разным критериям. 
Также в данных ноутбуках для краткости изложения предусмотрено подключения пакетов с функциями, которые автоматически(по алгоритму из baseline) предобрабатывают данные
и обучают модели.    
**ROC_AUC score данной модели = 0.822**

## Суть задания  
**по прошествию 2 дней с момента прервой активности пользователя на [курсе](https://stepik.org/course/129/syllabus) определить закончит ли он его**
  
## Структура проекта  
1. **data** - каталог данных для построения признаков  
    - *ROC_SCOR* - каталог со скринами, на которых система Stepic проверяет точность модели по метрике ROC_AUC  
    - *test* - каталог с данными для прогноза  
      - *events_data_test.zip* - действия пользователей со степами  
      - *submission_data_test.zip* - время и статусы сабмитов пользователей с практическими степами  
    - *train* - каталог с данными для обучения  
      - *event_data_train.zip* - действия пользователей со степами  
      - *submissions_data_train.zip* - время и статусы сабмитов пользователей с практическими степами  
      
2. **notebooks_eng** - каталог ноутбуков на английском языке с решениями данной проблемы  
    - *baseline_with_full_data_processing[ENG].ipynb* - baseline по признакам, которые были созданы в течении прохождения курса с подробным анализом  
    - *best_performance_with_new_features[ENG].ipynb* - решение, которое расширяет набор признаков из baseline. Добавлено оценку сложности каждого степа по разным критериям. 
    
3. **notebooks_rus** - каталог ноутбуков на русском языке с решениями данной проблемы  
    - *baseline_with_full_data_processing[RUS].ipynb* - baseline по признакам, которые были созданы в течении прохождения курса с подробным анализом  
    - *best_performance_with_new_features[RUS].ipynb* - решение, которое расширяет набор признаков из baseline. Добавлено оценку сложности каждого степа по разным критериям. 
    
4. **reports** - каталог с отчетами по предсказаниям вероятности отнесения пользователя к классу dropout student  
    - *reports.zip* - архив, в котором находятся такие предсказания. Для каждого такого прогноза в названии файла указана какая модель это предсказала  

5. **utils** - папка с кодом для генерации датасетов, признаков и обучения моделей с составлением сравнительных таблиц производительности  
    - *model_fit_utils.py* - функции, которые упрощают процесс обучения моделей. Также присутсвуют функции по составлению сравнительных таблиц  
    - *preprocessing_utils.py* - функции, которые упрощают процесс формирования датасетов и создания нужных признаков.
        Также присутствует функция, которая возвращает X и y по переданным events_data и submission_data  
## Описание данных  
 **events_train.csv** - данные о действиях, которые совершают студенты со стэпами

1. **step_id** - id стэпа  
2. **user_id** - анонимизированный id юзера  
3. **timestamp** - время наступления события в формате unix date  
4. **action** - событие, возможные значения:  
*discovered* - пользователь перешел на стэп  
*viewed* - просмотр шага,  
*started_attempt* - начало попытки решить шаг, ранее нужно было явно нажать на кнопку - начать решение, перед тем как приступить к решению практического шага  
*passed* - удачное решение практического шага  
  
**submissions_train.csv** - данные о времени и статусах сабмитов к практическим заданиям

1. **step_id** - id стэпа
2. **timestamp** - время отправки решения в формате unix date
3. **submission_status** - статус решения
4. **user_id** - анонимизированный id юзера
