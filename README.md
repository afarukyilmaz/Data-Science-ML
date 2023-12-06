# Data-Science-ML
** NLP -Sherlock **
Bu çalışmada gutenberg.com sitesinden aldığım sherlock kitabının NLP yöntemleri kullanarak analizi ve kümelemesini içeren bir çalışma yaptım.
Çalışmamda R programlama dili kullandım. Kullandığım kütüphaneler ise şu şekilde:

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/73d4d557-555b-4c53-baf7-ede5bec31422)

Dosyanın ilk 62 satırında ve son 371 satırında kitabın yazarı, katkı sağlayanlar vb. analiz çalışmasının kapsamına girmeyen kısımlar olduğunu gördüm. Önce bu kısımları çıkardım. Ardından metni okurken kullandığım "read_lines" fonksiyonu txt dosyasındaki her bir satırı ayrı birer eleman olarak okudu. Bu nedenle sherlock değeri 13088 elemanı olan bir large character olmuş oldu

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/b66d6e7d-82b1-4b72-a517-e77f48efa48e)

Sherlock değerini tek bir değer olacak şekilde atamak için paste() fonksiyonunu kullandım.

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/b1136aa4-f30f-49b9-996e-3ede03efc5df)

Bu kitap 12 bölümden oluşuyor. Bölümleri daha kolay ayırmak için txt dosyasının içerisinde her bölümden önce ">>" işareti kullandım.

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/ca7c1a21-b69d-41b4-ac20-74b509eea158)

Bu ifade daha sonrasında bölümleri ayırmada kolaylık sağlayacak. Aşağıdaki kodları çalıştırarak metnin 12 parçasını içeren12 elemanlı "A" large character değerini oluşturdum.

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/a15213bb-2f13-4477-97bc-39b3ee3d037f)

Ardından textmining kütüphanesi olan "tm" kütüphanesini kullanarak döküman vektörü ve corpus oluşturdum. 

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/d758cc80-c76d-4776-b1bd-781fbb5ece06)

Böylelikle istediğim değişkenleri oluşturmuş oldum. 

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/9b76f373-85fa-4046-8799-f7dc6d1a21f5)

Vcorpus aşağıdaki resimdeki bilgileri içeren ve textmining işlemlerinde kullanılan bir değişken türü. Bu çalışmada ihtiyaç duymadığım kısımlara girmedim. 

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/26e6b251-553b-4462-bfbd-2b5940807555)

Şimdi dokuman_derlem olarak isimlendirdiğim corpus tipli değişkeni temizleme adımına geçtim. 

Metindeki tüm harfleri küçük harf yaptım. Noktalama işaretleri ve rakamları da kaldırdım. Ayrıca çok sık tekrar eden kelimeleri de kaldırdım. Örneğin "the" kelimesi kaldırılmış oldu. Bu gibi "and", "a-an" gibi kelimelerin kaldırılmasını sağlamış oldum.

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/fd5546d8-a719-4bd4-a752-535a83a9ea87)

Ardından her bir kelimeyi köke indirgedim. Kelimelerin sonunda çoğul eki veya benzeri ekler olduğunda bu kelimeler R tarafından farklı olarak algılanıyor. Ancak aslında aynı kelime. Veya bir fiilin geçmiş zamanda sonuna "ed" eki gelmesi gibi. Tüm kelimeleri köke indirgersem bir kelimenin gerçekten kaç defa kullanılmış doluğunu daha sağlıklı bir şekilde öğrenebileceğimi düşündüm. Bu adımda "SnowballC" kütüphanesini kullandım. Bu kütüphane her ne kadar düşük bir başarıyla çalışsa da Türkçe dil desteği de olan bir kütüphane. Benim çalışmamdaki kitap ingilizce olduğu için daha düzgün çalışıyor. Silinen ekler yerine ise boşluk gelecek. Bu gereksiz boşlukları da silmek için aşağıdaki kodu yazdım. 

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/c75ab773-c93f-40d1-ba0c-125bb680b06e)

Sırada terim belge matrisi oluşturma adımı var. Bu adımda 12 adet metinde hangi kelimenin kaç defa geçtiği bilgisine ulaşacağım bir matris oluşturacağım. Bu matris sayesinde içerdikleri kelimeler bakımından metinlerin benzerliklerini inceleyebileceğim. Oluşturduğum matriste ulaşabileceğim attribute'ları inceledim. Bu matristen kaç adet eşsiz kelime olduğu bilgisine ulaştım. Toplamda 5784 adet kelime var. 12 adet de metin var (bu bilgiye zaten sahiptim). Metinlerin başlıklarını da yazdım. 

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/1f5c79cc-4704-4b96-a1ed-512f2878802a)

Arından toplamda en az 100 defa metinde geçmiş olan kelimeleri inceledim. 

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/7527241e-77e1-401e-9f92-6e4f2bceb97b)
![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/f9560763-d594-4bdb-89f1-475d954b02dd)

Bir de karakterleri inceledim. Bu kitpata "watson" ve "hudson" isimli karakterler hakkında kitabı okumadan da bilgi edinebilir miyim? Bu kelimelerde minimum %80 korelasyon içeren kelimelere bi bakalım. 

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/358c96b1-3032-4c82-a275-294ddc1c1556)![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/6df9d0e9-e3aa-4dd3-a2f7-124a29108269)

Sherlock'un sırdaşı ve güvendiği insan olan watson için çıkan sonuç hiç de şaşırtıcı değil. Bu kelimeler karakterler ile ilgili fikir verebilecek nitelikte. 

tdm isimli değişkeni incelediğimde ise içerisinde "Sparsity" (seyreklik) isimli bir değişken gördüm. Bu değişkenin değeri %75. 

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/101881cf-59b1-409e-8665-a543db69f18d)

Çok seyrek olan kelimeleri analizin dışında bırakmak için aşağıdaki fonksiyonu yazdım. sık geçen kelimeleri tdm_sik isimli değişkene kaydettim. Bu değişkeni incelediğimde ise sparsity değerinin %3'e düştüğünü gördüm. Kelime sayısı da 329'a düştü.

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/dc761539-1e72-4137-b8b5-c406ad937eb4)

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/696fe9cc-1263-4d5c-98ec-56bd321b62de)

Şimdi elde ettiğim seyrekliği azalttığım matristeki ilk 10 kelimenin ilk 5 metindeki geçme sıklığını gösteren bir matris oluşturayım. Bu matriste görülecek ki ilk baştaki matris gibi bir sürü 1 ve 0 yerine daha yüksek rakamlar var. Seyrek olan kelimelerden kurtulduğumu da bu şekilde görmüş oldum. 

![image](https://github.com/fisek48/Data-Science-ML/assets/114197020/ddc33302-fc75-480a-83a9-5eb9645f9d8f)























