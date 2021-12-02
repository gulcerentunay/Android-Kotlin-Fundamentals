# Kullanıcı Etkileşimi Ekleyin

- [ColorMyView Projesini Oluşturun](#1)
- [ConstraintLayout Oluşturmak İçin Layout Editor Kullanın](#2)
- [TextView'e Stil Verin](#3)
- [İkinci bir TextView Ekleyin ve Constrait Ekleyin (kısıtlamalar)](#4)
- [TextView Görünümleri Zinciri Oluşturun](#5)
- [Text görünümerine ClickHandler Ekleyin](#6)
- [Temel Constrait Ekleyin](#7)
- [Buton Zinciri Ekleyin](#8)
- [Butonlara ClickHandlers Ekleyin](#9)


ColorMyViews uygulaması, Hollandalı sanatçı Piet Mondrian'dan esinlenmiştir. Siyah, beyaz, gri ve ana renklerde yalnızca dikey ve yatay çizgiler ve dikdörtgen şekiller kullanan neoplastikizm adlı bir resim stili icat etti.

<img width="800" alt="Screen Shot 2021-11-26 at 23 31 16" src="https://user-images.githubusercontent.com/80598532/143627483-057419cd-37b9-4a7b-b248-e8c644c7f4d4.png">


Resimler statik olsa da uygulamanız interaktif (etkileşimli) olacak! Uygulama, dokunulduğunda rengi değişen tıklanabilir metin görünümlerinden ve bir constraintLayout'taki buton görünümlerinden oluşur.

<img width="802" alt="Screen Shot 2021-11-26 at 23 45 14" src="https://user-images.githubusercontent.com/80598532/143633610-93832f9c-1d23-4b53-bc3b-af0df067432c.png">


### ConstraintLayout
  ConstraintLayout, alt görünümleri esnek bir şekilde konumlandırmanıza ve boyutlandırmanıza izin veren bir ViewGroup'tur. Bir ConstraintLayout, düz görünüm hiyerarşileriyle (iç içe görünüm grupları olmadan) büyük, karmaşık düzenler oluşturmanıza olanak tanır. Bir ConstraintLayout oluşturmak için, kısıtlamalar eklemek ve görünümleri sürükleyip bırakmak için Layout Editor'ü kullanabilirsiniz. XML'i düzenlemeniz gerekmez.
  
  Not:ConstraintLayout, API düzeyi 9 ve üzeri sürümlerde bulunan bir destek kitaplığı olarak mevcuttur.
  
  ### Constraints
   Constraint, iki UI öğesi arasındaki bağlantı veya hizalamadır. Her Constraint, bir görünümü başka bir görünüme, üst düzene veya görünmez bir kılavuza bağlar veya hizalar. Bir ConstraintLayout'ta, en az bir yatay ve bir dikey kısıtlama tanımlayarak bir görünümü konumlandırırsınız.
  
  ![image](https://user-images.githubusercontent.com/80598532/143634494-6f0e93b4-eaf0-48ce-98b8-0fb8a8a10dd9.png)

  ![image](https://user-images.githubusercontent.com/80598532/143634735-dd283226-c8f0-4ec1-995b-9f2bdd1ade4a.png)
 Horizontal constraint: B, A'nın sağında kalacak şekilde sınırlandırılmıştır. (Bitmiş bir uygulamada, B'nin bu yatay kısıtlamaya ek olarak en az bir dikey kısıtlamaya ihtiyacı olacaktır.)
 
  ![image](https://user-images.githubusercontent.com/80598532/143634927-3b987382-445e-4b66-8ddb-735fe7ff64c5.png) Vertical constraint: C, A'nın altında kalacak şekilde sınırlandırılmıştır. (Bitmiş bir uygulamada, C'nin bu dikey kısıtlamaya ek olarak en az bir yatay kısıtlamaya ihtiyacı olacaktır.)
    

## <a name="1"></a>ColorMyView Projesini Oluşturun
    
    1. Henüz açık değilse Android Studio'yu açın ve aşağıdaki parametrelerle yeni bir proje oluşturun:
    
| Attribute | Value |
|---|---|
| Template | Telefon ve Tablet sekmesindeki Empty Activity |
| Application Name | ColorMyViews |
| Company Name android | com.android.example.colormyviews (veya kendi domain'iniz) |
| Language | Kotlin |
| Minimum API level | API 19: Android 4.4 (KitKat) |
| This project will support instant apps | (Bu kutuyu boş bırakın) |
| Use AndroidX artifacts | Bu kutuyu seçin. |

Empty Activity template'i, Mainactivity.kt dosyasında tek bir boş etkinlik oluşturur. Şablon ayrıca aktivite_main.xml adlı bir Layouts dosyası oluşturur. Layout, içerik olarak tek bir TextView ile kök görünüm grubu olarak ConstraintLayout'u kullanır.

2.Android Studio'nun Gradle derlemesini bitirmesini bekleyin. Herhangi bir hata görürseniz, Build > Rebuild Project.

3.Uygulamayı çalıştırın ve derlemenin tamamlanması için birkaç saniye bekleyin. "Hello World!" yazan bir ekran görmelisiniz. ortasında.

![image](https://user-images.githubusercontent.com/80598532/143635928-ea0cff87-7e74-44a9-afa3-25109a0c8d99.png)

## <a name="2"></a>ConstraintLayout Oluşturmak İçin Layout Editor Kullanın
Bu görevde, uygulamanız için bir ConstraintLayout oluşturmak için Android Studio LAyout Editor'ünü kullanın.

### 1. Adım: Android Studio çalışma alanınızı kurun.

1. Activity_main.xml dosyasını açın ve Design sekmesine tıklayın.
2. Constraint'leri manuel olarak ekleyeceksiniz, bu yüzden otomatik bağlantının kapalı olmasını istiyorsunuz. Toolbar'da, aşağıda gösterilen Otomatik Bağlantıyı Aç/Kapat geçiş butonunu bulun. (Toolbar'ı göremiyorsanız, Layout Editor'ün Design Editor alanına tıklayın.) Otomatik bağlantının kapalı olduğundan emin olun.

![image](https://user-images.githubusercontent.com/80598532/143638469-fecdb907-caa4-4010-87d0-5bf088efd522.png) : Otomatik bağlantı açık.

![image](https://user-images.githubusercontent.com/80598532/143638845-79756e6b-086e-4951-b888-8a943960345d.png) : Otomatik bağlantı kapalı; bu codelab için istediğiniz şey budur.

3.Varsayılan kenar boşluklarını 16dp'ye ayarlamak için toolbar'ı kullanın. (Varsayılan 8dp'dir.)

![image](https://user-images.githubusercontent.com/80598532/143639861-2bcbf788-9b57-4f10-ad9e-72b53a9651da.png)

Varsayılan marjı 16dp'ye ayarladığınızda, bu marjla yeni constraint'ler oluşturulur, böylece her constraint eklediğinizde marjı eklemeniz gerekmez.

4.Hello World metni texy view görünümünde görünene kadar araç çubuğunun sağ tarafındaki + simgesini ![image](https://user-images.githubusercontent.com/80598532/143642614-dabfb624-d028-475f-bb87-67f3ad36257c.png)
 kullanarak yakınlaştırın.
 5.Attributes bölmesini açmak için Hello World metin görünümüne çift tıklayın.
![image](https://user-images.githubusercontent.com/80598532/143647123-5f64dd28-c955-44c3-aa62-636dc82b2523.png)

### Görünüm denetçisi
Aşağıdaki ekran görüntüsünde gösterilen görünüm denetçisi, Attributes bölmesinin bir parçasıdır. Görünüm denetçisi, constraintler, constraint türleri, constraint sapması ve marjinler gibi layout attributeleri için kontroller içerir.

![image](https://user-images.githubusercontent.com/80598532/143650016-634084dd-0e35-4f73-98f9-bb5cd5c8fb2b.png)

İpucu: Görünüm denetçisi yalnızca ConstraintLayout içindeki görünümler için kullanılabilir.

### Constraint Sapmaları
Constraint sapmaları, view'ı yatay ve dikey eksenler boyunca konumlandırır. Varsayılan olarak, görünüm %50 sapma ile iki kısıtlama arasında ortalanır.

Sapmayı ayarlamak için, görünüm denetçisinde sapma kaydırıcılarını (![image](https://user-images.githubusercontent.com/80598532/143656604-ec332a69-d2f2-4d77-984e-e909db85a124.png)
) sürükleyebilirsiniz. Bir sapma kaydırıcısını sürüklemek, görünümün eksen boyunca konumunu değiştirir.
Sapmayı ayarlamak için, görünüm denetçisinde sapma kaydırıcılarını ( sürükleyebilirsiniz. Bir sapma kaydırıcısını sürüklemek, görünümün eksen boyunca konumunu değiştirir.

### 2. Adım Hello World text view'ına marjin ekleyin
1.Görünüm denetçisinde, text görünümü için sol, sağ, üst ve alt kenar boşluklarının (marjinlerin) 0 olduğuna dikkat edin. Bu görünüm, siz default (varsayılan) kenar boşluğunu değiştirmeden önce oluşturulduğundan, varsayılan kenar boşluğu otomatik olarak eklenmedi.

2.Sol, sağ ve üst marjinler için görünüm denetçisindeki açılır menüden 16dp'yi seçin. Örneğin, aşağıdaki ekran görüntüsünde layout_marginEnd (layout_marginRight) ekliyorsunuz.

![image](https://user-images.githubusercontent.com/80598532/143656723-8806340f-3a9e-4015-ac2f-f904abf430dc.png)

### 3. Adım Text görünümü için marjin ce constraintleri ayarlayın
Görünüm denetçisinde, karenin içindeki oklar constraintlerin türünü temsil eder:

- ![image](https://user-images.githubusercontent.com/80598532/143658545-be884b86-c47d-44a5-995d-ec80866c70ac.png)
 Wrap Content : View, yalnızca içeriğini içermesi gerektiği kadar genişler.
 
- ![image](https://user-images.githubusercontent.com/80598532/143658561-f27b5ba0-4f09-476a-9a0c-d1136279eeff.png) Fixed : Sabit kısıtlamalı okların yanındaki metin kutusunda görünüm marjı olarak bir boyut belirtebilirsiniz.
- ![image](https://user-images.githubusercontent.com/80598532/143658567-641cd082-0603-48f0-9524-af78450751f8.png)  Constraints : GView, kendi marjlarını hesaba kattıktan sonra, her iki taraftaki constraintlerini karşılamak için mümkün olduğunca genişler. Bu kconstraint, yerleşimin farklı ekran boyutlarına ve yönelimlerine uyum sağlamasına izin verdiği için çok esnektir. Görünümün constraintlerle eşleşmesine izin vererek, oluşturduğunuz uygulama için daha az layout'a ihtiyacınız olur.

1.Görünüm denetçisinde, sol ve sağ constraintleri Match Constraints ![image](https://user-images.githubusercontent.com/80598532/143658678-920ddf01-8635-4ee4-903d-a566a31b6cf5.png)
 olarak değiştirin (Constraints türleri arasında geçiş yapmak için ok simgesini tıklayın.)

![image](https://user-images.githubusercontent.com/80598532/143658685-bbafde73-2f34-40ee-aedf-26c246616f1f.png)

2.Görünüm denetçisinde, alt constraint'i silmek için karenin üzerindeki Delete Bottom Constraint'e tıklayın.

3.Text sekmesine geçin. layout_marginStart için boyut kaynağını açın ve Resource name'i margin_wide olarak ayarlayın.

![image](https://user-images.githubusercontent.com/80598532/143658842-577551c4-3b51-45f4-a8f3-143e94ad6459.png)


4.Üst ve uç marjinler için aynı boyut kaynağını @dimen/margin_wide olarak ayarlayın.

```

android:layout_marginStart="@dimen/margin_wide"
android:layout_marginTop="@dimen/margin_wide"
android:layout_marginEnd="@dimen/margin_wide"

```
## <a name="3"></a>TextView'e Stil Verin

### 1. Adım: Font Ekleyin
1.Attributes bölmesinde, fontFamily'yi arayın ve yanındaki açılır oku seçin.  More Font'u seçin. Resources açılır.
![image](https://user-images.githubusercontent.com/80598532/143660632-6f56b016-0b45-47db-a8ea-6bc8f10f28d3.png)

2.Resouces'da Roboto'yu arayın
3.Roboto'ya tıklayın ve Preview listesinde Normal'i seçin.
4.Projeye yazı tipi ekle butonunu seçin.
5.Tamamı tıklayın.

![image](https://user-images.githubusercontent.com/80598532/144382107-91a6df02-7b15-4f79-8191-107956a407cf.png)

Bu, roboto.ttf yazı tipi dosyasını içeren bir res/font klasörü ekler.Ayrıca, text görünümünüz için @font/Roboto attribute'u ayarlanır.


### 2.Adım: Stil ekleyin

1.res/values/dimens.xml dosyasını açın ve yazı tipi boyutu için aşağıdaki boyut kaynağını ekleyin.

```

<dimen name="box_text_size">24sp</dimen>

```

2.res/values/styles.xml dosyasını açın ve text görünümü için kullanacağınız aşağıdaki stili ekleyin.

```
<style name="whiteBox">
   <item name="android:background">@android:color/holo_green_light</item>
   <item name="android:textAlignment">center</item>
   <item name="android:textSize">@dimen/box_text_size</item>
   <item name="android:textStyle">bold</item>
   <item name="android:textColor">@android:color/white</item>
   <item name="android:fontFamily">@font/roboto</item>
</style>
```
Bu stilde, arka plan rengi ve metin rengi varsayılan Android renk kaynaklarına ayarlanmıştır. Yazı tipi Roboto olarak ayarlanmıştır. Metin ortaya hizalanmış ve kalın yazılmıştır ve metin boyutu box_text_size olarak ayarlanmıştır.

### 3.Adım: Text view için String kaynağı ekleyin.
1. Attributes bölmesinde text attribute'ü bulun. (Anahtar simgesi olmayanı istiyorsunuz.)
2. Resources iletişim kutusunu açmak için text attribute'ün yanındaki ... (üç nokta) öğesini tıklayın.
3. Resources iletişim kutusunda  Add new resource > New string Value seçin. Kaynak adını box_one ve değeri Box One olarak ayarlayın.
4. Tamam'ı tıklayın.

![image](https://user-images.githubusercontent.com/80598532/144399405-969ba2c2-7ca7-4226-9c9d-6be4541b1834.png)

### 4.Adım: Text View için Attributes ayarlarını tamamlayın.
1. Attributes bölmesinde text view ID'yi box_one_text olarak ayarlayın
2. Stili @style/whiteBox olarak ayarlayın.
3. Kodu temizlemek için Text sekmesine geçin ve android:fontFamily="@font/roboto" attribute'unu kaldırın, çünkü bu yazı tipi whiteBox stilinde mevcuttur.
4. Design sekmesine geri dönün. Design editor'ün üst kısmında, Device for preview (D) butonuna tıklayın. Farklı ekran konfigürasyonlarına sahip cihaz türlerinin bir listesi görüntülenir. Varsayılan cihaz Pixel'dir.
![image](https://user-images.githubusercontent.com/80598532/144399564-0ec8598c-61ce-42cf-8f47-fa774a253d6f.png)

5.Listeden farklı cihazlar seçin ve TextView'in farklı ekran konfigürasyonlarına nasıl uyum sağladığını görün.
6.Uygulamanızı çalıştırın. "Box One" metniyle birlikte stil sahibi bir yeşil metin görünümü görürsünüz.
![image](https://user-images.githubusercontent.com/80598532/144400237-3d32edaf-2783-4653-9deb-a0a0a7837592.png)


## <a name="4"></a>İkinci bir TextView Ekleyin ve Constrait Ekleyin (kısıtlamalar)
Bu görevde, box_one_text'in altına başka bir text view eklersiniz. Yeni text view'i box_one_text ve layoutsun üst öğesiyle sınırlandırırsınız.

### 1.Adım: Yeni bir Text View Ekleyin.
1.Activity_main.xml dosyasını açın ve Layouts sekmesine geçin.

2.Palet bölmesinden bir TextView'i aşağıda gösterildiği gibi doğrudan design editor önizlemesine sürükleyin. Text view'u sol kenar boşluğuyla hizalı olarak box_one_text'in altına yerleştirin.

![image](https://user-images.githubusercontent.com/80598532/144400524-2e39d353-ea68-4acf-802a-fddb0725627c.png)

3.Design editor'de, yeni text view'e tıklayın, ardından işaretçiyi text view'un üst tarafındaki noktanın üzerinde tutun. Aşağıda gösterilen bu noktaya kısıtlama tutamacı(constraint handle) denir.

![image](https://user-images.githubusercontent.com/80598532/144401219-9ef641cb-9576-468f-9597-a35835b7c60e.png)

İşaretçiyi kısıtlama tutamacı üzerinde tuttuğunuzda tutamaç yeşile döner ve yanıp söner.

### 2.Adım: Yeni text view'a kısıtlamalar(constraints) ekleyin.
Yeni text view'un üst kısmını Box One metin görünümününtext view'unun altına bağlayan bir kısıtlama oluşturun:

1.Yeni text view'de işaretçiyi üst kısıtlama tutamacı üzerinde tutun.

2.View'un üst kısıtlama tutamacına tıklayın ve yukarı sürükleyin. Bir kısıtlama çizgisi belirir. Kısıtlama çizgisini aşağıda gösterildiği gibi Box One text view'unun altına bağlayın.

![image](https://user-images.githubusercontent.com/80598532/144402374-e675e86a-a60d-4434-9611-8662d5b9bb41.png)

Tıklamayı bıraktığınızda, kısıtlama oluşturulur ve yeni text view Box One'ın altındaki 16 dp'lik mesafeye atlar. (Yeni text view'un üst kenar boşluğu 16 dp'dir çünkü bu, daha önce belirlediğiniz varsayılan değerdir.)

Şimdi bir sol kısıtlama oluşturun:

1.Yeni görünümün sol tarafındaki kısıtlama tutamacına tıklayın.

2.Kısıtlama çizgisini layout'un sol kenarına sürükleyin.

![image](https://user-images.githubusercontent.com/80598532/144404550-98392be7-cc5d-48e3-ab0e-073234f90fd8.png)


İpucu: Görünüm denetçisini kullanarak da kısıtlamalar oluşturabilirsiniz. Örneğin, yeni metin kutusunda bir sol kısıtlama oluşturmak için:
1.Önizlemede, seçmek için yeni metin kutusunu tıklayın.
2.Görünüm denetçisinde, aşağıda gösterildiği gibi kutunun sol tarafındaki + simgesine ![image](https://user-images.githubusercontent.com/80598532/144404585-96609f92-47dd-48ee-9a75-7c4b37b08eff.png)
 tıklayın.
 
 
 ![image](https://user-images.githubusercontent.com/80598532/144404615-0bf437c9-71bd-473c-bc14-aef6a803f6f8.png)


Bu şekilde bir kısıtlama oluşturduğunuzda, kısıtlama üst öğeye veya ona daha yakın bir görünüme eklenir.

### 3.Adım: Yeni text view için attribute'leri ayarlayın.

1.res/values/strings.xml dosyasını açın. Aşağıdaki kodla yeni bir dize kaynağı ekleyin:


```
<string name="box_two">Box Two</string>

```

2.Activity_main.xml dosyasını açın ve Design sekmesine tıklayın. Yeni text view'da aşağıdaki nitelikleri ayarlamak için Attributes bölmesini kullanın:


| Attribute | Value |
|---|---|
| id | box_two_text |
| layout_height | 130dp |
| layout_width | 130dp |
| style | @style/whiteBox |
| stext | @string/box_two |

Bu durumda, text view'un yüksekliği ve genişliği için sabit boyutlar atarsınız. Yalnızca görünümünüzün tüm cihazlarda ve düzenlerde her zaman sabit bir boyutu olması gerekiyorsa, yükseklik ve genişlik için sabit boyutlar atayın.


*Önemli: Gerçek dünya uygulamaları geliştirirken, mümkün olduğunda UI öğelerinizin yüksekliği ve genişliği için esnek kısıtlamalar kullanın. Örneğin, match_constraint veya wrap_content kullanın. Uygulamanızda ne kadar sabit boyutlu UI öğeleri varsa, layoutunuz farklı ekran yapılandırmaları için o kadar az uyarlanabilir.*

3.Uygulamanızı çalıştırın. Aşağıdaki ekran görüntüsüne benzer şekilde, biri diğerinin üzerinde iki yeşil TextView görünümü görmelisiniz:

![image](https://user-images.githubusercontent.com/80598532/144404692-45fcdc48-48b2-4340-9790-edef7b7ceb60.png)



## <a name="5"></a>TextView Görünümleri Zinciri Oluşturun
## <a name="6"></a>Text görünümerine ClickHandler Ekleyin
## <a name="7"></a>Temel Constrait Ekleyin
## <a name="8"></a>Buton Zinciri Ekleyin
## <a name="9"></a>Butonlara ClickHandlers Ekleyin
