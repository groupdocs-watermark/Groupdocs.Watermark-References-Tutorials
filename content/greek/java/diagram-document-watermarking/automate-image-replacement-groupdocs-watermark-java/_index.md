---
date: '2026-08-19'
description: Μάθετε πώς να αντικαθιστάτε εικόνες διαγράμματος σε Java χρησιμοποιώντας
  το GroupDocs.Watermark και επίσης να προσθέτετε υδατογράφημα στο διάγραμμα αποδοτικά.
  Κώδικας βήμα‑βήμα και βέλτιστες πρακτικές.
keywords:
- replace diagram images java
- add watermark to diagram
- groupdocs watermark java
lastmod: '2026-08-19'
og_description: Μάθετε πώς να αντικαθιστάτε εικόνες διαγράμματος σε Java χρησιμοποιώντας
  το GroupDocs.Watermark και επίσης να προσθέτετε υδατογράφημα στο διάγραμμα αποδοτικά.
  Κώδικας βήμα‑βήμα και βέλτιστες πρακτικές.
og_image_alt: Guide showing Java code to replace diagram images with GroupDocs.Watermark
og_title: Αντικατάσταση εικόνων διαγράμματος σε Java χρησιμοποιώντας το GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to replace diagram images in Java using GroupDocs.Watermark,
    and also add watermark to diagram efficiently. Step‑by‑step code and best practices.
  headline: Replace diagram images in Java using GroupDocs.Watermark
  type: TechArticle
- questions:
  - answer: Yes. Pass the password to `DiagramLoadOptions` when creating the `Watermarker`.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely – GroupDocs.Watermark supports the Draw.io XML format and treats
      each node as a shape.
    question: Does the library work with .drawio (XML) files?
  - answer: The library is thread‑safe for read‑only operations; for write operations,
      limit concurrency to the number of CPU cores to avoid file‑handle contention.
    question: How many diagrams can I process in parallel?
  - answer: Images up to 100 MB are supported; larger files should be resized beforehand
      to keep memory usage low.
    question: Is there a limit on image size?
  - answer: You can start with a free 30‑day trial; production use requires a paid
      license, which can be obtained from the GroupDocs store.
    question: What licensing options are available?
  type: FAQPage
tags:
- diagram image replacement
- groupdocs watermark
- java document processing
title: Αντικατάσταση εικόνων διαγράμματος σε Java χρησιμοποιώντας το GroupDocs.Watermark
type: docs
url: /el/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# Αντικατάσταση εικόνων διαγράμματος σε Java χρησιμοποιώντας το GroupDocs.Watermark

Η ενημέρωση εικόνων μέσα σε αρχεία διαγράμματος με το χέρι είναι χρονοβόρα και επιρρεπής σε σφάλματα. Σε αυτό το σεμινάριο θα μάθετε πώς να **αντικαταστήσετε εικόνες διαγράμματος σε Java** με λίγες μόνο γραμμές κώδικα, και επίσης θα δείτε πώς να **προσθέσετε υδατογράφημα σε διάγραμμα** όταν χρειάζεται. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο απόσπασμα κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Java που λειτουργεί με Visio, Draw.io ή άλλες υποστηριζόμενες μορφές διαγράμματος.

## Γρήγορες απαντήσεις
- **Ποια βιβλιοθήκη διαχειρίζεται την αντικατάσταση εικόνων διαγράμματος;** GroupDocs.Watermark for Java.
- **Πόσες γραμμές κώδικα απαιτούνται για μια βασική αντικατάσταση;** Only three lines after the Watermarker is created.
- **Μπορώ να προσθέσω υδατογράφημα ταυτόχρονα;** Yes – use the same Watermarker instance with a watermark object.
- **Ποια έκδοση της Java απαιτείται;** JDK 8 or higher.
- **Χρειάζομαι άδεια για χρήση σε παραγωγή;** A valid GroupDocs.Watermark license is required; a free trial is available.

## Τι είναι η αντικατάσταση εικόνων διαγράμματος σε Java;
Η αντικατάσταση εικόνων διαγράμματος σε Java σημαίνει τον προγραμματιστικό εντοπισμό σχημάτων που περιέχουν bitmap γραφικά μέσα σε ένα αρχείο διαγράμματος (όπως .vsdx, .drawio ή .svg) και την ανταλλαγή αυτών των ενσωματωμένων εικόνων με νέες χρησιμοποιώντας το GroupDocs.Watermark API. Αυτό αυτοματοποιεί τις ενημερώσεις που διαφορετικά θα απαιτούσαν χειροκίνητη επεξεργασία σε έναν επεξεργαστή διαγράμματος.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark για την αντικατάσταση εικόνων διαγράμματος;
Το GroupDocs.Watermark υποστηρίζει **50+ μορφές εισόδου και εξόδου** – συμπεριλαμβανομένων των Visio, Draw.io και SVG – και μπορεί να επεξεργαστεί **αρχεία έως 500 MB** χωρίς να φορτώνει ολόκληρο το έγγραφο στη μνήμη, παρέχοντάς σας **μείωση 30 % στη χρήση CPU** σε σύγκριση με τις απλές προσεγγίσεις ροής αρχείων.

## Προαπαιτούμενα
- JDK 8 ή νεότερο εγκατεστημένο.
- Ένα IDE (IntelliJ IDEA, Eclipse ή VS Code) για ανάπτυξη Java.
- Maven (ή η δυνατότητα προσθήκης JAR χειροκίνητα).
- Ένα έγκυρο άδεια GroupDocs.Watermark (δοκιμαστική ή μόνιμη). Μπορείτε να αποκτήσετε άδεια από [GroupDocs](https://purchase.groupdocs.com/temporary-license/).

### Απαιτούμενες βιβλιοθήκες, εκδόσεις και εξαρτήσεις
Προσθέστε το αποθετήριο και την εξάρτηση GroupDocs.Watermark στο `pom.xml` σας:

```xml
```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/watermark/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-watermark</artifactId>
      <version>24.11</version>
   </dependency>
</dependencies>
```
```

Αν προτιμάτε τη χειροκίνητη διαχείριση JAR, κατεβάστε την πιο πρόσφατη έκδοση από την επίσημη ιστοσελίδα: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Πώς να αντικαταστήσετε εικόνες διαγράμματος σε Java βήμα προς βήμα

### Πώς να αρχικοποιήσετε το Watermarker για ένα αρχείο διαγράμματος;
Το Watermarker είναι η κύρια κλάση που αντιπροσωπεύει ένα έγγραφο και παρέχει μεθόδους για την επεξεργασία περιεχομένου. Για να ξεκινήσετε, δημιουργήστε ένα αντικείμενο `Watermarker` που φορτώνει το αρχείο διαγράμματος στη μνήμη. Η κλάση `Watermarker` είναι το κεντρικό σημείο εισόδου του GroupDocs.Watermark, επιτρέποντάς σας να διαβάζετε, να τροποποιείτε και να αποθηκεύετε έγγραφα. Χρησιμοποιήστε το `DiagramLoadOptions` για να καθορίσετε ρυθμίσεις ειδικές για τη μορφή, όπως DPI ή εύρος σελίδων. Το `DiagramLoadOptions` διαμορφώνει πώς φορτώνεται ένα διάγραμμα, π.χ., ορίζοντας DPI ή τρόπο φόρτωσης.

```java
```java
import java.io.File;
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class FeatureWatermarkerInitialization {
    public static void run() throws Exception {
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(documentPath, loadOptions);
    }
}
```
```

### Πώς μπορείτε να αποκτήσετε πρόσβαση στο περιεχόμενο του διαγράμματος για να εντοπίσετε σχήματα;
Μετά τη φόρτωση του αρχείου, ανακτήστε ένα αντικείμενο `DiagramContent` από το `Watermarker`. Το `DiagramContent` αντιπροσωπεύει την εσωτερική ιεραρχία του διαγράμματος με σελίδες και σχήματα. Αυτό το μοντέλο εκθέτει συλλογές σελίδων και σχημάτων που μπορείτε να διασχίσετε, διευκολύνοντας τον εντοπισμό συγκεκριμένων στοιχείων όπως εικόνες ή κείμενο.

```java
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```
```

### Πώς να αντικαταστήσετε τις εικόνες σχήματος σε ένα διάγραμμα;
Επανάληψη σε κάθε `DiagramShape` στην επιθυμητή σελίδα, έλεγχος εάν το σχήμα περιέχει εικόνα, και αντικατάσταση των bytes της εικόνας με αυτά ενός νέου αρχείου. Το `DiagramShape` είναι το μοντέλο για ένα μεμονωμένο σχήμα σε ένα διάγραμμα, ενώ το `DiagramWatermarkableImage` αποθηκεύει τα δεδομένα εικόνας που μπορούν να εφαρμοστούν σε ένα σχήμα.

```java
```java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import com.groupdocs.watermark.contents.DiagramShape;
import com.groupdocs.watermark.contents.DiagramWatermarkableImage;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureReplaceShapeImages {
    public static void run(DiagramContent content) throws Exception {
        for (DiagramShape shape : content.getPages().get_Item(0).getShapes()) {
            if (shape.getImage() != null) {
                File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/test.png");
                byte[] imageBytes = new byte[(int) imageFile.length()];
                InputStream imageInputStream = new FileInputStream(imageFile);
                imageInputStream.read(imageBytes);
                imageInputStream.close();

                shape.setImage(new DiagramWatermarkableImage(imageBytes));
            }
        }
    }
}
```
```

### Πώς να αποθηκεύσετε τις αλλαγές και να κλείσετε το Watermarker;
Όταν ολοκληρωθούν όλες οι τροποποιήσεις, καλέστε `save` στο `Watermarker` για να γράψετε το ενημερωμένο διάγραμμα σε αρχείο, στη συνέχεια καλέστε `close` για να απελευθερώσετε τους εγγενείς πόρους. Αυτό εξασφαλίζει ότι τα handles των αρχείων ελευθερώνονται και αποτρέπει διαρροές μνήμης, ειδικά όταν επεξεργάζεστε πολλά διαγράμματα σε μια παρτίδα εργασίας.

```java
```java
import com.groupdocs.watermark.Watermarker;

public class FeatureSaveAndCloseWatermarker {
    public static void run(Watermarker watermarker) throws Exception {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/output.vsdx";
        watermarker.save(outputPath);
        watermarker.close();
    }
}
```
```

## Προσθήκη υδατογραφήματος στο ίδιο διάγραμμα (προαιρετικό)

Αν χρειάζεστε επίσης να επισημάνετε το διάγραμμα, μπορείτε να προσθέσετε υδατογράφημα πριν ή μετά την αντικατάσταση της εικόνας:

```java
// Example – adding a text watermark
Watermark watermark = new TextWatermark("Confidential", new Font("Arial", 12));
watermarker.add(watermark);
```

## Συνηθισμένα προβλήματα και αντιμετώπιση

| Σύμπτωμα | Πιθανή αιτία | Διόρθωση |
|----------|--------------|----------|
| Καμία αλλαγή εικόνας μετά την εκτέλεση του κώδικα | `DiagramShape.hasImage()` επέστρεψε false | Επαληθεύστε τον τύπο του σχήματος· ορισμένα διανυσματικά σχήματα αποθηκεύουν εικόνες διαφορετικά. |
| OutOfMemoryError σε μεγάλα αρχεία | Φόρτωση ολόκληρου του διαγράμματος ταυτόχρονα | Χρησιμοποιήστε `DiagramLoadOptions.setLoadMode(LoadMode.Stream)` για επεξεργασία σελίδων διαδοχικά. |
| Το υδατογράφημα δεν είναι ορατό | Το υδατογράφημα τοποθετήθηκε πίσω από το υπάρχον περιεχόμενο | Καλέστε `watermarker.setWatermarkPosition(Position.Foreground)` πριν την αποθήκευση. |

## Συχνές ερωτήσεις

**Q: Μπορώ να αντικαταστήσω εικόνες σε διαγράμματα με προστασία κωδικού;**  
A: Yes. Pass the password to `DiagramLoadOptions` when creating the `Watermarker`.

**Q: Η βιβλιοθήκη λειτουργεί με αρχεία .drawio (XML);**  
A: Absolutely – GroupDocs.Watermark supports the Draw.io XML format and treats each node as a shape.

**Q: Πόσα διαγράμματα μπορώ να επεξεργαστώ παράλληλα;**  
A: The library is thread‑safe for read‑only operations; for write operations, limit concurrency to the number of CPU cores to avoid file‑handle contention.

**Q: Υπάρχει όριο στο μέγεθος της εικόνας;**  
A: Images up to 100 MB are supported; larger files should be resized beforehand to keep memory usage low.

**Q: Ποιες επιλογές αδειοδότησης είναι διαθέσιμες;**  
A: You can start with a free 30‑day trial; production use requires a paid license, which can be obtained from the GroupDocs store.

---

**Τελευταία ενημέρωση:** 2026-08-19  
**Δοκιμάστηκε με:** GroupDocs.Watermark 23.9 for Java  
**Συγγραφέας:** GroupDocs

## Σχετικά σεμινάρια

- [Σεμινάρια Υδατογράφησης Διαγράμματος για GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [Αφαίρεση Υπερσυνδέσμων από Σχήματα Διαγράμματος χρησιμοποιώντας GroupDocs.Watermark Java για Βελτιωμένη Ασφάλεια Εγγράφων](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [Πώς να Προσθέσετε Υδατογράφημα Εικόνας σε Java χρησιμοποιώντας GroupDocs.Watermark: Οδηγός Βήμα‑Βήμα](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)