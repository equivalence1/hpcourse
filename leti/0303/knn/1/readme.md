Задание: Пул потоков (готово к проверке, поправил кодировки)

Реализовать пул потоков, состоящий из N постоянных ("горячих") потоков, готовых к приёму задач сразу после создания пула и переменной части - потоков, создаваемых по мере необходимости и исчезающих при отсутствии для них задач заданное время. Приложение, проверяющее работу пула, при запуске должно принимать 2 параметра:

    Число "горячих" потоков: всегда присутствуют в пуле, даже если задач для них нет (ключ -c)
    Timeout: время, в течение которого свободный поток удаляется из пула при отсутствии для него задач (ключ -t)

Дальнейший консольный интерфейс приложения должен позволять:

    Добавлять задачу длительностью N секунд и возвращать её идентификатор
    Снимать задачу с исполнения по её идентификатору, даже если задача не отработала положенного ей времени
    Завершать работу 

Требования

    Использовать язык разработки, имеющий простой уровень объетов-потоков (boost::thread, Thread...)
    Завершать потоки человеческими средствами interrupt
    Рабочие потоки не должны находиться в активном ожидании задач
    При отмене задачи на горячем потоке, сам поток должен остаться свободным горячим потоком
    Корректно обрабатывать сигнал завершения приложения SIGTERM, завершая существующие задачи (корректно прерывая их выполнение), не обрабатывая новых, не находящихся в данный момент на исполнении
    Задача, выполняемая в потоке должна возвращать результат ползователю
    Нельзя использовать реализованные очереди с методом типа poll 

Рекомендации

    Проверить работу под управлением valgrind (tool helgrind) или иными средствами поиска ошибок (Intel Parallel Studio и т.п.)
    Приветствуются модульные тесты
    Проверять наличие потоков системными средствами или в отладчике, не надеясь на дебажный вывод 