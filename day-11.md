# Day 11
"Her büyük programın içinde, dışarı çıkmaya çalışan küçük bir program vardır." Tony Hoare

### 1. Protocols
Protocollerde Class, Struct ve enumlar için uyulması gereken kuralları tanımlarız. Bir class miras alırken birden çok class'tan miras alamaz fakat istediğimiz kadar protocol tanımlayabiliriz. Ayrıca protocoldeki özelliklerimizin tiplerine miras bıraktığımız struct ya da claslarda uymamız gerekmez. Örneğin;
```swift
protocol Identifiable {
    var id: String {get set}
}
```
Yukarıdaki kodda string tipinde bir özellik tanımladık. Fakat bu protokolle tanımlayacağımız struct ya da classta bu tipi değiştirebiliriz. Bunu get set ile belirtiriz. Ayrıca protocollere değer gönderemeyiz.

```swift
struct User: Identifiable {
    var id: String
}
```
Şimdi bu identifiable objesiyle bir fonksiyon yazabiliriz.

```swift
func displayID(thing: Identifiable) {
    print("My ID is \(thing.id))
}
```
### 2. Protocol Inheritance
Bir protokol başka bir protocolden miras alabilir. Claslardan farklı olarak bir protocol birden çok protocolden miras alabilir.

```swift
protocol Payable {
    func calcWages () -> Int
}

protocol NeedsTraining {
    func study()
}

protocol HasVacation {
    func takeVacation(day: Int)
}
```
Yukarıda 3 adet protocol tanımladık. Şimdi ise bu 3 protocolü miras alan yeni bir protocol tanımlayalım.
```swift
protocol Employee: Payable, NeedsTraining, HasVacation {}
```
### 3. Extensions
Extensionlar var olan tiplere yöntemler eklememizi sağlar. Örneğin integerların karesini alan bir fonksiyon yazalım;
```swift
extension Int {
    func square() -> Int {
        return self * self
    }
}
```
Yukarıda integer değerleri için bir square yöntemi tanımlamış olduk. Artık bu yöntemi int değerlerle kullanabiliriz.
```swift
print(5.square()) // kodumuzun çıktısı 25 olacak.
```
 
### 3. Protocol Extensions
Protocoller ve extentionları birlikte kullanmamızı sağlar. Şöyle ki uygun bütün uyumlu törlerle işlem yapabileceğimiz bir extention oluştururuz. Çalışacağı tipi tanımlamamıza gerek kalmaz. Örneğin;

```swift
let pythons = ["Eric", "Graham", "John", "Michael", "Terry", "Terry"]
let beatles = Set(["John", "Paul", "George", "Ringo"])
```
elimizde bir array bir de set olsun.

Arrayler ve setler swiftte protocol olarak kabul edilir. Şimdi grubumuzun eleman sayısını ve ismini yazdıran bir extension yazalım.
```swift
extension Collection {
    func summarize() {
        print("There are \(count) of us:")

        for name in self {
            print(name)
        }
    }
}
```
```swift
pythons.summarize()
beatles.summarize()
```
### 4. Protocol-oriented Programming
Protocol extensionları gelecekte kullanacağımız protocol methodlarımız için uygulamalar yazmamızı sağlar. Buna protocol-oriented programming denir. Özetle kodumuzu protocoller ve protocol extensionlar etrafında kurmamuzu sağlar.
Öncelikle, herhangi bir tipte id özelliği ve identify methodu tutan bir protocol tanımlayalım;
```swift
protocol Identifiable {
    var id: String {get set}
    func identify()
}
```
Şimdi protocol extension yöntemiyle identify methodumuzu yazalım.
```swift
extension Identifiable {
    func identify() {
        print("My ID is \(id).")
    }
}
``` 
Şimdi bi protocolü miras alan bir struct yapı tanımlayalım.

```swift
struct User: Identifiable {
    var id: String
}
```
Yukarıdaki kodda User stringi identify methodunu miras aldı. Şimdi kodumuzu çağıralım.
```swift
var userID = User(id: "twostraws")
twostraws.identify()
```
Böylece Identifiable protocolü için extension içinde tanımladığımız methodu kullanıp mesajımızı yazdırabiliriz. 