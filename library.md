```sql
CREATE TABLE book(
	id int PRIMARY KEY AUTO_INCREMENT,
    name text NOT null,
    amount int NOT null,
    release_date date NOT null,
    id_NXB int NOT null,
    location TEXT
)

CREATE TABLE NXB(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT NULL,
    address TEXT NOT NULL,
    email TEXT NOT NULL,
    numbers INT NOT NULL
)

CREATE TABLE category(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT NULL,
)

CREATE TABLE authors(
	id INT PRIMARY KEY AUTO_INCREMENT,
    name TEXT NOT NULL,
    date_of_birth DATE,
    que_quan TEXT NOT null,
    ngay_mat DATE
)