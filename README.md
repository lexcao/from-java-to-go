# From Java To Go

> From Java To Go - Your Cheat Sheet For Java To Go

The Java code is from [from java to kotlin](https://github.com/MindorksOpenSource/from-java-to-kotlin)

## Print to Console

> Java

```java
System.out.print("Hello world.");
System.out.println("Hello world.");
```

> Go

```go
print("Hello world")
println("Hello world")
fmt.Print("Hello world")
fmt.Println("Hello world")
```

---

## Constants and Variables

> Java

```java
String language = "Java";
final String language = "Java";
```

> Go

```go
language := "Go"
var language = "Go"
var language string = "Go"
const language string = "Go"
```

---

## Assigning the null value

> Java

```java
String language;
language = null;
```

> Go

```go
var language string
language = nil // Cannot use 'nil' as the type string

// for other type such as interface{}
var language interface{}
language = nil

```

---

## Verify if value is null

> Java

```java
if (text != null) {
    int length = text.length();
}
```

> Go

```go
if text != "" {
    length := len(text)
}
```

---

## Verify if value is NotNull  OR NotEmpty

> Java

```java
String sampleString = "Lex";
if (!sampleString.isEmpty()) {
    myTextView.setText(sampleString);
}
if(sampleString!=null && !sampleString.isEmpty()){
    myTextView.setText(sampleString); 
}
```

> Go

```go
sampleString := "Lex"
if len(sampleString) != 0 {  // len will check type and size
    myTextView.text = sampleString
}
```

---

## Concatenation of strings

> Java

```java
String firstName = "Lex";
String lastName = "Cao";
String message = "My name is: " + firstName + " " + lastName;
```

> Go

```go
firstName := "Lex"
lastName := "Cao"
message := "My name is: " + firstName + " " + lastName
message := fmt.Sprintf("My name is: %s %s", firstName, lastName)

// or use string builder
var builder strings.Builder
builder.WriteString("My name is: ")
builder.WriteString(firstName)
builder.WriteString(" ")
builder.WriteString(lastName)
message := builder.String()
```

---

## New line in string

> Java

```java
String text = "First Line\n" +
              "Second Line\n" +
              "Third Line";
```

> Go

```go
text := `First Line
Second Line
Third Line
`
```

---

## Substring

> Java

```java
String str = "Java to Go Guide";
String substr = "";

//print java
substr = str.substring(0, 4);
System.out.println("substring = " + substr);

//print go
substr = str.substring(8, 10);
System.out.println("substring = " + substr);
```

> Go

```go
str := "Java to Go Guide"
substr := ""

//print java
substr = str[:4]
fmt.Println("substring", substr)

//print go
substr = str[8:10]
fmt.Println("substring", substr)
```

---

## Ternary Operations

> Java

```java
String text = x > 5 ? "x > 5" : "x <= 5";

String message = null;
log(message != null ? message : "");
```

> Go

```go
var text string
if x > 5 {
    text = "x > 5"
} else {
    text = "x <= 5"
}

var message interface{}
if message != nil {
    log(message)
}
```

---

## Bitwise Operators

> Java

```java
final int andResult  = a & b;
final int orResult   = a | b;
final int xorResult  = a ^ b;
final int rightShift = a >> 2;
final int leftShift  = a << 2;
final int unsignedRightShift = a >>> 2;
```

> Go

```go
andResult  := a & b
orResult := a | b
xorResult := a ^ b
rightShift := a >> 2
leftShift := a << 2
andNot := a &^ b
// there is no unsigned right shift for go
// the sign of right and left shift depend on type, go has both sign and unsigned integer
```

---

## Check the type and casting

> Java

```java
if (object instanceof Car) {
	Car car = (Car) object;
}
```

> Go

```go
if car, ok := interface{}(object).(Car); ok {
    // object is Car
}

// print type
fmt.fmt.Sprintf("%T", object)

// switch type
switch value := object.(type) {
    case Car:
        fmt.Println("Car:", value)
    case Vehicle:
        fmt.Println("Vehicle:", value)
    default:
        fmt.Println("unknown type")
}
```

---

## Multiple Conditions (Switch case)

> Java

```java
int score = // some score;
String grade;
switch (score) {
	case 10:
	case 9:
		grade = "Excellent";
		break;
	case 8:
	case 7:
	case 6:
		grade = "Good";
		break;
	case 5:
	case 4:
		grade = "OK";
		break;
	case 3:
	case 2:
	case 1:
		grade = "Fail";
		break;
	default:
	    grade = "Fail";				
}
```

> Go

```go
var score int // some score
var grade string
switch score {
    case 9, 10:
        grade = "Excellent"
    case 6, 7:
        fallthrough // fallthrough next case
    case 8:
        grade = "Good"
    case 4, 5:
        grade = "OK"
    default:
        grade = "Fail"
}
```

---

## For-loops

> Java

```java
for (int i = 1; i <= 10 ; i++) { }

for (String item : collection) { }

for (Map.Entry<String, String> entry: map.entrySet()) { }

while (true) { }
```

> Go

```go
for i := 0; i < 10; i++ { }

for index := array { }

for _, item := range collection { }

for index, item := range collection { }

for key, value := range someMap { }

for { }
```

---

## Collections

> Java

```java
final List<Integer> listOfNumber = Arrays.asList(1, 2, 3, 4);

final Map<Integer, String> keyValue = new HashMap<Integer, String>();
map.put(1, "Amit");
map.put(2, "Ali");
map.put(3, "Mindorks");

// Java 9
final List<Integer> listOfNumber = List.of(1, 2, 3, 4);

final Map<Integer, String> keyValue = Map.of(1, "Amit",
                                             2, "Ali",
                                             3, "Mindorks");
```

> Go

```go
// Slice
listOfNumber := []int{1, 2, 3, 4}

// Map
keyValue := map[int]string {
    1: "Amit",
    2: "Ali",
    3: "Mindorks",
}
```

---

## Splitting arrays

> java

```java
String[] splits = "param=car".split("=");
String param = splits[0];
String value = splits[1];
```

> Go

```go
splits := strings.Split("param=car", "=")
param := splits[0]
value := splits[1]
```

---

## Defining functions

> Java

```java
void doSomething() {
   // logic here
}

int shouldReturn() {
    return 1;
}
```

> Go

```go
func doSomething() {
    // logic here
}

func shouldReturn() int {
    return 1
}

func canDefineReturnVariable() (len int, cap int) {
    len = 0
    cap = 10
    return
}

func canReturnMultipleValues() (int, int, int, int) {
    return 1, 2, 3, 4
}
```

## Variable number of arguments

> Java

```java
void doSomething(int... numbers) {
   // logic here
}

int[] nums = new int[]{1, 2, 3};
doSomething(nums);
```

> Go

```go
func doSomething(numbers ...int) {
    // logic here
}

nums := []int{1, 2, 3}
doSomething(nums...)
```

---

## enum

> Java

```java
public enum Direction {
        NORTH(1),
        SOUTH(2),
        WEST(3),
        EAST(4);

        int direction;

        Direction(int direction) {
            this.direction = direction;
        }

        public int getDirection() {
            return direction;
        }
    }
```

> Go

```go
const (
    North = 1 + iota
    South
    West
    East
)

fmt.Println(North, South, West, East) // 1, 2, 3, 4
```

---

## Sorting List

> Java

```java
List<Profile> profiles = loadProfiles(context);
Collections.sort(profiles, new Comparator<Profile>() {
    @Override
    public int compare(Profile profile1, Profile profile2) {
        if (profile1.getAge() > profile2.getAge()) return 1;
        if (profile1.getAge() < profile2.getAge()) return -1;
        return 0;
    }
});

```

> Go

```go
profile := loadProfiles(context)
sort.Slice(profile, func (i, j int) bool {
    return profile[i].Age < profile[j].Age
})
```

---

## Anonymous Class

> Java

```java
 AsyncTask<Void, Void, Profile> task = new AsyncTask<Void, Void, Profile>() {
    @Override
    protected Profile doInBackground(Void... voids) {
        // fetch profile from API or DB
        return null;
    }

    @Override
    protected void onPreExecute() {
        super.onPreExecute();
        // do something
    }
};

```

> Go

```go
// Anonymous Struct
_ := struct {
    name string
    want string
    got  string
}{
    "test A",
    want,
    got,
}
```

---

## Initialization block

> Java

```java
public class User {
    {  //Initialization block
        System.out.println("Init block");
    }
}

```

> Go

```go
// will call before main on its package after imported
func init() {
    fmt.Println("Init func")
}
```

---

## Multiple Assignment

> Java

```java
void swap(int[] nums, int i, int j) {
    int t = nums[i];
    nums[i] = nums[j];
    nums[j] = t;
}
```

> Go

```go
func swap(nums []int, i, j int) {
    nums[i], nums[j] = nums[j], nums[i]
}
```

---

## Error handling

> Java

```java
try {
    byte[] bytes = Files.readAllBytes(Path.of("test.txt"));
} catch (IOException e) {
    // handle file exception
}
```

> Go

```go
bytes, err := os.ReadFile("test.text")
if err != nil {
    // handle file err
}
```

---

## OOP

> Java

```java
interface Movable {
    void move();
}

class Car implements Movable{
    @Override
    public void move() { }
}

Movable car = new Car();
```

> Go

```go
type Movable interface {
	Move()
}

type Car struct{}

func (c Car) Move() {}

var car Movable = new(Car)
```

---

# Some useful Go links

* [Official Website](https://go.dev/)
* [Awesome Go](https://github.com/avelino/awesome-go)
* [Practical Go of Dave](https://dave.cheney.net/practical-go)
* [High Performance Go](https://dave.cheney.net/high-performance-go)

# Found this project useful :heart:

* Support by clicking the :star: button on the upper right of this page. :v:

# License

```
   Copyright 2021 Lex Cao

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```

### Contributing to From Java To Go

Just make a pull request. You are in!