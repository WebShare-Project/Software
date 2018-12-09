# Software
DDL and DML scripts:

/* ---------------------------------------------------------------------- */


/* Script generated with: DeZign for Databases V8.1.2                     */

/* Target DBMS:           Oracle 11g                                      */

/* Project file:          webshare project.dez                            */

/* Project name:                                                          */

/* Author:                                                                */

/* Script type:           Database creation script                        */

/* Created on:            2018-12-06 13:14                                */

/* ---------------------------------------------------------------------- */



/* ---------------------------------------------------------------------- */

/* Add tables                                                             */

/* ---------------------------------------------------------------------- */


/* ---------------------------------------------------------------------- */

/* Add table "COURSE"                                               */

/* ---------------------------------------------------------------------- */

CREATE TABLE COURSE

 ( Course_Name VARCHAR2(80)

, Course_Number INTEGER CONSTRAINT NN_COURSE_Course_Number NOT NULL,

CONSTRAINT PK_COURSE PRIMARY KEY (Course_Number) );

 /* ---------------------------------------------------------------------- */

 /* Add table "USER_ACCOUNT" */

 /* ---------------------------------------------------------------------- */

CREATE TABLE USER_ACCOUNT ( Login_ID CHAR(9) CONSTRAINT NN_USER_ACCOUNT_Login_ID NOT NULL,

Password VARCHAR(40) CONSTRAINT NN_USER_ACCOUNT_Password NOT NULL,

 CONSTRAINT PK_USER_ACCOUNT PRIMARY KEY (Login_ID) );

/* ---------------------------------------------------------------------- */

/* Add table "STUDENT" */

 /* ---------------------------------------------------------------------- */

CREATE TABLE STUDENT ( Std_ID CHAR(9) CONSTRAINT NN_STUDENT_Std_ID NOT NULL,

Std_Fname VARCHAR2(40), Std_Lname VARCHAR2(40), Std_Major VARCHAR2(40),

CONSTRAINT PK_STUDENT PRIMARY KEY (Std_ID) );

 /* ---------------------------------------------------------------------- */

 /* Add table "URL" */

 /* ---------------------------------------------------------------------- */

CREATE TABLE URL ( URL_ID INTEGER NOT NULL, Topic_Name VARCHAR2(80) CONSTRAINT NN_URL_Topic_Name NOT NULL,

 Course_ID INTEGER CONSTRAINT NN_URL_Course_ID NOT NULL, Std_User_ID CHAR(9) CONSTRAINT NN_URL_Std_User_ID NOT NULL,

Link VARCHAR2(100), CONSTRAINT PK_URL PRIMARY KEY (URL_ID, Course_ID, Std_User_ID) );

/* ---------------------------------------------------------------------- */

 /* Add table "STUDENT_COURSE" */

 /* ---------------------------------------------------------------------- */

CREATE TABLE STUDENT_COURSE ( Course_Num INTEGER CONSTRAINT NN_STUDENT_COURSE_Course_Num NOT NULL,

 Std_ID CHAR(9) CONSTRAINT NN_STUDENT_COURSE_Std_ID NOT NULL, CONSTRAINT PK_STUDENT_COURSE PRIMARY KEY (Course_Num, Std_ID) );

 /* ---------------------------------------------------------------------- */

/* Add foreign key constraints */

 /* ---------------------------------------------------------------------- */ ALTER TABLE STUDENT ADD CONSTRAINT USER_ACCOUNT_STUDENT FOREIGN KEY (Std_ID) REFERENCES USER_ACCOUNT (Login_ID);

ALTER TABLE URL ADD CONSTRAINT COURSE_URL FOREIGN KEY (Course_ID) REFERENCES COURSE (Course_Number);

 ALTER TABLE URL ADD CONSTRAINT STUDENT_URL FOREIGN KEY (Std_User_ID) REFERENCES STUDENT (Std_ID);

ALTER TABLE STUDENT_COURSE ADD CONSTRAINT COURSE_STUDENT_COURSE FOREIGN KEY (Course_Num) REFERENCES COURSE (Course_Number);

 ALTER TABLE STUDENT_COURSE ADD CONSTRAINT STUDENT_STUDENT_COURSE FOREIGN KEY (Std_ID) REFERENCES STUDENT (Std_ID);

