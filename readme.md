В разных ветках разные версии. Во 2 лабе добавляется мульти импорт с файла и транзакционность. В 3 лабе добавляется s3 и двухфазный коммит изменений

---
# Проект на стеке Spring Boot + Angular


### Лабораторная работа по предмету Информационные системы
*вариант 66672*

ресурс с оригиналом задания: [ссылка](https://se.ifmo.ru/courses/is)

---

# Задание
### Разработанная система должна удовлетворять следующим требованиям:

-  Основное назначение информационной системы - управление объектами, созданными на основе заданного в варианте класса. 

-  Необходимо, чтобы с помощью системы можно было выполнить следующие операции с объектами: создание нового объекта, получение информации об объекте по ИД, обновление объекта (модификация его атрибутов), удаление объекта. Операции должны осуществляться в отдельных окнах (интерфейсах) приложения.При получении информации об объекте класса должна также выводиться информация о связанных с ним объектах. 

- При создании объекта класса необходимо дать пользователю возможность связать новый объект с объектами вспомогательных классов, которые могут быть связаны с созданным объектом и уже есть в системе.

-  Выполнение операций по управлению объектами должно осуществляться на серверной части (не на клиенте), изменения должны синхронизироваться с базой данных. 

-   На главном экране системы должен выводиться список текущих объектов в виде таблицы (каждый атрибут объекта - отдельная колонка в таблице).  При отображении таблицы должна использоваться пагинация (если все объекты не помещаются на одном экране).

- Нужно обеспечить возможность фильтровать/сортировать строки таблицы, которые показывают объекты (по значениям любой из строковых колонок). Фильтрация элементов должна производиться только по полному совпадению.

- Переход к обновлению (модификации) объекта должен быть возможен  из таблицы с общим списком объектов  и из области с визуализацией объекта (при ее реализации).

 -  При добавлении/удалении/изменении объекта, он должен автоматически появиться/исчезнуть/измениться в интерфейсах у других пользователей, авторизованных в системе. 

- Если при удалении объекта с ним связан другой объект, связанные объекты должны быть связаны с другим объектом (по выбору пользователя), а изначальный объект удален.

- Пользователю системы должен быть предоставлен интерфейс для авторизации/регистрации нового пользователя. У каждого пользователя должен быть один пароль. Требования к паролю: пароль должен быть уникален. В системе предполагается использование следующих видов пользователей (ролей):
	- незарегистрированные пользователи,
	- обычные пользователи 
	- и администраторы. 
	Если в системе уже создан хотя бы один администратор, зарегистрировать нового администратора можно только при одобрении одним из существующих администраторов (у администратора должен быть реализован интерфейс со списком заявок и возможностью их одобрения).

- Редактировать и удалять объекты могут только пользователи, которые их создали, и администраторы (администраторы могут редактировать и удалять все объекты).

-  Зарегистрированные пользователи должны иметь возможность просмотра всех объектов, но модифицировать (обновлять) могут только принадлежащие им (объект принадлежит пользователю, если он его создал). Для модификации объекта должно открываться отдельное диалоговое окно. При вводе некорректных значений в поля объекта должны появляться информативные сообщения о соответствующих ошибках. 

### В системе должен быть реализован отдельный пользовательский интерфейс для выполнения специальных операций над объектами:

- Рассчитать среднее значение поля height для всех объектов.

- Вернуть количество объектов, значение поля category которых равно заданному.

- Вернуть массив объектов, значение поля name которых начинается с заданной подстроки.

- Создать новый орден космодесанта и сохранить его в БД.

- Распустить указанный орден космодесанта.

### Особенности хранения объектов, которые должны быть реализованы в системе:

-  Организовать хранение данных об объектах в реляционной СУБД (PostgreSQL). Каждый объект, с которым работает ИС, должен быть сохранен в базе данных. 

-  Все требования к полям класса (указанные в виде комментариев к описанию классов) должны быть выполнены на уровне ORM и БД. 

-  Для генерации поля id использовать средства базы данных. 

 -  Пароли при хранении хэшировать алгоритмом MD5. 

- При хранении объектов сохранять информацию о пользователе, который создал этот объект, а также фиксировать даты и пользователей, которые обновляли и изменяли объекты. Для хранения информации о пользователях и об изменениях объектов нужно продумать и реализовать соответствующие таблицы.

- Таблицы БД, не отображающие заданные классы объектов, должны содержать необходимые связи с другими таблицами и соответствовать 3НФ.

### При создании системы нужно учитывать следующие особенности организации взаимодействия с пользователем:

- Система должна реагировать на некорректный пользовательский ввод, ограничивая ввод недопустимых значений и информируя пользователей о причине ошибки.

-  Переходы между различными логически обособленными частями системы должны осуществляться с помощью меню .

-  Во всех интерфейсах системы должно быть реализовано отображение информации о текущем пользователе (кто авторизован) и предоставляться возможность изменить текущего пользователя. 

- [Опциональное задание - +2 балл] В отдельном окне ИС должна осуществляться визуализация объектов коллекции. При визуализации использовать данные о координатах и размерах объекта. Объекты от разных пользователей должны быть нарисованы разными цветами. При нажатии на объект должна выводиться информация об этом объекте.

- При добавлении/удалении/изменении объекта, он должен автоматически появиться/исчезнуть/измениться на области у всех других клиентов.

## Классы по заданию
```java
public class SpaceMarine {
    private long id; //Значение поля должно быть больше 0, Значение этого поля должно быть уникальным, Значение этого поля должно генерироваться автоматически
    private String name; //Поле не может быть null, Строка не может быть пустой
    private Coordinates coordinates; //Поле не может быть null
    private java.time.LocalDate creationDate; //Поле не может быть null, Значение этого поля должно генерироваться автоматически
    private Chapter chapter; //Поле не может быть null
    private int health; //Значение поля должно быть больше 0
    private long height;
    private AstartesCategory category; //Поле не может быть null
    private Weapon weaponType; //Поле не может быть null
}
public class Coordinates {
    private int x; //Значение поля должно быть больше -585
    private Float y; //Максимальное значение поля: 118, Поле не может быть null
}
public class Chapter {
    private String name; //Поле не может быть null, Строка не может быть пустой
    private Long marinesCount; //Поле не может быть null, Значение поля должно быть больше 0, Максимальное значение поля: 1000
    private String world; //Поле может быть null
}
public enum AstartesCategory {
    SCOUT,
    AGGRESSOR,
    INCEPTOR,
    SUPPRESSOR,
    TERMINATOR;
}
public enum Weapon {
    HEAVY_BOLTGUN,
    BOLT_PISTOL,
    BOLT_RIFLE,
    COMBI_FLAMER,
    GRAV_GUN;
}
```
