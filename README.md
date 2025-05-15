# Reto_2
```mermaid
---
title: Academic Management System
---
classDiagram
class AcademicManagement {
    + students: List<Student>
    + professors: List<Professor>
    + courses: List<Course>
    + enrollments: List<Enrollment>
    + registerStudent()
    + assignProfessor()
    + generateReport()
}
class Student {
    + name: String
    + id: String
    + email: String
    + major: String
    + calculateGPA(): Float
    + listCourses(): List<Course>
    + enroll(c: Course)
}
class Professor {
    + name: String
    + id: String
    + area: String
    + email: String
    + addStudent(s: Student)
    + listStudents(): List<Student>
    + assignCourse(c: Course)
} 
class Course {
    + name: String
    + code: String
    + credits: Int
    + semester: Int
    + addStudent(s: Student)
    + listStudents(): List<Student>
    + assignProfessor(p: Professor)
}
class Enrollment {
    + semester: String
    + grade: Float
    + observation: String
    + student: Student
    + course: Course
    + approved(): Boolean
    + getGrade(): Float
}
AcademicManagement *-- "1..*" Student : manages
AcademicManagement *-- "1..*" Professor : manages
AcademicManagement *-- "1..*" Course : manages
AcademicManagement *-- "1..*" Enrollment : records
Enrollment --> "1" Student : belongs to
Enrollment --> "1" Course : refers to
Student --> "0..*" Enrollment : has
Student --> "0..*" Course : takes
Professor --> "0..*" Course : teaches
Course --> "0..1" Professor : taught by
Course --> "0..*" Student : includes
