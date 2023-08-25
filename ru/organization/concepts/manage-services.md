---
title: "Управление ресурсами {{ yandex-cloud }} в {{ org-full-name }}"
description: "Используйте {{ org-full-name }}, чтобы расширить возможности вашего бизнеса. Облако — это рабочее пространство вашей организации. Все облака, которые подключены к организации, отображаются в разделе «Облака и сервисы»."
---


# Управление облаками и сервисами

Используйте {{ org-full-name }}, чтобы расширить возможности вашего бизнеса: вы можете создать [облако](#cloud), подключить [сервисы для совместной работы и бизнес-аналитики](#collaboration).

Сервисы для совместной работы и инструменты бизнес-аналитики доступны для всех организаций. Чтобы использовать [сервисы {{ yandex-cloud }}]({{ link-cloud-services }}), создайте облако.

{% note info %}

Управлять всеми облаками и сервисами может пользователь с ролью `organization-manager.organizations.owner`. Как назначить роль пользователю, читайте в разделе [Роли](../security/index.md#admin).

{% endnote %}

Чтобы перейти к управлению облаками и сервисами:

1. [Войдите в аккаунт]({{link-passport}}) администратора или владельца организации.

1. Перейдите в сервис [{{org-full-name}}]({{link-org-main}}).

1. На панели слева выберите раздел [Облака и сервисы]({{link-org-services}}) ![icon-services](../../_assets/organization/icon-services.svg).

   На странице отображается список облаков, подключенных к организации, а также сервисы: {{ tracker-full-name }}, {{ wiki-full-name }}, {{ forms-full-name }}, {{ datalens-full-name }} и {{ ml-platform-full-name }}.

1. Чтобы перейти в сервис, нажмите карточку сервиса.

   Чтобы открыть облако в консоли {{ yandex-cloud }}, нажмите его название.



## Облако {#cloud}

Облако — это рабочее пространство вашей организации. Все облака, которые подключены к организации, отображаются в разделе **Облака и сервисы**.

Администратор организации может создавать в облаке новые каталоги и ресурсы, подключать сервисы {{ yandex-cloud }}, а также управлять правами доступа к ним. Подробнее о работе с ресурсами {{ yandex-cloud }} читайте в [документации {{ resmgr-full-name }}](../../resource-manager/concepts/resources-hierarchy.md).

Первое облако для организации будет подключено автоматически при входе администратора в [консоль {{ yandex-cloud }}]({{ link-console-main }}). Чтобы подключить дополнительное облако, вам потребуется создать [платежный аккаунт](../../billing/quickstart/).

Если в вашем аккаунте зарегистрировано несколько организаций, вы можете [переносить](../../resource-manager/operations/cloud/change-organization.md) облака из одной организации в другую.


## Сервисы для совместной работы и бизнес-аналитики {#collaboration}

Сервисы для совместной работы и инструменты бизнес-аналитики доступны для всех организаций и подключаются автоматически при первом входе любого пользователя организации. 

* [{{ tracker-full-name }}]({{ link-tracker }}) — это сервис для управления задачами и проектами вашей организации. {{ tracker-name }} поможет вам распределять ресурсы, ставить задачи и отслеживать их выполнение.

    Подробнее о сервисе и его возможностях читайте в [документации {{ tracker-full-name }}](../../tracker/).

* [{{ wiki-full-name }}]({{ link-wiki }}) —  это сервис для создания корпоративной базы знаний, которую наполняют и обновляют сотрудники компании. {{ wiki-name}} дает сотрудникам компании дополнительные возможности для совместной работы: они могут делиться информацией, искать ответы на частые вопросы, вести обсуждение в комментариях к странице.

    Подробнее о сервисе и его возможностях читайте в [документации {{ wiki-full-name }}](../../wiki/).

* [{{ forms-full-name }}]({{ link-forms-b2b }}) — это сервис, где вы можете проводить опросы среди коллег или клиентов, собирать отзывы и принимать заявки. Пользователям организаций доступны расширенные функции [{{ forms-full-name }} для бизнеса](../../forms/forms-for-org.md): интеграция с сервисами {{ tracker-name }} и {{ wiki-name}}, управление доступом к заполнению формы, а также специальные блоки вопросов.

    Подробнее о сервисе и его возможностях читайте в [документации {{ forms-full-name }}](../../forms/).

* [{{ datalens-full-name }}]({{ link-datalens-main }}) — это сервис, который позволяет отслеживать продуктовые и бизнес-метрики и принимать решения, основанные на данных. В {{ datalens-full-name }} можно подключить различные источники данных, строить визуализации, собирать дашборды и делиться полученными результатами.

    Подробнее о сервисе и его возможностях читайте в [документации {{ datalens-full-name }}](../../datalens/).

* [{{ ml-platform-full-name }}]({{ link-datasphere-main }}) — это сервис для ML-разработки полного цикла. {{ ml-platform-full-name }} является частью платформы данных и предоставляет широкие возможности для простого взаимодействия с сервисами {{ yandex-cloud }}. {{ ml-platform-name }} помогает значительно сократить стоимость машинного обучения по сравнению с выполнением вычислений на собственном оборудовании или на других облачных платформах за счет автоматического обслуживания вычислительных ресурсов.

    Подробнее о сервисе и его возможностях читайте в [документации {{ ml-platform-full-name }}](../../datasphere/)
