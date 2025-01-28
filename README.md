# praktika

В Java абстрактные методы и классы нужны для того, чтобы задать общий каркас (шаблон) для других классов. Они помогают создавать структуры, где базовые методы или свойства уже определены, а конкретные детали уточняются в наследниках.

Абстрактные классы
Это классы, которые нельзя создавать напрямую (то есть нельзя написать new AbstractClass()). Они служат основой для других классов. Абстрактный класс может содержать:

Абстрактные методы (без реализации).
Обычные методы (с реализацией).
Поля (переменные).
Конструкторы.

abstract class Animal {
    String name;
    // Конструктор
    Animal(String name) {
        this.name = name;
    }
    // Абстрактный метод — реализация будет в потомках
    abstract void makeSound();
    // Обычный метод
    void eat() {
        System.out.println(name + " is eating.");
    }
}

Абстрактные методы
Абстрактные методы не имеют тела (только заголовок). Они обязательны для реализации в дочерних классах.

class Dog extends Animal {
    Dog(String name) {
        super(name);
    }
    @Override
    void makeSound() {
        System.out.println(name + " says: Woof!");
    }
}
class Cat extends Animal {
    Cat(String name) {
        super(name);
    }
    @Override
    void makeSound() {
        System.out.println(name + " says: Meow!");
    }
}

