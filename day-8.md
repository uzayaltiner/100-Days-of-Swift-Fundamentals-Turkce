# Day 8
### 1. Creating Your Own Structs
Swift kendi yapılarınızı struct olarak tanımlamanıza izin verir. Structlar sabitlerine, değişkenlerine ve fonksiyonlarına sahip olabilir ve bu yapılar istediğimiz zaman kullanabiliriz. Örneğin;
```swift
struct Sport {
    var name: String
}
```
Yukarıda name değişkenin string olarak saklayacak bir sport struct'ı tanımladık.
```swift
var tenis = Sport(name: "Tenis")
print(tenis.name)
```
Burada name ve tenis olarak iki değişken tanımladık. Artık normal değişkenler gibi değiştirebiliriz.
```swift
tenis.name = "Lawn Tenis"
```

### 2. Computed Properties
Daha önce tanımladığımız bir sport struct'ı var.
```swift
struct Sport {
    var name : String
}
```
Bunlara depolanmış özellikler denir. Swift, değerini bulmak için kod çalıştıran, computed properties adı verilen bir depolama şekline sahiptir.
```swift
struct Sport {
    var name : String
    var isOlympic: Bool

    var olympicStatus: String {
        if isOlympic {
            return "\(name) olimpik bir spordur."
        } else {
            return "\(name) olimpik bir spor değildir."
        }
    }
}
```
isOlympic standart bir String yapısı gibi görünse de diğer özelliklere bağlı olarak farklı değerlere döner. 
```swift
let chess = Sport(name: "Chess", isOlympic: false)
print(chess.olympicStatus)
```
Yukarıdaki girdi bize olympicStatus'ün bu girdilere göre değerini verecek.

### 3. Property Observers