## Структура данных "дерево"

Деревья - это один из фундаментальных типов данных, который часто применяется в практических проектах. Дерево состоит из узлов, у каждого из которых может быть некоторое (в общем случае произвольное) количество дочерних узлов, связанных с родительским так называемой ветвью. Узел, у которого нету ни одного дочернего узла, называется лист.

Классический пример дерева:
<img src="https://skillsmart.ru/algo/15-121-cm/tree071.png" width=300>

Некоторые области применения:
- управление иерархией данных;
- упрощение поиска информации ([обход дерева](https://ru.wikipedia.org/wiki/%D0%9E%D0%B1%D1%85%D0%BE%D0%B4_%D0%B4%D0%B5%D1%80%D0%B5%D0%B2%D0%B0));
- управление сортированными списками данных;
- парсинг арифметических выражений, оптимизация программ.

## Структура программы

Дерево реализуется с помощью двух классов:
- узел дерева `SimpleTreeNode`;
- дерево `SimpleTree`.

#### Описание классов, их полей и методов

`SimpleTreeNode`
- Конструктор `__init__(self, val=None, parent)` - создает узел с заданными значением и указателем на родительский узел.
- Поле NodeValue` - для записи значения, хранимого в узле (default is None).
- Поле Parent` - поле для указателя на родительский узел. По умолчанию значение None (новый узел не привязан к другим). Наличие поля обеспечивает быстрое выполнение различных операций.
- Поле Children` - поле содержит список дочерних узлов. По умолчанию, пустой список.
- Поле NodeLevel` - поле содержит длину кратчайшего пути из корневого узла в данный, выраженную в количестве ветвей. Наличие данного поля позволяет получить информацию об уровне каждого узла без анализа всего дерева.

`SimpleTree`
- Конструктор `__init__(self, root=None)` - создает дерево (по умолчанию, пустое).
- Поле `Root` - хранит ссылку на корневой узел (default is None).
- метод `AddChild(self, ParentNode, NewChild)` - добавление дочернего узла к данному.       
тест: проверяем наличие добавленного узла
- метод `DeleteNode(self, NodeToDelete)` - удаление некорневого узла вместе со всем поддеревом
тест: проверяем отсутствие удалённого узла и его потомков
- метод `GetAllNodes(self)` - последовательно обойти всё дерево и сформировать список всех узлов в произвольном порядке 
- метод `FindNodesByValue(self, val)` - найти список подходящих узлов по заданному значению
тест: проверяем результат с тестовым списком
- метод `MoveNode(self, OriginalNode, NewParent)` - переместить некорневой узел дочерним узлом в другое место дерева (вместе с его поддеревом)
тест: проверяем, что узел отсутствует там где был исходно и появился в новом месте
- метод `Count(self)` - подсчитать общее количество узлов в дереве
тест: проверяем на контрольном дереве количество узлов 
- метод `LeafCount(self)` - подсчитать общее количество листьев в дереве
тест: проверяем на контрольном дереве количество листьев 

## Распределение исходного кода по файлам проекта

[Структура данных "дерево"](SimpleTree.py)

[Модульные тесты](SimpleTree_test.py)
