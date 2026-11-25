# Maven ile Çalıştırılabilir JAR

Maven Assembly eklentisiyle, bağımlılıklarını da içine alan ve `java -jar` ile doğrudan çalışan tek bir JAR
dosyası üretmeyi gösteren küçük örnek.

> **Not:** Bu depo 2017 yılında eğitim amaçlı yazıldı ve artık güncellenmiyor. Eklenti sürümleri eskidir.

## İçerik

- `src/com/mustafaergan/pack1/Islem.java` — `main` metodunu içeren giriş sınıfı.
- `src/com/mustafaergan/pack2/Nesne.java` — başka bir paketten kullanılan basit sınıf; ekrana "Merhaba Dunya" yazdırılır.
- `pom.xml` — kaynak klasörü `src` olarak tanımlanmış; `maven-assembly-plugin`, `jar-with-dependencies`
  tanımlayıcısı ve `com.mustafaergan.pack1.Islem` ana sınıfıyla `package` aşamasına bağlanmış.

## Teknolojiler

- Java 8 (`source`/`target` 1.8)
- Maven, `maven-compiler-plugin` 3.5.1, `maven-assembly-plugin`
- Dış bağımlılık yok

## Çalıştırma

```bash
mvn clean package
java -jar target/MavenJarDeneme-0.0.1-SNAPSHOT-jar-with-dependencies.jar
```

Eski anlatımdaki gibi derleme ve paketlemeyi tek komutla da yapabilirsiniz:

```bash
mvn clean compile assembly:single
```

Her iki durumda da `target/` altında adı `-jar-with-dependencies` ile biten JAR, kodu bağımlılıklarıyla
birlikte içeren çalıştırılabilir dosyadır.
