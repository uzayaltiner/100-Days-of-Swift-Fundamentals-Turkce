# Day 3
"Bilgisayarlar tanrılar gibidir: Çok fazla kuralları vardır ve acımaları yoktur." Joseph Campbell

### 1. Arithmetic Operators
Operatörler + ve - gibi matematiksel sembollerdir ve swiftte çok geniş bir kullanım alanı vardır.
```swift
let firstScore = 12
let secondScore = 4
``` 
Yukarıda tanımladığımız 2 tane sabitimiz olsun ve bular üzerinde çalışalım.

```swift
let toplam = firstScore + secondScore // 16
let fark = firstScore - secondScore // 8
let carpim = firstScore * secondScore // 48
let bolum = firstScore / secondScore // 3
```
Yukarıda gördüğünüz gibi 4 işlemi kolayca uygulayabildik. Bu kodların çıktısı açıklama satırındaki gibi olacaktır.

Swift bölmeden sonra kalanı hesaplayan bir operatöre sahiptir: %

Örneğin: 
```swift
let first = 13
let second = 4
```
Aşağıda gördüğünüz kodda kodun çıktısı 1 olacaktır. 13'ün 4'e bölümü 3, kalan 1'dir.
```swift
let kalan = first % second // 1
```

### 2. Operators Overloading
 Operators overloading aynı tipteki değerlerle toplama çıkarma gibi işlemler yapabilmemizi sağlar.Buna class ve structlar da dahildir. Örneğin:
 ```swift
 let sayı = 10
 let sayı2 = sayı + 5 // sonuc 15
 ```
 Bunu string yapıları için de kullanabiliriz. Örneğin;
 ```swift
 let name = "Uzay"
 let fullName = name + "Altıner" // Sonuc Uzay Altıner
 ```
 Hatta array gibi yapılar için bile kullanabiliriz. Örneğin;
 ```swift
 let firstTeam = ["Uzay", "Ali"]
 let secondTeam = ["Veli", "Mehmet"]

 let fullTeam = firstTeam + secondTeam 
 // Sonuc ["Uzay", "Ali", "Veli", "Mehmet"]
 ```
 Fakat unutmamalıyız ki Swift "Type-safe" bir dildir. Bu da farklı değer tipleriyle işlem yapamayacağımız anlamına gelmektedir. Örneğin aşağıdaki kullanım yanlıştır ve kodumuz hata verecektir.
 ```swift
 let name = "Uzay"
 let score = 80

 let scoreList = name + score
 ```
 ### 3. Compound Assignment Operators
 Swift bir değişkenin değerini değiştirmemize yarayan operatöre sahiptir. Bu bildiğimiz +, -, *, / fakat sonuna bir = atayarak işlemimizi değişkenimize atıyoruz. Örneğin;
 ```swift
 var sonuc = 95
 sonuc += 5
 // kodumuzun çıktısı 100 olacaktır.
 ```
 Bu operatörü string değerleri için de kullanabiliriz. Örneğin;
 ```swift
 var name = "Uzay"
 name += "Altıner"
 // kodumuzun çıktısı UzayAltıner olacaktır. String arasında boşluğu değişkenin içinde tanımlamalıyız. 
 var name = "Uzay " // gibi
 ```
 Fakat farklı değer tiplerini kullanamayız. Ayrıca bu operatörü kullanırken değerimizi "var" değişkeniyle tanımlamalıyız. Çünkü "let" sabiti değiştirilemez. 

 ### 4. Comparison Operators
 Swift karşılaştırma yapan birkaç operatöre sahiptir. Bu operatörler aşağı yukarı matematikteki gibi çalışır. Örneğin;
```swift
let a = 10
let b = 8
```
Yukarıdaki gibi iki adet sabitimiz olsun.

```swift
a == b // Eşitliği karşılaştırır.
a != b // eşitsizliği karşılaştırır.
```
Yukarıdaki iki karşılaştırmadan (boolean değeri olarak) ilkinde false, ikincisinde true çıktısını alacağız.

Bir değerin diğerinden küçük büyük ya da eşit olup olmadığını karşılaştıran 4 operatör daha vardır. Bunlar matematikteki gibi çalışır.
```swift
a <= b
a < b
a >= b
a > b
```
Bu operatörlerin hepsi string yapılarla da çalışır.

### 5. Conditions
Şimdi if koşulunu kurarken kullanabileceğimiz birçok operatör biliyoruz. If koşulu, koşulumuzu belirtikten sonra "{}" süslü parantez içerisine çalışacak komutu girerek oluşturulur. Else ile bu koşul dışı durumlarda çalışacak kod yazılır. If else ile farklı koşullar oluşturulur. Örneğin;
```swift
let firstCard = 11
let secondCard = 10

if firstCard + secondCard == 21 {
    print("Blackjack!")
} else if firstCard + secondCard == 2 {
    print("Ace")
} else {
    print(firstCard + secondCard)
}
```
### 6. Combining Conditions
Swift, birden çok koşulu birlikte kullanabildiğimiz 2 adet özel operatöre sahiptir. Bunlar ;

1. || "ya da" Operatörü

Ya da (or) operatörü 2 koşuldan birinin doğru olduğu koşulda çalışacaktır.

```swift
let age1 = 12
let age2 = 21

if age1 > 18 || age2 > 18 {
    print("Koşullardan biri doğru!")
}
```
2. && "ve" Operatörü

Ve (and) operatörü koşulların 2'sinin de doğru olduğu koşulda çalışacaktır. Örneğin;

```swift
let age1 = 20
let age2 = 19

if age1 > 18 && age2 > 18 {
    print("İki koşul da doğru.")
}
```
### 7. The Ternary Operator
Aynı anda üç değerle çalışır. İlk değerde belirtilen koşulu kontrol eder ve doğruysa ikinci, yanlışsa üçüncü değeri döndürür. Okuması zor bir operatördür. Bu yüzden nadiren kullanılır. Örneğin;
```swift
let firstCard = 11
let secondCard = 19

print(firstCard == secondCard ? "Kartlar aynı!" : "Kartlar farklı!")
```
Yukarıdaki kod aşağıdaki kodun aynısıdır.
```swift
if firstCard == secondCard {
    print("Kartlar aynı!")
} else {
    print("Kartlar farklı!")
}
```
### 8. Switch Statements
Birçok if ve if else koşulu kullanacağımız bir yapımız varsa switch ve case yapısını kullanmamız gerekir. Daha açık bir kullanımdır. Olabilecek bütün değerleri tanımlayarak kullanırız. Örneğin;
```swift
switch hava {
    case "yağmurlu":
        print("Şemsiye almayı unutma.")
    case "karlı":
        print("Kalın giyin.")
    case "güneşli":
        print("Güneş kremi sür.")
    default:
        print("İyi günler.")        
}
```
Yukarıda gördüğümüz örnekte hava durumlarına göre çıktılarımızı belirledik. Son satırdaki default komutunda ise sahip olmadığımız bir girdiye verilecek standart cevabı tanımladık. Default komutu kullanımı zorunludur.

Ayrıca kodunuzun bir sonraki case'e devam etmesini istiyorsanız "fallthrough" komutunu kullanın.
```swift
switch hava {
    case "yağmurlu":
        print("Şemsiye almayı unutma.")
    case "karlı":
        print("Kalın giyin.")
    case "güneşli":
        print("Güneş kremi sür.")
        fallthrough
    default:
        print("İyi günler.")        
}
```
bu switch koşulunda girdimiz güneşli olursa alacağımız çıktı;
```swift
Güneş kremini sür.
iyi günler.
```
olacaktır.

### 9. Range Operators
Swift bize aralık oluşturmak için iki çeşit imkanı sağlıyor. Bunlar;

1. ..<  Örneğin 1..<5 komutunun aralığı ; 1, 2, 3, 4 
2. ...  Örneğin 1...5 komutunun çıktısı ; 1, 2, 3, 4, 5

Aralıklar Switch yapıları için çok kullanışlıdır. Çünkü bunları her bir case için kullanabiliriz. Örneğin bir sınav notuna bağlı olarak farklı mesajlar yazdırabiliriz.

```swift
let not = 85
switch not {
    case 0..<50: 
        print("Başarısız!")
    case 50..<85: 
        print("Geçer")
    default:
        print("Tebrikler")     
}
```
Yukarıdaki kodun çıktısı Tebrikler olacaktır. 

Not: Tüm olası değerlerin kapsandığından emin olmak için default case olmalıdır. Case atanmamış bir değer girildiğinde default case'i dönecektir.