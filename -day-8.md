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
Struct içindeki değerimiz her değiştiğinde otomatik olarak bir mesaj yazdırmak isteyebiliriz. Swift bunu didSet komutuyla yapar. Buna property observers denir.
```swift
struct Progress {
    var task: String
    var amount: Int {
        didSet {
            print ("\(task) is now \(amount)% complete.")
        }
    }
}
```
Yukarıdaki struct'ımızda amount değeri her değiştiğinde otomatik olarak didSet komutu çalışacak. 
```swift
var progress = Progress(task: "Loading Data", amount: 0)
progress.amount = 30
progress.amount = 50
progress.amount = 80
```
Yukarıdaki komutumuzda progress.amount her değiştiğinde mesajımız print edilecek.

Eğer komutumuzu değer değişmeden önce çağırmak istersek bunu willSet komutuyla yaparız. Fakat bu çok fazla kullanılan bir yöntem değildir.

### 4. Methods
Struct'ların içinde fonksiyonlar tanımlayabiliriz. Bunlara Method adı verilir ve standart fonksiyonlar gibi tanımlanır(func).
```swift
struct City {
    var population: Int

    func collectTaxes() -> {
        return population * 1000
    }
}
```
Yukarıda nüfusa göre toplanan vergiyi çıkartan bir struct tanımladık. Hadi bu fonksiyonu çağıralım.

```swift
let istanbul = City(population: 9_000_000)
istanbul.collectTaxes()
```

### 5. Mutating Methods
Swift method tanımlarken özellikleri aksini belirtmediğiniz sürece sabit olarak kabul eder ve değiştirmenize izin vermez. Method'un içindeki özelliği değiştirilebilir olmasını istiyorsak, methodumuzu "mutating" anahtar kelimesiyle işaretlememiz lazım. Örneğin;

```swift
struct Person {
    var name: String

    mutating func makeAnonymous () {
        name = "Anonymous"
    }
}
```
### 6. Properties and Methods of String
Şimdiye kadar çok fazla string yapısı kullandık. Stringlerin sorgulamak ve manipüle etmek için kendilerine has methodları ve propertieleri vardır. Bunları örneklemek için önce bir string değişkeni tanımlayalım.
```swift
var string = " Merhaba dünya."
```
1. Count özelliğini kullanarak bir stringdeki karakter sayısını öğrenebiliriz.
```swift
print(string.count)
```
2. hasPrefix() özelliğiyle stringimiz sorguladığımız değerle başlıyorsa true ifadesini döndürebiliriz.
```swift
print(string.hasPrefix("Merhaba")) // true sonucunu alacağız.
```
3. uppercased() özelliğiyle stringimizin tüm harflerinin büyük olmasını sağlayabiliriz.
```swift
print(string.uppercased())
```
4. sorted() özelliğiyle stringimizin tüm elemanlarını arraye çevirebiliriz.
```swift
print(string.sorted())
```
Daha birçok özellik ve method var. Bunları Xcode ve ya Playgrounds üzerinden otomatik tamamlama özelliğiyle deneyebilirsiniz.

### 7. Properties and Methods of Arrays
Arrayler de stringler gibi kendi method ve propertielerine sahiptir.
```swift
var toys = ["Woody"]
```
1. count methoduyla array içindeki eleman sayısını öğrenebiliriz.
```swift
print(toys.count)
```
2. append() methoduyla arrayimize yeni bir eleman ekleyebiliriz.
```swift
toys.append("Buzz")
```
3. firstIndex() methoduyla bir elemanın array içindeki konumunu bulabiliriz.
```swift
toys.firstIndex(of: "Buzz")
```
4. sorted() methoduyla array içindeki elemanları alfabetik olarak sıralayabiliriz.
```swift
toys.sorted()
```
5. remove() methoduyla array içinden eleman silebiliriz.
```swift
toys.remove(at: 0)
```