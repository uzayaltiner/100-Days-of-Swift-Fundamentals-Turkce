# Day 5
### 1. Writing Functions
Fonksiyonlar kodu tekrar kullanmamıza izin verir. Yazdığımız kodu birçok yerde, tekrar tekrar çalıştırabiliriz. Kodu tekrarlamak kötü bir fikirdir ve fonksiyonlar bundan kaçınmamızı sağlar.Örneğin;

```swift
func merhaba() {
    let hosgeldin = "Uygulamamıza hoşgeldin."
}
```
Fonksiyonumuzu tanımladık. Şimdi aşağıdaki kod ile bu fonksiyonu istediğimiz yerde çalıştırabiliriz.
```swift
merhaba()
```
### 2. Accepting Parameters
Fonksiyonlar her çalıştırıldıklarında özelleştirilebildiği için daha kullanışlı hale gelirler. Swift, bir fonksiyona değer göndermemize izin verir. Fonksiyona gönderilen değerlere parametre denir. Fonksiyonların bu parametreleri tanımlayabilmesi için şu şekilde tanımlanması gerekir. Örneğin;

```swift
func numberSquare(number: Int) {
    print(number * number)
}
``` 
Yukarıdaki fonksiyonda fonksiyonumuzun number adında bir integer alacağını söyledik. Şu şekilde kullanacağız;
```swift
numberSquare(5) // Sonuç 25
```

### 3. Returning Values
Fonksiyonlara değer gönderebileceğimiz gibi fonksiyonların çıktısını da belirleyebiliriz. Örneğin;
```swift
func square(number: Int) -> Int {
    return number * number
}
```

Şimdi fonksiyonun çalıştığında çıkacak değeri yakalayabiliriz.

```swift
let result = square(number: 8)
print(result)
```

### 4. Parameter Labels
Swift, her parametre içine 2 isim yazmamıza olanak sağlar. Biri fonksiyon çağırılırken kullanılacak, diğeri fonksiyon içinde dahili olarak bulunacak.

```swift
func sayHello(to name: String) {
    print("Hello, \(name)!")
}
```
Yukarıda 2 isim kullanan bir fonksiyon görüyoruz. Bu fonksiyonda dahili olarak name atanmış. Fakat bu fonksiyonu çağırırken to ile çağıracağız.

```swift
sayHello(to: "Uzay")
```
### 5. Ommitting Parameter Labels
Swift'te print fonksiyonunu kullanırken hiçbir parametre ismi kullanmadığımızı fark etmişsinizdir. Bunu kendi fonksiyonlarımızda (_) alt tire ifadesiyle kullanırız. Örneğin;

```swift
func sayHi(_ name: String) {
    print("Hello, \(name)!")
}
```
Artık fonksiyonumuzu print("Uzay") şeklinde kullanabiliriz. Bu kodu okumayı daha kolay hale getiriyor fakat yine de karışıklığı gidermek için parametrelere isim vermek gerekir.

### 6. Default Parameters
Kendi parametrelerimize varsayılan bir değer atayabiliriz. Bunu parametrenin ismini ve tipini belirledikten sonra = işareti kullanarak yaparız. Örneğin;
```swift
func grade(_ person: String, basarı: Bool = true) {
    if basarı == true {
        print(Tebrikler \(person). Dersten geçtin.")
    } else {
        print("Daha çok çalışmalısın \(person)...)
    }
}
```
bu fonksiyonu iki şekilde çagırırız. 
```swift
grade("Uzay")
grade("Uzay", basarı: false)
```
### 7. Variadic Functions
Herhangi birparametreyi türünden sonra "..." kullanarak değişken yapabilirsiniz. Bunu örnek üzerinden deneyelim.
```swift
func square(numbers: Int...) {
    for number in numbers {
        print("\(number)'ın karesi \(number * number)'dır.")
    }
}
```
Yukarıdaki kodda iletilen değerleri Swift integer arreyine döndürür.
```swift
square(numbers: 1, 2, 3, 4, 5)
```
Şeklinde bir girdiyle elde edeceğimiz sonuç her bir değer için ayrı ayrı çalışacaktır.

### 8. Writing Throwing Functions
Bazen fonksiyonlar hatılı bir girdi yazıldığında başarısız olur. Öncelikle hatayı tanımlayan bir enum tanımlamamız gerekiyor.
```swift
enum PasswordError: Error {
    case obvious
}
``` 
şimdi bir şeyler ters gittiğinde hata göderecek fonksiyonumuzu yazabiliriz.
```swift
func chechPassword (_ password: String) throw -> Bool {
    if password == "password" {
        throw PasswordError.obvious
    }
}
```

### 9. Running Throwing Functions