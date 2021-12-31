# Day 10
"Herhangi biri bilgisayarın anlayabileceği bir kod yazabilir, fakat iyi bir programcı bir insanın anlayacağı kod yazar." Martin Fowler
### 1. Creating your own Classes
Classlar, structlarla oldukça benzerdir. Fakat 5 temel fark vardır. Bunlardan ilki; bir class yapınız varsa ve bu classın içinde özellikleriniz varsa, her zaman bir initializer tanımlamanız gerekir.
```swift
class Dog {
    var name: String
    var breed: String

    init(name: String, breed: String) {
        self.name = name
        self.breed = breed
    }
}
```
Yeni bir istek tanımlarken tamamen struct gibi tanımlarız.
```swift
var poppy = Dog(name: "Poppy", breed: "Poople")
```

### 2. Class Inheritance
Structlar ve classlar arasındaki ikinci fark; mevcut bir sınıfa bağlı başka bir sınıf oluşturabilmenizdir. Orjinal sınıfın tüm özelliklerini devralır. Buna class inheritance denir.
```swift
class Dog {
    var name: String
    var breed: String

    init(name: String, breed: String) {
        self.name = name
        self.breed = breed
    }
}
``` 
Yukarıda standart bir class var. Şimdi bu class'a dayalı yeni bir class oluşturalım.
```swift
class Poddle: Dog {
    init(name: String) {
        super.init(name: name, breed: "Poddle")
    }
}
```
Yukarıda gördüğünüz gibi Dog clasını çağıran bir Poddle clası oluşturduk. Bu puddle clası dog clasının init'ini çağırdığı gibi kendi init'ine de sahip. Parent class'ta olan initi çağırırken super.init olarak tanımlamalıyız.

# 3. Overriding Methods
Child class'lar parent classların methodlarını kullanabilir. Buna override denir.
```swift
class Dog {
    func makeNoise() {
        print("Woof!")
    }
}
```
Eğer Dog clasıyla bağlı yeni bir class tanımlarsak bu class da bu fonksiyonu kullanacaktır. Örneğin;
```swift
class Poodle: Dog {

}
let poppy = Poddle()
poppy.makeNoise() // bu girdi bize Woof! çıktısını verecektir.
```

Override metodu bize parent clasındaki fonksiyonu değiştirme olanağı tanır. Fakat bu override metodunu child classında tanımlamalıyız yoksa hata alırız.
```swift
class Poddle: Dog {
    override func makeNoise() {
        print("Yip!")
    }
}
```
# 4. Final Classes
Classları tanımlarken final anahtar kelimesini kullanırsanız; başka bir class ona bağlanamaz. 
```swift
final class Dog {
    var name: String
    var breed: String

    init(name: String, breed: String) {
        self.name = name
        self.breed = breed
    }
}
```
# 5. Copying Objects
Structlar ve classlar arasındaki 3. fark classları kopyaladığınız zaman bir hangisinde değişiklik yaparsanız yapın bu değişiklik diğerine de uygulanacaktır.
```swift
class Singer {
    var name = "Taylor Swift"

}
```
```swift
var singer = Singer()
print(singer.name)
```
Yukarıda Singer classımızın name'ini çağırdık. Bunun çıktısı Taylor Swift olacak. Şimdi bunu değiştirelim.

```swift
var singer2 = singer()
singer2.name = "Justin Bieber"
```
Bu kodun singer ve singer2 aynı şeylerdir. singer.name komutunu yazdırırsak Justin Bieber çıktısını alacağız. Yani Singer class'ımızın name değeri değişti.

Eğer bu yapımız struct olsaydı değişmeyecekti. singer ve singer1 özellikleri farklı özellikler olacaktı.

# 6. Deinitializers
Struct ve classlar arasındaki 4. fark classların deinitializer kullanmasıdır. Bu clasın bir örneği yok edilmeden bir kod çalıştırmamıza olanak sağlar.Örneğin bir class tanımlayalım;
```swift
class Person {
    var name: "Uzay"

    init() {
        print("\(name) is alive!")
    }

    func printGreating() {
        print("Hello, I'm \(name).")
    }
}
```
Şimdi bu classımızı çalıştıracak bir for loopu tanımlayalım.
```swift
for _ in 1...3 {
    let person = Person()
    person.printGreating()
}
```
Şimdi clasımızın içine clasımız çalışmayı tamamladıktan sonra bir string yazdıracak bir deinit tanımlayalım.
```swift
class Person {
    var name: "Uzay"

    init() {
        print("\(name) is alive!")
    }

    func printGreating() {
        print("Hello, I'm \(name).")
    }
    deinit {
        print("\(name) is no more!")
    }
}
```

# 7. Mutability
Structlar ve classlar arasındaki son fark; classların sabitlerle çalışabilmesidir. Örneğin;

```swift
class Singer {
    var name = "Taylor Swift"
}
let taylor = Singer()
taylor.name = "Ed Sheeran"
print(taylor.name)
```
Yukarıdaki kodun çıktısı Ed Sheeran olacaktır. taylor özelliğini tanımlarken let ile(sabit) tanımladık. Fakat taylor.name'i değiştirmemize izin verdi. Eğer bu değişikliği engellemek istersek classın içindeki özelliğimizi let ile tanımlamalıyız.
