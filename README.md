# SQL-Project
Project - University System Registration 

SQL CODE FOR CREATING DATABASE AND TABLES : 

create database SQL_Project;
use SQL_Project;

create table Students (
    student_id int primary key auto_increment,
    first_name varchar(50) not null,
    last_name varchar(50) not null,
    email varchar(100) unique not null,
    dob date,
    major varchar(50) default 'Undeclared'
);

create table Professors (
    professor_id int primary key auto_increment,
    first_name varchar(50) not null,
    last_name varchar(50) not null,
    email varchar(100) unique not null,
    department varchar(50) not null
);

create table Courses (
    course_id int primary key auto_increment,
    course_name varchar(100) not null,
    department varchar(50) not null,
    credits int not null,
    professor_id int not null,
    foreign key (professor_id) references Professors(professor_id)
);

create table Registrations (
    registration_id int primary key auto_increment,
    student_id int not null,
    course_id int not null,
    registration_date date,
    grade char(2) not null,
    foreign key (student_id) references Students(student_id),
    foreign key (course_id) references Courses(course_id)
);

create table Departments (
    department_id int primary key auto_increment,
    department_name varchar(50) unique not null
);

