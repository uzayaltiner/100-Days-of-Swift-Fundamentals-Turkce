# Day 9
"Zor bir iş yapması için tembel bir kişiyi seçerim. Çünkü tembel kişi kolay yolu bulacaktır." Bill Gates
### 1. Initializers
Initializer, structlarımızı farklı bir yöntemle yaratmamızı sağlayan özel bir methoddur. Örneğin;
```swift
struct User {
    var username: String
    init() {
        username = "Anonymous"
        print("Creating a new user!")
    }
}
```
Yukarıdaki structta initializers kullanırken func anahtar kelimesine ihtiyaç duymayız. Fakat tüm özelliklerimizin bir değer aldığından emin olmamız gerekir.

Initializer'ımız parametre kabul etmez. Struct'ımızı şu şekilde oluşturmamız gerekir.
```swift
var user = User()
user.username = "Uzay"
```

### 2. Referring to the Current Instance
Bunu bir örnek üzerinden çalışalım.
```swift
struct Person {
    var name: String

    init(name: String) {
        print("Benim adım \(name)")
        self.name = name
    }
}
```
Yukarıdaki struct'da initializer'ımıza name adında bir parametre tanımladık. "self" anahtar kelimesip parametreleri ve özellikleri ayırmamızı sağlar. Yukarıdaki methodda name adında bir parametremiz varken, "self.name" adında ve name değeriyle aynı olan bir propertymiz var.

### 3. Lazy Properties
Swift; performans için, bazı propertyleri sadece gerektiğinde oluşturmamıza izin verir.
```swift
struct FamilyTree {
    init() {
        print("Soyağacı oluşturuluyor.")
    }
}

// şimdi yukarıdaki struct'ı aşağıdaki struct'ta property olarak tanımlayalım. 

struct Person {
    var name: String
    lazy var familyTree: familyTree()

    init(name: String) {
        self.name = name
    }
}

var ed = Person(name: "Ed")
```
Yukarıdaki structta lazy var komutuyla Swift; FamilyTree struct'ını ilk çalıştırmada oluşturacak. Eğer bu mesajı tekrar görmek istersek şu şekilde çağırmalıyız.
```swift
ed.familyTree
```

