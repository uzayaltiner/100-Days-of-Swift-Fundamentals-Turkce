# Day 2
### 1. Arrays
Diziler tek bir değer gibi depolanan değerler topluğudur. Ve köşeli parantez içine tanımlanır. "[ ]"
```swift
let FB = "Fenerbahçe"
let GS = "Galatasaray"
let BJK = "Beşiktaş"
let TS = "Trabzonspor"

let takımlar = [FB, GS, BJK, TS]
```
Burada 4 adet değişkenden oluşan takımlar arrayini görmekteyiz. Dizi elemanlarının konumları 0'dan başlayacak şekilde sıralanır.
Örneğin:

```swift
takımlar[0]
```
Yukarıda takımlar arrayinin 0. elemanı işaret edilmekte. Bu da arrayin ilk elemanı olan FB değişkenidir. Bu kodun çıktısı Fenerbahçe olacaktır.

Not: Eğer array'de olmayan bir elemanı çağırırsak hata alırız. Yukarıdaki örnekten yola çıkarsak;
```swift
takımlar[4]
``` 
kodu var olmayan bir elemanı işaret ettiği için hata verecek.

Ayrıca değişkenlerde olduğu gibi arraylerin türünü de belirleyebiliriz. Bunu yaparken değişken türünü köşeli parantez içine alacağız.
Örneğin;

```swift
let ornekArray: [Int] = [1, 3, 5, 7]
```

### 2. Sets
Setler tek bir değer gibi depolanan değerler topluluğudur. Arrayle çok benzer yapılar olmasına rağmen 2 büyük farklılık vardır.
1. Elemanlar herhangi bir sırada değil rastgele bir düzende depolanır.
```swift
let renkler = set(["kırmızı", "sarı", "yeşil"])
```
Bu kodun çıktısı her seferinde faklı bir sıralamada olacaktır.

2. Bütün elemanlar benzersiz olmalıdır. Aynı eleman yinelenemez.
```swift
let renkler = set(["kırmızı", "sarı", "kırmızı", "yeşil", "sarı"])
```
bu kodun çıktısında kırmızı, sarı ve yeşil olarak yine 3 eleman olacak. Hata almayacağız fakat tekrarlayan elemanları görmezden gelecek.

### 3. Tuples 
Tuples bir değişkenin içinde birden fazla değeri tutmaya yarar. Kulağa array gibi geliyor fakat farklı.

1. Tuple'a yeni bir eleman ekleyemeyiz.
2. Tuple elemanlarının değerleri değiştirilebilir fakat tipleri değiştirilemez.
```swift
var person = ("Ali", "Veli", 25)
    person = ("Murat", "Mehmet", 23)
  ```
  Örneğin yukarıdaki kodda değişkenimizin değerlerini değiştirdik. Fakat integer değerimizi farklı bir tip olan boolena çevirseydik hata alacaktık.

3. Tuple içindeki elemanlara sayısal konumlarıyla da isimleriyle de erişilebilir. Fakat tuple içinde olmayan elemana ulaşmaya çalışırsak hata verir.
```swift
var name = (first: "Uzay", last: "Altiner")
```
Alttaki kodun çıktısı iki koşulda da Uzay sonucunu verir.
```swift
name.0 
name.first
```
Fakat alttaki kod buloğunda hata alacağız.
```swift
name.3
name.age
```
 
### 4. Array vs Set vs Tuple

Üçünün de birbirine benzediği konusunda hemfikiriz. Fakat hepsinin belirgin farkları var.
1. Eğer değişkenimizin değerlerinin kesin bir konumu ya da sabit bir ilişkili değeri varsa Tuple kullanmalıyız. Örneğin;
```swift
var person = (first: "Uzay", last: "Altıner", age: 25)
```
2. Eğer değerler topluluğumuzun içindeki değerlerin tamamı benzersiz olması gerekiyorsa ve belirli bir öğenin orda olup olmadığını hızlıca kontrol etmemiz gerekiyorsa Set kullanmalıyız. Örneğin;
```swift
var name = set(["Paul Hudson", "Hackingwithswift", "100 day of Swift"])
``` 
3. Tekrarlanabilecek elemanlara ihtiyacımız varsa ya da elemanlarımızın sırası önemliyse Array kullanmalıyız.
```swift
var persons = ["Uzay", "Ali", "Veli", "Mehmet", "Ali"]
```
Bu üç seçenek arasından en çok kullanılan yöntem Array yöntemidir.

### 5. Dictionaries
 Arrayler gibi değerler topluluğudur. Bu değerlere istediğimiz anahtarlar atayarak değerlere ulaşmak için kullanırız. Örneğin;
 ```swift
 var notes = [
     "Uzay": 80,
     "Ali": 85,
     "Veli": 90
 ]
 ```
 Bu anahtar kelimeleri kullanarak istediğimiz değere kolayca ulaşabiliriz. Örneğin;
 ```swift
 notes["Uzay"]
 ```
 Yukarıdaki kod bize 80 değerini verecek. Bu yöntemde anahtar kelime olarak genellikle string değerler atanır.

 ### 6. Dictionaries Default Values
 Bir dictionary'nin içinde bulunmayan bir anahtar kelime ile arama yaptığımızda "nill" çıktısını alırız. Bu bir hata değildir. Fakat bunun önüne geçmek için içerisinde değer bulunmayan bir anahtar kelimeye default değer atayabiliriz. Örneğin;
 ```swift
 var ages = [
     "Uzay" = 27,
     "Ali" = 25,
     "Veli" = 30
 ]

 ages["Mehmet"]
 ```
 Yukarıdaki kodun çıktısı nill olacaktır. Fakat bunun yerine 
```swift
ages["Mehmet", default: "Bilinmiyor"]
```
şeklinde kullanırsak çıktımız "Bilinmiyor" olacaktır.

### 6. Creating Empty Collections
 Arrayler, Setler ve Dictionaryler koleksiyon olarak adlandırılır çünkü değerleri bir arada tutarlar. Boş koleksiyonlar oluşturmak için şu yolları kullanabiliriz.
 
 1. Boş bir dictionary oluşturmak için değişkenimizi şöyle tanımlarız:
 ```swift
 var notes = [String: Int]()
 ```
 Bu bize string anahtar kelimesiyle tanımlanacak ve değeri integer olacak bir eleman tanımlayacağımızı gösterir. Ve bu dictionarye elemanı şu şekilde ekleriz.
 ```swift
 var notes["Uzay"] = 80
 ```
 2. Boş bir array oluşturmak için değişkenimizi aşağıdaki gibi tanımlarız:
 ```swift
 var notes = [Int]()
 ```
 Bu bize notes arrayimizin elemanlarının integer olacağını göstermektedir.
 3. Set tanımlama yöntemi diğerlerinden biraz farklı. Örneğin;
 ```swift
 var words = set<String>()
 ```
 Fakat set tanımlamada kullandığımız yöntemle array ve dictionary tanımlamamız mümkün.
 ```swift
 var numbers = Array<Int>()
 var capitals = Dictionary<String, String>()
 ``` 
 
 ### 7. Enumerations
  Genellikle enum olarak kullanılırlar. Birbiriyle ilgili değer gruplarını kullanımını kolaylaştıracak şekilde gruplamaktır.
  Örneğin bir sonuç çıktısı için tanımladığımız değişkeni unutup farklı bir değişken tanımlayabiliriz.
  ```swift
  let sonuc = "Hata"
  let sonuc2 = "Fail" 
  let sonuc3 = "Failure"
  ``` 
  Yukarıda da göründüğü gibi sonuç sabiti için birden çok hata belirten konum tanımladık. Enum'u kullanarak bunu engelleyebiliriz. Örneğin;
  ```swift
  enum result {
      case success
      case failure
  }
```
```swift
let sonuc4 = result.success
let sonuc5 = result.failure
```

Bu her seferinde yanlışlıkla farklı string tanımlamamızı engeller.

### 8. Enum Associated Values
Enum kullanırken her bir case için yanında tutabileceği ek değerler verebiliriz. Örneğin;
```swift
enum notes = {
    case matematik(note: Int)
    case türkçe(note: Int)
    case tarih(note: Int)
}
```
Şimdi matematik caseimize notumuzu ekleyelim.

```swift
let matematik = notes.matematik(note: 80)
```

### 9. Enum Raw Values
Bazen enumların içindeki değerlerin bir anlam ifade etmesi için enumlara değer atamamız gerekir. Bunu örnek üstünden daha iyi anlayacağız.
```swift
enum gezegenler: Int{
    case merkür = 1
    case venüz
    case dünya
    case mars
}
```
Yukarıda integer ile ilişkilendirmiş bir enumumuz var. Merkür değerine 1 değerini tanımlarsak swift bizim için otomatik olarak diğer değerleri sıralayacaktır. 

Bir diğer örnekte ise string değeri atayalım.
```swift
enum yonler: String {
    case kuzey = "K"
    case guney = "G"
    case dogu = "D"
    case batı = "B"
}
```
burada ise;
```swift
yonler.kuzey.rawValue
```
bu kodun çıktısı "K" olacaktır.