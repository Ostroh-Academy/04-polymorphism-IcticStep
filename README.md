[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/5ZerStQK)

**Назва роботи: Використання механізму віртуальних методів
Мета роботи: Ознайомитися з особливостями використання віртуальних методів.** 

# Результати
## Приклад роботи програми з віртуальними методами

![1](https://github.com/Ostroh-Academy/04-polymorphism-IcticStep/assets/59373161/4b5056e1-26f2-491d-b296-26e93f8f391d)
![2](https://github.com/Ostroh-Academy/04-polymorphism-IcticStep/assets/59373161/3e1ab08a-496b-4a5c-bed8-9a33fddb7b13)

Як видно з цих зображень, при роботі з віртуальними перевизначеними методами, без залежності від того, до якого типу приведений конкретний екзепляр, робота з ним відбувається через його перевизначені методи ключовим словом **override**.

## Приклад роботи програми без віртуальних методів

![3](https://github.com/Ostroh-Academy/04-polymorphism-IcticStep/assets/59373161/82f732d3-809e-4cee-adde-4a8d0999fa53)
![4](https://github.com/Ostroh-Academy/04-polymorphism-IcticStep/assets/59373161/494e69be-9c29-4ee9-9dab-c9544b790c28)

Як видно з цих зображень, при роботі без віртуальних методів, а з методами перевизначеними через ключове слово **new**, викликаний метод залежить від того, до якого типу приведений конкретний екземпляр.

# **Теоретичні відомості**
Мова С# включає таку властивість, як поліморфізм – можливість для об’єктів різних класів, зв’язаних з допомогою наслідування, реагувати різними способами при виклику однієї функції-елементу. До найважливіших форм поліморфізму можна віднести:
перевантаження методів та операцій;
віртуальні методи (функції);
Перевантаження методів та операцій називаються статичним поліморфізмом, тому що він підтримується на етапі компіляції (тобто до запуску програми). Віртуальні методи відносяться до динамічного поліморфізму, тому що він реалізується при виконанні програм.
При використанні віртуального методу запит здійснюється з допомогою вказівника базового класу (або посилання), тобто середовище виконання С# вибирає правильно перевизначений метод у відповідному похідному класі, який зв’язаний з цим об’єктом.
Іноді метод визначається в базовому класі як віртуальний, але просто перевизначений в похідному класі. Якщо такий метод викликається через вказівник похідного класу, то використовується версія похідного класу. Це не поліморфна поведінка.
Завдяки використанню поліморфних методів та поліморфізму виклик функції-елемента може привести до різних дій, які залежать від типу об’єкту, який викликається.
Завдання
Написати програму, описавши батьківський та похідний класи і використавши віртуальні методи. За основу візьміть попередню лабораторну і додайте віртуальні методи. Використайте динамічне створення об’єктів та показчики на екземпляр класу. 
Продемонструвати роботу віртуальних методів на практичному прикладі коли наперед невідомо який об’єкт буде створено (невідомо на етапі компіляції):
  

      //Вибрати режим роботи-запитати в користувача, змінна userChoose
        if (userChoose=='1'){
            //Працюємо з одним об'єктом
            //Створюємо, ініціалізуємо ітд
    
        }
            else{
            //Працюємо з іншим об'єктом
            //Створюємо, ініціалізуємо ітд
        }
           //Виклик віртуальної функції через вказівник/показчик на базовий клас

Змініть віртуальні методи на звичайні та перевірте роботу програми. Проаналізуйте зміни.


Приклад програми:


> using System; using System.Collections.Generic; using System.Linq;
> using System.Text;
> 
> namespace ConsoleApplication1 {
>     class Celipsoid
>     {
>         public int a1, a2, a3, b1, b2, b3;
>         public double v;
>         virtual public void inita()
>         {
>             System.Console.WriteLine("Введiть пiвосi елiпсоїда a1, a2, a3:");
>             a1 = Convert.ToInt32(Console.ReadLine());
>             a2 = Convert.ToInt32(Console.ReadLine());
>             a3 = Convert.ToInt32(Console.ReadLine());
>         }
>         virtual public void initb()
>         {
>             System.Console.WriteLine("Введiть координати змiщення центру b1, b2, b3:");
>             b1 = Convert.ToInt32(Console.ReadLine());
>             b2 = Convert.ToInt32(Console.ReadLine());
>             b3 = Convert.ToInt32(Console.ReadLine());
>         }
>         virtual public void show()
>         {
>             Console.WriteLine("a1= " + a1);
>             Console.WriteLine("a2= " + a2);
>             Console.WriteLine("a3= " + a3);
>             Console.WriteLine("b1= " + b1);
>             Console.WriteLine("b2= " + b2);
>             Console.WriteLine("b3= " + b3);
>         }
>         virtual public double size()
>         {
>             v = 4.0 * a1 * a2 * a3 / 3.0;
>             Console.Write("v елiпсоїда = ");
>             Console.WriteLine(v);
>             return (v);
>         }
> 
>     }
>     class Cball : Celipsoid
>     {
>         public int r;
>         public override void inita()
>         {
>             System.Console.Write("Введiть радiус кулi:");
>             r = Convert.ToInt32(Console.ReadLine());
>             base.initb();
>         }
>         public override void show()
>         {
>             Console.WriteLine("r= " + r);
>             Console.WriteLine("b1= " + b1);
>             Console.WriteLine("b2= " + b2);
>             Console.WriteLine("b3= " + b3);
>         }
>         public override double size()
>         {
>             v = 4.0 * r * r * r / 3.0;
>             Console.Write("v кулi = ");
>             Console.WriteLine(v);
>             return (v);
>         }
>     }
> 
>     class Program
>     {
>         static void Main(string[] args)
>         {
>             int userSelect;
>             Celipsoid baseobj = new Celipsoid();
>             do
>             {
>                 Console.WriteLine("Enter '0' if you want to work with elipsoid and '1' - with ball");
>                 userSelect = Convert.ToInt32(Console.ReadLine());
>                 if (userSelect == 0)
>                 {
>                     baseobj = new Celipsoid();
>                     baseobj.initb();
>                 }
>                 else if (userSelect == 1)
>                 {
>                     baseobj = new Cball();
>                 }
>                 else
>                 {
>                     return;
>                 }
>                 baseobj.inita();
>                 baseobj.show();
>                 baseobj.size();
>             } while (true);
>         }
>     } }



Варіанти завдань 
Згідно попередньої роботи.

**Хід виконання**
1.	Розробити алгоритми створення класів згідно варіантів завдань.
2.	Написати відповідну програму на мові програмування С#. 
3		Проаналізувати роботу програми з віртуальними методами та звичайними. Тобто потрібно дослідити механізм динамічного поліморфізму. Зверніть увагу на приклад коду, зокрема на механізм створення об'єкту одного з класів. На етапі компіляції програми невідомо який вибір зробить користувач під час виконання програми. 
4.	Порівняти результати виконання програми з віртуальними методами та без віртуальних методів.
5.	В README файл додати скріншоти роботи програми з віртуальними методами і без віртуальних. Описати різницю. 
