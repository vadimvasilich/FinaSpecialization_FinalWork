# Итоговая контрольная работа по блоку специализация

## Задание:

- Необходимо организовать систему учета для питомника в котором живут домашние и вьючные животные.

1. Используя команду cat в терминале операционной системы Linux, создать два файла "Домашние животные" (заполнив файл "собаками", "кошками", "хомяками") и "Вьючные животные" (заполнив файл "лошадьми", "верблюдами" и " ослами"), а затем объединить их. Просмотреть содержимое созданного файла. Переименовать файл, дав ему новое имя "Друзья человека".

2. Создать директорию, переместить файл туда.

3. Подключить дополнительный репозиторий MySQL. Установить любой пакет из этого репозитория.

4. Установить и удалить deb-пакет с помощью dpkg.

5. Выложить историю команд в терминале Ubuntu.

6. Нарисовать диаграмму, в которой есть классы - родительский, домашние животные и вьючные животные, в составы которых в случае домашних животных войдут классы: собаки, кошки, хомяки, а в класс вьючные животные войдут: лошади, верблюды и ослы.

7. В подключенном MySQL репозитории создать базу данных “Друзья человека”.

8. Создать таблицы с иерархией из диаграммы в БД.

9. Заполнить низкоуровневые таблицы именами (животных), командами которые они выполняют и датами рождения.

10. Удалить из таблицы верблюдов, т.к. верблюдов решили перевезти в другой питомник на зимовку. Объединить таблицы "лошади", и "ослы" в одну таблицу.

11. Создать новую таблицу "молодые животные" в которую попадут все животные старше 1 года, но младше 3 лет и в отдельном столбце, с точностью до месяца, подсчитать возраст животных в новой таблице.

12. Объединить все таблицы в одну, при этом сохраняя поля, указывающие на прошлую принадлежность к старым таблицам.

13. Создать класс с Инкапсуляцией методов и наследованием по диаграмме.

14. Написать программу, имитирующую работу реестра домашних животных. В программе должен быть реализован следующий функционал:

- 14.1. Завести новое животное;

- 14.2. Определять животное в правильный класс;

- 14.3. Увидеть список команд, которое выполняет животное;

- 14.4. Обучить животное новым командам;

- 14.5. Реализовать навигацию по меню.

15. Создайте класс Счетчик, у которого есть метод add(), увеличивающий̆ значение внутренней̆ int переменной̆ на 1 при нажатии “Завести новое животное”. Сделайте так, чтобы с объектом такого типа можно было работать в блоке try-with-resources. Нужно бросить исключение, если работа с объектом типа счетчик была не в ресурсном try и/или ресурс остался открыт. Значение считать в ресурсе try, если при заведения животного заполнены все поля.

# Решение:
1. 
```
cat > "Домашние животные"
Собаки
Кошки
Хомяки

'Ctrl+d'
```
```
cat > "Вьючные животные"
Лошади
Верблюды
Ослы

'Ctrl+d'
```
```
cat "Домашние животные" "Вьючные животные" > Animals
cat Animals
mv "Animals" "Друзья человека"
```
![](1.png)

2.
```
mkdir folder_for_attestation
mv 'Друзья человека' folder_for_attestation/
ls
cd folder_for_attestation/
ls
```
![](2.png)

3.
```
sudo apt-get update
sudo apt update
sudo apt install mysql-server
sudo service mysql status
```
![](3.png)
![](4.png)
![](5.png)
![](6.png)

4.
```
wget http://ftp.us.debian.org/debian/pool/main/s/sl/sl_5.02-1_amd64.deb
sudo dpkg -i sl_5.02-1_amd64.deb
sudo dpkg -r sl
```
![](7.png)

5.
```
  730  mkdir attestation

  731  cd attestation/

  732  cat > Домашние животные

  733  cat > "Домашние животные"

  734  cat > "Вьючные животные"

  735  cat "Домашние животные" "Вьючные животные" > Animals 

  736  cat Animals

  737  mv "Animals" "Друзья человека"

  738  clear

  739  mkdir folder_for_attestation && mv "Друзья человека" /attestation/folder_for_attestation 

  740  ls

  741  rmdir folder_for_attestation/

  742  ls

  743  clear

  744  mkdir folder_for_attestation

  745  mv "Друзья человека" /attestation/folder_for_attestation

  746  mv "Друзья человека" attestation/folder_for_attestation

  747  ls

  748  mkdir folder_for_attestation

  749  rmdir folder_for_attestation

  750  clear

  751  mkdir folder_for_attestation

  752  mv 'Друзья человека' attestation/folder_for_attestation/

  753  mv 'Друзья человека' folder_for_attestation/

  754  ls

  755  cd folder_for_attestation/

  756  ls

  757  clear

  758  cd..

  759  cd.

  760  cd..

  761  cd 

  762  cd attestation/

  763  clear

  764  sudo apt-get update

  765  sudo apt update

  766  sudo apt install mysql

  767  sudo apt install mysql-server

  768  sudo service mysql status

  769  clear

  770  wget http://ftp.us.debian.org/debian/pool/main/s/sl/sl_5.02-1_amd64.deb

  771  sudo dpkg -i sl_5.02-1_amd64.deb

  772  sudo dpkg -r sl

  773  clear

  774  history

```
![](8.png)

6.
![](9.png)

7.
```
CREATE DATABASE Друзья_человека;
```
![](10.png)

8.
```
CREATE TABLE Родительский_класс (
  id INT PRIMARY KEY AUTO_INCREMENT,
  тип VARCHAR(50)
);


CREATE TABLE Домашние_животные (
  id INT PRIMARY KEY,
  вид VARCHAR(50),
  FOREIGN KEY (id) REFERENCES Родительский_класс(id)
);


CREATE TABLE Собаки (
  id INT PRIMARY KEY,
  имя VARCHAR(50),
  команда VARCHAR(50),
  дата_рождения DATE,
  FOREIGN KEY (id) REFERENCES Домашние_животные(id)
);


CREATE TABLE Кошки (
  id INT PRIMARY KEY,
  имя VARCHAR(50),
  команда VARCHAR(50),
  дата_рождения DATE,
  FOREIGN KEY (id) REFERENCES Домашние_животные(id)
);


CREATE TABLE Хомяки (
  id INT PRIMARY KEY,
  имя VARCHAR(50),
  команда VARCHAR(50),
  дата_рождения DATE,
  FOREIGN KEY (id) REFERENCES Домашние_животные(id)
);


CREATE TABLE Вьючные_животные (
  id INT PRIMARY KEY,
  вид VARCHAR(50),
  FOREIGN KEY (id) REFERENCES Родительский_класс(id)
);


CREATE TABLE Лошади (
  id INT PRIMARY KEY,
  имя VARCHAR(50),
  команда VARCHAR(50),
  дата_рождения DATE,
  FOREIGN KEY (id) REFERENCES Вьючные_животные(id)
);


CREATE TABLE Верблюды (
  id INT PRIMARY KEY,
  имя VARCHAR(50),
  команда VARCHAR(50),
  дата_рождения DATE,
  FOREIGN KEY (id) REFERENCES Вьючные_животные(id)
);


CREATE TABLE Ослы (
  id INT PRIMARY KEY,
  имя VARCHAR(50),
  команда VARCHAR(50),
  дата_рождения DATE,
  FOREIGN KEY (id) REFERENCES Вьючные_животные(id)
);

show databases;
show tables;
```

![](11.png)

9. 
```
INSERT INTO Верблюды ( имя, команда, дата_рождения)
VALUES ('Зефир', 'Но, пошел', '2019-09-01'),
       ('Багдад', 'На месте' '2020-11-12'),
       ('Скорость', 'Ждать' '2021-04-05');

INSERT INTO Кошки ( имя, команда, дата_рождения)
VALUES ('Маркиз', 'Кис-кис', '2021-01-20'),
       ('Снежка', 'Давай играть', '2022-03-08');

INSERT INTO Лошади ( имя, команда, дата_рождения)
VALUES ('Спирит', 'Но', '2020-01-21'),
       ('Воронок', 'Бррррр', '2022-03-08');

INSERT INTO Ослы ( имя, команда, дата_рождения)
VALUES ('Нарик', 'Пошёл', '2019-01-21'),
       ('Степан', 'Стой', '2021-03-08');

INSERT INTO Собаки ( имя, команда, дата_рождения)
VALUES ('Шарик', 'Дай лапу', '2019-01-21'),
       ('Бим', 'Лежать', '2020-03-08');

INSERT INTO Хомяки ( имя, команда, дата_рождения)
VALUES ('Долгожитель', 'Кушать', '2022-01-21'),
       ('Хома', 'Отойди', '2023-03-08');
```
10.

```
TRUNCATE TABLE Верблюды;
CREATE TABLE Парнокопытные AS
SELECT * FROM Лошади
UNION
SELECT * FROM Ослы;
```

11.
```
CREATE TABLE Парнокопытные AS
SELECT *, TIMESTAMPDIFF(MONTH, дата_рождения, CURDATE()) AS возраст_в_месяцах
FROM (
    SELECT 'Собаки' AS тип_животного, имя, команда, дата_рождения FROM Собаки
    UNION ALL
    SELECT 'Кошки' AS тип_животного, имя, команда, дата_рождения FROM Кошки
    UNION ALL
    SELECT 'Хомяки' AS тип_животного, имя, команда, дата_рождения FROM Хомяки
    UNION ALL
    SELECT 'Лошади' AS тип_животного, имя, команда, дата_рождения FROM Лошади
    UNION ALL
    SELECT 'Ослы' AS тип_животного, имя, команда, дата_рождения FROM Ослы
) AS животные
WHERE дата_рождения >= DATE_SUB(CURDATE(), INTERVAL 3 YEAR)
AND дата_рождения <= DATE_SUB(CURDATE(), INTERVAL 1 YEAR);

```

12.
```
CREATE TABLE Полный_состав AS
SELECT 'Собаки' AS тип_животного, имя, команда, дата_рождения FROM Собаки
UNION ALL
SELECT 'Кошки' AS тип_животного, имя, команда, дата_рождения FROM Кошки
UNION ALL
SELECT 'Хомяки' AS тип_животного, имя, команда, дата_рождения FROM Хомяки
UNION ALL
SELECT 'Лошади' AS тип_животного, имя, команда, дата_рождения FROM Лошади
UNION ALL
SELECT 'Ослы' AS тип_животного, имя, команда, дата_рождения FROM Ослы;

```

13, 14, 15 в папке Java

