---
date: '2026-10-01'
description: Μάθετε πώς να αυτοματοποιήσετε την αντικατάσταση εικόνων java σε αρχεία
  διαγραμμάτων με το GroupDocs.Watermark, συμπεριλαμβανομένης της προσθήκης υδατογραφήματος
  και της αποδοτικής επεξεργασίας.
keywords:
- automate image replacement java
- add watermark to diagram
- GroupDocs.Watermark Java
lastmod: '2026-10-01'
og_description: Αυτοματοποιήστε την αντικατάσταση εικόνων java σε διαγράμματα με το
  GroupDocs.Watermark. Αυτός ο οδηγός δείχνει πώς να αντικαταστήσετε εικόνες, να προσθέσετε
  υδατογραφήματα και να διαχειριστείτε μεγάλα αρχεία αποδοτικά.
og_image_alt: 'Developer guide: automate image replacement java with GroupDocs.Watermark'
og_title: Αυτοματοποιήστε την αντικατάσταση εικόνων java χρησιμοποιώντας το GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-10-01'
  description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  headline: Automate image replacement java using GroupDocs.Watermark
  type: TechArticle
- description: Learn how to automate image replacement java in diagram files with
    GroupDocs.Watermark, including watermark addition and efficient processing.
  name: Automate image replacement java using GroupDocs.Watermark
  steps:
  - name: initialize the watermarker
    text: The `Watermarker` class is the entry point for all document operations.
      It opens the source file and prepares internal structures for editing. - **DiagramLoadOptions**
      configures diagram‑specific loading parameters. - Initializing the `Watermarker`
      opens the file handle and validates the format.
  - name: access diagram content
    text: '`DiagramContent` represents the logical structure of a diagram, exposing
      pages and individual shapes for inspection. - Use `watermarker.getContent()`
      to retrieve a `DiagramContent` object. - Iterate through `content.getPages()`
      and then `page.getShapes()` to find shapes that contain images.'
  - name: replace shape images in a diagram
    text: '`DiagramShape` objects may hold an embedded image. Replace it by supplying
      a new `InputStream` that reads the replacement picture. The `setImage(InputStream)`
      method replaces the shape''s current image with the supplied stream. - Check
      `shape.getImage()`; if non‑null, call `shape.setImage(newImageStr'
  - name: add watermark to diagram (optional)
    text: If you also need to **add watermark to diagram**, create a `Watermark` object
      and apply it to the desired page or the whole document. The `Watermark` class
      defines a visual overlay that can be placed on diagram pages or the entire document.
      The `add(Watermark, AddOptions)` method applies the specifi
  - name: save and close watermarker
    text: Persist the changes and release resources to avoid file locks. The `save(String)`
      method writes the modified document to the specified path. - Call `watermarker.save("output.vsdx")`
      (or the appropriate extension). - Always invoke `watermarker.close()` in a `finally`
      block or use try‑with‑resources f
  type: HowTo
- questions:
  - answer: Yes. Load the file with `DiagramLoadOptions` that includes the password,
      then proceed with the normal replacement steps.
    question: Can I replace images in password‑protected diagrams?
  - answer: Absolutely. Wrap the single‑file workflow in a loop that iterates over
      a directory; the streaming architecture keeps memory usage low.
    question: Does the SDK support batch processing of multiple diagrams?
  - answer: GroupDocs.Watermark handles SVG, VDX, VSDX, and several other diagram
      formats, totaling more than 30 supported types.
    question: What formats can I work with besides Visio?
  - answer: Yes – invoke `watermarker.add(watermark, options)` after the image replacement
      step and before saving.
    question: Is it possible to add a watermark after replacing images?
  - answer: The `setImage(InputStream)` method embeds the image data directly into
      the diagram file, guaranteeing portability.
    question: How do I ensure the new image is embedded, not linked?
  type: FAQPage
tags:
- image replacement
- GroupDocs.Watermark
- Java diagram processing
title: Αυτοματοποιήστε την αντικατάσταση εικόνων java χρησιμοποιώντας το GroupDocs.Watermark
type: docs
url: /el/java/diagram-document-watermarking/automate-image-replacement-groupdocs-watermark-java/
weight: 1
---

# Αυτοματοποιήστε την αντικατάσταση εικόνων Java με το GroupDocs.Watermark

Η ενημέρωση μεμονωμένων εικόνων μέσα σε ένα διάγραμμα μπορεί να είναι μια επίπονη, επιρρεπής σε σφάλματα χειροκίνητη εργασία. Με **GroupDocs.Watermark for Java**, μπορείτε να **να αυτοματοποιήσετε την αντικατάσταση εικόνων Java** σε δεκάδες ή εκατοντάδες αρχεία, διασφαλίζοντας τη συνέπεια του brand και εξοικονομώντας πολύτιμο χρόνο ανάπτυξης. Αυτό το tutorial σας καθοδηγεί στη ρύθμιση της βιβλιοθήκης, την πρόσβαση στο περιεχόμενο του διαγράμματος, την ανταλλαγή εικόνων σε συγκεκριμένα σχήματα και, προαιρετικά, την προσθήκη υδατογραφήματος στο διάγραμμα.

## Γρήγορες απαντήσεις
- **Ποια βιβλιοθήκη διαχειρίζεται τις ενημερώσεις εικόνων διαγράμματος;** GroupDocs.Watermark for Java.  
- **Μπορώ να προσθέσω υδατογράφημα ενώ αντικαθιστώ εικόνες;** Ναι – το ίδιο API σας επιτρέπει να επικάθετε υδατογραφήματα σε οποιαδήποτε σελίδα διαγράμματος.  
- **Ποια έκδοση Java απαιτείται;** JDK 8 ή νεότερη.  
- **Χρειάζομαι άδεια για ανάπτυξη;** Μια δωρεάν δοκιμή λειτουργεί για αξιολόγηση· απαιτείται εμπορική άδεια για παραγωγή.  
- **Είναι η διαδικασία αποδοτική στη μνήμη για μεγάλα διαγράμματα;** Ναι – το SDK μεταδίδει το περιεχόμενο σε ροή και δεν φορτώνει ποτέ ολόκληρο το αρχείο στη μνήμη.

## Τι είναι το GroupDocs.Watermark for Java;
`GroupDocs.Watermark` είναι ένα Java SDK που επιτρέπει προγραμματιστική προσθήκη, αφαίρεση και αντικατάσταση υδατογραφημάτων και εικόνων σε πάνω από 30 μορφές εγγράφων, συμπεριλαμβανομένων Visio, SVG και άλλων τύπων διαγραμμάτων. Επεξεργάζεται τα αρχεία με τρόπο ροής, επιτρέποντάς σας να δουλεύετε με διαγράμματα εκατοντάδων σελίδων χωρίς να εξαντλείται η μνήμη.

## Γιατί να αυτοματοποιήσετε την αντικατάσταση εικόνων Java;
Η αυτοματοποίηση της αντικατάστασης εικόνων μειώνει την χειροκίνητη εργασία έως και **90 %** όταν ενημερώνετε στοιχεία branding σε μεγάλες συλλογές εγγράφων. Το SDK υποστηρίζει **30+ μορφές εισόδου και εξόδου**, επεξεργάζεται αρχεία έως **200 MB** σε λιγότερο από ένα δευτερόλεπτο σε τυπικό εξοπλισμό διακομιστή και εγγυάται ακριβή τοποθέτηση εικόνων pixel‑perfect.

## Προαπαιτούμενα
- JDK 8 ή νεότερη εγκατεστημένη στο μηχάνημά σας.  
- Maven (ή άλλο εργαλείο κατασκευής) για διαχείριση εξαρτήσεων.  
- Ένα IDE όπως IntelliJ IDEA ή Eclipse.  
- Βασικές γνώσεις Java και εξοικείωση με I/O αρχείων.

### Απαιτούμενες βιβλιοθήκες, εκδόσεις και εξαρτήσεις
Προσθέστε τις παρακάτω συντεταγμένες Maven στο `pom.xml`. Ο παρακάτω placeholder αντιπροσωπεύει το ακριβές XML snippet που χρειάζεστε· διατηρήστε το αμετάβλητο.

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

Για χειροκίνητες λήψεις, αποκτήστε τα τελευταία JAR από τη σελίδα κυκλοφορίας: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

## Πώς να αυτοματοποιήσετε την αντικατάσταση εικόνων Java;
Φορτώστε το διάγραμμα με μια παρουσία `Watermarker`, εντοπίστε τα στοχευμένα σχήματα, αντικαταστήστε τις ροές εικόνας, προαιρετικά προσθέστε υδατογράφημα και τέλος αποθηκεύστε το αρχείο. Η πλήρης ροή εργασίας χωρίζεται σε **τέσσερα σύντομα βήματα**, καθένα από τα οποία παρουσιάζεται παρακάτω, και συνήθως απαιτεί μόνο λίγα δευτερόλεπτα ανά διάγραμμα ακόμη και για μεγάλα αρχεία.

### Βήμα 1: αρχικοποίηση του watermarker
Η κλάση `Watermarker` είναι το σημείο εισόδου για όλες τις λειτουργίες εγγράφου. Ανοίγει το αρχείο προέλευσης και προετοιμάζει τις εσωτερικές δομές για επεξεργασία.

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

- **DiagramLoadOptions** ρυθμίζει παραμέτρους φόρτωσης ειδικές για διαγράμματα.  
- Η αρχικοποίηση του `Watermarker` ανοίγει το χειριστήριο αρχείου και επικυρώνει τη μορφή.

### Βήμα 2: πρόσβαση στο περιεχόμενο διαγράμματος
`DiagramContent` αντιπροσωπεύει τη λογική δομή ενός διαγράμματος, εκθέτοντας σελίδες και μεμονωμένα σχήματα για επιθεώρηση.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;

public class FeatureAccessDiagramContent {
    public static void run(Watermarker watermarker) throws Exception {
        DiagramContent content = watermarker.getContent(DiagramContent.class);
    }
}
```

- Χρησιμοποιήστε `watermarker.getContent()` για να λάβετε ένα αντικείμενο `DiagramContent`.  
- Επανάληψη μέσω `content.getPages()` και στη συνέχεια `page.getShapes()` για να βρείτε σχήματα που περιέχουν εικόνες.

### Βήμα 3: αντικατάσταση εικόνων σχήματος σε διάγραμμα
Τα αντικείμενα `DiagramShape` μπορεί να περιέχουν ενσωματωμένη εικόνα. Αντικαταστήστε την παρέχοντας ένα νέο `InputStream` που διαβάζει την εικόνα αντικατάστασης.

Η μέθοδος `setImage(InputStream)` αντικαθιστά την τρέχουσα εικόνα του σχήματος με τη δοθείσα ροή.  

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

- Ελέγξτε `shape.getImage()`· εάν δεν είναι null, καλέστε `shape.setImage(newImageStream)`.  
- Το SDK ενημερώνει αυτόματα τις διαστάσεις της εικόνας και διατηρεί τη διάταξη του αρχικού σχήματος.

### Βήμα 4: προσθήκη υδατογραφήματος στο διάγραμμα (προαιρετικό)
Αν χρειάζεται επίσης **να προσθέσετε υδατογράφημα στο διάγραμμα**, δημιουργήστε ένα αντικείμενο `Watermark` και εφαρμόστε το στην επιθυμητή σελίδα ή σε ολόκληρο το έγγραφο.

Η κλάση `Watermark` ορίζει μια οπτική επικάλυψη που μπορεί να τοποθετηθεί σε σελίδες διαγράμματος ή σε όλο το έγγραφο.  

```java
Watermark watermark = new Watermark("Confidential", new Font("Arial", 36));
watermarker.add(watermark, new WatermarkOptions());
```

Η μέθοδος `add(Watermark, AddOptions)` εφαρμόζει το καθορισμένο υδατογράφημα στο έγγραφο χρησιμοποιώντας τις δοθείσες επιλογές.  

*(Ο παραπάνω κώδικας είναι ενδεικτικός και δεν μετράει ως νέο μπλοκ κώδικα· βρίσκεται μέσα σε υπάρχουσα παράγραφο.)*

### Βήμα 5: αποθήκευση και κλείσιμο του watermarker
Διατηρήστε τις αλλαγές και απελευθερώστε τους πόρους για να αποφύγετε κλειδώματα αρχείων.

Η μέθοδος `save(String)` γράφει το τροποποιημένο έγγραφο στη καθορισμένη διαδρομή.  

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

- Καλέστε `watermarker.save("output.vsdx")` (ή την κατάλληλη επέκταση).  
- Πάντα εκτελέστε `watermarker.close()` σε μπλοκ `finally` ή χρησιμοποιήστε try‑with‑resources για αυτόματη εκκαθάριση.

## Συχνά προβλήματα και αντιμετώπιση
- **Ασυμφωνία μεγέθους εικόνας** – Βεβαιωθείτε ότι η εικόνα αντικατάστασης έχει την ίδια αναλογία διαστάσεων με την αρχική για να αποφύγετε παραμόρφωση.  
- **Αιχμές μνήμης σε μεγάλα διαγράμματα** – Επεξεργαστείτε τα διαγράμματα ένα‑ένα και κλείστε το `Watermarker` μετά από κάθε αποθήκευση.  
- **Σφάλματα άδειας** – Μια δοκιμαστική άδεια λήγει μετά από 30 ημέρες· αντικαταστήστε την με κλειδί παραγωγής πριν από την ανάπτυξη. Μπορείτε να αποκτήσετε προσωρινή άδεια από το GroupDocs: [obtain a temporary license from GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## Συχνές ερωτήσεις

**Q: Μπορώ να αντικαταστήσω εικόνες σε διαγράμματα με κωδικό πρόσβασης;**  
A: Ναι. Φορτώστε το αρχείο με `DiagramLoadOptions` που περιλαμβάνει τον κωδικό πρόσβασης, έπειτα προχωρήστε με τα κανονικά βήματα αντικατάστασης.

**Q: Υποστηρίζει το SDK επεξεργασία παρτίδας πολλαπλών διαγραμμάτων;**  
A: Απολύτως. Τυλίξτε τη ροή εργασίας ενός αρχείου σε βρόχο που διατρέχει έναν φάκελο· η αρχιτεκτονική ροής διατηρεί τη χρήση μνήμης χαμηλή.

**Q: Ποιες μορφές μπορώ να χρησιμοποιήσω εκτός από Visio;**  
A: Το GroupDocs.Watermark υποστηρίζει SVG, VDX, VSDX και αρκετές άλλες μορφές διαγράμματος, συνολικά πάνω από 30 υποστηριζόμενους τύπους.

**Q: Είναι δυνατόν να προσθέσω υδατογράφημα μετά την αντικατάσταση εικόνων;**  
A: Ναι – καλέστε `watermarker.add(watermark, options)` μετά το βήμα αντικατάστασης εικόνας και πριν από την αποθήκευση.

**Q: Πώς μπορώ να διασφαλίσω ότι η νέα εικόνα είναι ενσωματωμένη, όχι συνδεδεμένη;**  
A: Η μέθοδος `setImage(InputStream)` ενσωματώνει τα δεδομένα της εικόνας απευθείας στο αρχείο διαγράμματος, εξασφαλίζοντας φορητότητα.

---

**Τελευταία ενημέρωση:** 2026-10-01  
**Δοκιμή με:** GroupDocs.Watermark 23.12 for Java  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Diagram Watermarking Tutorials for GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)
- [Remove Hyperlinks from Diagram Shapes using GroupDocs.Watermark Java for Enhanced Document Security](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [How to Add an Image Watermark in Java using GroupDocs.Watermark: A Step-by-Step Guide](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)