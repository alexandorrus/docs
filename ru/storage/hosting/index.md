# Хостинг статических сайтов

Вы можете разместить свой статический сайт в [!KEYREF objstorage-full-name]. Статический сайт строится на клиентских технологиях, таких как  HTML, CSS и JavaScript. Он не может содержать каких-либо скриптов, требующих запуска на стороне веб-сервера.

Для размещения сайта:

- Загрузите файлы сайта в бакет, специально созданный для размещения сайта.
- [Настройте бакет](bucket-configuration.md) для хостинга.

После настройки бакета для хостинга сайт становится доступен по адресу:

```
http(s)://<имя_бакета>.[!KEYREF s3-web-host]
```

или

```
http(s)://[!KEYREF s3-web-host]/<имя_бакета>
```

> [!NOTE]
> 
> Протокол HTTPS можно использовать только если имя бакета не содержит точку.

## Собственный домен

Для отображения сайта вы можете использовать собственный домен, например, `www.example.com`.

В этом случае:

- Имя бакета должно совпадать с именем домена, например `www.example.com`. 

    > [!NOTE] 
    > 
    > Используйте для хостинга в [!KEYREF objstorage-name] домены не ниже третьего уровня. Это связано с особенностями обработки записей `CNAME` на DNS-хостингах. Читайте подробнее в п.2.4 [RFC 1912](https://www.ietf.org/rfc/rfc1912.txt).

- Необходимо настроить алиас для бакета у своего провайдера DNS или на собственном DNS сервере.

    Например, для домена `www.example.com` необходимо добавить запись

    ```
    www.example.com CNAME www.example.com.[!KEYREF s3-web-host]
    ```

>[!NOTE]
>
>Сайт доступен только по протоколу HTTP, например, `http://www.example.com` или `http://www.example.com.[!KEYREF s3-web-host]`.
