---
title: "Мониторинг состояния базы данных Managed Service for YDB"
description: "Вы можете отслеживать состояние базы данных Managed Service for YDB с помощью инструментов мониторинга в консоли управления. Эти инструменты предоставляют диагностическую информацию в виде графиков. Также вы можете настроить алерты Yandex Monitoring для автоматического мониторинга состояния БД."
---

# Мониторинг состояния базы данных

Данные о состоянии базы данных доступны в консоли управления. Их можно посмотреть на вкладке **{{ ui-key.yacloud.ydb.database.switch_monitoring }}** страницы управления БД или в сервисе {{ monitoring-full-name }}.

Диагностическая информация о состоянии БД представлена в виде графиков. Период обновления графиков - 1 минута.

{% include [note-monitoring-auto-units](../../_includes/mdb/note-monitoring-auto-units.md) %}


Вы можете [настроить алерты](#monitoring-integration) в сервисе {{ monitoring-full-name }} для получения уведомлений о сбоях в работе БД. В {{ monitoring-full-name }} используются два порога срабатывания алерта: `{{ ui-key.yacloud_monitoring.alert.status_warn }}` и `{{ ui-key.yacloud_monitoring.alert.status_alarm }}`. При превышении заданного порога вы получите оповещения через настроенные [каналы уведомлений](../../monitoring/concepts/alerting.md#notification-channel).


## Просмотр графиков мониторинга {#monitoring-database}

Для просмотра детальной информации о состоянии базы данных {{ ydb-name }}:

1. Перейдите на страницу каталога и выберите сервис **{{ ui-key.yacloud.iam.folder.dashboard.label_ydb }}**.
1. Нажмите на имя нужной базы данных и выберите вкладку **{{ ui-key.yacloud.ydb.database.switch_monitoring }}**.
1. {% include [open-in-yandex-monitoring](../../_includes/mdb/open-in-yandex-monitoring.md) %}

На открывшейся страницы вы увидите графики состояния БД.

## Интеграция с {{ monitoring-full-name }} {#monitoring-integration}

Чтобы настроить алерты показателей состояния базы данных:

1. [Создайте алерт](../../monitoring/operations/alert/create-alert.md).
1. Добавьте метрику состояния.
1. Задайте в параметрах алерта значения порогов для оповещения.

Подробнее о метриках состояния {{ ydb-name }} смотрите в [справочнике метрик](../../monitoring/metrics-ref/ydb-ref.md).
