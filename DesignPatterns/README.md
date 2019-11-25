# PhoneShop design patterns
При реализации данного проекта были использованы паттерны проектирования. Некоторые из них используются применяемыми фреймворками, некоторые реализованы собственноручно. Ниже приводится объяснение некоторых из них:
### Singletone
Данный паттерн очень популярен при разработке ПО, особенно в фреймворках, использующих Inversion of Control. Механизм Dependency Injection (для данного проекта это механизм в Spring Framework и Angular Framework) манипулирует бинами и выполняет их внедрение при обращении из различных классов. В данном проекте, используя scope бинов, реализован данный паттерн (все бины являются синглтонами).
### Factory
Паттерн Factory применяется при инициализации бинов приложения. Для данного проекта при инициализации бинов используется класс BeanFactory. При инициализации SpringContext вызывается метод getBean, который создает бин в соответствии с xml конфигурацией (для данного проекта вместо xml используются java аннотации).

![BeanFactory](https://raw.githubusercontent.com/s1ovak/PhoneShop/master/DesignPatterns/Screens/springFactory.png)
### MVC
Паттерн Model View Controller является основопологающим при разработке многих проектов. Идея состоит в разделении данных, UI и управляющей логики. Для данного проекта используются аннотации @RestController, @Entity, @Service для указания к какому блоку относится данный бин.

![MVC](https://raw.githubusercontent.com/s1ovak/PhoneShop/master/DesignPatterns/Screens/mvc.png)
### Observer
Данный паттерн был реализован при создании frontendа. Идея заключается в создании класса наблюдателя за другим классом. Наблюдатель подписывается на изменение состояния наблюдаемого объекта и реакции на него. Для примера можно взять любой компонент frontend.Для примера рассмотрим plp.component.ts. Метод onSort() выполняет запрос, используя productService.getAllProducts метод. Данный метод возвращает Observable<Product[]>, на который подписывается метод onSort(). После изменения состояния страница обновляет содержимое в зависимости от результата метода сортировки.