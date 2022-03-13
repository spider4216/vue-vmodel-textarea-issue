# vue v-model textarea mobile devices issue

## Problem

v-model on textarea and input forms doesn't work properly on some mobile devices. When user type something, value sync only after unfocus (blur)

## Code

```
<div id="app">
  <textarea v-model="text"></textarea>
  <div><span>{{ text }}</span></div>
</div>

<script type="text/javascript">
      Vue.createApp({
          data() {
              return {
                  text: ''
              }
          }
      }).mount('#app');
</script>
```

Works on most mobile devices and browsers, i.e Meizu C9 PRO (android 8.1.0 Chrome 99.0.4844.58)

![Image](https://github.com/spider4216/vue-vmodel-textarea-issue/blob/main/old_meizu_work.gif?raw=true)

But doen't work correctly on several mobile devices, i.e. Samsung Galaxy A50 (Android 11 Chrome 99.0.4844.58)

![Image](https://github.com/spider4216/vue-vmodel-textarea-issue/blob/main/old_samsung_not_work.gif?raw=true)

Our technical support kept information from clients about devices where problems also occured:

- Samsung s10e (internal browser)
- Xiaomi Mi6 (internal browser)
- Apple Iphone XS (Safari v12.10.5-go)

But via "@input" it work's fine

```
<div id="app">
    <textarea @input="typing" type="text"></textarea>
    <div><span>{{ text }}</span></div>
</div>

<script type="text/javascript">
        Vue.createApp({
            data() {
                return {
                    text: ''
                }
            },
            methods: {
                typing(event) {
                    this.text = event.target.value
                }
            }
        }).mount('#app');
</script>
```

Samsung Galaxy A50

![Image](https://github.com/spider4216/vue-vmodel-textarea-issue/blob/main/new_samsung_work.gif?raw=true)

## Versions

Vue 3
