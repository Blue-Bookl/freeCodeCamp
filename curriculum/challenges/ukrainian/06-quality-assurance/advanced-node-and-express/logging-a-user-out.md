---
id: 58965611f9fc0f352b528e6c
title: Вихід з облікового запису
challengeType: 2
forumTopicId: 301560
dashedName: logging-a-user-out
---

# --description--

Логіка logout легко створюється. The route should just unauthenticate the user, and redirect to the home page instead of rendering any view.

In passport, unauthenticating a user is as easy as just calling `req.logout()` before redirecting. Add this `/logout` route to do that:

```js
app.route('/logout')
  .get((req, res) => {
    req.logout();
    res.redirect('/');
});
```

You may have noticed that you are not handling missing pages (404). Поширений спосіб обробки цієї помилки у Node є наступне проміжне програмне забезпечення. Додайте це після всіх інших маршрутів:

```js
app.use((req, res, next) => {
  res.status(404)
    .type('text')
    .send('Not Found');
});
```

Відправте свою сторінку коли впевнились, що все правильно. Якщо виникають помилки, ви можете <a href="https://forum.freecodecamp.org/t/advanced-node-and-express/567135#logging-a-user-out-10" target="_blank" rel="noopener noreferrer nofollow">переглянути проєкт, виконаний до цього етапу</a>.

# --hints--

`req.logout()` should be called in your `/logout` route.

```js
async (getUserInput) => {
  const url = new URL("/_api/server.js", getUserInput("url"));
  const res = await fetch(url);
  const data = await res.text();
  assert.match(
    data,
    /req.logout/gi,
    'You should be calling req.logout() in your /logout route'
  );
}
```

`/logout` should redirect to the home page.

```js
async (getUserInput) => {
  const url = new URL("/logout", getUserInput("url"));
  const res = await fetch(url);
  const data = await res.text();
  assert.match(
    data,
    /Home page/gi,
    'When a user logs out they should be redirected to the homepage'
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
