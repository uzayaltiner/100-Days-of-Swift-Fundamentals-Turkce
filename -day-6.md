# Day 6
"Makineye birkaç kuruş koymazsan, büyük ikramiyeyi kazanmayı bekleyemezsin." Flip Wilson
### 1. Creating Basic Closures
Swift, diğer değerler gibi (string, integer...) fonksiyonları da değişkenlere ve sabitlere atayabilmemize izin verir. Bu sayede o değişkeni kullanarak bu fonksiyonu çağırabiliriz. Hatta başka bir fonksiyonda parametre olarak kullanabiliriz. Örneğin;
```swift
let welcome = {
    print("Uygulamama hoşgeldin.")
}
```
Yukarıdaki kod isimsiz bir fonksiyon oluşturur ve bu fonksiyonu sabitimizle çağırabiliriz. 
```swift
welcome()
```
### 2. Accepting Parameters in a Closures
Bir closure oluşturduğunuzda, bir parametre almak için bir boşluk ya da isimleri yoktur. Bu bunu yapamayacakları anlamına gelmez. Bir parametre tanımlamak için değişkeni tanımlarken süslü parantezi açtıktan hemen sonra parantez içine parametre tanımlayın ve parametreyi tanımladıktan sonra "in" ile bitirin.

```swift
let welcome = {(ame: String) in
    print("Hoşgeldin \(name)!")
}
```
Fonksiyonlar ve closureler arasındaki fark closureleri çalıştırırken parametre adını kullanmanıza gerek duymaz.
```swift
welcome("Uzay")
```
### 3. Returning values from a Closures
Closure değerler döndürebilir. Parametrelere benzer şekilde yazılırlar. "in" anahtar sözcüğünden hemen önce "->" ile yazılır. 

```swift
let welcome = {(name: String) -> String in
    return print("Uygulamama hoşgeldin \(name).")
}
```
Artık bu closure'u çalıştırıp return değerini yazdırabiliriz.
```swift
let message = welcome("Uzay")
print(message)
```
### 4. Closures as Parameters
Eğer bir closure'u fonksiyonun içinde kullanmak istersek, "() -> Void" parametresini kullanmamız gerekir. Örnek üstünden açıklarsak;

Önce closure'umuzu tanımlayalım.
```swift
let driving = {
    print("I'm driving")
}
```
Şimdi closure parametresi alacak bir fonksiyon tanımlayabiliriz.
```swift
func travel (action: () -> Void) {
    print("Getting ready to go")
    action()
    print("I'm arrived")
}
```
Şimdi driving closure'umuzu travel fonksiyonu içinde çağıralım.
```swift
travel(action: driving)
```
### 5. Trailing Closure Syntax
Bir fonksiyonun son parametresi bir closure ise, Swift; trailing closure syntax adı verilen bu sözdizimini kullanmanıza izin verir. 
```swift
func travel(action: () -> Void) {
    print("Gettting ready to go")
    ation()
    print("I'm Arrived")
}
```
Yukarıdaki fonksiyonda son parametremiz closure'dur. Bu sebeple bu syntaxı kullanabiliriz.
```swift
travel() {
    print("I'm driving")
}
```
Hatta başka bir parametre olmadığı için parantezleri de kaldırabiliriz.
```swift
travel {
    print("I'm driving")
}
```
Swift'te çokca kullanılan bir yöntemdir.
