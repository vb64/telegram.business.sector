# Справочник товаров для ParcelTeleBot

В редакторе справочника товаров вы можете скачать текущий справочник в виде json-файла, отредактировать его содержимое и затем загрузить в редактор справочника товаров. При загрузке такого файла его данные заменяют собой текущее содержание справочника товаров компании, удаляются все существующие заявки и документы компании, поскольку они содержат ссылки на старые элементы справочника, которые удаляются при загрузке json-файла. Кроме того, по той же причине, очищаются шаблоны заявок на всех точках компании.

Списки точек и сотрудников компании остаются прежними.

Справочник товаров представляет собой текстовый файл в формате json, строки которого должны быть в кодировке UTF-8.

Пустому списку товаров соответствует файл со следующим содержанием:

```
{}
```
Чтобы добавить два товара в корневой каталог справочника, нужно отредактировать файл следующим образом:

```
{
 "": [
  ["Товар1"],
  ["Товар2"]
 ]
}
```

Пробелы и переводы строки являются необязательными и предназначены для лучшей читаемости содержимого. Файл можно создавать без них. Например, следующий фрагмент идентичен предыдущему:

```
{"":[["Товар1"],["Товар2"]]}
```

Каждый товар, помимо первого поля наименования, может иметь два необязательных дополнительных поля:

- описание
- идентификатор

```
{
 "": [
  ["Товар1, шт", "99 рублей за штуку", "XXYY1234"],
  ["Товар2, кг", "АКЦИЯ!!!"]
 ]
}
```

Третье поле может содержать уникальный идентификатор товара во внешних программах. Его значение можно использовать его при обмене данными с этими программами.

Справочник товаров может содержать вложенные подкаталоги товаров. Чтобы добавить в корневой каталог справочника подкаталог "Каталог1", содержащий пустой каталог "Каталог2", файл нужно отредактировать таким образом:

```
{
 "": [
  ["Товар1, шт", "99 рублей за штуку", "XXYY1234"],
  ["Товар2, кг", "АКЦИЯ!!!"]
 ],
 "Каталог1": {
  "Каталог2": {}
 }
}
```

В подкаталоги можно добавлять товары, как в корневой каталог справочника. Для добавления Товар3 в Каталог2 и Товар4 в Каталог1 файл data.json нужно изменить следующим образом:

```
{
 "": [
  ["Товар1, шт", "99 рублей за штуку", "XXYY1234"],
  ["Товар2, кг", "АКЦИЯ!!!"]
 ],
 "Каталог1": {
  "Каталог2": {
   "": [
    ["Товар3"]
   ],
  "": [
   ["Товар4"]
  ]
  }
 }
}
```
