# Video.js

[Video.js](https://github.com/videojs/video.js) - это библиотека с открытым исходным кодом, предназначенная для
создания видео плеера.

Сама по себе библиотека очень проста. Дополнительная функциональность поставляется в плагинах(плейлисты, аналитика,
реклама, и расширенные форматы видео - `HLS` или `DASH`).

## Установка

### NPM

```bash
npm install --save video.js
```

### CDN

```html
<script src="http://vjs.zencdn.net/6.9.0/video.js"></script>
```

```html
<link href="http://vjs.zencdn.net/6.9.0/video-js.css" rel="stylesheet">
```

## Инициализация

На странице должен присутствовать тег:

```html
<video class="video-js"></video>
```

Передаем строку содержащую `id` элемента:

```js
let video = videojs('id');
```

Или `DOM` элемент

```js
let video = videojs(document.querySelector('.video-js'));
```

## Опции

Опции передаются вторым параметром:

```js
let video = videojs('my-video', {
    autoplay: false,
});
```

**Основные опции:**

* `autoplay: boolean` - автоматическое воспроизведение;
* `controls: boolean` - отображать ли интерфейс плеера;
* `loop: boolean` - зацикливание воспроизведения видео;
* `muted: boolean` - приглушение звука;
* `poster: string` - ссылка на превью видео;
* `width: string|number` - ширина видео;
* `height: string|number` - высота видео;

**Дополнительные опции:**

* `fluid: boolean` - подгонять ли видео под размер контейнера;
* `aspectRatio: string` - соотношение сторон видео (16:9, 4:3);

## Методы

* `src(string|array)` - позволяет задать источник видео;

   ```js
   video.src('/path/to/video.mp4');

   video.src([
       {
           type: 'video/mp4',
           src: '/path/to/video.mp4',
       },
       {
           type: 'video/webm',
           src: '/path/to/video.webm',
       },
       {
           type: 'video/ogg',
           src: '/path/to/video.ogg',
       },
   ]);
   ```

* `poster(string)` - позволяет задать превью видео;

* `play()` - воспроизводит видео;

* `pause()` - ставит видео на паузу;

* `paused()` - возвращает `true`, если видео стоит на паузе, иначе `false`;

* `dispose()` - полностью удаляет плеер (вызывает событие `dispose`, удаляет все обработчики событий, удаляет `DOM` элементы);

* `volume(number)` - задает горомкость звука (число от `0` до `1`); если вызвать без параметра - возвращает текущее значение;

* `muted(bolean)` - возвращае `true`, если звук выключен, иначе `false`; если передано `true` - выключает звук.

* `requestFullscreen()` - вход в полноэкранный режим;

* `exitFullscreen()` - выход из полноэкранного режима;

* `isFullscreen()` - возвращает `true` если видео находится в полноэкранном режиме, иначе `false`;

* `currentTime(number)` - возвращает текущее место воспроизведения (в секундах); если передать число - устанавливает текущее место;

* `duration()` - возвращает длину видео;

* `remainingTime()` - возвращает оставшееся время;

**Пример:**

```js
let video = videojs('video', {
    controls: true,
    autoplay: false,
    loop: false,
    poster: '/video/cover.jpg',
});

video.src({
    src: '/video/video.mp4',
    withCredentials: true,
});

video.on('ready', () => {
    // ...
});

```

## События

События те же, что у нативного элемента `video`.
Полный список [тут](https://developer.mozilla.org/ru/docs/Web/Guide/Events/Media_events).

**Пример:**

```js
video.on('dispose', () => {
    // ...
});

video.on('play', () => {
    // ...
});

video.on('ended', () => {
    // ...
});
```
