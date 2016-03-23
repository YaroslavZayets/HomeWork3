public class Main {

    public static void main(String[] args) {
        Group gr = new Group();

        gr.addStudents(new Student (" Сергей ", " Ковалец ", 24, 56),1);
        gr.addStudents(new Student (" Андрей ", " Шевченко ", 21, 66),2);
        gr.addStudents(new Student (" Иван ", " Петрович ", 19, 78.8),3);
        gr.addStudents(new Student (" Игорь ", " Кузьмич ", 20, 60),4);
        gr.addStudents(new Student (" Игнат ", " Федаренко ", 24, 56),10);

        gr.searchStudent(" Ковалец ");
        gr.searchStudent(" Петко "); //Не найдено

    }


public class Man {
    private String name;
    private String surname;
    private int age;

    public Man (String name, String surname, int age){
        this.name=name;
        this.surname = surname;
        this.age = age;
    }

    public String getSurname() {
        return surname;
    }

    public String toString(){
        return "Имя " + name + " , фамилия " + surname + " , возраст " + age;
    }


public class Student extends Man{

    private double rating;

    public Student(String name, String surname, int age ,double rating){
        super(name,surname,age);
        this.rating=rating;
    }


    public String getSurname(){
        return super.getSurname();
    }

    @Override
    public String toString(){
        return super.toString() + " , средняя оценка :  " + rating;
    }


public class MyException extends Exception {

    @Override
    public String getMessage(){
        return " Не больше 10-ти студентов в данной ггруппе! ";
    }


public class Group {
    private Student[] students = new Student[10];

    public void addStudents(Student stud, int i)
    {
        try {
            if (i>10){
                throw new MyException();
            }
            if (this.students[i-1]==null) {
                this.students[i - 1] = stud;
            }
        } catch (MyException e){
            System.out.println(e.getMessage());
        }
    }

    public void searchStudent(String surname)  {
        boolean isFound = false;
        for (int i = 0; i<students.length; i++){
            if (students[i]!=null){
                if (students[i].getSurname()==surname){
                    isFound = true;
                    System.out.println(" Студент под фамилией  " + surname + " - " + students[i].toString());
                }
            }
        }
        if (!isFound) System.out.println("Не найдено");
    }


    public void showInfo(){
        for (int i = 0; i<students.length; i++){
            if (students[i]!=null){
                System.out.println(students[i].toString());
            } else
                System.out.println(" Ячейка " + (i+1) + " пуста");
        }
    }


