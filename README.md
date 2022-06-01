## Demo ⚡
[https://markmaksi74.github.io/countdown/](https://markmaksi74.github.io/countdown/)

## Features 🥁
- Set a custom countdown
- Video background from [https://pixabay.com/](https://pixabay.com/)
- The countdown is saved in localStorage

## Techniques 🛠
- Set responsive video background
- We put video overlay over low quality videos, so it's ok to use 720p video quality
- Basic dealing with Date object

## Lessons Learned 📚
### CSS
- Make `<li>` elements next to each others: 
```
li {
  display: inline-block; /* in one line next to each others */
  list-style-type: none; /* removes the dots */
}
```

- Create animations
```
.complete-title {
  animation: complete 4s infinite;
}
@keyframes complete {
    0% {
      color: rgb(233, 12, 12);
    }
}
```

### Javascript
- `new Date()` gets the current date and time with the system timezone with the right UTC offset

- `new Date().toISOString()` returns a string in simplified extended ISO format for both date and the timezone is always zero UTC offset

- `new Date().toISOString().split("T")[0]` returns a string in simplified extended ISO format for date only

- The code below returns a string in simplified extended ISO format for both date and the timezone is the system timezone with the right UTC offset

```
function toIsoString(date) {
  var tzo = -date.getTimezoneOffset(),
      dif = tzo >= 0 ? '+' : '-',
      pad = function(num) {
          return (num < 10 ? '0' : '') + num;
      };

  return date.getFullYear() +
      '-' + pad(date.getMonth() + 1) +
      '-' + pad(date.getDate()) +
      'T' + pad(date.getHours()) +
      ':' + pad(date.getMinutes()) +
      ':' + pad(date.getSeconds()) +
      dif + pad(Math.floor(Math.abs(tzo) / 60)) +
      ':' + pad(Math.abs(tzo) % 60);
}

var dt = new Date();
console.log(toIsoString(dt));
```

- Get submitted date in minutes and hours, assuming `distance` is in milliseconds:
```
const second = 1000;
const minute = second * 60;
const hour = minute * 60;
const day = hour * 24;

const days = Math.floor(distance / day);
const hours = Math.floor((distance % day) / hour);
const minutes = Math.floor((distance % day) / minute);
const seconds = Math.floor((distance % minute) / second);
```
