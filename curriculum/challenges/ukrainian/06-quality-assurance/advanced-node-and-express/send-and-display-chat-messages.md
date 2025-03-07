---
id: 589fc832f9fc0f352b528e79
title: Відправлення та відображення повідомлень чату
challengeType: 2
forumTopicId: 301562
dashedName: send-and-display-chat-messages
---

# --description--

Настав час почати надсилати повідомлення чату на сервер всім клієнтам! У файлі `client.js`, ви бачите, що вже існує блок обробки коду, після відправлення форми повідомлення.

```js
$('form').submit(function() {
  /*logic*/
});
```

У межах коду відправлення форми ви повинні видати (emit) подію після визначення `messageToSend`, але перед тим, як ви очистите текстову панель `#m`. Код повинен називатися `'chat message'` і дані повинні бути `messageToSend`.

```js
socket.emit('chat message', messageToSend);
```

Тепер на вашому сервері, ви мусите прослухати сокет для події `'chat message'` з назвою `message`. Once the event is received, it should emit the event `'chat message'` to all sockets using `io.emit`, sending a data object containing the `username` and `message`.

In `client.js`, you should now listen for event `'chat message'` and, when received, append a list item to `#messages` with the username, a colon, and the message!

На даний момент чат повинен бути повністю функціональним і спроможним відправляти повідомлення всім клієнтам!

Відправте свою сторінку коли впевнились, що все правильно. Якщо виникають помилки, ви можете <a href="https://forum.freecodecamp.org/t/advanced-node-and-express/567135#send-and-display-chat-messages-11" target="_blank" rel="noopener noreferrer nofollow">переглянути проєкт, виконаний до цього етапу</a>.

# --hints--

Сервер має слухати `'chat message'` та переміщувати (emit) його належним чином.

```js
async (getUserInput) => {
  const url = new URL("/_api/server.js", getUserInput("url"));
  const res = await fetch(url);
  const data = await res.text();
  assert.match(
    data,
    /socket.on.*('|")chat message('|")[^]*io.emit.*('|")chat message('|").*username.*message/s,
    'Your server should listen to the socket for "chat message" then emit to all users "chat message" with name and message in the data object'
  );
}
```

Клієнт повинен правильно обробляти та показувати нові дані із події `'chat message'`.

```js
async (getUserInput) => {
  const url = new URL("/public/client.js", getUserInput("url"));
  const res = await fetch(url);
  const data = await res.text();
  assert.match(
    data,
    /socket.on.*('|")chat message('|")[^]*messages.*li/s,
    'You should append a list item to #messages on your client within the "chat message" event listener to display the new message'
  );
}
```

# --solutions--

```js
/**
  Backend challenges don't need solutions, 
  because they would need to be tested against a full working project. 
  Please check our contributing guidelines to learn more.
*/
```
