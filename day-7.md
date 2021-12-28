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

