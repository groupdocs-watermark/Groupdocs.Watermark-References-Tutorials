---
date: '2026-02-05'
description: Μάθετε πώς να εξάγετε σχήματα από έγγραφα Word χρησιμοποιώντας το GroupDocs.Watermark
  για Java, συμπεριλαμβανομένου του πώς να φορτώσετε ένα έγγραφο Word σε Java και
  να διαχειριστείτε τα δεδομένα σχήματος.
keywords:
- GroupDocs.Watermark
- extract shapes from Word documents
- Java document manipulation
title: Πώς να εξάγετε σχήματα από έγγραφα Word χρησιμοποιώντας το GroupDocs.Watermark
  Java
type: docs
url: /el/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Πώς να Εξάγετε Σχήματα από Έγγραφα Word Χρησιμοποιώντας το GroupDocs.Watermark σε Java

Σε αυτό το tutorial θα ανακαλύψετε **πώς να εξάγετε σχήματα** από έγγραφα Word με τη βιβλιοθήκη GroupDocs.Watermark για Java. Είτε χρειάζεστε να αναλύσετε διαγράμματα, να εξάγετε ενσωματωμένες εικόνες, είτε να αυτοματοποιήσετε τη δημιουργία αναφορών, η εξαγωγή μεταδεδομένων σχήματος σας δίνει τον έλεγχο για να δημιουργήσετε πιο έξυπνες διαδικασίες επεξεργασίας εγγράφων. Θα περάσουμε από τη ρύθμιση της βιβλιοθήκης, τη φόρτωση ενός εγγράφου Word και την εξαγωγή λεπτομερών πληροφοριών σχήματος—όλα σε σαφή, βήμα‑βήμα κώδικα Java.

## Γρήγορες Απαντήσεις
- **Τι σημαίνει “εξαγωγή σχημάτων”;** Ανάκτηση μεταδεδομένων (τύπος, μέγεθος, θέση, κείμενο, εικόνες) για κάθε αντικείμενο σχεδίασης σε ένα αρχείο Word.  
- **Ποια βιβλιοθήκη το διαχειρίζεται;** GroupDocs.Watermark για Java.  
- **Χρειάζομαι άδεια;** Η δοκιμαστική έκδοση λειτουργεί για ανάπτυξη· μια πλήρης άδεια αφαιρεί τους περιορισμούς χρήσης.  
- **Μπορώ επίσης να λάβω εικόνες από σχήματα;** Ναι – το API εκθέτει τα bytes της εικόνας για σχήματα εικόνας.  
- **Ποια έκδοση Java απαιτείται;** JDK 8 ή νεότερη.

## Τι σημαίνει “Πώς να Εξάγετε Σχήματα” στο Πλαίσιο των Εγγράφων Word;
Η εξαγωγή σχημάτων σημαίνει προγραμματιστική πρόσβαση σε κάθε στοιχείο σχεδίασης—εικόνες, WordArt, αυτόματα σχήματα, διαγράμματα, και ακόμη σχήματα ενσωματωμένα σε κεφαλίδες ή υποσέλιδα. Αυτές οι πληροφορίες μπορούν να χρησιμοποιηθούν για επικύρωση, μετανάστευση ή ανάλυση βάσει περιεχομένου.

## Γιατί να Χρησιμοποιήσετε το GroupDocs.Watermark για Java;
Το GroupDocs.Watermark παρέχει ένα υψηλού επιπέδου, μνήμης-αποδοτικό API που αφαιρεί την πολυπλοκότητα του υποκείμενου μορφότυπου Office Open XML. Σας επιτρέπει να:
- Φορτώνετε έγγραφα γρήγορα (`WordProcessingLoadOptions`).  
- Επανάληψη μέσω ενοτήτων και σχημάτων χωρίς να ασχοληθείτε με χαμηλού επιπέδου XML.  
- Ανακτήσετε δεδομένα εικόνας, κείμενο, στοίχιση και περιστροφή με μία κλήση.  
- Ενσωματώσετε αβίαστα σε υπάρχουσες υπηρεσίες Java ή μικρο‑υπηρεσίες.

## Προαπαιτούμενα
- **Java Development Kit (JDK)** 8 ή νεότερο.  
- **IDE** όπως IntelliJ IDEA ή Eclipse.  
- Βασικές γνώσεις Java I/O.  
- Πρόσβαση σε άδεια **GroupDocs.Watermark για Java** ή δοκιμαστική έκδοση.

## Ρύθμιση του GroupDocs.Watermark για Java
Ενσωματώστε τη βιβλιοθήκη μέσω Maven ή άμεσης λήψης.

### Χρήση Maven
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

### Άμεση Λήψη
Εναλλακτικά, κατεβάστε το πιο πρόσφατο JAR από [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Απόκτηση Άδειας
Μια δωρεάν δοκιμαστική έκδοση είναι επαρκής για δοκιμές. Για παραγωγή, ζητήστε μόνιμη άδεια για να ξεκλειδώσετε όλες τις δυνατότητες.

## Οδηγός Υλοποίησης
Θα χωρίσουμε την υλοποίηση σε δύο σαφή βήματα: **φόρτωση του εγγράφου Word** και **εξαγωγή πληροφοριών σχήματος**.

### Βήμα 1: Φόρτωση Εγγράφου Word (load word document java)
Αρχικά, διαμορφώστε τις επιλογές φόρτωσης και δημιουργήστε μια παρουσία `Watermarker`. Αυτό προετοιμάζει το έγγραφο για περαιτέρω επιθεώρηση.

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

> **Συμβουλή:** Κρατήστε την παρουσία `Watermarker` όσο πιο περιορισμένη γίνεται· το άμεσο κλείσιμο της ελευθερώνει τους εγγενείς πόρους και αποτρέπει διαρροές μνήμης.

### Βήμα 2: Εξαγωγή Πληροφοριών Σχήματος (extract images from shapes)
Τώρα θα εξάγουμε τις λεπτομέρειες κάθε σχήματος, συμπεριλαμβανομένων τυχόν ενσωματωμένων εικόνων. Ο κώδικας επαναλαμβάνει κάθε ενότητα και κάθε σχήμα, εκτυπώνοντας χρήσιμα μεταδεδομένα.

```java
import com.groupdocs.watermark.contents.WordProcessingContent;

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

            // If the shape contains an image, output its details
            if (shape.getImage() != null) {
                System.out.println(shape.getImage().getWidth());
                System.out.println(shape.getImage().getHeight());
                System.out.println(shape.getImage().getBytes().length);
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

**Τι κάνει αυτός ο κώδικας:**  
- Ανακτά το **τύπο** κάθε σχήματος (π.χ., εικόνα, WordArt).  
- Εκτυπώνει τις τιμές **μεγέθους**, **θέσης** και **περιστροφής**.  
- Εμφανίζει το **εναλλακτικό κείμενο** και το **όνομα**, που είναι χρήσιμα για ελέγχους προσβασιμότητας.  
- Εάν το σχήμα περιέχει εικόνα, εκτυπώνει τις **διαστάσεις pixel** και το **μέγεθος σε bytes** της εικόνας—ιδανικό για εξαγωγή εικόνων από σχήματα.  

### Συνηθισμένα Προβλήματα & Πώς να Τα Διορθώσετε
| Πρόβλημα | Αιτία | Λύση |
|----------|-------|------|
| `FileNotFoundException` | Λάθος διαδρομή αρχείου ή έλλειψη δικαιωμάτων | Επαληθεύστε την απόλυτη/σχετική διαδρομή και βεβαιωθείτε ότι το αρχείο είναι αναγνώσιμο. |
| Null `shape.getImage()` | Το σχήμα δεν είναι εικόνα (π.χ., auto‑shape) | Χρησιμοποιήστε έλεγχο `if (shape.getImage() != null)` όπως φαίνεται. |
| Υψηλή χρήση μνήμης σε μεγάλα έγγραφα | Φόρτωση ολόκληρου του εγγράφου ταυτόχρονα | Επεξεργαστείτε τις ενότητες μία τη φορά ή αυξήστε το heap της JVM (`-Xmx`). |
| Απουσία σχημάτων σε κεφαλίδα/υποσέλιδο | Μη έλεγχος `shape.getHeaderFooter()` | Το παράδειγμα ήδη καταγράφει όταν ένα σχήμα ανήκει σε κεφαλίδα/υποσέλιδο. |

## Πρακτικές Εφαρμογές
1. **Αυτοματοποιημένη Δημιουργία Αναφορών** – Εξαγωγή διαγραμμάτων και σχημάτων για ενσωμάτωση σε επόμενα PDF.  
2. **Έλεγχος Συμμόρφωσης** – Επαλήθευση ότι όλα τα σχήματα περιέχουν κατάλληλο εναλλακτικό κείμενο για προσβασιμότητα.  
3. **Μετανάστευση Περιεχομένου** – Εξαγωγή ενσωματωμένων εικόνων από παλιά αρχεία Word σε σύστημα διαχείρισης ψηφιακών πόρων.  

## Σκέψεις Απόδοσης
- **Απελευθέρωση πόρων**: Πάντα καλέστε `watermarker.close()` σε μπλοκ `finally` ή χρησιμοποιήστε try‑with‑resources αν τυλίγετε το API.  
- **Επεξεργασία κατά τμήματα**: Για έγγραφα άνω των 50 MB, εξετάστε την επεξεργασία κάθε ενότητας ξεχωριστά για να διατηρήσετε μικρό αποτύπωμα μνήμης.  
- **Ασφάλεια νήματος**: Οι παρουσίες `Watermarker` δεν είναι thread‑safe· δημιουργήστε μια νέα παρουσία ανά νήμα.  

## Συμπέρασμα
Τώρα γνωρίζετε **πώς να εξάγετε σχήματα** από έγγραφα Word χρησιμοποιώντας το GroupDocs.Watermark για Java, από τη φόρτωση του αρχείου μέχρι την ανάγνωση των μεταδεδομένων κάθε σχήματος και των ενσωματωμένων δεδομένων εικόνας. Αυτή η δυνατότητα ανοίγει δρόμους σε προχωρημένες αναλύσεις εγγράφων, αυτοματοποιημένες ροές περιεχομένου και έλεγχο προσβασιμότητας.

### Επόμενα Βήματα
- Πειραματιστείτε με την τροποποίηση ιδιοτήτων σχήματος (π.χ., αλλαγή μεγέθους ή θέσης).  
- Συνδυάστε αυτή την προσέγγιση με **GroupDocs.Parser** για εξαγωγή του περιβάλλοντος κειμένου.  
- Ενσωματώστε τη λογική εξαγωγής σε μια υπηρεσία REST για επεξεργασία κατ' απαίτηση.

## Ενότητα Συχνών Ερωτήσεων
**Q: Τι είναι το GroupDocs.Watermark για Java;**  
A: Είναι μια ολοκληρωμένη βιβλιοθήκη σχεδιασμένη για τη διαχείριση υδατογραφιών και περιεχομένου εγγράφων σε διάφορες μορφές, επιτρέποντας εργασίες όπως εξαγωγή σχημάτων, ανάκτηση εικόνων και επεξεργασία κειμένου.

**Q: Μπορώ να εξάγω εικόνες από σχήματα χωρίς άδεια;**  
A: Η δοκιμαστική έκδοση επιτρέπει την εξαγωγή, αλλά μια πλήρης άδεια αφαιρεί τους περιορισμούς χρήσης και επιτρέπει εμπορική ανάπτυξη.

**Q: Λειτουργεί αυτό με αρχεία `.doc` (δυαδικά);**  
A: Ναι, το API υποστηρίζει τόσο `.docx` όσο και παλαιότερες μορφές `.doc`.

**Q: Πώς διαχειρίζομαι έγγραφα με κωδικό πρόσβασης;**  
A: Παρέχετε τον κωδικό μέσω `WordProcessingLoadOptions.setPassword("yourPassword")` πριν δημιουργήσετε το `Watermarker`.

**Q: Υπάρχει τρόπος να εξάγω τα εξαγόμενα δεδομένα σχήματος σε JSON;**  
A: Μπορείτε να αντιστοιχίσετε τις εκτυπωμένες τιμές σε ένα POJO και να χρησιμοποιήσετε οποιαδήποτε βιβλιοθήκη JSON (π.χ., Jackson) για να σειριοποιήσετε τη συλλογή.

---

**Τελευταία Ενημέρωση:** 2026-02-05  
**Δοκιμάστηκε Με:** GroupDocs.Watermark 24.11 for Java  
**Συγγραφέας:** GroupDocs