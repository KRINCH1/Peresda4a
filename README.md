ЛЕКЦИИ ПО КТ (АРХИТЕКТУРА КОРПОРАТИВНЫХ ПРИЛОЖЕНИЙ)
КТ №1: Работа с Git
Цель работы
Научиться работать с системой контроля версий Git: создавать локальные и удалённые репозитории, выполнять коммиты, работать с ветками, сливать их с разрешением конфликтов, откатывать изменения, синхронизировать с GitHub.

Задание (по балльно-рейтинговой системе)
Запустить Git GUI или консоль Git.

Создать новый репозиторий в папке по фамилии студента.

Добавить файлы и зафиксировать состояние (commit).

Внести изменения и снова зафиксировать.

Создать новую ветку, внести изменения (добавить новый файл, изменить существующий: добавить, удалить и изменить строки), зафиксировать.

Переключиться на ветку master, внести изменения (добавить новый файл, изменить существующие файлы: добавить, удалить, изменить строки), зафиксировать.

Выполнить слияние веток и разрешить конфликты.

Просмотреть дерево изменений (историю).

Выполнить откат изменений в ветке.

Создать удалённый репозиторий на GitHub.

Отправить данные на удалённый репозиторий (один студент), добавить участников.

Получить данные из удалённого репозитория (остальные студенты).

Изменить полученные данные, зафиксировать и отправить на удалённый репозиторий (все студенты).

Снова получить данные из удалённого репозитория.

Просмотреть историю изменений.

Ход выполнения с пояснениями
1. Создание локального репозитория

Репозиторий — это хранилище всех версий файлов. Инициализация создаёт скрытую папку .git, где Git хранит историю.

bash
mkdir KRINCH1
cd KRINCH1
git init
2. Первый коммит

Коммит — это снимок состояния всех файлов на момент времени. Каждый коммит имеет уникальный хеш.

bash
echo "Version 1" > hello.txt
git add hello.txt
git commit -m "Первый коммит"
3. Второй коммит (изменение)

Git отслеживает изменения строк. При новом коммите сохраняется только разница.

bash
echo "Version 2" > hello.txt
git commit -am "Второй коммит"
4. Создание ветки feature и изменения в ней

Ветка — это отдельная линия разработки. Изменения в одной ветке не влияют на другие.

bash
git branch feature
git checkout feature
echo "Feature file" > new.txt
echo "Version 2 + change in feature" > hello.txt
git add .
git commit -m "Изменения в ветке feature"
5. Изменения в ветке master

bash
git checkout master
echo "Master new file" > master.txt
echo "Version 2 + change in master" > hello.txt
git add .
git commit -m "Изменения в master"
6. Слияние веток и разрешение конфликта

При слиянии Git пытается объединить изменения автоматически. Конфликт возникает, если одни и те же строки изменены по-разному.

bash
git merge feature
Конфликт в hello.txt. Открываем файл, видим:

text
<<<<<<< HEAD
Version 2 + change in master
=======
Version 2 + change in feature
>>>>>>> feature
Вручную исправляем, оставляя нужный текст (можно объединить обе строки). Затем:

bash
git add hello.txt
git commit -m "Resolved merge conflict"
7. Просмотр истории и дерева изменений

bash
git log --graph --oneline --all
Это показывает граф коммитов, ветки и слияния.

8. Откат изменений в ветке feature

Откат удаляет последний коммит, возвращая состояние на шаг назад.

bash
git checkout feature
git reset --hard HEAD~1
9. Создание удалённого репозитория на GitHub

На сайте GitHub создаётся пустой репозиторий Peresda4a. Затем связываем локальный с удалённым:

bash
git remote add origin https://github.com/KRINCH1/Peresda4a.git
git push -u origin master
10. Добавление участников

В настройках репозитория Settings → Collaborators добавляются другие студенты.

11. Получение данных другими студентами

bash
git clone https://github.com/KRINCH1/Peresda4a.git
12. Изменение, коммит и отправка изменений всеми студентами

bash
echo "new data" > data.txt
git add .
git commit -m "Added data"
git push
13. Получение изменений из удалённого репозитория

bash
git pull
Вывод по КТ №1
В ходе работы освоены все основные операции Git: инициализация репозитория, фиксация изменений (commit), создание и переключение веток (branch, checkout), слияние (merge) с разрешением конфликтов, просмотр истории (log), откат изменений (reset), работа с удалённым репозиторием (remote, push, pull, clone). Эти навыки необходимы для командной разработки и контроля версий программных проектов.

КТ №2: Разработка UML диаграмм
Цель работы
Научиться создавать диаграммы UML для визуализации архитектуры программных систем. По любой предметной области построить: диаграмму прецедентов, диаграмму классов, диаграмму активностей, диаграмму последовательности.

Предметная область: Интернет-магазин
1. Диаграмма прецедентов (Use Case Diagram)
Диаграмма прецедентов показывает, какие действия могут выполнять пользователи (актёры) в системе. Актёры — это внешние сущности, взаимодействующие с системой. Прецеденты — это конкретные функции системы.

Актёры:

Покупатель (обычный пользователь)

Администратор (управляет магазином)

Прецеденты для покупателя:

Просмотр каталога товаров

Добавление товара в корзину

Оформление заказа

Оплата заказа

Прецеденты для администратора:

Управление товарами (добавление, редактирование, удаление)

Просмотр всех заказов

Текстовое описание связи:

text
Покупатель ──(добавить товар)──→ Корзина
Покупатель ──(оформить заказ)──→ Заказ
Покупатель ──(оплатить)───────→ Оплата
Администратор ──(управлять товарами)──→ Товар
Администратор ──(просмотреть заказы)──→ Заказ
2. Диаграмма классов (Class Diagram)
Диаграмма классов описывает структуру системы: классы, их атрибуты, методы и связи между ними. Типы связей: наследование (стрелка с пустым треугольником), ассоциация (простая линия), композиция (ромб).

Классы и их атрибуты:

Класс	Атрибуты
Пользователь	id: int, имя: string, email: string
Покупатель	адрес: string (наследует Пользователя)
Администратор	права: string (наследует Пользователя)
Товар	id: int, название: string, цена: float
Корзина	товары: List<Товар>
Заказ	id: int, статус: string
Оплата	сумма: float, метод: string
Связи:

Пользователь ← Покупатель (наследование)

Пользователь ← Администратор (наследование)

Покупатель → Корзина (ассоциация, один к одному)

Корзина → Товар (композиция: корзина состоит из товаров)

Покупатель → Заказ (ассоциация, один ко многим)

Заказ → Оплата (ассоциация, один к одному)

Текстовое представление диаграммы:

text
┌─────────────────┐     ┌─────────────────┐
│   Пользователь   │     │     Покупатель   │
│  - id: int       │<────│  - адрес: string │
│  - имя: string   │     └─────────────────┘
│  - email: string │              │
└─────────────────┘              │
         △                       │
         │                       ▼
┌─────────────────┐     ┌─────────────────┐
│  Администратор   │     │     Корзина      │
│  - права: string │     │ - товары: List   │
└─────────────────┘     └─────────────────┘
                                  │
                                  ▼
                        ┌─────────────────┐
                        │     Товар        │
                        │ - id: int        │
                        │ - название: string│
                        │ - цена: float    │
                        └─────────────────┘
3. Диаграмма активностей (Activity Diagram)
Диаграмма активностей описывает алгоритм или бизнес-процесс в виде потока управления. Начало — чёрный круг, конец — чёрный круг с ободком. Действия — прямоугольники со скруглёнными углами. Ветвления — ромбы.

Процесс: Оформление заказа покупателем

text
[Начало]
    │
    ▼
Просмотр каталога товаров
    │
    ▼
Добавление товара в корзину
    │
    ▼
Оформление заказа
    │
    ▼
Выбор способа оплаты
    │
    ▼
Оплата заказа
    │
    ▼
Подтверждение заказа
    │
    ▼
[Конец]
4. Диаграмма последовательности (Sequence Diagram)
Диаграмма последовательности показывает обмен сообщениями между объектами во времени. Вертикальные линии — "линии жизни" объектов. Стрелки — сообщения (вызовы методов). Время идёт сверху вниз.

Процесс: Покупатель оформляет заказ

text
Покупатель    Система       Корзина       Оплата
    │            │             │            │
    │──Добавить товар─────────>│            │
    │            │             │            │
    │<──Товар добавлен─────────│            │
    │            │             │            │
    │──Оформить заказ──────────>│            │
    │            │             │            │
    │            │──Создать заказ──────────>│
    │            │             │            │
    │            │<──Заказ создан───────────│
    │            │             │            │
    │──Выбрать оплату──────────>│            │
    │            │             │            │
    │            │──Обработать оплату──────>│
    │            │             │            │
    │            │<──Оплата подтверждена────│
    │            │             │            │
    │<──Заказ подтвержден───────│            │
Вывод по КТ №2
Созданы четыре основных типа UML диаграмм для предметной области "Интернет-магазин". Диаграмма прецедентов выявила требования к системе. Диаграмма классов определила структуру данных. Диаграмма активностей описала алгоритм оформления заказа. Диаграмма последовательности показала взаимодействие объектов. UML является стандартным языком для проектирования архитектуры корпоративных приложений.

КТ №3: Порождающие паттерны
Цель работы
Создать по одному примеру на каждый порождающий паттерн проектирования. Порождающие паттерны решают проблемы создания объектов, делая систему независимой от способа создания, композиции и представления объектов.

Паттерн 1: Singleton (Одиночка)
Проблема: Нужно гарантировать, что у класса есть только один экземпляр, и предоставить к нему глобальную точку доступа (например, для подключения к базе данных или логгера).

Решение: Приватный конструктор, статическое поле с единственным экземпляром, статический метод для его получения. Ленивая инициализация — создание при первом запросе.

Пример: Логгер системы

java
class Singleton {
    private static Singleton instance = null;
    
    private Singleton() {}  // приватный конструктор
    
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
    
    public void setUp() {
        System.out.println("Singleton: setUp");
    }
}

public class SingletonTest {
    public static void main(String[] args) {
        Singleton singleton = Singleton.getInstance();
        singleton.setUp();
    }
}
Объяснение: При первом вызове getInstance() создаётся объект. При последующих вызовах возвращается тот же самый экземпляр.

Паттерн 2: Factory Method (Фабричный метод)
Проблема: Код должен работать с разными типами объектов, но заранее неизвестно, с какими именно. Нужно вынести логику создания объектов в отдельный метод.

Решение: Создаётся интерфейс продукта и множество его реализаций. Фабричный метод определяет, какой именно продукт создать, на основе входного параметра.

Пример: Определение операционной системы

java
interface OS {
    void getOS();
}

class WindowsOS implements OS {
    public void getOS() {
        System.out.println("Применить для Windows");
    }
}

class LinuxOS implements OS {
    public void getOS() {
        System.out.println("Применить для Linux");
    }
}

class MacOS implements OS {
    public void getOS() {
        System.out.println("Применить для Mac");
    }
}

class Factory {
    public OS getCurrentOS(String inputs) {
        if (inputs.equals("windows")) {
            return new WindowsOS();
        } else if (inputs.equals("linux")) {
            return new LinuxOS();
        } else if (inputs.equals("mac")) {
            return new MacOS();
        }
        return null;
    }
}

public class FactoryTest {
    public static void main(String[] args) {
        Factory factory = new Factory();
        OS os = factory.getCurrentOS("linux");
        os.getOS();
    }
}
Объяснение: Клиентский код не зависит от конкретных классов WindowsOS, LinuxOS, MacOS. Фабрика решает, какой объект создать.

Паттерн 3: Abstract Factory (Абстрактная фабрика)
Проблема: Нужно создавать семейства связанных объектов без привязки к конкретным классам. Например, фабрика автомобилей для разных стран.

Решение: Создаётся интерфейс абстрактной фабрики, который объявляет методы для создания каждого продукта. Затем создаются конкретные фабрики для разных вариаций.

Пример: Фабрика автомобилей для Украины

java
interface Lada {
    long getLadaPrice();
}

interface Ferrari {
    long getFerrariPrice();
}

interface Porsche {
    long getPorschePrice();
}

interface CarFactory {
    Lada getLada();
    Ferrari getFerrari();
    Porsche getPorsche();
}

class UaLadaImpl implements Lada {
    public long getLadaPrice() {
        return 1000;
    }
}

class UaFerrariImpl implements Ferrari {
    public long getFerrariPrice() {
        return 3000;
    }
}

class UaPorscheImpl implements Porsche {
    public long getPorschePrice() {
        return 2000;
    }
}

class UaCarFactory implements CarFactory {
    public Lada getLada() {
        return new UaLadaImpl();
    }
    
    public Ferrari getFerrari() {
        return new UaFerrariImpl();
    }
    
    public Porsche getPorsche() {
        return new UaPorscheImpl();
    }
}
Объяснение: Если потребуется создать фабрику для другой страны (UsaCarFactory), достаточно реализовать интерфейс CarFactory с другими ценами.

Паттерн 4: Builder (Строитель)
Проблема: Создание сложного объекта с множеством необязательных частей. Конструктор с десятком параметров неудобен и трудно читаем.

Решение: Отделяется конструирование сложного объекта от его представления. Один и тот же процесс сборки может создавать разные представления.

Пример: Сборка автомобиля

java
class Car {
    public void buildBase() {
        System.out.println("Делаем кузов");
    }
    public void buildWheels() {
        System.out.println("Ставим колеса");
    }
    public void buildEngine(String engineType) {
        System.out.println("Ставим двигатель: " + engineType);
    }
}

interface Engine {
    String getEngineType();
}

class OneEngine implements Engine {
    public String getEngineType() {
        return "Первый двигатель";
    }
}

class TwoEngine implements Engine {
    public String getEngineType() {
        return "Второй двигатель";
    }
}

abstract class Builder {
    protected Car car;
    public Builder() {
        car = new Car();
    }
    public abstract void buildCar();
    public Car getCar() {
        return car;
    }
}

class OneBuilderImpl extends Builder {
    public void buildCar() {
        car.buildBase();
        car.buildWheels();
    }
}
Объяснение: Builder определяет шаги сборки. Конкретный строитель OneBuilderImpl решает, какие шаги выполнять. Клиент получает готовый объект через getCar().

Паттерн 5: Prototype (Прототип)
Проблема: Создание нового объекта путём копирования существующего прототипа, когда создание объекта дороже копирования или требуется скрыть сложность создания.

Решение: Объект сам поддерживает копирование через метод clone() или copy(). Позволяет создавать объекты на основе существующих.

Пример: Копирование сложного объекта

java
interface Copyable {
    Copyable copy();
}

class ComplicatedObject implements Copyable {
    private String type;
    
    public void setType(String type) {
        this.type = type;
    }
    
    public String getType() {
        return type;
    }
    
    public ComplicatedObject copy() {
        ComplicatedObject clone = new ComplicatedObject();
        clone.setType(this.type);
        return clone;
    }
}

public class PrototypeTest {
    public static void main(String[] args) {
        ComplicatedObject prototype = new ComplicatedObject();
        prototype.setType("Type ONE");
        
        ComplicatedObject clone = prototype.copy();
        System.out.println("Cloned object type: " + clone.getType());
    }
}
Объяснение: Метод copy() создаёт новый объект и копирует все поля из текущего. Клиент получает независимую копию.

Вывод по КТ №3
Реализованы пять порождающих паттернов: Singleton (один экземпляр), Factory Method (создание по параметру), Abstract Factory (семейства объектов), Builder (пошаговая сборка), Prototype (копирование). Каждый решает свою задачу создания объектов и повышает гибкость системы.

КТ №4: Структурные паттерны
Цель работы
Создать по одному примеру на выбранные структурные паттерны. Структурные паттерны определяют, как классы и объекты объединяются в более крупные структуры.

Паттерн 1: Adapter (Адаптер)
Проблема: Нужно использовать класс с несовместимым интерфейсом. Например, у нас есть класс ABank с методом getBalance(), но клиент ожидает метод getBalance() от PBank.

Решение: Адаптер оборачивает несовместимый класс и предоставляет нужный интерфейс. Он получает вызовы на своём интерфейсе и переводит их в вызовы адаптируемого класса.

Пример: Адаптер для банка

java
class PBank {
    private int balance;
    public PBank() {
        balance = 100;
    }
    public void getBalance() {
        System.out.println("PBank balance = " + balance);
    }
}

class ABank {
    private int balance;
    public ABank() {
        balance = 200;
    }
    public void getBalance() {
        System.out.println("ABank balance = " + balance);
    }
}

class PBankAdapter extends PBank {
    private ABank abank;
    
    public PBankAdapter(ABank abank) {
        this.abank = abank;
    }
    
    @Override
    public void getBalance() {
        abank.getBalance();
    }
}

public class AdapterTest {
    public static void main(String[] args) {
        PBank pbank = new PBank();
        pbank.getBalance();
        
        PBankAdapter abank = new PBankAdapter(new ABank());
        abank.getBalance();
    }
}
Объяснение: PBankAdapter наследует PBank (принимает его интерфейс), но внутри использует ABank. Клиент вызывает getBalance() и получает результат от ABank.

Паттерн 2: Composite (Компоновщик)
Проблема: Нужно работать с группой объектов так же, как с отдельным объектом. Например, отрисовать один автомобиль или группу автомобилей.

Решение: Компоновщик объединяет объекты в древовидную структуру. Компонент — общий интерфейс для листьев и контейнеров. Лист — простой объект. Контейнер может содержать другие компоненты.

Пример: Рисование группы автомобилей

java
import java.util.ArrayList;
import java.util.List;

interface Car {
    void draw(String color);
}

class SportCar implements Car {
    public void draw(String color) {
        System.out.println("SportCar color: " + color);
    }
}

class UnknownCar implements Car {
    public void draw(String color) {
        System.out.println("UnknownCar color: " + color);
    }
}

class Drawing implements Car {
    private List<Car> cars = new ArrayList<>();
    
    public void draw(String color) {
        for (Car car : cars) {
            car.draw(color);
        }
    }
    
    public void add(Car car) {
        this.cars.add(car);
    }
    
    public void clear() {
        System.out.println("Clearing all cars");
        this.cars.clear();
    }
}

public class CompositeTest {
    public static void main(String[] args) {
        Car sportCar = new SportCar();
        Car unknownCar = new UnknownCar();
        
        Drawing drawing = new Drawing();
        drawing.add(sportCar);
        drawing.add(unknownCar);
        
        drawing.draw("green");
        drawing.clear();
        
        drawing.add(sportCar);
        drawing.add(unknownCar);
        drawing.draw("white");
    }
}
Объяснение: Drawing реализует тот же интерфейс Car, что и отдельные автомобили. Клиент может вызвать draw() для одного автомобиля или для группы через Drawing.

Паттерн 3: Decorator (Декоратор)
Проблема: Нужно динамически добавлять новые обязанности объекту без изменения его кода и без использования наследования (которое статично и может привести к взрывному росту числа подклассов).

Решение: Декоратор оборачивает объект и добавляет новое поведение до или после вызова исходного объекта. Декораторы можно накладывать друг на друга.

Пример: Добавление цвета к автомобилю

java
interface Car {
    void draw();
}

class SportCar implements Car {
    public void draw() {
        System.out.println("SportCar");
    }
}

class UnknownCar implements Car {
    public void draw() {
        System.out.println("UnknownCar");
    }
}

abstract class CarDecorator implements Car {
    protected Car decorated;
    
    public CarDecorator(Car decorated) {
        this.decorated = decorated;
    }
    
    public void draw() {
        decorated.draw();
    }
}

class BlueCarDecorator extends CarDecorator {
    public BlueCarDecorator(Car decorated) {
        super(decorated);
    }
    
    public void draw() {
        decorated.draw();
        setColor();
    }
    
    private void setColor() {
        System.out.println("Color: blue");
    }
}

public class DecoratorTest {
    public static void main(String[] args) {
        Car sportCar = new SportCar();
        Car blueUnknownCar = new BlueCarDecorator(new UnknownCar());
        
        sportCar.draw();
        System.out.println();
        blueUnknownCar.draw();
    }
}
Объяснение: BlueCarDecorator добавляет цвет к любому автомобилю, не изменяя классы SportCar или UnknownCar. Декоратор вызывает исходный метод draw(), затем добавляет setColor().

Паттерн 4: Proxy (Заместитель)
Проблема: Нужно контролировать доступ к объекту (ленивая загрузка, кэширование, проверка прав). Создание реального объекта дорого, поэтому создавать его нужно только когда понадобится.

Решение: Заместитель имеет тот же интерфейс, что и реальный объект. Он хранит ссылку на реальный объект и создаёт его только при первом вызове метода.

Пример: Ленивая загрузка изображения

java
interface Image {
    void display();
}

class RealImage implements Image {
    private String file;
    
    public RealImage(String file) {
        this.file = file;
        load(file);
    }
    
    private void load(String file) {
        System.out.println("Загрузка " + file);
    }
    
    public void display() {
        System.out.println("Просмотр " + file);
    }
}

class ProxyImage implements Image {
    private String file;
    private RealImage image;
    
    public ProxyImage(String file) {
        this.file = file;
    }
    
    public void display() {
        if (image == null) {
            image = new RealImage(file);
        }
        image.display();
    }
}

public class ProxyTest {
    public static void main(String[] args) {
        Image image = new ProxyImage("test.jpg");
        image.display();  // загружает и показывает
        image.display();  // только показывает (кэш)
    }
}
Объяснение: Реальное изображение загружается только при первом вызове display(). При повторных вызовах используется уже загруженный объект. Это экономит ресурсы.

Вывод по КТ №4
Реализованы четыре структурных паттерна: Adapter (преобразует интерфейс), Composite (объединяет объекты в дерево), Decorator (добавляет обязанности динамически), Proxy (контролирует доступ). Эти паттерны позволяют гибко строить сложные структуры классов.

КТ №5: Дополнительные паттерны
Цель работы
Создать по одному примеру на дополнительные паттерны. В рамках данной КТ рассмотрены паттерны, которые часто используются в архитектуре корпоративных приложений: Bridge, Chain of Responsibility, Command, Observer, State, Strategy.

Паттерн 1: Bridge (Мост)
Проблема: Нельзя размножать подклассы при наличии нескольких независимых измерений (тип автомобиля и тип двигателя). Наследование приведёт к комбинаторному взрыву.

Решение: Разделить абстракцию и реализацию на две независимые иерархии, связав их через композицию.

Пример: Автомобиль с разными двигателями

java
interface Engine {
    void setEngine();
}

abstract class Car {
    protected Engine engine;
    
    public Car(Engine engine) {
        this.engine = engine;
    }
    
    abstract public void setEngine();
}

class SportCar extends Car {
    public SportCar(Engine engine) {
        super(engine);
    }
    
    public void setEngine() {
        System.out.print("SportCar engine: ");
        engine.setEngine();
    }
}

class UnknownCar extends Car {
    public UnknownCar(Engine engine) {
        super(engine);
    }
    
    public void setEngine() {
        System.out.print("UnknownCar engine: ");
        engine.setEngine();
    }
}
Объяснение: Иерархия Car (SportCar, UnknownCar) отделена от иерархии Engine. Любой двигатель можно поставить в любую машину без создания подклассов.

Паттерн 2: Chain of Responsibility (Цепочка обязанностей)
Проблема: Запрос должен быть обработан одним из нескольких объектов, но обработчик заранее неизвестен. Нужно избежать жёсткой привязки отправителя к получателю.

Решение: Объекты-обработчики связываются в цепочку. Запрос передаётся по цепочке, пока какой-то обработчик не примет его.

Пример (в общем виде): Логгеры разных уровней (INFO, DEBUG, ERROR), система валидации, фильтры в веб-приложениях.

Паттерн 3: Command (Команда)
Проблема: Нужно параметризовать объекты выполняемым действием, ставить действия в очередь, логировать их или поддерживать отмену.

Решение: Команда инкапсулирует запрос как объект, позволяя передавать его, хранить и выполнять в разное время.

Пример (в общем виде): Кнопки в графическом интерфейсе (каждая кнопка — команда), поддержка Undo/Redo, транзакции.

Паттерн 4: Observer (Наблюдатель)
Проблема: При изменении состояния одного объекта нужно уведомлять множество других объектов. Необходима слабая связанность.

Решение: Издатель (субъект) хранит список подписчиков (наблюдателей) и уведомляет их об изменениях.

Пример (в общем виде): Подписка на новости, обновление UI при изменении данных, событийная модель в GUI.

Паттерн 5: State (Состояние)
Проблема: Поведение объекта зависит от его состояния, и объект должен менять поведение во время выполнения. Длинные условные операторы (if/else) становятся нечитаемыми.

Решение: Состояние выносится в отдельные классы. Объект делегирует поведение текущему состоянию.

Пример (в общем виде): Заказ может быть в состояниях "Новый", "Оплачен", "Отправлен", "Доставлен". В каждом состоянии его методы ведут себя по-разному.

Паттерн 6: Strategy (Стратегия)
Проблема: Нужно использовать разные алгоритмы (стратегии) в одном объекте, с возможностью замены алгоритма во время выполнения.

Решение: Алгоритмы выносятся в отдельные классы, реализующие общий интерфейс. Контекст содержит ссылку на стратегию и делегирует ей выполнение.

Пример (в общем виде): Сортировка массива разными алгоритмами, расчёт налогов разными формулами, сжатие файлов разными методами.

Конкретный реализованный пример на основе ваших файлов — Decorator (уже был в КТ4)
Ваш файл photo_2026-05-19_18-18-52.jpg содержит пример абстрактной фабрики (CarFactory, UaCarFactory, Lada, Ferrari, Porsche) — это дополнение к порождающим паттернам.
Ваш файл photo_2026-05-19_18-18-58.jpg и photo_2026-05-19_18-18-58 (3).jpg содержат Builder (уже в КТ3) и Singleton (уже в КТ3).
Файл image_c3711e53-0ef5-498f-a260-967487695216.png содержит Decorator — покрыто в КТ4.

Вывод по КТ №5
Рассмотрены дополнительные паттерны, которые решают задачи: разделения абстракции и реализации (Bridge), передачи запроса по цепочке (Chain of Responsibility), инкапсуляции запроса (Command), оповещения об изменениях (Observer), изменения поведения в зависимости от состояния (State), выбора алгоритма (Strategy). В совокупности со структурными и порождающими паттернами они покрывают большинство типовых задач проектирования архитектуры корпоративных приложений.

