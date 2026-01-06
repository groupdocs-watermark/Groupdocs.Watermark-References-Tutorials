---
date: '2025-12-20'
description: Μάθετε πώς να εξάγετε εικόνες από έγγραφα Word και να εξάγετε σχήματα
  χρησιμοποιώντας το GroupDocs.Watermark για Java, ιδανικό για αυτοματοποίηση και
  διαχείριση εγγράφων.
keywords:
- GroupDocs.Watermark
- extract images from word
- how to extract shapes
- load word document java
title: Πώς να εξάγετε εικόνες από έγγραφα Word χρησιμοποιώντας το GroupDocs.Watermark
  σε Java
type: docs
url: /el/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Πώς να Εξάγετε Εικόνες από Έγγραφα Word Χρησιμοποιώντας το GroupDocs.Watermark σε Java

Σε σύγχρονες εφαρμογές επεξεργασίας εγγράφων, η **εξαγωγή εικόνων από word** εγγράφων είναι συχνή απαίτηση—είτε χρειάζεστε να επαναχρησιμοποιήσετε γραφικά, να εκτελέσετε OCR, ή απλώς να ελέγξετε το περιεχόμενο. Αυτό το σεμινάριο σας δείχνει, βήμα προς βήμα, πώς να φορτώσετε ένα έγγραφο Word σε Java με το GroupDocs.Watermark και στη συνέχεια **να εξάγετε εικόνες από word** αρχεία ενώ επίσης παρουσιάζει **πώς να εξάγετε σχήματα**. Στο τέλος, θα έχετε ένα επαναχρησιμοποιήσιμο κομμάτι κώδικα που ταιριάζει άμεσα στη γραμμή αυτοματισμού σας.

## Quick Answers
- **Ποια βιβλιοθήκη διαχειρίζεται την εξαγωγή εικόνων;** GroupDocs.Watermark for Java  
- **Μπορώ να εξάγω τόσο εικόνες όσο και διανυσματικά σχήματα;** Ναι – το API παρέχει πρόσβαση σε εικόνες και μεταδεδομένα σχήματος.  
- **Ποια έκδοση Java απαιτείται;** JDK 8 ή νεότερη.  
- **Χρειάζομαι άδεια για παραγωγή;** Συνιστάται εμπορική άδεια· μια δωρεάν δοκιμή λειτουργεί για αξιολόγηση.  
- **Είναι η διαδικασία αποδοτική στη μνήμη για μεγάλα αρχεία;** Ναι, μπορείτε να απελευθερώσετε πόρους άμεσα και να επεξεργαστείτε τμήματα σταδιακά.

## Τι είναι η “Εξαγωγή Εικόνων από Word”;
Η εξαγωγή εικόνων από Word σημαίνει προγραμματιστική εντόπιση κάθε εικόνας, σχεδίου ή ενσωματωμένου γραφικού μέσα σε αρχείο `.docx` και ανάκτηση των δυαδικών δεδομένων ή των μεταδεδομένων του. Αυτό επιτρέπει επόμενες εργασίες όπως ανάλυση εικόνων, μετανάστευση περιεχομένου ή δημιουργία δυναμικών αναφορών.

## Γιατί να Χρησιμοποιήσετε το GroupDocs.Watermark για Αυτό το Καθήκον;
Το GroupDocs.Watermark προσφέρει ένα υψηλού επιπέδου API που αφαιρεί τις πολυπλοκότητες της μορφής OpenXML. Σας επιτρέπει να **φορτώσετε word document java** έργα με μόνο λίγες γραμμές κώδικα, ενώ επίσης εκθέτει λεπτομερείς πληροφορίες σχήματος—ιδανικό για προγραμματιστές που χρειάζονται τόσο εξαγωγή εικόνων όσο και ανάλυση σχημάτων.

## Προαπαιτούμενα
- **Java Development Kit (JDK)** 8 ή νεότερο  
- **IDE** – IntelliJ IDEA, Eclipse ή οποιονδήποτε επεξεργαστή συμβατό με Java  
- Βασικές γνώσεις Java I/O  
- Πρόσβαση σε άδεια GroupDocs.Watermark (η δοκιμή λειτουργεί για δοκιμές)

## Ρύθμιση του GroupDocs.Watermark για Java
Ενσωματώστε τη βιβλιοθήκη μέσω Maven ή άμεσης λήψης.

### Using Maven
Προσθέστε το αποθετήριο και την εξάρτηση στο `pom.xml` σας:

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

### Direct Download
Εναλλακτικά, κατεβάστε το πιο πρόσφατο JAR από [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### License Acquisition
Για πλήρη λειτουργικότητα, αποκτήστε ένα κλειδί άδειας από το portal του GroupDocs. Μπορείτε να ζητήσετε προσωρινή δοκιμαστική άδεια για να εξερευνήσετε όλες τις δυνατότητες χωρίς περιορισμούς.

## Οδηγός Υλοποίησης
Θα χωρίσουμε την υλοποίηση σε δύο λογικά μέρη:

1. **Πώς να φορτώσετε ένα έγγραφο Word σε Java**  
2. **Πώς να εξάγετε σχήματα και εικόνες (δηλαδή, εξαγωγή εικόνων από word)**

### Φόρτωση Εγγράφου Word
Πρώτα, διαμορφώστε τις επιλογές φόρτωσης και δημιουργήστε το `Watermarker`.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void loadDocument() {
    // Configure load options for loading a Word document
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    
    // Create an instance of Watermarker with the specified document and load options
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);
    
    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Συμβουλή:** Αντικαταστήστε `"YOUR_DOCUMENT_DIRECTORY/document.docx"` με μια απόλυτη ή σχετική διαδρομή που δείχνει στο αρχείο που θέλετε να επεξεργαστείτε.

### Εξαγωγή Πληροφοριών Σχήματος και Εικόνας
Τώρα που το έγγραφο είναι φορτωμένο, μπορείτε να επαναλάβετε κάθε τμήμα και κάθε σχήμα, εξάγοντας τόσο δεδομένα διανυσματικών σχημάτων όσο και λεπτομέρειες ενσωματωμένων εικόνων.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.WordProcessingContent;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;

public void extractShapeInformation() {
    // Load the Word document as configured previously
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/document.docx", loadOptions);

    // Obtain WordProcessingContent from the watermarker
    WordProcessingContent content = watermarker.getContent(WordProcessingContent.class);

    // Iterate over each section in the document's content
    for (var section : content.getSections()) {
        // Iterate over each shape within the current section
        for (var shape : section.getShapes()) {
            // Check if the shape is part of a header or footer
            if (shape.getHeaderFooter() != null) {
                System.out.println("In header/footer");
            }
            
            // Output details about each shape, such as type and dimensions
            System.out.println(shape.getShapeType());
            System.out.println(shape.getWidth());
            System.out.println(shape.getHeight());
            System.out.println(shape.isWordArt());
            System.out.println(shape.getRotateAngle());
            System.out.println(shape.getAlternativeText());
            System.out.println(shape.getName());
            System.out.println(shape.getX());
            System.out.println(shape.getY());
            System.out.println(shape.getText());

            // If the shape contains an image, output its details (this is the core of “extract images from word”)
            if (shape.getImage() != null) {
                System.out.println("Image width: " + shape.getImage().getWidth());
                System.out.println("Image height: " + shape.getImage().getHeight());
                System.out.println("Image byte size: " + shape.getImage().getBytes().length);
            }
            
            // Output alignment information of the shape
            System.out.println(shape.getHorizontalAlignment());
            System.out.println(shape.getVerticalAlignment());
            System.out.println(shape.getRelativeHorizontalPosition());
            System.out.println(shape.getRelativeVerticalPosition());
        }
    }

    // Close the watermarker to release resources
    watermarker.close();
}
```

> **Γιατί είναι σημαντικό:** Η κλήση `shape.getImage()` σας δίνει άμεση πρόσβαση στην δυαδική αναπαράσταση κάθε εικόνας, επιτρέποντάς σας να την αποθηκεύσετε στο δίσκο, να τη στείλετε μέσω δικτύου ή να τη δώσετε σε μια βιβλιοθήκη επεξεργασίας εικόνας.

## Συνηθισμένα Προβλήματα και Λύσεις
| Problem | Solution |
|---------|----------|
| **FileNotFoundException** – wrong path | Επαληθεύστε τη διαδρομή του αρχείου και βεβαιωθείτε ότι η εφαρμογή έχει δικαιώματα ανάγνωσης. |
| **OutOfMemoryError** on large docs | Επεξεργαστείτε τα τμήματα ένα προς ένα και καλέστε `watermarker.close()` αμέσως μόλις ολοκληρώσετε μια παρτίδα. |
| Shapes return `null` for `getImage()` | Δεν όλα τα σχήματα είναι εικόνες· κάποια είναι αντικείμενα σχεδίου. Ελέγξτε `shape.getShapeType()` πριν προσπελάσετε την εικόνα. |
| License not applied | Προσθέστε `License.setLicense("path/to/license/file.lic");` πριν δημιουργήσετε το `Watermarker`. |

## Πρακτικές Εφαρμογές
- **Αυτοματοποιημένη Δημιουργία Αναφορών:** Ανάκτηση διαγραμμάτων και λογοτύπων από πρότυπα για επαναχρησιμοποίηση σε πίνακες ελέου.  
- **Έλεγχος Περιεχομένου:** Σάρωση εταιρικών εγγράφων για απαγορευμένα γραφικά.  
- **Έργα Μετανάστευσης:** Εξαγωγή ενσωματωμένων εικόνων πριν τη μεταφορά του περιεχομένου σε νέο CMS.  

## Σκέψεις Απόδοσης
- Απελευθερώστε άμεσα την παρουσία `Watermarker` (`watermarker.close()`).  
- Για τεράστια αρχεία (>50 MB), σκεφτείτε τη ροή τμημάτων αντί για τη φόρτωση ολόκληρου του εγγράφου στη μνήμη.  
- Χρησιμοποιήστε την πιο πρόσφατη έκδοση του GroupDocs.Watermark για βελτιώσεις απόδοσης.  

## Συμπέρασμα
Τώρα έχετε μια πλήρη, έτοιμη για παραγωγή προσέγγιση για **εξαγωγή εικόνων από word** έγγραφα και ανάκτηση μεταδεδομένων σχημάτων χρησιμοποιώντας το GroupDocs.Watermark για Java. Αυτή η δυνατότητα ανοίγει ισχυρά σενάρια αυτοματισμού, από τη δημιουργία δυναμικών αναφορών μέχρι την εκτέλεση εκτεταμένων ελέγχων εγγράφων.

### Επόμενα Βήματα
- Πειραματιστείτε με την αποθήκευση των εξαγόμενων εικόνων στο δίσκο (`Files.write(Paths.get("output.png"), shape.getImage().getBytes());`).  
- Εξερευνήστε πρόσθετα API όπως η αφαίρεση ή η προσθήκη υδατογραφήματος.  
- Ενσωματώστε αυτή τη λογική στην υπάρχουσα ροή εργασίας διαχείρισης εγγράφων.  

## Ενότητα Συχνών Ερωτήσεων
**Ε: Τι είναι το GroupDocs.Watermark για Java;**  
Είναι μια ολοκληρωμένη βιβλιοθήκη σχεδιασμένη για τη διαχείριση υδατογραφημάτων και την εξαγωγή οπτικών στοιχείων σε διάφορες μορφές εγγράφων, ενισχύοντας τον αυτοματισμό εργασιών επεξεργασίας εγγράφων.

**Ε: Μπορώ να εξάγω εικόνες από Word αρχεία με κωδικό πρόσβασης;**  
Ναι. Φορτώστε το έγγραφο με `WordProcessingLoadOptions` που περιλαμβάνει τον κωδικό πρόσβασης, μετά προχωρήστε με την ίδια λογική εξαγωγής.

**Ε: Υποστηρίζει το API επίσης αρχεία .doc (δυαδικά);**  
Η βιβλιοθήκη στοχεύει κυρίως στη μορφή OpenXML `.docx`, αλλά μπορεί επίσης να ανοίξει παλαιά αρχεία `.doc` μετά από μετατροπή.

**Ε: Πώς αποθηκεύω τις εξαγόμενες εικόνες στο σύστημα αρχείων;**  
Χρησιμοποιήστε `java.nio.file.Files.write(Paths.get("image.png"), shape.getImage().getBytes());` μέσα στον βρόχο όπου `shape.getImage()` δεν είναι null.

**Ε: Υπάρχει όριο στον αριθμό των σχημάτων που μπορώ να επεξεργαστώ;**  
Δεν υπάρχει σκληρό όριο, αλλά η κατανάλωση μνήμης αυξάνεται με το μέγεθος του εγγράφου· επεξεργαστείτε τα τμήματα διαδοχικά για πολύ μεγάλα αρχεία.

---

**Τελευταία Ενημέρωση:** 2025-12-20  
**Δοκιμάστηκε Με:** GroupDocs.Watermark 24.11 for Java  
**Συγγραφέας:** GroupDocs