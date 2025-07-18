#  DataCon2025: Генерация ингибиторов HDAC6 для терапии болезни Альцгеймера
## Описание проекта
Данный проект посвящен генерации новых молекул, потенциально способных взаимодействовать с мишенью HDAC6, участвующей в патогенезе болезни Альцгеймера. Проект разработан в рамках соревнования DataCon2025 и использует современные методы машинного обучения для работы с химическими данными.
##  1. Выбор мишени
###  Целевая мишень: **HDAC6**
Болезнь Альцгеймера (БА) — одно из наиболее распространённых нейродегенеративных заболеваний, характеризующееся образованием и отложением амилоидных β (Aβ) бляшек в мозге. Эти бляшки запускают каскад патологических процессов: гиперфосфорилирование тау-белка, нейровоспаление, дегенерация нейронов и снижение когнитивных функций.
Хотя амилоидный каскад остаётся одной из главных гипотез происхождения болезни, попытки создать эффективные препараты против Aβ до сих пор не увенчались значительным успехом, в основном из-за биологической сложности заболевания. Современные исследования предлагают новые подходы: от биомаркеров и генетических стратегий до терапевтической диагностики, однако необходимость в альтернативных мишенях остаётся крайне актуальной
Гистондеацетилазы (HDACs) — это эпигенетические регуляторы, удаляющие ацетильные группы с гистонов и тубулинов. Среди 18 известных изоформ HDAC особое внимание привлекает HDAC6. Исследования показали, что у пациентов с БА наблюдается повышенная экспрессия HDAC6, что связано с снижением уровня ацетилированного α-тубулина и нарушением работы нейронов. Более того, HDAC6 взаимодействует с тау-белком, способствуя его гиперфосфорилированию и формированию нейрофибриллярных клубков (NFTs). Интерес к ингибиторам HDAC6 (HDAC6i) вырос после того, как в доклинических моделях БА селективные HDAC6i показали: снижение уровня тау-белка, восстановление аксонального транспорта, улучшение обучаемости и памяти, противовоспалительное действие.

##  2. Датасеты и обработка данных
## Данные
Использовалась база данных BindingDB, содержащая 10098 молекул, отфильтрованных по IC50.
## Обработка данных
1) Предподготовка данных:
- обработка пропущенных значений и дубликатов
- проверка корректности молекул по SMILES
- фильтрация датасета по сайту связывания мишени
- фильтрация датасета по PDB структурам мишени
2) Расчет и отбор дескрипторов:
- с использованием библиотек RDKit и Padelpy рассчитаны молекулярные дескрипторы
- рассчитаны MACCS фингепринты
- фильтрация и отбор признаков с некорректными значениями;
нулевой дисперсией; высокой корреляцией (r > 0.7 между признаками)

##  3. Обучение моделей для предсказания биологической активности
Использовались модели XGBoost и ChemProp

## Использование молекулярных отпечатков (Fingerprints)
В данном проекте были использованы Morgan Fingerprints и MACCS Keys.
Для прогнозирования активности молекул с использованием Fingerprints была обучена модель XGBoostRegressor. После оптимизации гиперпараметров с помощью GridSearchCV были получены следующие метрики на тестовом наборе данных:

*   **R^2 (коэффициент детерминации):** 0.657
*   **MAE (средняя абсолютная ошибка):** 0.423
*   **RMSE (среднеквадратичная ошибка):** 0.582
---





---
