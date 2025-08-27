# Library-Management-System-
Here,A Library Management System is a software built to handle the primary housekeeping functions of a library. Libraries rely on library management systems to manage asset collections as well as relationships with their members.
#Write a procedure which will return the list of books drawn in a day, it must show columns as member_id, member_name, book_id, book_name
![image](https://github.com/user-attachments/assets/221a0234-2914-4e6f-aa79-13ae340d8e63)

> CREATE OR REPLACE PROCEDURE get_books_drawn_in_a_day (p_date IN DATE) IS
  2  BEGIN
  3    FOR rec IN (
  4      SELECT m.member_id, m.member_name, b.book_id, b.book_name
  5      FROM member_master m
  6      INNER JOIN book_issue_details bd ON m.member_id = bd.member_id
  7      INNER JOIN book_master b ON bd.book_id = b.book_id
  8      WHERE TRUNC(bd.issue_date) = TRUNC(p_date) ) LOOP
  9      DBMS_OUTPUT.PUT_LINE('Member ID: ' || rec.member_id);
 10      DBMS_OUTPUT.PUT_LINE('Member Name: ' || rec.member_name);
 11      DBMS_OUTPUT.PUT_LINE('Book ID: ' || rec.book_id);
 12      DBMS_OUTPUT.PUT_LINE('Book Name: ‘|| 
rec.book_name);
 13  END LOOP;
 14  END;
 15  /

Procedure created.
SQL> begin
  2   get_books_drawn_in_a_day('04-sep-18');
  3  end;
  4  /

  #Write a procedure which will return the list of members whose books return date is expired, it must show columns as  member_id, member_name, book_id, book_name
 > CREATE OR REPLACE PROCEDURE GetExpiredBooks AS BEGIN
  2    FOR rec IN (SELECT m.member_id, m.member_name, b.book_id, b.book_name
  3                FROM member_master m
  4                INNER JOIN book_issue_details bd ON m.member_id = bd.member_id
  5                INNER JOIN book_master b ON bd.book_id = b.book_id
  6                WHERE bd.issue_expiry < '02-sep-18') LOOP
  7      DBMS_OUTPUT.PUT_LINE('Member ID: ' || rec.member_id);
  8      DBMS_OUTPUT.PUT_LINE('Member Name: ' || rec.member_name);
  9      DBMS_OUTPUT.PUT_LINE('Book ID: ' || rec.book_id);
 10      DBMS_OUTPUT.PUT_LINE('Book Name: ' || rec.book_name);
 11    END LOOP;
 12  END;
 13  /
Procedure created.
SQL> BEGIN
  2    GetExpiredBooks;
  3  END;
  4  /
# Write a procedure which will do transaction processing when a book is issued to a  member details must be stores in the respective tables
> select book_id,member_id,issue_date from book_issue_details;
# Write a procedure which will Add transaction of  a new book in the database  
> insert into book_master values(105,'book5','author5','12-oct-05','GK',250,'about nation');
> select book_id,book_name,book_type from book_master;
![image](https://github.com/user-attachments/assets/ceca2f3d-2d52-40d0-8cec-c863c3657a12)
![image](https://github.com/user-attachments/assets/168a869d-9f1f-4285-ab2f-d129acd45312)

![image](https://github.com/user-attachments/assets/7b26d4d9-6bf2-4bd9-82c5-5fa52cd8a569)
![image](https://github.com/user-attachments/assets/31f5e11f-4d5b-44dd-8355-86ce77449cdb)
![image](https://github.com/user-attachments/assets/7694fd43-d46d-4a82-a0f7-3e38b32c9c47)
 
![image](https://github.com/user-attachments/assets/e651a9a9-0000-40a4-a1d6-65aeab6c1fd5)

![image](https://github.com/user-attachments/assets/a62f9f86-7036-4d32-a104-959f8ecb3de5)

![image](https://github.com/user-attachments/assets/8e1745a2-fd3f-430e-87da-2e2d235d35f8)
