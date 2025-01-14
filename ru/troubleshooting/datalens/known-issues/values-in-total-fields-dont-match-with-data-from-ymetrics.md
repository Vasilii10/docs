# У табличных чартов DataLens не совпадают значения в полях «Итого» с аналогичными данными из Метрики

## Описание проблемы {#issue-description}

В DataLens используется подключение к данным из Яндекс Метрики. 
У чарта табличного типа в DataLens и данных из Метрики отображаются разные данные в полях «Итого».

## Решение {#issue-resolution}

Такое поведение является особенностью работы Яндекс Метрики. При запросе данных через API Метрика отдает приблизительный результат. 
На точность поставляемых данных также влияет [сэмплирование](https://yandex.ru/dev/metrika/doc/api2/api_v1/sampling.html), производимое на стороне Яндекс Метрики.

Для того чтобы аддитивные величины показывали верные значения в итогах, измените в настройках подключения точность на 100%.

Подключение к Метрике напрямую имеет ряд ограничений. Мы рекомендуем выгружать сырые данные из метрики в промежуточную базу данных. Например, для выгрузки и/или репликации данных из Яндекс Метрики вы можете использовать [БД ClickHouse](../../../managed-clickhouse/quickstart.md).

После выгрузки данных в промежуточную базу вы можете [настроить подключение к ней](../../../datalens/operations/connection/create-clickhouse.md) со стороны DataLens.

## Если проблема осталась {#if-issue-still-persists}
Если вышеописанные действия не помогли решить проблему, [создайте запрос в техническую поддержку](https://console.cloud.yandex.ru/support?section=contact).
В запросе укажите следующую информацию:
1. Ссылку на проблемный объект из адресной строки браузера.
2. Полный текст сообщения об ошибке с содержанием Request ID;
3. [HAR-файл](../../../support/create-har.md) с сохраненными результатами взаимодействия браузера с серверами DataLens.