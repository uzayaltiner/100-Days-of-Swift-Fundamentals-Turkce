# Day 12

### 1. Handling Missing Data
Bir değer tutmak istiyorsak fakat değerin bilgisi henüz elimizde yoksa, Swift bize optionals opsiyonunu sunar. Tüm veri tipleri için kullanılır. Hadi bir optional tanımlayalım.

```swift
var age: Int? = nil
```
Yukarıda tanımladığımız optionalda int değeri alacak bir değer tanımladık. Nil değeriyle bu değişkenin bir değeri olduğunu fakat henüz bilmediğimizi gösteriyoruz. Bu bilgiyi edindiğimiz zaman standart değişken değiştirir gibi değiştirebiliriz.
```swift
age = 27 
```

# 2. Unwrapping Optionals
Optional string yapısı bir string değeri ya da nil değeri tutar. String methodlarından count kullanırsak optinalımız bir değer tutuyorsa çalışır fakat nil ise çalışmaz. Çünkü nil'in tuttuğu değer boştur. Bunun için bu gibi methodla çalışırken önce değerimiz var mı diye kontrol etmemiz gerekir. Bunu da yaygın olarak if let syntax'ı ile kullanırız. unwrapped anahtarını kullanarak bir if let kodu yazalım;
```swift
var name: String? = nil

if let unwrapped = name {
    print("\(unwrapped.count) harf var.")
} else {
    print("İsim yok")
}
```

Yukarıdaki kodumuzda önce unwrapped optional'ıyla değişkenimizin var olup olmadığını kontrol ediyoruz. Sonrasında true ise sonucu, false ise hatayı yazdırıyoruz.

### 3. Unwrapping with Guard
İf let'e alternatif olarak guard let'de kullanabiliriz. Guard let opsiyonlarımızla çalışmamızı sağlar fakat opsiyonumuzun değeri nil ise içinde kullandığımız yapıdan(for, func, if vs.) çıkmamızı bekler. Örneğin;
```swift
func greeting(_ name: String?) {
    guard let unwrapped = name else {
        print("Lütfen adınızı giriniz!")
        return
    }
    print("Hoşgeldin, \(unwrapped)!")
}
```
Yukarıdaki kodu çalıştırdığımızda, gönderdiğimiz değer nil ise kod hatayı fonksiyonun başında çalıştırıp yazdıracak.

### 4. Force Unwrapping
Optional bir değerin orda olup olmadığı anlamına gelir. Fakat bazen bir değerin orda olup olmasa da nil olmadığını bilirsiniz. Bu durumda optionalınıza force unwrapping yöntemiyle istediğiniz tipe döndürmeye zorlayabilirsiniz. Örneğin içinde integer tutan bir string yapımız olduğunu biliyorsak bu değeri integer'a çevirebiliriz;
```swift
var str = "5"
var int = Int(str)
```
Yukarıdaki kod optionaldır. Çünkü str olan yapının içinde numara tutmuyor olabiliriz. Fakat bu durumdan eminsek kodumuzun sonuna ! ekleyerek bu işleme zorlayabiliriz:
```swift
var int = Int(str)!
```
Fakat yukarıdaki kodun içinde str, integer harici bir tip tutuyorsa kodumuz hata verecektir. 

### 5. Implicitly Unwrapped Optionals
Normal optional gibidirler. Bir değer ya da nil değerini taşırlar. Fakat kullanmak için açmaya(unwrap) gerek yoktur. 
```swift
var age: Int! = nil
```
if let ya da guard let kullanmamıza gerek yoktur. Fakat eğer içinde bir değer tutmuyorsa yani nil ise kodumuz hata verecektir. Oluşturulurken boş olurlar fakat her kullanmanız gerektiğinde bir değer alacağı bellidir. Her seferinde if let kullanmamak için iyi bir alternatiftir.

### 6. Nil Coalescing
Bunu bir örnek üzerinden öğrenelim.
```swift
func username(for id: Int) -> String? {
    if id == 1 {
        return "Taylor Swift"
    } else {
        return nil
    }
}
```
Yukarıdaki kodumuzda int parametresi alıp string optionalına dönen bir fonksiyonumuz var. Eğer bu fonksiyonu direkt değerle çağırırsak ve bu değer 1 değilse nil'e dönecek. Bunu istemezsek nil coalescing kullanarak farklı bir stringe dönmesini sağlayabiliriz.

```swift
var name = username(for: 15) ?? "Anonymous"
```
### 7. Optional Chaining
Swift, optionalları kullanırken bize kısayollar sunar. Eğer bir şeye uşalmak istiyorsak ve bu a.b.c gibi tanımlanıyorsa; ve b bu tanımda opsiyonelse b? şeklinde tanımlayabiliriz.
Bir örnekle deneyelim;

```swift
let name = ["John", "Paul", "George", "Ringo"]
```
4 adet elemanı olan bir array tanımladık. Şimdi ilk elemanını uppercase yapalım.

```swift
let beatles = names.first?.uppercased()
```
Burada first seçimindeki "?" soru işareti optional olduğunu temsil ediyor. Eğer arrayimizde hiç eleman yoksa ya da ilk eleman boşsa nil dönecek.

### 8. Optional Try
Throwing fonksiyona çalışırken şu kodu görmüştük;
```swift
enum PasswordError: Error {
    case obvious
}

func checkPassword(_ password: String) throws -> Bool {
    if password == "password" {
        throw PasswordError.obvious
    }

    return true
}

do {
    try checkPassword("password")
    print("That password is good!")
} catch {
    print("You can't use that password.")
}
```
Bu kod bloğunda try,do,catch yapısına alternatif kullanabileceğimiz 2 yöntem var.
1. try? yöntemi
```swift
if let result = try? checkPassword("password") {
    print("Result was \(result)")
} else {
    print("D'oh.")
}
```
2. try! yöntemi
```swift
try! checkPassword("sekrit")
print("OK!")
```

### 9. Failable Initializers
Structların ve classların içinde kullanılan init methodunun çalışıp çalışmayacağına karar verir. Örneğin 9 harfli bir kullanıcı adı oluşturmayı deniyelim;
```swift
struct Username {
    var id: String

    init?(id: String) {
        if id.count == 9 {
            self.id = id
        } else {
            return nil
        }
    }
}
```
Bu koda girecek değer 9 harfli olmazsa nil değeri  dönecektir. Fakat kodumuz 9 harfli olursa hiçbir şey olmadan çalışacaktır.

### 10. Typecasting
Bunu bir örnekle çalışalım.
```swift
class Animal { }
class Fish: Animal { }

class Dog: Animal {
    func makeNoise() {
        print("Woof!")
    }
}
```
Yukarıda 3 adet classımız var. Bu classlarla bir array oluşturalım.
```swift
let pets = [Fish(), Dog(), Fish(), Dog()]
```
Eğer bu arraye bir loop oluşturmak istersek ve her dog elemanı geldiğinde elemanımızın makeNoise() fonksiyonunu çalıştırmasını istersek bunu typecasting ile sağlarız.

```swift
for pet in pets {
    if let dog = pet as? Dog {
        dog.makeNoise()
    }
}
```
