---
description: "Úvod do frameworku Vue 3."
image: /images/vue-logo.png
head:
  meta:
    - name: "og:image"
      content: /images/vue-logo.png

published: 2024-09-01 17:00
---

# Predstavenie frameworku Vue 3

![Vue 3 Introduction](/images/vue-logo.png)

## Čo je Vue 3?

Vue.js 3 je progresívny JavaScript framework na vytváranie používateľských rozhraní na webe. Je navrhnutý tak, aby bol postupne prijateľný a môže sa ľahko škálovať medzi knižnicou a plnohodnotným frameworkom.

---

## Prečo si vybrať Vue 3?

Vue 3 prichádza s niekoľkými vzrušujúcimi funkciami, ktoré z neho robia vynikajúcu voľbu pre vývojárov:

- **Composition API:** Tento nový API poskytuje súbor aditívnych, funkčne orientovaných API, ktoré umožňujú flexibilnú kompozíciu logiky komponentov.
- **Rýchlejšie renderovanie:** Vue 3 obsahuje rýchlejší virtuálny DOM a vylepšený výkon za behu.

- **Vylepšená podpora TypeScript:** Kódová základňa Vue 3 je napísaná v TypeScript, čo umožňuje lepšiu integráciu TypeScriptu.

---

## Začíname s Vue 3

Tu je základná konfigurácia aplikácie Vue 3:

```javascript
const { createApp } = Vue;
const app = createApp({
  data() {
    return {
      message: "Hello Vue 3!",
    };
  },
});
app.mount("#app");
```
