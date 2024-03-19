---
title: "Управление доступом в {{ marketplace-full-name }}"
description: "Управление доступом в {{ marketplace-short-name }}. В разделе описано, на какие ресурсы можно назначить роль, какие роли действуют в сервисе, какие роли необходимы для того или иного действия."
---

# Управление доступом в {{ marketplace-short-name }}

В этом разделе вы узнаете:
* [на какие ресурсы можно назначить роль](#resources);
* [какие роли действуют в сервисе](#roles-list).

## На какие ресурсы можно назначить роль {#resources}

{% include [basic-resources](../../_includes/iam/basic-resources-for-access-control.md) %}

## Какие роли действуют в сервисе {#roles-list}

### Сервисные роли {#service-roles}

#### license-manager.auditor {#license-manager-auditor}

{% include [license-manager.auditor](../../_roles/license-manager/auditor.md) %}

#### license-manager.viewer {#license-manager-viewer}

{% include [license-manager.viewer](../../_roles/license-manager/viewer.md) %}
  
#### license-manager.user {#license-manager-user}

{% include [license-manager.user](../../_roles/license-manager/user.md) %}
