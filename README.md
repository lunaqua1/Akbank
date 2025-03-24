# Metro Ağı Simülasyonu
Bu proje, kullanıcıların bir metro ağındaki iki istasyon arasındaki en hızlı ve en az aktarmalı rotayı bulmalarını sağlamak amacıyla hazırlanmıştır.
Simülasyon Python yazılım diliyle hazırlanmış, Bread-First Search ve A* algoritmaları kullanılmıştır.

# Kullanılan Teknolojiler ve Kütüphaneler
Bu projede aşağıdaki kütüphaneler kullanılmıştır:

collections: BFS algoritmasını uygulamak için deque yapısını içerir.
heapq: A* algoritması için öncelikli kuyruk oluşturmak amacıyla kullanılır.
typing: Python'un tür ipuçlarını sağlamak için Dict, List, Set, Tuple, Optional gibi veri türleri kullanılmıştır.

# BFS Algoritmasının Çalışma Mantığı

BFS algoritmasnın temel amacı iki hedef arasındaki en kısa mesafeyi bulmaktır. BFS kullanılırken queue yani kuyruk veri yapısı kullanılır. Bu veri yapısı Fİrst-In-Fİrst-Out çalışma prensibiyle işler. İlk olarak bir başlangıç node'u yani düğümü seçilir. Bu düğüm daha sonra tekrar kontrol etmemek için ziyaret edilennler listesine eklenir. Ardından bu düğümün komşuları da kuyruğa eklenir ve ilk başta ziyaret ettiğimiz düğüm kuyruktan çıkarılır. Bu da FIFO çalışma prensibinden kaynaklanır. Bu işlem aynı şekilde tüm düğümler üzerinde devam eder.  Bu projede bu algoritmanın çalışma mantığı şu şekildedir:

Metronun başlangıç istasyonu queue içine eklenir ve ziyaret edilen istasyon listesine eklenir. Bu istasyon kuyruktan çıkarılır ve istasyonun komşuları kontrol edilir. Eğer varılmak istenile istasyon komşu değerlerinden biriyse en kısa aktarma tespit edilmiş olur. Eğer hedef istasyon değilse tüm komşular sırayla kuyruğa eklenir ve bulunana kadar devam eder.


# A* Algoritmasının Çalışma Mantığı
A* algoritması, en hızlı rotayı bulmak için öncelikli kuyruk (priority queue) kullanır.En düşük f(n) değerine sahip olan düğüm her zaman kuyruğun önüne gelir. En düşük değeri olan düğümü alır ve bu düğümü kuyruktan çıkarır. Bu düğüme göre komşu düğümlerin de değeri güncellenir. Hedefe varılana kadar yani kuyrukta düğüm kalmayana kkdar bu adımlar tekrar edilir.
f(n) = g(n) + h(n)
f(n) = hesaplama yapan sezgisel (heuristic) fonksiyon.
g(n) = Başlangıç düğümünden mevcut düğüme kadar gelmenin maliyeti
h(n) = Mevcut düğümden hedef düğüme varmak için tahmin edilen mesafe.

Başlangıç istasyonu öncelik kuyruğuna eklenir. İstasyonları ziyaret ederek, en düşük maliyetli (toplam süre açısından) komşuya öncelik verir. Her iterasyonda, toplam süre hesaplanır ve en kısa sürede ulaşılabilecek rota takip edilir. Hedef istasyona ulaşıldığında, istasyon listesi ve toplam süre kullanıcıya döndürülür.


# Neden Bu Algoritmaları Kullandık?

BFS: En az aktarmalı rotayı bulmak için idealdir, çünkü her seviyedeki düğümleri aynı anda genişletir ve ilk bulunan hedef en kısa yoldur.

A*: A* algoritması, tahmini mesafeyi (h(n)) ve şu ana kadarki maliyeti (g(n)) hesaplayarak en kısa sürede hedefe ulaşan yolu seçer.

# Örnek Kullanım ve Test Sonuçları
M1 -> K4:
En az aktarmalı rota: AŞTİ -> Kızılay -> Kızılay -> Ulus -> Demetevler -> OSB
En hızlı rota (25 dakika): AŞTİ -> Kızılay -> Kızılay -> Ulus -> Demetevler -> OSB

T1 -> T4:
En az aktarmalı rota: Batıkent -> Demetevler -> Gar -> Keçiören
En hızlı rota (21 dakika): Batıkent -> Demetevler -> Gar -> Keçiören

T4 -> M1:
En az aktarmalı rota: Keçiören -> Gar -> Gar -> Sıhhiye -> Kızılay -> AŞTİ
En hızlı rota (19 dakika): Keçiören -> Gar -> Gar -> Sıhhiye -> Kızılay -> AŞTİ

M2 -> K1:
En az aktarmalı rota: Kızılay -> Kızılay
En hızlı rota (2 dakika): Kızılay -> Kızılay

T3 -> T2:
En az aktarmalı rota: Gar -> Demetevler
En hızlı rota (9 dakika): Gar -> Demetevler

M4 -> T1:
En az aktarmalı rota: Gar -> Gar -> Demetevler -> Batıkent
En hızlı rota (18 dakika): Gar -> Gar -> Demetevler -> Batıkent










