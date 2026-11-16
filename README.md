# Классификация видов спорта с ResNet18

Пет-проект по многоклассовой классификации изображений. Модель ResNet18 реализована вручную на PyTorch и обучается с нуля распознавать 30 видов спорта.

## Что есть в проекте

- собственная реализация `ResidualBlock` и ResNet18;
- ленивое чтение изображений с диска без загрузки всего датасета в память;
- аугментации `RandomHorizontalFlip`, `RandomVerticalFlip`, `ElasticTransform` и `RandomChannelPermutation`;
- отдельные train, validation и test-выборки;
- выбор лучшего чекпоинта только по validation accuracy;
- финальная оценка на test, classification report и confusion matrix;
- фиксированный seed и автоматический выбор CPU/CUDA.

## Данные

Используется датасет фотографий 100 видов спорта. Для эксперимента берутся первые 30 классов. Ноутбук автоматически скачивает архив размером около 445 МБ с Google Drive и распаковывает его в `data/`.

Данные и веса модели не входят в Git.

## Структура

```text
.
├── sports_classification_resnet18.ipynb
├── requirements.txt
├── .gitignore
└── README.md
```

## Запуск

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# Linux/macOS: source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

Откройте `sports_classification_resnet18.ipynb` и выполните ячейки по порядку. На первом запуске будет скачан датасет. CUDA заметно ускоряет обучение, но код работает и на CPU.

## Оценка качества

Лучшая модель выбирается по `validation accuracy`. Test-выборка используется один раз после завершения обучения. Целевой ориентир эксперимента — test accuracy не ниже 0.80.

Ноутбук в репозитории не содержит придуманной метрики: итоговое значение появится после полного запуска обучения в вашей среде.
