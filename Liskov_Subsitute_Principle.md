# NE
Kod kullanılabilirliğini, bakımını artıran, sınıf bağımlılığını azaltan Solid yazılım prensiplerinden birisidir.
# NEDEN
Birbiriyle kalıtım yapan sınıfların Open/Close prensibine uymasını zorunlu kılarak koddaki 'Code Smelli' azaltır, yeni özelliklerin eklenmesini kolaylaştırır; modelleri soyut parçalara
bölerek kodun daha anlaşılır olmasını sağlar.
# NASIL
Türetilen sınıflar, türeyen sınıfların tüm özelliklerini kullanmak zorundadır. Extend edilen alt sınıf interface'i ile üst sınıf interface'i yer değiştirdiğinde koddaki fonksiyonalitenin değişmemesine dikkat edilir.

`Sınıf ilişkileri üzerinden bir örnek gösterelim;`

Personel adında abstract bir sınıfımız olsun

```java
public abstract class Personel {

    public void calis() { 
      ...
    }
    
}
```

Özelleştirilmiş bir arayüz tanımlayalım

```java
public interface Denetleyebilir {

    void personelDenetle();
    
}
```

İşçi bir personeldir

```java
public class Isci extends Personel {
    ...
}
```

Müdür bir personeldir, diğer personellere ek olarak denetleme görevine sahiptir

```java
public class Mudur extends Personel implements Denetleyebilir {
     
     @Override
     void personelDenetle() {
          ...
     }

}
```

Yukarıda örnekte tıpkı Liskov prensibinin dediği gibi türetilen sınıflar, türeyen sınıfların tüm özelliklerini kullanırlar, hiyerarşik sınıflar yer değiştirdiğinde aynı davranışı sergilerler.
Ayrıca sadece ihtiyacı olan alt sınıfa Interface implemente edebildiğim için Open/Close prensibine aykırı davranmamış oluruz.


