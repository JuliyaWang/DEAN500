## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/JuliyaWang/Hellow-/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# SQL Note 

DROP TABLE Students;
DROP TABLE Enrolled;

CREATE TABLE Students
        (sid CHAR(5),
         name VARCHAR(20),
         login VARCHAR(20),
         age INTEGER check (age>0),
         gpa REAL check (gpa>=0.0 AND gpa <= 4.0),
         PRIMARY KEY (sid));

CREATE TABLE Enrolled
        (sid CHAR(5),
        cid VARCHAR(20),
        grade CHAR(1),
        Foreign key (sid) REFERENCES Students(sid));

INSERT INTO Students (sid, name, login, age, gpa)
        VALUES(53666,"Jones","jones@cs",18,3.4);
INSERT INTO Students (sid, name, login, age, gpa)
        VALUES(53688,"Smith","smith@eecs",18,3.2);
INSERT INTO Students (sid, name, login, age, gpa)
        VALUES(53650,"Smith","amith@math",19,3.9);

INSERT INTO Enrolled (sid, cid,grade)
        VALUES(53831,"Carnatic101","C");
INSERT INTO Enrolled (sid, cid,grade)
        VALUES(53831,"Reggae203","B");
INSERT INTO Enrolled (sid, cid,grade)
        VALUES(53650,"Topology112","A");
INSERT INTO Enrolled (sid, cid,grade)
        VALUES(53666,"History105","B");

INSERT INTO Enrolled (sid, cid, grade) VALUES (NULL,"Carnatic101","C");

## becausethe Enrolled table has the sid that Students table doesn’t have. Fk is reference to the pk. We need to fix the code with the adding Null on the deleting value. 

## Result
MySQL [ywang74]> show tables;
+-------------------+
| Tables_in_ywang74 |
+-------------------+
| Enrolled          |
| Students          |
+-------------------+
2 rows in set (0.00 sec)

MySQL [ywang74]> select* from Students;
+-------+-------+------------+------+------+
| sid   | name  | login      | age  | gpa  |
+-------+-------+------------+------+------+
| 53650 | Smith | amith@math |   19 |  3.9 |
| 53666 | Jones | jones@cs   |   18 |  3.4 |
| 53688 | Smith | smith@eecs |   18 |  3.2 |
+-------+-------+------------+------+------+
3 rows in set (0.01 sec)

MySQL [ywang74]> select * from Enrolled;
+-------+-------------+-------+
| sid   | cid         | grade |
+-------+-------------+-------+
| 53650 | Topology112 | A     |
| 53666 | History105  | B     |
| NULL  | Carnatic101 | C     |
+-------+-------------+-------+
3 rows in set (0.01 sec)

MySQL [ywang74]> delete from Students where sid="53650";
Query OK, 1 row affected (0.05 sec)

MySQL [ywang74]> select * from Enrolled;
+-------+-------------+-------+
| sid   | cid         | grade |
+-------+-------------+-------+
| NULL  | Topology112 | A     |
| 53666 | History105  | B     |
| NULL  | Carnatic101 | C     |
+-------+-------------+-------+
3 rows in set (0.00 sec)

MySQL [ywang74]> UPDATE Students SET sid = 12345 where name ="Jones";
Query OK, 1 row affected (0.05 sec)
Rows matched: 1  Changed: 1  Warnings: 0

MySQL [ywang74]> select *from Students;
+-------+-------+------------+------+------+
| sid   | name  | login      | age  | gpa  |
+-------+-------+------------+------+------+
| 12345 | Jones | jones@cs   |   18 |  3.4 |
| 53688 | Smith | smith@eecs |   18 |  3.2 |
+-------+-------+------------+------+------+
2 rows in set (0.00 sec)




### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
