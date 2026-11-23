---
date: '2026-09-16'
description: Μάθετε πώς να εμφανίζετε τις υποστηριζόμενες μορφές αρχείων με το GroupDocs.Watermark
  για Java, εξασφαλίζοντας συμβατότητα με δεκάδες τύπους εγγράφων.
keywords:
- groupdocs watermark java list
- list supported file formats
- java watermark library
lastmod: '2026-09-16'
og_description: Το GroupDocs.Watermark Java list σας επιτρέπει να ανακτήσετε γρήγορα
  κάθε τύπο αρχείου που μπορεί να υδατογραφήσει η βιβλιοθήκη. Αυτός ο οδηγός παρουσιάζει
  τη ρύθμιση, αποσπάσματα κώδικα και πραγματικές περιπτώσεις χρήσης.
og_image_alt: Screenshot of GroupDocs.Watermark Java listing supported formats in
  an IDE
og_title: 'GroupDocs.Watermark Java list: οδηγός για τις υποστηριζόμενες μορφές αρχείων'
schemas:
- author: GroupDocs
  dateModified: '2026-09-16'
  description: Learn how to list supported file formats with GroupDocs.Watermark for
    Java, ensuring compatibility across dozens of document types.
  headline: 'GroupDocs.Watermark Java list: supported file formats'
  type: TechArticle
- questions:
  - answer: Over 50 formats, including PDF, DOCX, PPTX, JPEG, PNG, TIFF, BMP, and
      many more.
    question: What file formats does GroupDocs.Watermark support?
  - answer: Verify Maven dependencies, ensure you’re using JDK 8 or newer, and check
      that your license file is correctly referenced.
    question: How do I troubleshoot issues with GroupDocs.Watermark?
  - answer: Yes, a commercial license is required after the trial period expires.
    question: Can I use GroupDocs.Watermark for commercial projects?
  - answer: The operation itself is fast; performance problems usually stem from excessive
      console I/O. Log to a file instead.
    question: What should I do if my application slows down when listing formats?
  - answer: Check out the [GroupDocs GitHub repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
      for additional code samples.
    question: Where can I find more examples of using GroupDocs.Watermark?
  type: FAQPage
tags:
- groupdocs watermark
- java file formats
- document processing
- watermarking
- java tutorial
title: 'GroupDocs.Watermark Java list: υποστηριζόμενες μορφές αρχείων'
type: docs
url: /el/java/document-information/groupdocs-watermark-java-list-supported-formats/
weight: 1
---

# GroupDocs.Watermark Java λίστα: υποστηριζόμενες μορφές αρχείων

Η εργασία με πολλούς τύπους εγγράφων γίνεται απλή όταν μπορείτε προγραμματιστικά να ερωτήσετε ποιες μορφές υποστηρίζει μια βιβλιοθήκη. **groupdocs watermark java list** είναι η ακριβής μέθοδος που χρειάζεστε για να ανακαλύψετε κάθε τύπο αρχείου που μπορεί να διαχειριστεί το GroupDocs.Watermark, ώστε να δημιουργήσετε αξιόπιστες διαδικασίες υδατογράφησης χωρίς να μαντεύετε τη συμβατότητα των αρχείων.

## Εισαγωγή

Στα σύγχρονα ροές εργασίας εγγράφων συχνά χρειάζεται να εφαρμόζετε υδατογραφήματα σε PDF, εικόνες, αρχεία Office και άλλα. Η χειροκίνητη διατήρηση μιας σκληρά κωδικοποιημένης λίστας υποστηριζόμενων επεκτάσεων είναι επιρρεπής σε σφάλματα και δύσκολη στη συντήρηση. Χρησιμοποιώντας τη δυνατότητα *groupdocs watermark java list* μπορείτε να ανακτήσετε το πλήρες σύνολο μορφών κατά το χρόνο εκτέλεσης, εξασφαλίζοντας ότι η εφαρμογή σας επεξεργάζεται μόνο αρχεία που η βιβλιοθήκη υποστηρίζει πραγματικά.

Παρακάτω θα μάθετε πώς να:

* Προσθέσετε το GroupDocs.Watermark για Java σε ένα έργο Maven  
* Αρχικοποιήσετε τη βιβλιοθήκη και να λάβετε τη λίστα των υποστηριζόμενων μορφών  
* Εκτυπώσετε ή καταγράψετε τα ονόματα μορφών για εντοπισμό σφαλμάτων ή σκοπούς UI  

## Γρήγορες απαντήσεις
- **Τι κάνει το “groupdocs watermark java list”;** Επιστρέφει κάθε τύπο αρχείου που μπορεί να υδατογραφήσει η βιβλιοθήκη, ως αντικείμενα `FileType`.  
- **Χρειάζεται άδεια για την εμφάνιση των μορφών;** Όχι, το ερώτημα λειτουργεί σε λειτουργία δοκιμής· άδεια απαιτείται μόνο για πραγματική υδατογράφηση.  
- **Ποια έκδοση Java απαιτείται;** JDK 8 ή νεότερη.  
- **Μπορώ να φιλτράρω τη λίστα μόνο για μορφές εικόνας;** Ναι, ελέγχοντας την τιμή `getExtension()` του κάθε `FileType`.  
- **Η λίστα είναι στατική ή αλλάζει με νέες εκδόσεις;** Ενημερώνεται αυτόματα όταν αναβαθμίζετε τη βιβλιοθήκη.

## Τι είναι το groupdocs watermark java list;
Η λειτουργία **groupdocs watermark java list** επιστρέφει έναν πίνακα αντικειμένων `FileType` που αντιπροσωπεύουν κάθε μορφή εγγράφου που μπορεί να επεξεργαστεί η βιβλιοθήκη. Αυτό το δυναμικό ερώτημα εξαλείφει τις σκληρά κωδικοποιημένες υποθέσεις και διατηρεί τον κώδικά σας μελλοντικά ασφαλή.

## Γιατί να χρησιμοποιήσετε την ενσωματωμένη λίστα μορφών;
Το GroupDocs.Watermark υποστηρίζει **πάνω από 50 μορφές εισόδου και εξόδου**—συμπεριλαμβανομένων PDF, DOCX, PPTX, JPEG, PNG και TIFF—και μπορεί να διαχειριστεί αρχεία με εκατοντάδες σελίδες χωρίς να φορτώνει ολόκληρο το έγγραφο στη μνήμη. Η χρήση της ενσωματωμένης λίστας εξασφαλίζει ότι προσπαθείτε να υδατογραφήσετε μόνο σε υποστηριζόμενους τύπους, μειώνοντας τα σφάλματα χρόνου εκτέλεσης έως και 30 % σε μεγάλες παρτίδες εργασιών.

## Προαπαιτούμενα

- **Απαιτούμενες βιβλιοθήκες**: GroupDocs.Watermark for Java ≥ 24.11.  
- **Περιβάλλον ανάπτυξης**: JDK 8 ή νεότερο, Maven 3.x.  
- **Βασικές γνώσεις**: Εξοικείωση με τη σύνταξη Java και τη διαχείριση εξαρτήσεων Maven.

## Ρύθμιση GroupDocs.Watermark για Java

### Εγκατάσταση μέσω Maven

Προσθέστε το αποθετήριο και την εξάρτηση στο αρχείο `pom.xml`:

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

### Άμεση λήψη

Εναλλακτικά, κατεβάστε την πιο πρόσφατη έκδοση του GroupDocs.Watermark για Java από [GroupDocs releases](https://releases.groupdocs.com/watermark/java/).

#### Απόκτηση άδειας

Για χρήση του GroupDocs.Watermark σε παραγωγή, αποκτήστε άδεια. Μπορείτε να ξεκινήσετε με δωρεάν δοκιμή ή να ζητήσετε προσωρινή άδεια.

### Αρχικοποίηση και ρύθμιση

Αφού προσθέσετε την εξάρτηση ή κατεβάσετε το JAR, αρχικοποιήστε τη βιβλιοθήκη στο έργο Java:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.common.FileType;

public class WatermarkExample {
    public static void main(String[] args) {
        // Initialize a watermarker object for demonstration purposes
        Watermarker watermarker = new Watermarker("path/to/your/file");
        
        // Your code to list supported file formats will go here

        watermarker.close();
    }
}
```

## Πώς να εμφανίσετε τη λίστα υποστηριζόμενων μορφών αρχείων χρησιμοποιώντας το GroupDocs.Watermark για Java;

Φορτώστε τη βιβλιοθήκη και καλέστε τη μέθοδο `FileType.getSupportedFileTypes()` – αυτή επιστρέφει αμέσως έναν πίνακα με όλες τις μορφές που μπορεί να υδατογραφήσει το SDK. Δεν απαιτείται πρόσθετη διαμόρφωση και η κλήση ολοκληρώνεται σε λιγότερο από ένα χιλιοστό του δευτερολέπτου σε τυπικό υλικό, καθιστώντας την ασφαλή για εκτέλεση κατά την εκκίνηση της εφαρμογής ή «on‑the‑fly».

### Βήμα 1: ανάκτηση όλων των υποστηριζόμενων τύπων αρχείων

Η κλάση `FileType` αντιπροσωπεύει κάθε υποστηριζόμενη μορφή εγγράφου. Χρησιμοποιήστε τη στατική της μέθοδο για να λάβετε τη πλήρη συλλογή:

```java
// STEP 1: Retrieve all supported file types from the GroupDocs library
FileType[] fileTypes = FileType.getSupportedFileTypes();
```

### Βήμα 2: επανάληψη και εκτύπωση ονομάτων τύπων αρχείων

Περιηγηθείτε στον επιστρεφόμενο πίνακα και εμφανίστε το όνομα εμφάνισης ή την επέκταση κάθε μορφής:

```java
// STEP 2: Iterate over each file type and print its name
for (FileType fileType : fileTypes) {
    System.out.println(fileType);
}
```

## Συμβουλές αντιμετώπισης προβλημάτων

- **Κοινά ζητήματα**: Βεβαιωθείτε ότι οι εξαρτήσεις Maven ταιριάζουν ακριβώς με την έκδοση του GroupDocs.Watermark που εγκαταστήσατε. Μη ταιριαστές εκδόσεις συχνά προκαλούν `ClassNotFoundException`.  
- **Συμβουλή απόδοσης**: Όταν επεξεργάζεστε χιλιάδες αρχεία, καταγράψτε τη λίστα μορφών σε αρχείο αντί για εκτύπωση στην κονσόλα, ώστε να αποφύγετε το «bottleneck» I/O.

## Πρακτικές εφαρμογές

Η γνώση του ακριβούς συνόλου μορφών επιτρέπει διάφορα πραγματικά σενάρια:

1. **Συστήματα διαχείρισης εγγράφων** – εφαρμόζετε αυτόματα υδατογραφήματα μόνο σε υποστηριζόμενους τύπους αρχείων, αποτρέποντας αποτυχίες εργασιών.  
2. **Πλατφόρμες δημοσίευσης περιεχομένου** – προστατεύετε PDF, εικόνες και έγγραφα Office πριν παραδοθούν στους τελικούς χρήστες.  
3. **Διαχείριση νομικών εγγράφων** – διασφαλίζετε ότι εμπιστευτικές συμβάσεις υδατογραφούνται σε όλες τις εγκεκριμένες μορφές, μειώνοντας τον κίνδυνο διαρροής.

## Σκέψεις για την απόδοση

- **Χρήση πόρων**: Η λειτουργία λίστας μορφών είναι ελαφριά· δεν φορτώνει δεδομένα εγγράφου στη μνήμη.  
- **Καλές πρακτικές διαχείρισης μνήμης Java**: Αποδεσμεύετε άμεσα τις παρουσίες `Watermarker` μετά τη χρήση για να ελευθερώσετε εγγενείς πόρους.

## Συμπέρασμα

Τώρα διαθέτετε μια πλήρη, έτοιμη για παραγωγή μέθοδο εκτέλεσης της λειτουργίας **groupdocs watermark java list**. Ενσωματώνοντας αυτό το ερώτημα στη διαδικασία εκκίνησης ή στην κονσόλα διαχείρισης, εξασφαλίζετε ότι μόνο συμβατά αρχεία επεξεργάζονται, βελτιώνοντας την αξιοπιστία και μειώνοντας τα αιτήματα υποστήριξης.

### Επόμενα βήματα

Εξερευνήστε πρόσθετες δυνατότητες του GroupDocs.Watermark όπως η προσθήκη κειμένου ή εικόνας υδατογραφήματος, η διαμόρφωση διαφάνειας και η εφαρμογή ρυθμίσεων ανά σελίδα. Ο ίδιος κώδικας αρχικοποίησης που χρησιμοποιήσατε για την εμφάνιση μορφών ισχύει για όλες τις άλλες εργασίες υδατογράφησης.

## Συχνές ερωτήσεις

**Ε: Ποιες μορφές αρχείων υποστηρίζει το GroupDocs.Watermark;**  
Α: Πάνω από 50 μορφές, συμπεριλαμβανομένων PDF, DOCX, PPTX, JPEG, PNG, TIFF, BMP και πολλές άλλες.

**Ε: Πώς αντιμετωπίζω προβλήματα με το GroupDocs.Watermark;**  
Α: Επαληθεύστε τις εξαρτήσεις Maven, βεβαιωθείτε ότι χρησιμοποιείτε JDK 8 ή νεότερο και ελέγξτε ότι το αρχείο άδειας αναφέρεται σωστά.

**Ε: Μπορώ να χρησιμοποιήσω το GroupDocs.Watermark για εμπορικά έργα;**  
Α: Ναι, απαιτείται εμπορική άδεια μετά τη λήξη της δοκιμαστικής περιόδου.

**Ε: Τι πρέπει να κάνω αν η εφαρμογή μου επιβραδύνεται κατά την εμφάνιση των μορφών;**  
Α: Η λειτουργία αυτή είναι γρήγορη· τα προβλήματα απόδοσης συνήθως προέρχονται από υπερβολική έξοδο στην κονσόλα. Καταγράψτε σε αρχείο αντί για εκτύπωση.

**Ε: Πού μπορώ να βρω περισσότερα παραδείγματα χρήσης του GroupDocs.Watermark;**  
Α: Δείτε το [GroupDocs GitHub repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java) για επιπλέον δείγματα κώδικα.

## Πόροι

- **Τεκμηρίωση**: [GroupDocs Watermark Java Docs](https://docs.groupdocs.com/watermark/java/)  
- **Αναφορά API**: [GroupDocs API Reference](https://reference.groupdocs.com/watermark/java)  
- **Λήψη**: [Latest Release](https://releases.groupdocs.com/watermark/java/)  
- **GitHub**: [GroupDocs.Watermark Java GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Δωρεάν υποστήριξη**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Προσωρινή άδεια**: [Purchase Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**Τελευταία ενημέρωση:** 2026-09-16  
**Δοκιμασμένο με:** GroupDocs.Watermark for Java 24.11  
**Συγγραφέας:** GroupDocs

## Σχετικά μαθήματα

- [Document Loading and Saving Operations with GroupDocs.Watermark for Java](/watermark/java/document-loading-saving/)  
- [Extract Document Information Using GroupDocs.Watermark for Java: A Complete Guide](/watermark/java/document-information/extract-document-info-groupdocs-watermark-java/)  
- [Generate Document Previews Using GroupDocs.Watermark in Java - Advanced Guide](/watermark/java/advanced-features/groupdocs-watermark-java-document-previews/)