### FileSystemNotifier

## Задача
    Создание приложения file-watcher (приложение которое следит за изменениями файла\
    папки и выполняет определенные действия, если файл изменился), запуск его как сервиса
    (демона). (50 баллов)

## Установка: 
  - `sudo make install`
    
## Управление файлами и директориями
    - Добавление нового файла/директории осуществляется с помощью флага -add: `sudo fsn -add /some/path`
    - Привязку скриптов к событиям необходимо осуществлять во время добавления файла/директории: `sudo fsn -add /some/path -on_create /cr.sh -on_delete /rm.sh -on_modify /mod.sh`
    - Если вы хотите добавить папку и отслеживать изменения на нескольких уровнях вложенности - во время добавления необходимо использовать флаг -r: `sudo fsn -add /some/path -r 2. Число передаваемое с флагом означает глубину проверки. При указании -r -1 будут учитываться все файлы и папки внутри директории. При указании -2 и менее рекурсивный обход выполняться не будет (Дефолтное значение -2).`
    - Остановка отслеживания объекта доступна с помощью флага -stop: `sudo fsn -stop /some/path`
    - Возобновление отслеживания объекта доступна с помощью флага -run: `sudo fsn -run /some/path`
    - Удаление объекта доступно через флаг -delete: `sudo fsn -delete /some/path`

## Управление сервисом
    - Остановка сервиса:
        - `systemctl stop fsn`
        - `sudo fsn -service stop`
    - Перезапуск сервиса: `systemctl restart fsn` 
    - Сброс настроек сервиса: `sudo fsn -service reset`
    - Получение текущих настроек сервиса: `sudo fsn -service info`
    - Логирование каждой сессии сервиса осуществляется в файл лога по пути `/etc/fsnotifier/log`. Название файла соответствует времени и дате запуска сессии.
    

