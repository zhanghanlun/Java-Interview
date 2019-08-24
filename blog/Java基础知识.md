
# 1 Object类的方法
 - toString()
 - getClass()
 - clone()
 - equal()
 - notify()
 - notifyAll()
 - wait()
 - finalize()

# 2 Java的反射机制
## 2.1 基本概念
Java的反射机制是在运行状态中，对于任意一个类，可以知道其所有属性和方法，对于任意一个对象，可以调用其任意一个方法和属性，这种动态获取信息和动态调用方法的功能称为Java的反射机制。
## 2.2 用途
各种框架中使用Java的反射机制去加载对象。比如Spring中通过xml配置文件加载java bean。

# 3 Java序列化
Java的序列化常用的来说包括三种：Java原生序列化、Hessian序列化和JSON序列化。
## 3.1 Java原生序列化
实现Serializable接口,Java例子如下。交给Java来实现就好了

```java
import java.io.*;

public class Student implements Serializable {

    private static final long serialVersionUID = 1L;

    private String name;
    private Integer age;
    private Integer grade;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Integer getAge() {
        return age;
    }

    public void setAge(Integer age) {
        this.age = age;
    }

    public Integer getGrade() {
        return grade;
    }

    public void setGrade(Integer grade) {
        this.grade = grade;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", grade=" + grade +
                '}';
    }

    public static void main(String[] args) {
        File file = new File("D://output.log");
        try {
            ObjectOutputStream objectOutputStream = new ObjectOutputStream(new FileOutputStream(file));
            Student student = new Student();
            student.setAge(10);
            student.setName("zhang");
            student.setGrade(3);
            objectOutputStream.writeObject(student);
            objectOutputStream.close();
            ObjectInputStream inputStream = new ObjectInputStream(new FileInputStream(file));
            Student student1 = (Student)inputStream.readObject();
            System.out.println(student1);
            inputStream.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## 3.2 Hessian序列化

# 2.ArrayList和LinkedList区别

## 底层结构

 1. ArrayList的底层结构是数组
 2. LinkedList的底层结构是双向链表

## 执行效率

>* ArrayList随机存取 O(1),插入删除效率低
>* LinkedList随机存取O(n)，插入删除效率高

# 3.HashMap和ConcurrentHashMap
## hashMap

 1. HashMap在Java 8中底层结构升级了，由**数组+链表**变成了**数组+链表或红黑树**组成
 2. HashMap默认负载因子为0.75
 3. HashMap中链表的长度变大后会进行树化操作变成红黑树

## ConcurrentHashMap

 1. ConcurrentHashMap在Java 8的底层结构也升级了，有**segment数组+链表**变成了**数组+链表或红黑树**组成
 2. 在Java 8 其并发性由 **CAS + synchronized** 来保证