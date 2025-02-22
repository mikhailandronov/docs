#### Можно ли подключаться к отдельным хостам {{ CH }}? {#connect-node}

Да. Подключиться к хостам {{ CH }}-кластера можно:

* через [HTTPS-интерфейс]({{ ch.docs }}/interfaces/http/):
    * по шифрованному соединению с использованием SSL — порт 8443;
    * без шифрования — порт 8123;

* через [клиент командной строки]({{ ch.docs }}/interfaces/cli/):
    * по шифрованному соединению с использованием SSL — порт 9440;
    * без шифрования — порт 9000.

Подключение по [SSH](../../glossary/ssh-keygen.md) не поддерживается.

#### Почему я не могу подключиться к хосту из интернета? {#fail-connection}

Скорее всего в кластере не включен публичный доступ, поэтому к нему можно подключаться только с ВМ в {{ yandex-cloud }}. Запросить публичный доступ можно только при [создании нового хоста](../../managed-clickhouse/concepts/network.md#public-access-to-a-host) в кластере.

#### Как подключиться к непубличному хосту в {{ yandex-cloud }}? {#private-host}

[Подключитесь](../../managed-clickhouse/operations/connect.md) к хосту с виртуальной машины {{ yandex-cloud }}, расположенной в той же облачной сети, или [добавьте](../../managed-clickhouse/operations/hosts.md#add-host) в кластер еще один хост с публичным доступом и подключайтесь к непубличному хосту через него.

#### Можно ли подключиться к публичному кластеру без SSL? {#without-ssl}

Нет, к публичным хостам подключиться можно только используя SSL-соединение. Подробнее см. в [документации](../../managed-clickhouse/operations/connect.md).
