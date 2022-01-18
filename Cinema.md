# Tạo database và table

```sql
CREATE DATABASE Cinema

CREATE TABLE film(
	film_id INT PRIMARY KEY AUTO_INCREMENT,
    title TEXT NOT null,
    director TEXT NOT null,
    release_date DATE NOT null,
    length TEXT NOT null,
    film_studio TEXT NOT null,
    product_country TEXT NOT null
)

CREATE TABLE film_studio(
	studio_id INT PRIMARY KEY AUTO_INCREMENT,
    name INT NOT null
)

CREATE TABLE category(
	category_id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT null
)

CREATE TABLE actor(
	actor_id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT null
)

CREATE TABLE shows(
	shows_id INT PRIMARY KEY AUTO_INCREMENT,
    opening_day DATE NOT null,
    price ENUM('50000','80000') NOT null
)

CREATE TABLE room(
	room_id INT PRIMARY KEY AUTO_INCREMENT,
    room_name TEXT NOT null,
    total_seat INT NOT null
)

CREATE TABLE showtime(
	showtime_id INT PRIMARY KEY AUTO_INCREMENT,
    Show_time TIME NOT null
)

CREATE TABLE seat(
	seat_id INT PRIMARY KEY AUTO_INCREMENT,
    status ENUM('emppty','full')
)

CREATE TABLE customer(
	customer_id INT PRIMARY KEY AUTO_INCREMENT,
   	name TEXT NOT null,
    birthday DATE NOT null,
    address TEXT NOT null,
    mobile VARCHAR(11) NOT null,
    email TEXT NOT null
)

CREATE TABLE ticket(
	seat_id INT NOT null,
    shows_id INT NOT null,
    FOREIGN KEY (seat_id) REFERENCES seat(seat_id),
    FOREIGN KEY (shows_id) REFERENCES shows(shows_id)
)

CREATE TABLE shows_room(
	room_id INT NOT null,
    shows_id INT NOT null,
    FOREIGN KEY (room_id) REFERENCES room(room_id),
    FOREIGN KEY (shows_id) REFERENCES shows(shows_id)
)

CREATE TABLE room_seat(
	room_id INT NOT null,
    seat_id INT NOT null,
    FOREIGN KEY (room_id) REFERENCES room(room_id),
    FOREIGN KEY (seat_id) REFERENCES seat(seat_id)
)

CREATE TABLE shows_showtime(
	showtime_id INT NOT null,
    shows_id INT NOT null,
    FOREIGN KEY (showtime_id) REFERENCES showtime(showtime_id),
    FOREIGN KEY (shows_id) REFERENCES shows(shows_id)
)

CREATE TABLE customer_film(
	customer_id INT NOT null,
	seat_id INT NOT null,
    shows_id INT NOT null,
    FOREIGN KEY (customer_id) REFERENCES customer(customer_id),
    FOREIGN KEY (seat_id) REFERENCES seat(seat_id),
    FOREIGN KEY (shows_id) REFERENCES shows(shows_id)
)

CREATE TABLE film_studio(
	studio_id INT NOT null,
    film_id INT NOT null,
    FOREIGN KEY (studio_id) REFERENCES studio(studio_id),
    FOREIGN KEY (film_id) REFERENCES film(film_id)
)
```
# Thêm dữ liệu


```sql
insert into film (title, director, release_date, length) values ('I, Monster', 'Lambert Sommersett', '4/24/2018', 113);
insert into film (title, director, release_date, length) values ('Ref, The', 'Noelani Glading', '3/21/2018', 104);
insert into film (title, director, release_date, length) values ('Charisma (Karisuma)', 'Alex Hought', '4/25/2019', 102);
insert into film (title, director, release_date, length) values ('Putin''s Kiss', 'Timmie Bisgrove', '6/7/2018', 126);
insert into film (title, director, release_date, length) values ('Acacia', 'Yankee McNeely', '8/11/2019', 115);
insert into film (title, director, release_date, length) values ('Beautiful Ohio', 'Adolphus Ramsey', '7/7/2018', 112);
insert into film (title, director, release_date, length) values ('We''re No Angels', 'Arel Dunbobbin', '10/31/2019', 128);
insert into film (title, director, release_date, length) values ('Fast Five (Fast and the Furious 5, The)', 'Edvard Nisius', '10/29/2018', 129);
insert into film (title, director, release_date, length) values ('Peter''s Friends', 'Grace Norsworthy', '2/20/2019', 104);
insert into film (title, director, release_date, length) values ('Frownland', 'Klement Beaty', '3/5/2018', 126);

insert into studio (name) values ('Twimm');
insert into studio (name) values ('Dazzlesphere');
insert into studio (name) values ('Bluejam');
insert into studio (name) values ('Dabfeed');
insert into studio (name) values ('Yombu');
insert into studio (name) values ('Browsetype');
insert into studio (name) values ('DabZ');
insert into studio (name) values ('Jaxworks');
insert into studio (name) values ('Youopia');
insert into studio (name) values ('Fivechat');

insert into showtime (Show_time) values ('11:20');
insert into showtime (Show_time) values ('11:13');
insert into showtime (Show_time) values ('10:19');
insert into showtime (Show_time) values ('9:22');
insert into showtime (Show_time) values ('9:46');
insert into showtime (Show_time) values ('12:49');
insert into showtime (Show_time) values ('9:07');
insert into showtime (Show_time) values ('10:24');
insert into showtime (Show_time) values ('8:05');
insert into showtime (Show_time) values ('8:23');

insert into room (room_name,total_seat) values ('Room 1',30);
insert into room (room_name,total_seat) values ('Room 2',30);
insert into room (room_name,total_seat) values ('Room 3',30);
insert into room (room_name,total_seat) values ('Room 4',30);
insert into room (room_name,total_seat) values ('Room 5',30);
insert into room (room_name,total_seat) values ('Room 6',30);
insert into room (room_name,total_seat) values ('Room 7',30);
insert into room (room_name,total_seat) values ('Room 8',30);
insert into room (room_name,total_seat) values ('Room 9',30);
insert into room (room_name,total_seat) values ('Room 10',30);

insert into actor (name) values ('Mildrid Canon');
insert into actor (name) values ('Kahlil Ferras');
insert into actor (name) values ('Goldarina Crysell');
insert into actor (name) values ('Saunderson Skedge');
insert into actor (name) values ('Gretchen Barnhart');
insert into actor (name) values ('Davina Weightman');
insert into actor (name) values ('Wilfred Ashpole');
insert into actor (name) values ('Camala Freegard');
insert into actor (name) values ('Sharlene Loadsman');
insert into actor (name) values ('Thain Burfield');

insert into category (name) values ('Documentary');
insert into category (name) values ('Action|Adventure|Sci-Fi|Thriller');
insert into category (name) values ('Animation');
insert into category (name) values ('Comedy');
insert into category (name) values ('Drama|Romance');
insert into category (name) values ('Crime|Drama');
insert into category (name) values ('Crime|Mystery');
insert into category (name) values ('Crime|Thriller');
insert into category (name) values ('Comedy|Thriller');
insert into category (name) values ('Drama|Romance')

insert into shows (opening_day) values ('3/6/2021');
insert into shows (opening_day) values ('12/20/2021');
insert into shows (opening_day) values ('9/10/2021');
insert into shows (opening_day) values ('11/4/2021');
insert into shows (opening_day) values ('9/8/2021');
insert into shows (opening_day) values ('8/17/2021');
insert into shows (opening_day) values ('10/1/2021');
insert into shows (opening_day) values ('7/28/2021');
insert into shows (opening_day) values ('2/22/2021');
insert into shows (opening_day) values ('12/22/2021');
```