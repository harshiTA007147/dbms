1. creating tables
 CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(50),
    course VARCHAR(50),
    roll_no int, marks int, fees int);

2. CREATE TABLE student_information (
    student_id INT,
    city VARCHAR(50),
    mobile_number VARCHAR(15),
    FOREIGN KEY (student_id) REFERENCES students(student_id)
);

3. inserting data
. INSERT INTO students (student_id, name, course, roll_no)
VALUES 
(4494, 'Rohit', '1A', 6689, 80 , 40000),
(4495, 'Priya', '1B', 5673, 30, 30000),
(4496, 'Amit', '2A', 7765, 67, 50000),
(4498, 'Karan', NULL, 6554, 55),
(4497, 'Sneha', '2B', 3345,70, 60000);

. INSERT INTO student_information (student_id, city, mobile_number)
VALUES
(4494, 'Delhi', '2222222222'),
(4495, 'Mumbai', '4444444444'),
(4496, 'Chennai', '6666666666'),
(4498, 'Karan',555555555'),
(4497, 'Kolkata', '9999999999');

4.views
a. all data 
SELECT * FROM students;
b. any specific column
SELECT name, course FROM students;
c. specific student
SELECT * FROM students WHERE student_id = 4494;

4.ASC STATEMENT
. SELECT * FROM students
ORDER BY name ASC;

5.DEC STATEMENT
. SELECT * FROM students
ORDER BY name DESC;

6. AND,OR,NOT statements
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
    
11. USING LETTERS TO FIND FROM THE DATA
    A.SELECT NAME FROM STUDENTS
    WHERE NAME LIKE '%S';
    B.SELECT NAME FROM STUDENTS
    WHERE ROLL_NO LIKE '_6%';


12. INNER JOIN
SELECT s.student_id, s.name, s.course, si.city, si.mobile_number
FROM students s
INNER JOIN student_information si
ON s.student_id = si.student_id;

13. LEFT JOIN
SELECT s.student_id, s.name, s.course, si.city, si.mobile_number
FROM students s
LEFT JOIN student_information si
ON s.student_id = si.student_id;

14. RIGHT JOIN
SELECT s.student_id, s.name, s.course, si.city, si.mobile_number
FROM students s
RIGHT JOIN student_information si
ON s.student_id = si.student_id;

15. FULL JOIN
SELECT s.student_id, s.name, s.course, si.city, si.mobile_number
FROM students s
FULL OUTER JOIN student_information si
ON s.student_id = si.student_id;

16. CARTESIAN/CROSS JOIN
SELECT s.name, si.city
FROM students s
CROSS JOIN student_information si;

17. SELF JOIN
SELECT a.name AS student1, b.name AS student2, a.course
FROM students a
JOIN students b
ON a.course = b.course AND a.student_id <> b.student_id;

18. Examples of Arithmetic Functions
SELECT 18+6 AS Addition,
       18-6 AS Subtraction,
       18*6 AS Multiplication,
       18/6 AS Division,
       MOD(10,3) AS Modulus
FROM dual;

19. Student names, course fees, and 10% scholarship

(Assume fees: 1A=40000, 2A=30000, 1B=50000, 2B=60000)

SELECT s.StudentName, 
       CASE s.Course
            WHEN '1A' THEN 40000
            WHEN '2A' THEN 30000
            WHEN '1B' THEN 50000
            WHEN '2B' THEN 60000
       END AS CourseFee,
       (CASE s.Course
            WHEN '1A' THEN 40000
            WHEN '2A' THEN 30000
            WHEN '1B' THEN 50000
            WHEN '2B' THEN 60000
       END)*0.10 AS Scholarship
FROM Students;


20. Count the number of students enrolled in the 1B course
SELECT COUNT(*) AS 1B_Students
FROM Students
WHERE Course = '1B';

21. Count the total number of students in the Student table
SELECT COUNT(*) AS Total_Students
FROM Students;

22. Create a table with all columns having NOT NULL constraints
CREATE TABLE Faculty (
    STUDENT_ID   NUMBER(3) NOT NULL,
    NAME VARCHAR2(50) NOT NULL,
    COURSE    VARCHAR2(30) NOT NULL
);


23. Create a table with a UNIQUE key constraint on a column
CREATE TABLE Library (
    STUDENT_ID    NUMBER(4) PRIMARY KEY,
    NAME       VARCHAR2(20) UNIQUE,
    COURSE      VARCHAR2(100)
);

24. Display the list of students ordered by course
SELECT StudentName, Course
FROM Student
ORDER BY Course; 
