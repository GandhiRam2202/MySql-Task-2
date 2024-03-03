# MySql Task 2
 
![taskmysql](https://github.com/GandhiRam2202/MySql-Task-2/assets/152801640/d89c10e3-b701-4231-ac64-9b774a23285d)

# 1.Create Course Table
create table courses (
course_id varchar(5)primary key,
course_name varchar(20)
);
# 2.Creating Coordinator Table
create table coordinator(
coor_id varchar(5)primary key,
coor_name varchar(20),
course_id varchar(5),
mentor_id varchar(5)
);

# 3.Altering Coordinator For Adding Foreign Key
alter table coordinator add foreign key (course_id) references courses(course_id);

# 4.Creating Mentor Table

create table mentor(
mentor_id varchar(5)primary key,
mentor_name varchar(20),
course_id varchar(5),
course_name varchar(20),
foreign key (course_id)references courses(course_id),
foreign key (course_id)references coordinator(course_id)
);

# 5.Creating Student Table

create table student(
student_id varchar(5)primary key,
student_name varchar(20),
batch_id varchar(5),
course_id varchar(5),
course_name varchar(20),
coor_id varchar(5),
mentor_id varchar(5),
foreign key (course_id)references courses(course_id),
foreign key (coor_id)references coordinator(coor_id),
foreign key (mentor_id)references mentor(mentor_id)
);

# 6.Creating Batch Details Table

create table batch_det(
batch_id varchar(5)primary key,
batch_name varchar(20),
course_id varchar(5),
mentor_id varchar(5),
coor_id varchar(5),
student_id varchar(5),
foreign key(student_id)references student(student_id),
foreign key(mentor_id)references mentor(mentor_id),
foreign key(course_id)references courses(course_id),
foreign key(coor_id)references coordinator(coor_id)
);

# 7.Creating Task Details Tabl

create table task_det(
task_id varchar(5)primary key,
task_name varchar(20),
task_desctiption varchar(50),
dead_line date,
coor_id varchar(5),
mentor_id varchar(5),
student_id varchar(5),
foreign key (coor_id)references coordinator(coor_id),
foreign key (mentor_id)references mentor(mentor_id),
foreign key (student_id)references student(student_id)
);

# 8.Creating Query Handeler Table

create table query_handeler(
query_id varchar(5)primary key,
query_name varchar(20),
query_desc varchar(50),
mentor_id varchar(5),
coor_id varchar(5),
student_id varchar(5),
foreign key(coor_id)references coordinator(coor_id),
foreign key(mentor_id)references mentor(mentor_id),
foreign key(student_id)references student(student_id)
);

# 9.Altering Student Table to Add Task Mark Column

alter table student add column (task_mark int);
