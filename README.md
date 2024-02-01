
DROP TABLE if EXISTS autor;
CREATE TABLE IF NOT EXISTS autor (
    id INTEGER PRIMARY KEY,
    nombre TEXT
);

DROP table if EXISTS libro;
CREATE TABLE IF NOT EXISTS libro (
    codigo INTEGER PRIMARY KEY,
    titulo TEXT,
    autor_id INTEGER,
    editorial TEXT,
    precio REAL,
    FOREIGN KEY (autor_id) REFERENCES autor(id)
);

INSERT INTO autor (nombre) VALUES
    ('J.K. Rowling'),
    ('Stephen King'),
    ('George Orwell'),
    ('Jane Austen'),
    ('Agatha Christie');

INSERT INTO libro (titulo, autor_id, editorial, precio) VALUES
    ('The Great Gatsby', 6, 'Charles Scribner''s Sons', 20.99),
    ('To Kill a Mockingbird', 7, 'J.B. Lippincott & Co.', 15.95),
    ('The Catcher in the Rye', 8, 'Little, Brown and Company', 18.75),
    ('One Hundred Years of Solitude', 9, 'Harper & Row', 22.50),
    ('Brave New World', 3, 'Chatto & Windus', 17.99),
    ('The Hobbit', 10, 'George Allen & Unwin', 24.99),
    ('The Lord of the Rings', 10, 'George Allen & Unwin', 35.50),
    ('The Chronicles of Narnia', 11, 'Geoffrey Bles', 28.99),
    ('The Odyssey', 12, 'Homer', 14.95),
    ('The Iliad', 12, 'Homer', 14.95),
    ('Moby-Dick', 13, 'Harper & Brothers', 19.99),
    ('The Road', 14, 'Alfred A. Knopf', 16.75),
    ('The Grapes of Wrath', 15, 'The Viking Press', 21.50),
    ('Wuthering Heights', 16, 'Emily Brontë', 12.99),
    ('The Old Man and the Sea', 17, 'Charles Scribner''s Sons', 18.95),
    ('The Count of Monte Cristo', 18, 'Pétion', 27.99),
    ('The Picture of Dorian Gray', 19, 'Ward, Lock, and Company', 14.50),
    ('The Adventures of Sherlock Holmes', 20, 'George Newnes', 16.99),
    ('Frankenstein', 21, 'Lackington, Hughes, Harding, Mavor, & Jones', 13.25),
    ('Alice''s Adventures in Wonderland', 22, 'Macmillan', 11.50),
    ('The Prince', 23, 'Niccolò Machiavelli', 10.99),
    ('Don Quixote', 24, 'Francisco de Robles', 26.75),
    ('The Divine Comedy', 25, 'Dante Alighieri', 20.50),
    ('Anna Karenina', 26, 'The Russian Messenger', 23.99),
    ('Les Misérables', 27, 'A. Lacroix, Verboeckhoven & Cie.', 29.75),
    ('The Jungle Book', 28, 'Macmillan Publishers', 14.99),
    ('The Wind in the Willows', 29, 'Methuen & Co.', 17.50),
    ('War and Peace', 26, 'The Russian Messenger', 33.25),
    ('Crime and Punishment', 30, 'The Russian Messenger', 19.99);

/*
-- Selección de libros cuyo título comienza con "H".
    SELECT * FROM libro WHERE titulo LIKE '%H%';
    ┌────────┬───────────────────────────────────┬──────────┬───────────────────────────┬────────┐
    │ codigo │              titulo               │ autor_id │         editorial         │ precio │
    ├────────┼───────────────────────────────────┼──────────┼───────────────────────────┼────────┤
    │ 1      │ The Great Gatsby                  │ 6        │ Charles Scribner's Sons   │ 20.99  │
    │ 3      │ The Catcher in the Rye            │ 8        │ Little, Brown and Company │ 18.75  │
    │ 4      │ One Hundred Years of Solitude     │ 9        │ Harper & Row              │ 22.5   │
    │ 6      │ The Hobbit                        │ 10       │ George Allen & Unwin      │ 24.99  │
    │ 7      │ The Lord of the Rings             │ 10       │ George Allen & Unwin      │ 35.5   │
    │ 8      │ The Chronicles of Narnia          │ 11       │ Geoffrey Bles             │ 28.99  │
    │ 9      │ The Odyssey                       │ 12       │ Homer                     │ 14.95  │
    │ 10     │ The Iliad                         │ 12       │ Homer                     │ 14.95  │
    │ 12     │ The Road                          │ 14       │ Alfred A. Knopf           │ 16.75  │
    │ 13     │ The Grapes of Wrath               │ 15       │ The Viking Press          │ 21.5   │
    │ 14     │ Wuthering Heights                 │ 16       │ Emily Brontë              │ 12.99  │
    │ 15     │ The Old Man and the Sea           │ 17       │ Charles Scribner's Sons   │ 18.95  │
    │ 16     │ The Count of Monte Cristo         │ 18       │ Pétion                    │ 27.99  │
    │ 17     │ The Picture of Dorian Gray        │ 19       │ Ward, Lock, and Company   │ 14.5   │
    │ 18     │ The Adventures of Sherlock Holmes │ 20       │ George Newnes             │ 16.99  │
    │ 21     │ The Prince                        │ 23       │ Niccolò Machiavelli       │ 10.99  │
    │ 23     │ The Divine Comedy                 │ 25       │ Dante Alighieri           │ 20.5   │
    │ 26     │ The Jungle Book                   │ 28       │ Macmillan Publishers      │ 14.99  │
    │ 27     │ The Wind in the Willows           │ 29       │ Methuen & Co.             │ 17.5   │
    │ 29     │ Crime and Punishment              │ 30       │ The Russian Messenger     │ 19.99  │
    └────────┴───────────────────────────────────┴──────────┴───────────────────────────┴────────┘

-- Libros escritos por autores cuyos nombres terminan con "ing".
    SELECT * FROM autor WHERE nombre LIKE "%ing";

┌────┬──────────────┐
│ id │    nombre    │
├────┼──────────────┤
│ 1  │ J.K. Rowling │
│ 2  │ Stephen King │
└────┴──────────────┘

-- Libros con títulos que contienen la palabra "and" en cualquier posición.
SELECT * FROM libro WHERE titulo LIKE '%and%';

┌────────┬──────────────────────────────────┬──────────┬─────────────────────────┬────────┐
│ codigo │              titulo              │ autor_id │        editorial        │ precio │
├────────┼──────────────────────────────────┼──────────┼─────────────────────────┼────────┤
│ 15     │ The Old Man and the Sea          │ 17       │ Charles Scribner's Sons │ 18.95  │
│ 20     │ Alice's Adventures in Wonderland │ 22       │ Macmillan               │ 11.5   │
│ 28     │ War and Peace                    │ 26       │ The Russian Messenger   │ 33.25  │
│ 29     │ Crime and Punishment             │ 30       │ The Russian Messenger   │ 19.99  │
└────────┴──────────────────────────────────┴──────────┴─────────────────────────┴────────┘

-- Libros cuyo título comienza con una vocal.
SELECT * FROM libro WHERE titulo REGEXP '^[aeiouAEIOU]';

┌────────┬──────────────────────────────────┬──────────┬───────────────────────┬────────┐
│ codigo │              titulo              │ autor_id │       editorial       │ precio │
├────────┼──────────────────────────────────┼──────────┼───────────────────────┼────────┤
│ 4      │ One Hundred Years of Solitude    │ 9        │ Harper & Row          │ 22.5   │
│ 20     │ Alice's Adventures in Wonderland │ 22       │ Macmillan             │ 11.5   │
│ 24     │ Anna Karenina                    │ 26       │ The Russian Messenger │ 23.99  │
└────────┴──────────────────────────────────┴──────────┴───────────────────────┴────────┘

-- Libros cuyo autor tiene al menos una vocal repetida.

-- Libros con precios que tienen dos dígitos decimales exactos.

-- Libros cuyos títulos tienen al menos tres palabras.
SELECT * FROM libro WHERE titulo LIKE '% % %'

-- Obtener todos los autores cuyo nombre empieza con la letra "A":

-- Seleccionar los libros cuyo título contiene la palabra "SQL":

-- Obtener todos los autores cuyo nombre termina con "ez":

-- Obtener todos los autores cuyo nombre tiene al menos 5 caracteres:

-- Seleccionar los libros cuya editorial es diferente de "EditorialX":

-- Ob tener todos los autores cuyo nombre contiene al menos una vocal:

-- Seleccionar los libros cuyo título comienza con una letra mayúscula:
    
-- Obtener todos los autores cuyo nombre no contiene la letra "r":

-- Seleccionar los libros cuya editorial empieza con la letra "P":

-- Obtener todos los autores cuyo nombre tiene exactamente 6 caracteres:

-- Seleccionar los libros cuyo título contiene al menos un número:

-- Obtener todos los autores cuyo nombre inicia con una vocal:

-- Obtener todos los autores cuyo nombre no contiene espacios en blanco:

-- Seleccionar los libros cuyo título termina con una vocal:

-- Obtener todos los autores cuyo nombre contiene la secuencia "er":

-- Seleccionar los libros cuyo título empieza con la palabra "The":

-- Obtener todos los autores cuyo nombre tiene al menos una letra mayúscula:

-- Seleccionar los libros cuyo precio es un número decimal con exactamente dos decimales:

-- Obtener todos los autores cuyo nombre no contiene números:

-- Seleccionar los libros cuyo título contiene al menos tres vocales:

-- Obtener todos los autores cuyo nombre inicia con una consonante:

-- Seleccionar los libros cuyo título no contiene la palabra "Science":

-- Obtener todos los autores cuyo nombre tiene al menos una letra repetida consecutivamente:

-- Obtener todos los autores cuyo nombre empieza con "M" o termina con "n":

-- Obtener todos los autores cuyo nombre no contiene caracteres especiales:

/*# tarea-bas-ed-edatos
