* `modelUri` — идентификатор модели, которая будет использоваться для генерации ответа.
* `completionOptions` — параметры конфигурации запроса:

  * `stream` — включает потоковую передачу частично сгенерированного текста. Принимает значения `true` или `false`.
  * `temperature` — чем выше значение этого параметра, тем более креативными и случайными будут ответы модели. Принимает значения от `0` (включительно) до `1` (включительно). Значение по умолчанию: `0.6`.
  * `maxTokens` — устанавливает ограничение на выход модели в [токенах](../../yandexgpt/concepts/tokens.md). Максимальное число токенов генерации зависит от модели. Подробнее см. в разделе [{#T}](../../yandexgpt/concepts/limits.md).

* `messages` — список сообщений, которые задают контекст для модели:

  * `role` — роль отправителя сообщения:

    * `user` — используется для отправки пользовательских сообщений к модели.
    * `system` — позволяет задать контекст запроса и определить поведение модели.
    * `assistant` — используется для ответов, которые генерирует модель.

  * `text` — текстовое содержимое сообщения.
