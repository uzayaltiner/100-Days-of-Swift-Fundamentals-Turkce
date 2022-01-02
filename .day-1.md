# Day1
"İlerlemenin sırrı, başlamaktan geçer" Mark Twain
### 1. Variables ve Constants
**Variables**
```swift
var ornek = ""
``` 
Üstteki kod bloğu şeklinde tanımlanır. Tanımlandıktan sonra değiştirilebilir. Örneğin;
```swift
var name = "Uzay"
name = "Ali"
```
**Constants**
```swift
let ornek = ""
```
Üstteki kod bloğu şeklinde tanımlanırlar. Sabittir. Bir kere değer atandıktan sonra değiştirilemez.
### 2. String, Integer, Double, Boolean yapıları
**String** 

 String yapısı yazı şeklinde tanımlanır.
 ```swift
 let name = "Uzay"
 ````
**Integer**

Integer yapısı tamsayı şeklinde tanımlanır. 
```swift
let age = 27
```
**Double**

Double yapısı kesirli sayılar şeklinde tanımlanır.
```swift
let height = 1.78
```
 Not: Bir integer ve double birbiriyle işlem göremez. İşlem yapabilmek için iki veri türünün de aynı olması gerekir.

```swift
var number1 = 1
var number2 = 1.0

var total = number1 + number2 
```

Sonucun 2 olmasını bekleriz fakat değişkenlerimizden biri integer diğeri ise double'dır. Bu sebeple bu işlem yapılmaz ve hata alırız.

**Boolean**
Boolean yapısı true false olarak tanımlanır.
```swift
var isWorking = true
````
### 3. Multi-line String
```swift
var name = """
        Uzay
        Altıner
        """
```
şeklinde tanımlanır. Bu kodun çıktısı da iki satır olarak döner. 

Fakat satır sonlarına (son satır hariç) eklenen  " \ " (backslash) değişkenimizi birkaç satırda tanımlayabilmemizi sağlar. Bu kullanımın çıktısı tek satır olarak döner.
```swift
var name = """
        Uzay \
        Altıner 
        """
```

Bu kodun çıktısı yine tek satır olacaktır.

### 4. String Interpolation
 Değişlen içine değişken tanımlamak olarak tanımlanabilir.
 ```swift
 var score = 85
 var str = "Sınav sonucunuz: \(score)"
 ```
 şeklinde kullanılır. Bu kodun çıktısı;
 ```
 Sınav sonucunuz: 85
 ```
 olacaktır.

 ### 5. Type Annotations
 Değişken tipini tanımlamak için kullanılır. 
 ```swift
 var name: String = "Uzay"
 var age: Int = 27
 var height: Double = 1.78
 var isWorking: Bool = true
 ```

 Tip tanımlarken değişken türünün ilk harfi büyük olmalı. 
 ```swift
 var isActive: bool = true
 ```
 Üstteki kullanım yanlıştır.

 Doğrusu;
 ```swift
 var isActive: Bool = true
 ```

 Ayrıca değişkene bir değer atamadan da tanımlama yapılabilir. Değişkenin türünü belirtip değeri sonra vermek istediğimiz durumlarda bu yöntemi kullanırız.

 ```swift
 var age: Int
 ```