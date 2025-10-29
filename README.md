1. creating tables
. CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(50),
    course VARCHAR(50),
    roll_no int, marks int);

. CREATE TABLE student_information (
    student_id INT,
    city VARCHAR(50),
    mobile_number VARCHAR(15),
    FOREIGN KEY (student_id) REFERENCES students(student_id)
);

2. inserting data
. INSERT INTO students (student_id, name, course, roll_no)
VALUES 
(4494, 'Rohit', '1A', 6689, 80),
(4495, 'Priya', '1B', 5673, 30),
(4496, 'Amit', '2A', 7765, 67),
(4498, 'Karan', NULL, 6554, 55),
(4497, 'Sneha', '2B', 3345,70);

. INSERT INTO student_information (student_id, city, mobile_number)
VALUES
(4494, 'Delhi', '2222222222'),
(4495, 'Mumbai', '4444444444'),
(4496, 'Chennai', '6666666666'),
(4498, 'Karan',555555555'),
(4497, 'Kolkata', '9999999999');

3.views
a. all data 
SELECT * FROM students;
b. any specific column
SELECT name, course FROM students;
c. specific student
SELECT * FROM students WHERE student_id = 4494;

4.ASC & DESC statements
. SELECT * FROM students
ORDER BY name ASC;

. SELECT * FROM students
ORDER BY name DESC;

5. AND,OR,NOT statements
   a. AND
. SELECT * FROM students
WHERE course = '1A' AND name = 'Rohit';
   b. OR
. SELECT * FROM students
WHERE course = '1A' OR course = '1B';
   c. NOT
. SELECT * FROM students
WHERE NOT course = '1A';

6. NULL
   SELECT * FROM students
WHERE course IS NULL;

7.UPDATE
UPDATE students
SET course = '3A'
WHERE student_id = 4498;

8.DELETE
DELETE FROM students
WHERE student_id = 4498;

9. COUNT,SUM & AVERAGE
    A. SELECT COUNT(*) AS total_students FROM students;
   B.SELECT SUM(marks) AS total_marks FROM students;
   C.SELECT AVG(marks) AS average_marks FROM students;

10. MIN & MAX
    A. SELECT MIN(marks) AS minimum_marks FROM students;
    B.SELECT MAX(marks) AS maximum_marks FROM students;

11. JOINS
a. INNER JOIN
SELECT s.student_id, s.name, s.course, si.city, si.mobile_number
FROM students s
INNER JOIN student_information si
ON s.student_id = si.student_id;

b. LEFT JOIN
SELECT s.student_id, s.name, s.course, si.city, si.mobile_number
FROM students s
LEFT JOIN student_information si
ON s.student_id = si.student_id;

c. RIGHT JOIN
SELECT s.student_id, s.name, s.course, si.city, si.mobile_number
FROM students s
RIGHT JOIN student_information si
ON s.student_id = si.student_id;

d. FULL JOIN
SELECT s.student_id, s.name, s.course, si.city, si.mobile_number
FROM students s
FULL OUTER JOIN student_information si
ON s.student_id = si.student_id;

e. CARTESIAN/CROSS JOIN
SELECT s.name, si.city
FROM students s
CROSS JOIN student_information si;

f. SELF JOIN
SELECT a.name AS student1, b.name AS student2, a.course
FROM students a
JOIN students b
ON a.course = b.course AND a.student_id <> b.student_id;
    
