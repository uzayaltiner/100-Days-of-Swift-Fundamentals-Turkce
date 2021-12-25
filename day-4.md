# Day 4
"Bir makineyi hızlı kılan donanım. Hızlı bir makineyi yavaşlatan yazılımdır." Craig Bruce

### 1. For Loops
Swiftte birkaç farklı loop yöntemi vardır. Looplar bir kodu çalıştırıp koşul false olana kadar devam ettirmeye yarar.

Swift'ye en çok kullanılan loop for loopudur. Arrayler ve aralıklarla çalışır. Örneğin;
```swift
let count = 1...10

for number in count {
    print("Number is \(number)")
}
```
Bu for döngüsünde 1 ile 10 arasındaki her sayı için döngümüz çalışacak ve 10 adet çıktı alacağız.

Aynı işlemi arrayle gerçekleştirelim.
```swift
let people = ["Uzay", "Ali", "Veli", "Mehmet"]

for person in peope {
    print("\(person) is here.")
}
```
Eğer döngümüzü bir sabitle tanımlamayacaksak Swift'in gereksiz değerler yaratmaması için "_" kullanmalıyız.

```swift
for _ in 1...5 {
    print("Hi")
}
```
Yukarıdaki kodda 5 kere Hi çıktısı alacağız.

### 2. While Loops
İkinci döngümüz while döngüsü. Bu döngüde while ile birlikte bir koşul tanımlıyoruz ve bu koşul doğru olduğu sürece kodumuz çalışıyor. Örneğin;
```swift
var number = 1

while number <= 10 {
    print(number)
    number += 1
    }
```
Bu döngüde number değerimiz 1 den başlıyor ve 10 a kadar 1'er 1'er artarak her sayıyı çıktı olarak veriyor. Ve değişkenimiz 10 değerine ulaştığında döngümüz tamamlanıyor.

### 3. Repeat Loops
Pek fazla kullanılmaz. While dögüsüyle tek farkı koşulun sonda olmasıdır.

```swift
var number = 1

repeat {
    print(number)
    number += 1
} while number <= 20
```

Koşul repeat döngüsünün sonunda geldiğinden, göngü içindeki kod her zaman en az bir kere çalıştırılır. While döngüsünde böyle değildir. Koşul sağlanmıyorsa kod çalışmaz. Örneğin;

```swift
var nuber = 1

while number < 1 {
    print(number)
    number += 1
}
```
Yukarıdaki while döngüsünün çalışmayacağını biliyoruz. Hadi bu döngüyü repeat döngüsüne çevirelim.
```swift
var number = 1
repeat {
    print(number)
    number += 1
} while number < 1
```
Yukarıdaki 2 kod aynı olmasına rağmen while döngüsü çalışmazken repeat döngüsü çalışır. Bunun sebebi repeat döngüsünde önce kod okunup sonra koşula bakılır. Koşul hiç sağlanmasa bile kodumuz 1 kere çalışmış olur.

### 4. Exiting Loops
 Break operatörü ile bir döngüyü bitirmemiz mümkün. Bunu bir örnek üstünden deneyelim.
 ```swift
 var countDown = 10

 while countDown >= 0 {
     print(countDown)
     if countDown == 4 {
         print("Done!")
         break
     }
     countDown += 1
 }
 ```
 Standart bir while döngüsünde 10 dan geriye doğru saydığımızı varsayalım. 4 sayısına kadar geri sayıp yapılıp 4 de döngümüz yarıda kesilecek.

 ### 5. Exiting Multiple Loops
 Loop içine loop koyarsak buna nested loop denir ve iki loopu birden sonlandırmak isteyebiliriz. Örneğin;
 ```swift
 for i in 1...10 {
     for j in 1...10 {
         var sonuc = i * j
         print ("\(i) * \(j) = \(sonuc)")
     }
 }
 ```
 Yukarıda iç içe bir döngü görüyorsunuz. Bu döngüde 50 sonucuna ulaşınca 2 loopu da durdukmak istiyorsak breakin standart kullanımı çalışmayacaktır. İçerdeki döngüyü break operatörü ile sonlandırsak bile dışardaki döngü çalışmaya devam edecektir. İki dönğüyü de sonlandırmak için uygulamamız gereken 2 şey vardır. Bunlar;

 1. Dışarıdaki döngüye "outerLoop:" tagi atamak.
 2. İçerideki döngüye "break outerLoop" komutunu yazmak.

 ```swift
outerloop: for i in 1...10 {
    for j in 1...10 {
        var sonuc = i * j
        print("\(i) * \(j) = \(sonuc)")

        if sonuc == 50 {
            print("50'ye ulaştık.")
            break outerLoop
    }
}
}
```

### 6. Skipping Items
Gördüğünüz gibi break komutu loop'u sonlandırıyor. Fakat loopu bitirmeyip sadece mevcut sonucu atlamak istersek continue operatörünü kullanabiliriz. Örneğin;

```swift
for i in 1...10 {
    if i % 2 == 1 {
        continue
    }
    print(i)
}
```
Yukarıdaki kodun çıktısı "2 4 6 8 10" olacaktır. Continue operatörüyle 2 ye bölümünden kalan 1 olan değerler atlanacaktır.

### 7. Infinite Loops
Sonsuz döngüler oluşturmak için genellikle while döngüleri kullanılır. Sonsuz bir döngü oluşturmak için koşul olarak true koşulu kullanılır. Bu sayede döngümüz her zaman çalışacaktır. Fakat döngüden çıkacak bir breakimiz olması lazım yoksa döngüden asla çıkamayız. Örneğin;

```swift
var counter = 0

while true {
    print(" ")
    counter += 1

    if counter == 273 {
        break
    }
}