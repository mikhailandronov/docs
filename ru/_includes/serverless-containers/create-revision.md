{% include [revision-service-account-note](./revision-service-account-note.md) %}

{% list tabs group=instructions %}

- Консоль управления {#console}

  1. В [консоли управления]({{ link-console-main }}) перейдите в [каталог](../../resource-manager/concepts/resources-hierarchy.md#folder), в котором находится [контейнер](../../serverless-containers/concepts/container.md).
  1. Выберите сервис **{{ ui-key.yacloud.iam.folder.dashboard.label_serverless-containers }}**.
  1. Выберите контейнер, [ревизию](../../serverless-containers/concepts/container.md#revision) которого хотите создать.
  1. Перейдите на вкладку **{{ ui-key.yacloud.serverless-containers.label_editor }}**.
  1. Укажите параметры ревизии.
  1. Нажмите кнопку **{{ ui-key.yacloud.serverless-containers.button_deploy-revision }}**.

- CLI {#cli}

  Чтобы создать [ревизию](../../serverless-containers/concepts/container.md#revision) [контейнера](../../serverless-containers/concepts/container.md), выполните команду:

  ```bash
  yc serverless container revision deploy \
    --container-name <имя_контейнера> \
	--image <URL_Docker-образа> \
	--cores 1 \
	--memory 1GB \
	--concurrency 1 \
	--execution-timeout 30s \
	--service-account-id <идентификатор_сервисного_аккаунта>
  ```

  Где:
  * `--cores` — количество ядер, которые доступны контейнеру.
  * `--memory` — требуемая память. По умолчанию — 128 МБ.
  * `--concurrency` — максимальное количество одновременных вызовов одного экземпляра контейнера. По умолчанию — 1, максимальное значение — 16. Если вызовов контейнера больше, чем значение `concurrency`, [{{ serverless-containers-full-name }}](../../serverless-containers/) масштабирует контейнер — запускает его дополнительные экземпляры.

    {% note info %}

	Количество экземпляров контейнеров и одновременных запросов к ним в каждой зоне доступности не может превышать [квоты](../../serverless-containers/concepts/limits.md#serverless-containers-quotas).

	{% endnote %}

  * `--execution-timeout` — таймаут. По умолчанию — 3 секунды.
  * `--service-account-id` — [идентификатор сервисного аккаунта](../../iam/operations/sa/get-id.md), у которого есть права на скачивание образа.

  Результат:

  ```text
  id: bbajn5q2d74c********
  container_id: bba3fva6ka5g********
  created_at: "2021-07-09T15:04:55.135Z"
  image:
	image_url: {{ registry }}/crpd3cicopk7********/test-container:latest
	image_digest: sha256:de8e1dce7ceceeafaae122f7670084a1119c961cd9ea1795eae92bd********
  resources:
	memory: "1073741824"
	cores: "1"
  execution_timeout: 3s
  service_account_id: ajeqnasj95o7********
  status: ACTIVE
  ```

- {{ TF }} {#tf}

  {% include [terraform-definition](../../_tutorials/_tutorials_includes/terraform-definition.md) %}

  {% include [terraform-install](../../_includes/terraform-install.md) %}

  В {{ TF }} [ревизия](../../serverless-containers/concepts/container.md#revision) создается при каждом обновлении параметров работы ресурса.

  Чтобы создать ревизию:
  1. Обновите в конфигурационном файле параметры работы ресурса `yandex_serverless_container`:

     ```hcl
     provider "yandex" {
       token     = "<OAuth>"
       cloud_id  = "<идентификатор_облака>"
       folder_id = "<идентификатор_каталога>"
       zone      = "{{ region-id }}-a"
     }

     resource "yandex_serverless_container" "test-container" {
        name               = "<имя_контейнера>"
        memory             = <объем_памяти>
        service_account_id = "<идентификатор_сервисного_аккаунта>"
        image {
            url = "<URL_Docker-образа>"
        }
     }
     ```

     Более подробную информацию о параметрах ресурса `yandex_serverless_container` в {{ TF }}, см. в [документации провайдера]({{ tf-provider-resources-link }}/serverless_container).
  1. Проверьте корректность конфигурационных файлов.
     1. В командной строке перейдите в папку, где был создан конфигурационный файл.
     1. Выполните проверку с помощью команды:

        ```bash
        terraform plan
        ```

     Если конфигурация описана верно, в терминале отобразится список создаваемых или обновляемых ресурсов и их параметров. Если в конфигурации есть ошибки, {{ TF }} на них укажет.
  1. Если в конфигурации нет ошибок, выполните команду:

     ```bash
     terraform apply
     ```

  1. Подтвердите создание или обновление ресурсов: введите в терминал слово `yes` и нажмите **Enter**.

     После этого будет создана ревизия. Проверить создание ревизии можно в [консоли управления]({{ link-console-main }}) или с помощью команды [CLI](../../cli/):

     ```bash
     yc serverless container revision list
     ```

- API {#api}

  Чтобы создать [ревизию](../../serverless-containers/concepts/container.md#revision) [контейнера](../../serverless-containers/concepts/container.md), воспользуйтесь методом REST API [deployRevision](../../serverless-containers/containers/api-ref/Container/deployRevision.md) для ресурса [Container](../../serverless-containers/containers/api-ref/Container/index.md) или вызовом gRPC API [ContainerService/DeployRevision](../../serverless-containers/containers/api-ref/grpc/container_service.md#DeployRevision).

{% endlist %}