# Изменение настроек кластера

После создания кластера вы можете:

* [Изменить класс хостов](#change-resource-preset).

* [Увеличить размер хранилища](#change-disk-size) (доступно только для сетевого хранилища, `network-hdd` и `network-nvme`).

* [Настраивать серверы](#change-mongod-config) [!KEYREF MG] согласно [документации [!KEYREF MG]](https://docs.mongodb.com/v3.6/reference/configuration-options/).


## Изменить класс хостов {#change-resource-preset}

---

**[!TAB CLI]**

[!INCLUDE [cli-install](../../_includes/cli-install.md)]

[!INCLUDE [default-catalogue](../../_includes/default-catalogue.md)]

Чтобы изменить [класс хостов](../concepts/instance-types.md) для кластера:

1. Посмотрите описание команды CLI для изменения кластера:

    ```
    $ [!KEYREF yc-mdb-mg] cluster update --help
    ```

2. Запросите список доступных классов хостов (в колонке `ZONES` указаны зоны доступности, в которых можно выбрать соответствующий класс):

   ```bash
   $ [!KEYREF yc-mdb-mg] resource-preset list
   
   +-----------+--------------------------------+-------+----------+
   |    ID     |            ZONE IDS            | CORES |  MEMORY  |
   +-----------+--------------------------------+-------+----------+
   | s1.nano   | ru-central1-a, ru-central1-b,  |     1 | 4.0 GB   |
   |           | ru-central1-c                  |       |          |
   | s1.micro  | ru-central1-a, ru-central1-b,  |     2 | 8.0 GB   |
   |           | ru-central1-c                  |       |          |
   | ...                                                           |
   +-----------+--------------------------------+-------+----------+
   ```

3. Укажите нужный класс в команде изменения кластера:

    ```
    $ [!KEYREF yc-mdb-mg] cluster update <имя кластера>
         --mongod-resource-preset <ID класса>
    ```

    [!KEYREF mmg-short-name] запустит операцию изменения класса хостов для кластера.


**[!TAB API]**

Изменить [класс хостов](../concepts/instance-types.md) кластера можно с помощью метода API [update](../api-ref/Cluster/update.md): передайте в запросе нужные значения в параметре `configSpec.mongodbSpec_3_6.mongod.config.resourcePresetId`.

Список поддерживаемых значений запрашивайте методом [list](../api-ref/ResourcePreset/list.md) для ресурсов `ResourcePreset`.

---


## Увеличить размер хранилища {#change-disk-size}

---

**[!TAB CLI]**

[!INCLUDE [cli-install](../../_includes/cli-install.md)]

[!INCLUDE [default-catalogue](../../_includes/default-catalogue.md)]

Чтобы увеличить размер хранилища для кластера:

1. Посмотрите описание команды CLI для изменения кластера:

    ```
    $ [!KEYREF yc-mdb-mg] cluster update --help
    ```

1. Проверьте, что в облаке хватает квоты на увеличение хранилища: откройте страницу [Квоты](https://console.cloud.yandex.ru/?section=quotas) для вашего облака и проверьте, что в секции [!KEYREF mmg-full-name] не исчерпано место в строке **space**.

3. Проверьте, что нужный кластер использует именно сетевое хранилище (увеличить размер локального хранилища пока невозможно). Для этого запросите информацию о кластере и найдите поле `disk_type_id` — его значение должно быть `network-hdd` или `network-nvme`:

    ```
    $ [!KEYREF yc-mdb-mg] cluster get <имя кластера>
    
    id: c7qkvr3u78qiopj3u4k2
    folder_id: b1g0ftj57rrjk9thribv
    ...
    config:
      mongodb_3_6:
        mongod:
          config:
            user_config: {}
          resources:
            resource_preset_id: s1.micro
            disk_size: "21474836480"
            disk_type_id: network-nvme
    ...
    ```

4. Укажите нужный объем хранилища в команде изменения кластера (должен быть не меньше, чем значение `disk_size` в свойствах кластера):

    ```
    $ [!KEYREF yc-mdb-mg] cluster update <имя кластера>
         --mongod-disk-size <размер хранилища в ГБ>
    ```

    Если все условия выполнены, [!KEYREF mmg-short-name] запустит операцию по увеличению объема хранилища.

**[!TAB API]**

Изменить размер хранилища для кластера можно с помощью метода API [update](../api-ref/Cluster/update.md): передайте в запросе нужные значения в параметре `configSpec.mongodbSpec_3_6.mongod.resources.diskSize`.

Проверьте, что в облаке хватает квоты на увеличение хранилища: откройте страницу [Квоты](https://console.cloud.yandex.ru/?section=quotas) для вашего облака и проверьте, что в секции [!KEYREF mmg-full-name] не исчерпано место в строке **space**.

---


## Изменить настройки [!KEYREF MG] {#change-mongod-config}

Вы можете изменить настройки СУБД для хостов вашего кластера. Все поддерживаемые настройки описаны [в справочнике API](../api-ref/Cluster/update.md).

---

**[!TAB CLI]**

[!INCLUDE [cli-install](../../_includes/cli-install.md)]

[!INCLUDE [default-catalogue](../../_includes/default-catalogue.md)]

Чтобы изменить настройки СУБД для кластера, используйте команду:
```
$ [!KEYREF yc-mdb-mg] cluster update-config
```

Например, для установки значения параметра [net.maxIncomingConnections](https://docs.mongodb.com/v4.0/reference/configuration-options/#net.maxIncomingConnections) в `4096`, выполните следующую команду:

```
$ [!KEYREF yc-mdb-mg] cluster update-config <имя кластера>
    --set net.max_incoming_connections=4096
```

[!KEYREF mmg-short-name] запустит операцию изменения настроек СУБД для кластера. Если изменяемая настройка применяется только с перезапуском СУБД, то [!KEYREF mmg-short-name] последовательно перезапустит СУБД на всех хостах кластера.

**[!TAB API]**

Изменить настройки СУБД для кластера можно с помощью метода API [update](../api-ref/Cluster/update.md): передайте в запросе нужные значения в параметре `configSpec.mongodbSpec_3_6.mongod.config.resourcePresetId`.

---
