Здесь собрана часть информации об игре [Chat Wars](https://telegram.me/ChatWarsBot?start=bb6bc6065e8648c0911c8776e277181d), используемой в рамках вспомогательного бота [Redwing](https://t.me/RedwingBot).

Следить за новостями бота можно в канале: [Redwing News](https://t.me/RedwingNews).

Если вы нашли ошибку в предоставленных данных, пожалуйста, [свяжитесь](https://t.me/motw_we) со мной.

# Установка
```
$ npm install chatwarsdata --save
```

# Использование
## ES6
```javascript
import { items, resources, recipes } from 'chatwarsdata';
```

## ES5
```javascript
const { items, resources, recipes } = require('chatwarsdata');
```

# resources.json
```json
{
    "id": 175,
    "name": "Упаковочный материал",
    "aliases": [
        "Упаковочный материал"
    ],
    "cost": 1,
    "weight": 1,
    "recipeId": 145,
    "commands": {
        "buy": "/buy_wrapping"
    }
}
```
* `id` - номер ресурса в игре. Используется в командах:
	* 🏰Замок -> ⚖️Биржа:
		* `/wtb_{id}`
		* `/wtb_{id}_{amount}`
		* `/wts_{id}_{amount}_{price}`
	* 🏰Замок -> ⚒Мастерская -> ⚒Верстак:
		* `/a_{id}`
		* `/d_{id}`
	* `/inv`:
		* `/view_{id}` (для рецептов)
		* `/use_{id}` (для сундуков и горшочка леприкона)
	* [@ChatWarsTradeBot](https://t.me/ChatWarsTradeBot): `/add_{id}`, `/del_{id}`;
	* [deprecated] 🏰Замок -> 🏚Лавка -> Скупка ресурсов: `/s_{id}`.
* `name` - название ресурса, как его отображает [Redwing](https://t.me/RedwingBot), в целом избыточное поле, можно использовать варианты из `aliases`;
* `aliases` - массив имен, под которыми ресурс встречался / встречается в игре. Первый элемент массива всегда соответствует названию ресурса в [@ChatWarsTradeBot](https://t.me/ChatWarsTradeBot);
* [deprecated] `cost` - цена ресурса при продаже гномам;
* `weight` - место, занимаемое ресурсом на складе;
* `recipeId` - номер рецепта, если ресурс можно скрафтить. Иначе поле отсутствует.
* `commands` - команды, связанные с предметом, но не использующие его `id`. На данный момент это только покупка предметов в лавке;

# items.json
```json
{
    "id": 111,
    "name": "Хранитель",
    "aliases": ["Хранитель", "Комплекс Судного дня"],
    "type": "spear",
    "cost": 5270,
    "weight": 180,
    "wrap": 2,
    "attributes": {
        "attack": 17,
        "defense": 15
    },
    "restrictions": {
        "level": 20,
        "defense": 10
    },
    "recipeId": 119
}
```
* `id` - номер предмета в игре. Используется в командах:
	* /inv:
		* `/on_{id}`
		* `/off_{id}`
		* `/use_{id}` (для зелий)
	* /inv -> 🏷Снаряжение: `/bind_{id}`;
	* 🏰Замок -> 🏚Лавка -> 🐾Зверинец -> 🎟Завести питомца: `/getpet_{id}` (для талонов на животных);
	* 🏰Замок -> 🏚Лавка -> Скупка предметов: `/sell_{id}`;
	* 🏰Замок -> ⚒Мастерская -> 🏷Упаковать: `/wrap_{id}`;
	* [@ChatWarsTradeBot](https://t.me/ChatWarsTradeBot): `/add_{id + 1101}`, `/del_{id + 1101}`;
* `name` - имя предмета, в целом избыточное поле, можно использовать варианты из `aliases`;
* `aliases` - массив имен, под которыми предмет встречался / встречается в игре. Первый элемент массива всегда соответствует названию передмета в [@ChatWarsTradeBot](https://t.me/ChatWarsTradeBot);
* `type` - тип предмета, сейчас не всегда точен и требует переделки под реально имеющиеся слоты под вещи у персонажа;
* `cost` - цена предмета при покупке в лавке. При продаже обратно стоимость равняется `floor(0.3 * cost)`. Для предметов, которые нельзя купить в лавке, цена установлена так, чтобы рассчетная стоимость продажи совпадала с игровым значением. `0.1` - индикатор того, что на данный момент значение неизвестно;
* `weight` - место, занимаемое предметом на складе. Для экипировки указано значение в завернутом состоянии (вещи в рюкзаке не занимают места на складе). `0.1` - индикатор того, что на данный момент значение неизвестно;
* `wrap` - количество упаковочного материала необходимое, чтобы запаковать предмет с помощью `/wrap_{id}`. `0.1` - индикатор того, что на данный момент значение неизвестно;
* `attributes` - характеристики предмета (⚔️|🛡|🍀|🔋|⛏|💧);
* `restrictions` - требования, необходимые, чтобы надеть предмет. Вероятно, информация по ним не полная;
* `commands` - команды, связанные с предметом, но не использующие его `id`. На данный момент это только покупка предметов в лавке;
* `recipeId` - номер соответствующего рецепта, если предмет крафтовый.

# recipes.json
```json
{
    "recipeId": 130,
    "name": "Трезубец",
    "type": "item",
    "tier": 4,
    "ingredients": [
        { "id": 102, "count": 1200 },
        { "id": 117, "count": 5 },
        { "id": 123, "count": 23 },
        { "id": 126, "count": 23 },
        { "id": 139, "count": 5 },
        { "id": 144, "count": 1 },
        { "id": 145, "count": 1 },
        { "id": 146, "count": 14 }
    ],
    "mana": 200,
    "status": "confirmed"
}
```
* `recipeId` - номер рецепта. Используется в команде `/craft_{recipeId} {amount}` (🏰Замок -> ⚒Мастерская -> 📖Рецепты);
* `name` - имя изготавливаемого предмета или ресурса;
* `type` - `(resource|item)`;
* `tier` - уровень навыка "Ремесло", необходимый для использования рецепта.
* `ingredients` - массив ингредиентов, входящих в состав ресурса. `id` - номер ресурса, `count` - его количество;
* `mana` - мана, необходимая на использование рецепта мастером, добытчиком или кузенцом. `0.1` - индикатор того, что на данный момент значение неизвестно;
* `status` - статус рецепта:
	* `incomplete` - рецепт не открыт до конца;
	* `complete` - рецепт открыт целиком, но по нему еще никто не крафтил;
	* `confirmed` - рецептом успешно воспользовались.
