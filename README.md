## Hashed and Hierarchical Timing Wheels Implement

[![Greenkeeper badge](https://badges.greenkeeper.io/axetroy/wheel-timer.svg)](https://greenkeeper.io/)
[![Build Status](https://travis-ci.org/axetroy/wheel-timer.svg?branch=master)](https://travis-ci.org/axetroy/wheel-timer)
![License](https://img.shields.io/badge/license-Apache-green.svg)
[![Prettier](https://img.shields.io/badge/Code%20Style-Prettier-green.svg)](https://github.com/prettier/prettier)
![Node](https://img.shields.io/badge/node-%3E=6.0-blue.svg?style=flat-square)
[![npm version](https://badge.fury.io/js/%40axetroy%2Fstruct.svg)](https://badge.fury.io/js/%40axetroy%2Fstruct)
![Size](https://github-size-badge.herokuapp.com/axetroy/wheel-timer.svg)
[![Coverage Status](https://coveralls.io/repos/github/axetroy/wheel-timer/badge.svg?branch=master)](https://coveralls.io/github/axetroy/wheel-timer?branch=master)
[![Dependency](https://david-dm.org/axetroy/wheel-timer.svg)](https://david-dm.org/axetroy/wheel-timer)

![](https://github.com/axetroy/wheel-timer/raw/master/screenshot.png)

## Usage

```javascript
const HashWheelTimer = require('wheel-timer');

const timer = new HashWheelTimer(60);

timer.on('tick', values => {});

timer.add({ uid: 'xxxx-xxxx-xxxx' });

setInterval(() => {
  timer.tick();
}, 1000);
```

## Example

Here is a example to use with multiple time wheel

```javascript
const HashWheelTimer = require('../index');

class SecondTimer extends HashWheelTimer {
  constructor() {
    super(60);
    this.currentIndex = new Date().getSeconds(); // get current minute and set
  }
  tick() {
    const beforeRound = this.round;
    super.tick();
    const afterRound = this.round;

    if (afterRound > beforeRound) {
      minute.tick();
    }
  }
}

class MinuteTimer extends HashWheelTimer {
  constructor() {
    super(60);
    this.currentIndex = new Date().getMinutes(); // get current minute and set
  }
  tick() {
    const beforeRound = this.round;
    super.tick();
    const afterRound = this.round;

    if (afterRound > beforeRound) {
      hour.tick();
    }
  }
}

class HourTimer extends HashWheelTimer {
  constructor() {
    super(24);
    this.currentIndex = new Date().getHours(); // get current hour and set
  }
}

const second = new SecondTimer();
const minute = new MinuteTimer();
const hour = new HourTimer();

second.on('tick', () => {
  console.log(`current second: ${second.currentIndex}`);
});

minute.on('tick', () => {
  console.log(`current minute: ${minute.currentIndex}`);
});

hour.on('tick', () => {
  console.log(`current hour: ${hour.currentIndex}`);
});

setInterval(() => {
  second.tick();
}, 1000);
```

## Contributing

[Contributing Guid](https://github.com/axetroy/wheel-timer/blob/master/CONTRIBUTING.md)

## Contributors

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->

| [<img src="https://avatars1.githubusercontent.com/u/9758711?v=3" width="100px;"/><br /><sub>Axetroy</sub>](http://axetroy.github.io)<br />[💻](https://github.com/axetroy/wheel-timer/commits?author=axetroy) [🐛](https://github.com/axetroy/wheel-timer/issues?q=author%3Aaxetroy) 🎨 |
| :-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |


<!-- ALL-CONTRIBUTORS-LIST:END -->

## License

[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Faxetroy%2Fwheel-timer.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Faxetroy%2Fwheel-timer?ref=badge_large)
