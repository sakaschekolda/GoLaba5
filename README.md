1. Создать структуру Person с полями name и age. Реализовать метод для вывода информации о человеке.

2. Реализовать метод birthday для структуры Person, который увеличивает возраст на 1 год.

3. Создать структуру Circle с полем radius и метод для вычисления площади круга.

4. Создать интерфейс Shape с методом Area(). Реализовать этот интерфейс для структур Rectangle и Circle.

5. Реализовать функцию, которая принимает срез интерфейсов Shape и выводит площадь каждого объекта.

6. Создать интерфейс Stringer и реализовать его для структуры Book, которая хранит информацию о книге.

main.go 
```
package main

import (
	"fmt"
	"math"
)

func main() {
	MyPeople()

	circle := Circle{}
	SquareForCircle(&circle)
	fmt.Print("square my circle - ", math.Pi*circle.Radius*circle.Radius)

	rect := Rectangle{Width: 10, Height: 5}
	circ := Circle{Radius: 7}

	shapes := []Shape{rect, circ}
	printAreas(shapes)

	book := Book{Title: "Go Programming", Author: "John Doe", Year: 2023}
	fmt.Println(book.String())
}

// task_1
type Person struct {
	name string
	age  int
}

func MyPeople() {

	people := Person{"Anton", 19}
	people1 := Person{"Danila", 20}
	fmt.Print("\n1st task\n", people, people1)

	fmt.Print("\n\n2nd task")
	birthday(people)
	birthday(people1)

}

// task_2
func birthday(person Person) {
	fmt.Print("\n", person.name, " ", person.age+1)
}

// task_3
type Circle struct {
	Radius float64
}

func SquareForCircle(c *Circle) {
	fmt.Print("\n\n3rd task\nEnter the radius of the circle: ")
	fmt.Scan(&c.Radius)
}

// task_4
type Shape interface {
	Area() float64
}

type Rectangle struct {
	Width, Height float64
}

func (r Rectangle) Area() float64 {
	return r.Width * r.Height
}

func (c Circle) Area() float64 {
	return math.Pi * c.Radius * c.Radius
}

// task_5
func printAreas(shapes []Shape) {

	fmt.Print("\n\n5th task\n")
	for _, shape := range shapes {
		fmt.Printf("Area: %.2f\n", shape.Area())
	}
}

// task_6
type Stringer interface {
	String() string
}

type Book struct {
	Title  string
	Author string
	Year   int
}

func (b Book) String() string {
	return fmt.Sprintf("\ntask_6\nTitle: %s\nAuthor: %s\nYear: %d", b.Title, b.Author, b.Year)
}

```
![{032FC489-B66B-48D6-8AC7-D6863DAFA9CE}](https://github.com/user-attachments/assets/bc1ea3c7-bd44-4e81-bd2b-c470a8629d9b)
