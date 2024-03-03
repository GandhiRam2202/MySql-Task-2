# MySql Task 2
 
![taskmysql](https://github.com/GandhiRam2202/MySql-Task-2/assets/152801640/d89c10e3-b701-4231-ac64-9b774a23285d)

# 1.Create Course Table
create table courses (<br>
course_id varchar(5)primary key,<br>
course_name varchar(20)<br>
);<br>
# 2.Creating Coordinator Table
create table coordinator(<br>
coor_id varchar(5)primary key,<br>
coor_name varchar(20),<br>
course_id varchar(5),<br>
mentor_id varchar(5)<br>
);<br>

# 3.Altering Coordinator For Adding Foreign Key
alter table coordinator add foreign key (course_id) references courses(course_id);

# 4.Creating Mentor Table

create table mentor(<br>
mentor_id varchar(5)primary key,<br>
mentor_name varchar(20),<br>
course_id varchar(5),<br>
course_name varchar(20),<br>
foreign key (course_id)references courses(course_id),<br>
foreign key (course_id)references coordinator(course_id)<br>
);<br>

# 5.Creating Student Table

create table student(<br>
student_id varchar(5)primary key,<br>
student_name varchar(20),<br>
batch_id varchar(5),<br>
course_id varchar(5),<br>
course_name varchar(20),<br>
coor_id varchar(5),<br>
mentor_id varchar(5),<br>
foreign key (course_id)references courses(course_id),<br>
foreign key (coor_id)references coordinator(coor_id),<br>
foreign key (mentor_id)references mentor(mentor_id)<br>
);<br>

# 6.Creating Batch Details Table

create table batch_det(<br>
batch_id varchar(5)primary key,<br>
batch_name varchar(20),<br>
course_id varchar(5),<br>
mentor_id varchar(5),<br>
coor_id varchar(5),<br>
student_id varchar(5),<br>
foreign key(student_id)references student(student_id),<br>
foreign key(mentor_id)references mentor(mentor_id),<br>
foreign key(course_id)references courses(course_id),<br>
foreign key(coor_id)references coordinator(coor_id)<br>
);<br>

# 7.Creating Task Details Tabl

create table task_det(<br>
task_id varchar(5)primary key,<br>
task_name varchar(20),<br>
task_desctiption varchar(50),<br>
dead_line date,<br>
coor_id varchar(5),<br>
mentor_id varchar(5),<br>
student_id varchar(5),<br>
foreign key (coor_id)references coordinator(coor_id),<br>
foreign key (mentor_id)references mentor(mentor_id),<br>
foreign key (student_id)references student(student_id)<br>
);<br>

# 8.Creating Query Handeler Table

create table query_handeler(<br>
query_id varchar(5)primary key,<br>
query_name varchar(20),<br>
query_desc varchar(50),<br>
mentor_id varchar(5),<br>
coor_id varchar(5),<br>
student_id varchar(5),<br>
foreign key(coor_id)references coordinator(coor_id),<br>
foreign key(mentor_id)references mentor(mentor_id),<br>
foreign key(student_id)references student(student_id)<br>
);<br>

# 9.Altering Student Table to Add Task Mark Column

alter table student add column (task_mark int);
