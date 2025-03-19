# Интерпретатор. Домашнее задание №13

Разработать систему команд для космических кораблей

## Цель:

Научиться применять интерпретатор.

Необходимо научить игровые объекты реагировать на действия игроков.

## Описание/Пошаговая инструкция выполнения домашнего задания:

Предположим, что приказ имеет следующий вид:

```json
{
    "ID": "ид объекта, которому адресован приказ",
    "action": "действие, которое необходимо выполнить",
    // какие-то специфичные параметры для данного приказа
}
```

Например, вот так может выглядеть приказ танку с id "548" начать двигаться по прямой со скоростью 2.

```json
{
    "id": "548",
    "action": "StartMove",
    "initialVelocity": 2
}
```

Приказы будем представлять также, как и игровые объекты, с помощью интерфейса UObject

## Необходимо реализовать:

1. Команду, которая получает на вход приказ и с помощью IoC выполняет необходимое действие.
2. Необходимо запретить одному игроку отдавать приказы другому игроку.

## Критерии оценки:

1. Задача сдана на проверку. 1 балл
2. Оформлен MR/PR. 1 балл
3. CI. 1 балл.
4. Реализован интерпретатор приказов из п. 1.
   - балл, если с помощью этого интерпретатора можно обработать приказы на старт/стоп движения, выстрел.
   - балла, если преподаватель не может привести пример приказа для управления игровыми объектами, для реализации которого требуется изменить код.
   - балла, если можно обрабатывать не только приказы игровым объектам, но и любе другие.
   - балл, если код покрыт тестами.
5. Реализована защита, которая не позволяет отдавать приказы чужим объектам.
   - балл, если защита реализована любым способом.
   - балла, если защита реализована через отдельные скоупы для каждого игрока.
   - балл, если код покрыт тестами.
6. Максимальная оценка в 10 баллов
7. Задание принято, если оценено не менее, чем в 7 баллов

## Реализация:

Требования к этому ДЗ явно были взяты из другого курса\потока ВУЗа, потому что до сих пор мы никогда не использовали понятие `id объекта`, а реализацию `StartMoveCommand` и `InterpretationCommand` можно найти на [github.com](https://github.com) как  [лабораторную работу 1](https://github.com/Korolevlvan/OOAIP/pull/3#issue-2716599000), [лабораторную работу 2](https://github.com/SeitovaRalina/Spaceship-Labs/pull/7#issue-2059093806)

В лекции рассказывается про паттерн [Интерпретатор](https://metanit.com/sharp/patterns/3.8.php?ysclid=m4kbcr8gxu857363990), но ничего общего с решением ДЗ он не имеет. Поэтому необходимо опять отойти от требований и сделать иначе.

Реализацию, которую вы найдете у меня в ветке [30_Interpreter](https://github.com/hemicide/otus-main-patterns-2024-06/pull/11/files) лишь приближена к требованиям ДЗ, но вписывается в контекст проекта `space battle`, за исключением пары моментов:

- нет разделения прав выполнения команды одного игрока, другому
- не используется очередь выполнения команд.

Работа принята на 10 баллов 🤷

Удачи :)

## Источники:

1. [StartMoveCommand by melskiy](https://github.com/melskiy/Malenkiyprins/blob/lab10Part1/SpaceBattle.Lib/Command/StartMoveCommand.cs)
2. [InterpretingCommand by melskiy](https://github.com/melskiy/Malenkiyprins/blob/lab10_2/SpaceBattle.Lib/Command/InterpretingCommand.cs)
3. [StartMoveCommand by LRKZZ](https://github.com/LRKZZ/ooaip23-24/blob/3b44b8e580e960ebb0b45dee5f3c17843e3b41b1/spacebattle/StartMoveCommand.cs)
4. [InterpretationCommand by LRKZZ](https://github.com/LRKZZ/ooaip23-24/blob/InterpretingCommandBranch/spacebattle/InterpretationCommand.cs)
5. [StartMoveCommand by egor951769794](https://github.com/egor951769794/SpaceBattle/blob/startmovecommand/SpaceBattle.Lib/StartMoveCommand.cs)
6. [InterpretCommand by egor951769794](https://github.com/egor951769794/SpaceBattle/blob/interpret_command/SpaceBattle.Lib/InterpretCommand.cs)
7. [hw13-interpreter by olga-larina 🔥](https://github.com/olga-larina/2022-11-otus-main-patterns-Larina/tree/main/hw13-interpreter)
