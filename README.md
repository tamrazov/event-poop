# Макротасок не существует.

Один из самых частых вопросов на собеседованиях для frontend разработчиков: Расскажите про событийный цикл? как выполняются таски? что такое микротаски и макротаски?

Для начала, я хочу сказать, что на собеседованиях первое, что не стоит делать это хамить, спорить и думать что вы знаете истину, когда отвечаете на вопросы от интервьера.

Итак, я не буду вдаваться в подробности event loop, вы и так скорее всего его знаете. Также если вы учили, читали javascript учебник, то скорее всего вы знаете такое слово как макротаски. В архитектуре event loop вообще нет такого слова как макротаски(macrotasks). Я вообще не смог найти ни одной спецификации, где было бы  mнаписано слово macrotask. Кроме [Promises/A+](https://promisesaplus.com/). Слово макротаск просто используется для объяснения разницу между ассинхронными Promise и setTimeout. Так в чем же разница между Promise и setTimeout? Почему Промисы всегда будут исполняться в приоритете?

Браузер имеет несколько очередей задач(task queues) для разных типов тасок. Таска - это любой javascript код, запланированный стандартными механизмами, такие как запуск программы, запуск события или коллбэки. Помимо этого вы можете создать таску с помощью API, например WindowTimers(setTimeout, setInterval). Микротаски же в свою очередь такие же конструкции javascript, которые позволяют выполнять операции не дожидаясь запуска нового цикла event loop (process.nextTick, Promises, queueMicrotask). Так вот, так как setTimeout, setInterval относятся к браузерному API, то очередь микротасок, таких как Promise и т.д. всегда будет в приоритете выполнения, перед браузерным API.
