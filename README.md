# vue-loadingbar

## Usage

- 引入模块

```js
import Vue from 'vue';
import LoadingBar from '@liejy/vue-loadingbar';
Vue.use(LoadingBar);

LoadingBar.start();
LoadingBar.update({
  percent: 90, // 0~100
  status: 'success', // success|error
  show: false, // true|false
});
LoadingBar.config({
  height: 2,
  duration: 800,
});
LoadingBar.start();
LoadingBar.finish();
LoadingBar.error();
LoadingBar.destroy();
```
