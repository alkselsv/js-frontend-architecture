# Состояние форм

В этой задаче предстоит реализовать форму регистрации. Форма состоит из 4 полей (имя, email, пароль и его подтверждение). Начальный HTML доступен в `./index.html`.

Форма должна быть контролируемой. Во время ввода данных выполняется валидация сразу всех полей (для простоты). Валидацию нужно построить на базе библиотеки `yup`. В коде уже описана вся нужная валидация. Осталось только вызвать проверку и записать тексты ошибок в объект состояния.

Кнопка отправки формы по умолчанию заблокирована. Она разблокируется, когда валидна вся форма целиком и блокируется сразу, как только появляется невалидное значение.

HTML, когда введены невалидные email и password (один из возможных вариантов):

```html
<div data-container="sign-up">
  <form data-form="sign-up" method="post">
    <div class="form-group">
      <label for="sign-up-name">Name</label>
      <input id="sign-up-name" type="text" class="form-control" name="name">
    </div>
    <div class="form-group">
      <label for="sign-up-email">Email<sup>*</sup></label>
      <!-- Если поле невалидно, то добавляется класс is-invalid -->
      <input id="sign-up-email" required="" type="email" class="form-control is-invalid" name="email">
      <div class="invalid-feedback">Value is not a valid email</div>
    </div>
    <div class="form-group">
      <label for="sign-up-password">Password<sup>*</sup></label>
      <input id="sign-up-password" required="" type="password" class="form-control is-invalid" name="password">
      <div class="invalid-feedback">Must be at least 6 letters</div>
    </div>
    <div class="form-group">
      <label for="sign-up-password-confirmation">Password Confirmation<sup>*</sup></label>
      <input id="sign-up-password-confirmation" required="" type="password" class="form-control" name="passwordConfirmation">
    </div>
    <input type="submit" class="btn btn-primary" value="Submit" disabled>
  </form>
</div>
```

После того, как все поля заполнены правильно, данные формы отправляются POST-запросом на адрес `/users`. Во время отправки кнопка отправки блокируется (во избежание двойной отправки).

Когда форма отправлена, HTML меняется на следующий:

```html
<div data-container="sign-up">User Created!</div>
```

## Задание

Экспортируйте функцию по умолчанию, которая реализует всю необходимую логику.

## Подсказки

- Документация [axios](https://github.com/axios/axios). Он работает очень похоже на fetch.
- Для навигации по DOM-дереву полезно использовать [nextElementSibling](https://developer.mozilla.org/en-US/docs/Web/API/Element/nextElementSibling).
- API on-change позволяет получить [предыдущее значение](https://github.com/sindresorhus/on-change#usage).
- Текст ошибок может отличаться от примера выше и подставляется `yup`.
- Данные формы можно отправлять в любом виде.