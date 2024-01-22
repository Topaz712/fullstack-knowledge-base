# CLASS 5 BACKEND_SQL

- Coach Will from CodeLabs gave these examples during class

# 1:1 Relationship(One-to-One)

In a one-to-one relationship, an entity in one table is linked to at most one entity in another table.

User and User Profile: In a user management system, each user has exactly one profile, and each profile is associated with exactly one user.

Users might contain login information, and UserProfiles might contain personal details like address and phone number.

Person and Passport: Each person can have at most one passport, and each passport is issued to at most one person.

Persons might contain personal information, while Passports contain passport-specific data like passport number and issue date.

CEO and Company: In a corporate database, each company has at most one CEO, and each CEO is head of at most one company (assuming they don't lead multiple companies).

< --! Note on this last one… this is highly relevant to your application… it may make sense to NOT have a 1:1 relationship for CEO and Company. Database modeling is sometimes subjective! !-->

# 1:M Relationship (One-to-Many)

In a one-to-many relationship, an entity in one table can be linked to multiple entities in another table.

Author and Books: An author can write multiple books, but each book is written by one specific author.

Authors contains author details, while Books contains details about the books.

Teacher and Students: A teacher can have multiple students in a class, but each student is assigned to one teacher (in the context of a specific class).

Parent and Children: A parent can have multiple children, but each child has one set of parents.

# M:N Relationship (Many-to-Many)

In a many-to-many relationship, entities in one table can be linked to multiple entities in another table and vice versa. These are typically implemented using a junction table.

Students and Courses: Students can enroll in multiple courses, and each course can have multiple students.

Tables: Students, Courses, and a junction table like StudentCourses.

Doctors and Patients: Doctors can have multiple patients, and patients can see multiple doctors.

Tables: Doctors, Patients, and a junction table like DoctorPatient.

Authors and Research Papers: Authors can co-write multiple research papers, and each paper can have multiple authors.

Tables: Authors, ResearchPapers, and a junction table like AuthorPapers.
