# Day 3
"Bilgisayarlar tanrılar gibidir: Çok fazla kuralları vardır ve acımaları yoktur." Joseph Campbell

### 1. Arithmetic Operators
Operatörler + ve - gibi matematiksel sembollerdir ve swiftte çok geniş bir kullanım alanı vardır.
```swift
let firstScore = 12
let secondScore = 4
``` 
Yukarıda tanımladığımız 2 tane sabitimiz olsun ve bular üzerinden çalışalım.

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