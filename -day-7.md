# Day 7
"Enerji ve ısrar her şeyi fetheder." Benjamin Franklin
 
### 1. Using Closures as Parameters when they Accept Parameters
Bir fonksiyona parametre olarak atadığımız closure kendi parametrelerini de alabilir. "() -> Void" Closurelerı tanımladığımız gibi kullanacağız fakat parantezin içine closure'umuz içinde yazılacak parametreyi yazacağız. Örneğin;
```swift
func travel(action: (String) -> Void) {
    print("Gitmeye hazırım.")
    action("İstanbul")
    print("ulaştım.")
}
```
Trailing Closure Syntax ile fonksiyonumuzu çağırdığımızda, closure'umuz string parametresi kabul edecek.
```swift
travel { (place: String) in
    print("\(place)'a gidiyorum.")
}
```
### 2. Using closures as parameters when they return values
Void parametresiyle kurduğumuz fonksiyonların döneceği bir yer yoktur. Void'i herhangi bir veri türüyle değiştirip closure'u return'e döndürebiliriz.
```swift
func travel(action: String) -> String {
    print("Gitmeye hazırım.")
    let istanbul = action("İstanbul")
    print(istanbul)
    print("Ulaştım.")
}
```
Yukarıdaki kodda action İstanbul olarak tanımlandı. Şimdi "Action: İstanbul" closure'umuzu tanımlayalım. Burada dikkat etmemiz gereken String tipi girdi(İstanbul) sonucunda String bir çıktı alacağız.
```swift
travel { (place: String) -> String in
    return "\(place)'a gidiyorum."
    } 
```
Bu closure'da yukarıdaki fonksiyondan gelen İstanbul stringi place olarak fonksiyona giriyor. Closure'un tamamı yukarıdaki fonksiyona dönüyor. 

### 3. Shorthand Parameter Names
```swift
func travel(action: String) -> String {
    print("Gitmeye hazırım.")
    let istanbul = action("İstanbul")
    print(istanbul)
    print("Ulaştım.")
}
```
Bu konuyu bu örnek üzerinden çalışacağız.

Bu fonksiyonu şu şekilde çağırırız.
```swift
travel {(place: String) -> String in
    return "\(place)'a gidiyorum"
}
```
Fakat Swift, bu closure'un parametresinin string olduğunu bildiği için şu şekilde yazabiliriz.
```swift
travel { place -> String in
    return "\(place)'a gidiyorum"
}
```

Ayrıca Swift, closure'un string'e dönmesi gerektiğini de biliyor. Yani;
```swift
travel {place in
    return "\(place)'a gidiyorum"
}
```
Yalnızca değer döndüren bir satır kodumuz olduğu için swift return anahtarını kaldırmamıza da izin verir.
```swift
travel { place in
    "\(place)'a gidiyorum"
}
```
Swift closure'u daha da kısaltmaya yarayan bir syntax'a sahiptir. Parametremizi kaldırıp Dolar işareti ve 0'dan başlayan bir sayı yazılarak tanımlanır.
```swift
travel {
    "\($0)'a gidiyorum"
}
```

## Advanced Closures

### 4. Closures with Multiple Parameters
Closure'lar birden çok parametre alabilirler. Demin tanımladığımız fonksiyon üzerinden deneyelim.
```swift
func travel (action: String, Int) -> String {
    print("Gitmeye hazırım.")
    let closureOrnek = action("İstanbul", 80)
    print("Ulaştım")
}
```
Yukarıdaki fonksiyonun closure'unu çağıralım.
```swift
travel {
    "\($1) km hızla \($0)'a gidiyorum."
}
```
Closuru'umuzu olabildiğince kısaltarak tanımladık. Gördüğünüz gibi 2 farklı parametre alıyor. İstanbul ve 80. Action'un içindeki ilk parametremiz olan string'i $0 olarak, ikinci parametremiz olan integer'ı $1 olarak çağırdık.
Kimi developerlar shorthand kullanmayı okunmayı zorlaştırdığı için kullanmıyor. Tercih size kalmış. Hangisi sizin için iyi yöntemse onu kullanabilirsiniz. Standart closure çağırma ise şöyle olacak.
```swift
travel {(place: String, hız: Int) -> String
    return "\(hız) km hızla \(place)'a gidiyorum.
}
```
### 5. Returning Closures from Functions
Bir fonksiyona closure iletebildiğiniz gibi, bir fonksiyondan dönen bir closure'u da alabilirsiniz. Biraz kafa karıştırıcı olabilir çünkü; iki kere "->" kullanılır. İlk ok fonksiyonun return değerini gösterir, İkinci ok ise closure'un return değerini gösterir. Örneğin;
```swift
func travel () -> (String) -> Void {
    return {
        print("\($0)'a gidiyorum.")
    }
}
```
Bu closure'u şu şekilde çağırırız;
```swift
let result = Travel()
result("İstanbul")
```

### 6. Capturing Values
Hadi bir travel fonksiyonu tanımlayalım. String parametresi alıp closure'a dönmeyen. 
```swift
func travel () -> (String) -> Void {
    return {
        print("\($0)'a gidiyorum.")
    }
}
```
Şimdi bu closure'u çağıralım. 
```swift
let result = travel()
    result("İstanbul")
```
Örneğin döndürülen closure'un kaç kere çağrıldığını bilmek isteyebiliriz.
```swift
func travel () -> (String) -> Void {
    let counter = 1
    return {
        print("\(counter). \($0)'a gidiyorum.")
        counter += 1
    }
}
```

Bu counter fonksiyon içinde tanımlanmış olsa da closure bunu çalıştırmaya devam edecektir. Çünkü closure'umuzu fonksiyon içinden yakalıyoruz.

```swift
result("İstanbul")
result("İstanbul")
result("İstanbul")
```
Her bir çıktımız için counter değeri ayrı tutulacaktır.