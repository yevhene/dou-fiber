# React Next (Fiber і далі)

Код презентації та демо: http://github.com/yevhene/present-fiber

Презентація: https://present-fiber.herokuapp.com/

## Fiber

Fiber - це нова архітектура що покладена в основу React 16. І також це назва нового алгоритму погодження (reconciliation). Розпочати знайомство кращє всього з проблеми що вона вирішує.

## Відкладені оновлення (Deferred update)

### Problem

Демо: https://present-fiber-demo.herokuapp.com/

## Фрагменти (Fragments)

Відтепер, не обов'язково обгортати набір елементів, що повертає компонент, в один корневий елемент. Ви можете повертати масиви елементів, що дуже зручно в місцях, де неможливо просто обгорнути набір елементів в `<div>`. Наприклад в роботі з таблицями і списками, якщо компонент має повернути декілька рядків або елементів списку. Також можна повертати строки.

```javascript
const TableHeader = () => {
  return [
    <tr><th colspan="2">Автомобіль</th><th colspan="2">Водій</th></tr>,
    <tr><th>Номер</th><th>Марка</th><th>Позивний</th><th>Телефон</th></tr>,
  ]
}
```

## Кордони помилок (Error boundaries)

Запроваджена нова система обробки помилок. Тепер, якщо в компоненті виникає помилка, можна застосувати новий метод життєвого циклу `componentDidCatch`.

```javascript
class Map extends React.Component {
  constructor(props) {
    super(props)

    this.state = { hasError: false }
  }

  componentDidCatch(error, info) {
    this.setState(() => { hasError: true })
  }

  render() {
    if (this.state.hasError) {
      return <h1>Нажаль сталась прикра помилка.</h1>
    }
    return <MapContent />;
  }
}
```

## Портали (Portals)
Іноді виникає необхідність створити елемент не в рамках поточної ієрахії, а наприклад, як у випадку з модальними вікнами, приєднати до `<body>`. На допомогу приходять портали.

```javascript
render() {
  return ReactDOM.unstable_createPortal(<Modal />, domElement)
}
```

## Migration
### When?
### Callbacks
### Errors
