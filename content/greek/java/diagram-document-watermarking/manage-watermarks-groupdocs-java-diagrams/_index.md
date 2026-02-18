---
date: '2026-02-18'
description: Μάθετε πώς να προσθέτετε υδατογράφημα και πώς να αφαιρείτε υδατογράφημα
  σε αρχεία διαγράμματος όπως .vsdx με το GroupDocs.Watermark για Java. Προστατέψτε
  την ακεραιότητα του εγγράφου με το groupdocs watermark java.
keywords:
- GroupDocs.Watermark Java
- manage watermarks in diagrams
- Java diagram document watermarking
title: Πώς να προσθέσετε υδατογράφημα σε διαγράμματα χρησιμοποιώντας το GroupDocs.Watermark
  για Java
type: docs
url: /el/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# Πώς να Προσθέσετε Υδατογράφημα σε Διαγράμματα χρησιμοποιώντας το GroupDocs.Watermark για Java

Η διαχείριση υδατογραφημάτων σε αρχεία διαγραμμάτων αποτελεί βασικό μέρος της προστασίας της πνευματικής ιδιοκτησίας και της διατήρησης των εγγράφων καθαρών για δημόσια διανομή. Σε αυτόν τον οδηγό θα μάθετε **πώς να προσθέσετε υδατογράφημα** σε ένα διάγραμμα Visio, καθώς και **πώς να αφαιρέσετε υδατογράφημα** όταν δεν χρειάζεται πλέον, όλα με τη βιβλιοθήκη **groupdocs watermark java**. Είτε δημιουργείτε μια επιχειρησιακή γραμμή επεξεργασίας εγγράφων είτε ένα γρήγορο βοηθητικό σενάριο, αυτά τα βήματα θα σας δώσουν πλήρη έλεγχο της υδατογράφησης διαγραμμάτων.

## Quick Answers
- **Ποια βιβλιοθήκη διαχειρίζεται υδατογραφήματα διαγραμμάτων σε Java;** GroupDocs.Watermark for Java.  
- **Μπορώ να προσθέσω και να αφαιρέσω υδατογραφήματα στην ίδια εκτέλεση;** Ναι – φορτώστε το διάγραμμα μία φορά και εφαρμόστε και τις δύο λειτουργίες προσθήκης και αφαίρεσης.  
- **Ποια μορφές αρχείων υποστηρίζονται;** Μορφές Visio όπως `.vsdx`, `.vdx`, καθώς και άλλους τύπους διαγραμμάτων.  
- **Χρειάζομαι άδεια;** Μια δοκιμαστική άδεια λειτουργεί για ανάπτυξη· απαιτείται πλήρης άδεια για παραγωγή.  
- **Ποια έκδοση Java απαιτείται;** JDK 8 ή νεότερη.

## Τι σημαίνει “πώς να προσθέσετε υδατογράφημα” στο πλαίσιο των διαγραμμάτων;
Η προσθήκη υδατογραφήματος σημαίνει ενσωμάτωση ενός ορατού ή αόρατου δείκτη—κειμένου, λογότυπου ή εικόνας—σε ένα αρχείο διαγράμματος. Αυτός ο δείκτης μετακινείται μαζί με το αρχείο, καθιστώντας εύκολο το να αποδείξετε την ιδιοκτησία ή να επισημάνετε εκδόσεις πρόχειρων.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark για Java;
* **Rich API** – Αναζήτηση, προσθήκη και διαγραφή τόσο κειμενικών όσο και εικόνων υδατογραφημάτων με λίγες γραμμές κώδικα.  
* **Cross‑format support** – Λειτουργεί με Visio (`.vsdx`, `.vdx`) και πολλούς άλλους τύπους διαγραμμάτων.  
* **Performance‑focused** – Φορτώνει μόνο τα τμήματα ενός διαγράμματος που χρειάζονται για λειτουργίες υδατογράφησης, διατηρώντας τη χρήση μνήμης χαμηλή.

## Prerequisites
1. **Java Development Kit (JDK) 8+** – Βεβαιωθείτε ότι η εντολή `java -version` εμφανίζει 1.8 ή νεότερη.  
2. **IDE** – IntelliJ IDEA, Eclipse ή οποιονδήποτε επεξεργαστή προτιμάτε.  
3. **GroupDocs.Watermark for Java** – Προσθέστε το στο έργο σας μέσω Maven ή άμεσης λήψης JAR.  

### Required Libraries and Dependencies
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

*Αν προτιμάτε να μην χρησιμοποιήσετε Maven, μπορείτε να κατεβάσετε το πιο πρόσφατο JAR από [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).*

### License Acquisition
- **Free Trial:** Δοκιμάστε όλες τις λειτουργίες χωρίς κλειδί άδειας.  
- **Temporary License:** Ζητήστε ένα κλειδί περιορισμένου χρόνου για αξιολόγηση.  
- **Full License:** Αγοράστε συνδρομή για απεριόριστη χρήση σε παραγωγή.

## Setting Up GroupDocs.Watermark for Java
1. **Add the library** στο έργο σας (Maven ή χειροκίνητο JAR).  
2. **Create a `Watermarker` instance** – αυτό το αντικείμενο είναι το σημείο εισόδου για τη φόρτωση διαγραμμάτων, την αναζήτηση, την προσθήκη και την αφαίρεση υδατογραφημάτων.

## Implementation Guide

### Loading a Diagram Document
Η φόρτωση είναι το πρώτο βήμα πριν μπορέσετε να **προσθέσετε υδατογράφημα** ή **αφαιρέσετε υδατογράφημα**. Ο παρακάτω κώδικας δείχνει πώς να ανοίξετε ένα αρχείο `.vsdx` με προσαρμοσμένες επιλογές φόρτωσης.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;

public class LoadDiagramDocument {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        DiagramLoadOptions loadOptions = new DiagramLoadOptions();
        
        Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
        watermarker.close();
    }
}
```

### Searching for Text Watermarks
Πριν προσθέσετε ένα νέο υδατογράφημα, ίσως θέλετε να επαληθεύσετε αν υπάρχει ήδη κειμενικό υδατογράφημα. Αυτό το απόσπασμα ψάχνει τη φράση “Company Name”.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchTextWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        Watermarker watermarker = new Watermarker(inputFilePath);

        DiagramContent content = watermarker.getContent(DiagramContent.class);
        
        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria);

        watermarker.close();
    }
}
```

### Searching for Image Watermarks
Αν χρειάζεται να εντοπίσετε ένα λογότυπο ή οποιαδήποτε εικόνα που χρησιμοποιήθηκε ως υδατογράφημα, χρησιμοποιήστε το `ImageDctHashSearchCriteria`. Αυτό είναι χρήσιμο όταν θέλετε να **αφαιρέσετε υδατογράφημα** που ταιριάζει με ένα γνωστό λογότυπο.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class SearchImageWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String imagePath = "YOUR_DOCUMENT_DIRECTORY/logo.png";
        
        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria(imagePath);
        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(imageSearchCriteria);

        watermarker.close();
    }
}
```

### Removing Watermarks
Μόλις εντοπίσετε τα υδατογραφήματα—κειμενικά, εικόνας ή και τα δύο—μπορείτε να τα αφαιρέσετε από το διάγραμμα. Το παρακάτω παράδειγμα δείχνει μια συνδυαστική λειτουργία αφαίρεσης.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.search.TextSearchCriteria;
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;
import com.groupdocs.watermark.search.PossibleWatermarkCollection;

public class RemoveWatermarks {
    public static void main(String[] args) throws Exception {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
        String outputFilePath = "YOUR_OUTPUT_DIRECTORY/updated_diagram.vsdx";

        Watermarker watermarker = new Watermarker(inputFilePath);
        DiagramContent content = watermarker.getContent(DiagramContent.class);

        TextSearchCriteria textSearchCriteria = new TextSearchCriteria("Company Name");
        ImageDctHashSearchCriteria imageSearchCriteria = new ImageDctHashSearchCriteria("YOUR_DOCUMENT_DIRECTORY/logo.png");

        PossibleWatermarkCollection possibleWatermarks = content.getPages().get_Item(0).search(textSearchCriteria.or(imageSearchCriteria));
        possibleWatermarks.clear();

        watermarker.save(outputFilePath);
        watermarker.close();
    }
}
```

## Practical Applications
1. **Enterprise Software Integration** – Ενσωματώστε τη διαχείριση υδατογραφημάτων στο ERP ή στην πλατφόρμα δημιουργίας εγγράφων σας για επιβολή branding.  
2. **Content Management Systems (CMS)** – Αυτόματη σάρωση των ανεβασμένων διαγραμμάτων για μη εξουσιοδοτημένα λογότυπα και αφαίρεσή τους.  
3. **Legal Document Handling** – Προσθέστε ένα κειμενικό υδατογράφημα “Confidential” κατά τις φάσεις πρόχειρων και αργότερα **αφαιρέστε υδατογράφημα** πριν την τελική υποβολή.

## Common Issues and Solutions
| Σύμπτωμα | Πιθανή Αιτία | Διόρθωση |
|---------|--------------|----------|
| Δεν βρέθηκαν υδατογραφήματα | Το κείμενο/εικόνα αναζήτησης δεν ταιριάζει ακριβώς | Χρησιμοποιήστε `or()` για να συνδυάσετε κριτήρια ή προσαρμόστε τις ρυθμίσεις ευαισθησίας σε πεζά/κεφαλαία. |
| `OutOfMemoryError` σε μεγάλα αρχεία | Το διάγραμμα φορτώθηκε πλήρως στη μνήμη | Χρησιμοποιήστε `DiagramLoadOptions.setLoadPages()` για να φορτώσετε μόνο τις απαραίτητες σελίδες. |
| Το αποθηκευμένο αρχείο είναι κατεστραμμένο | `watermarker.save()` κλήθηκε πριν την εκκαθάριση όλων των υδατογραφημάτων | Βεβαιωθείτε ότι το `possibleWatermarks.clear()` ολοκληρώνεται και ότι το `watermarker.close()` καλείται μετά την αποθήκευση. |

## Frequently Asked Questions

**Q: Μπορώ να αναζητήσω ταυτόχρονα κείμενο και εικόνες;**  
A: Ναι. Συνδυάστε `TextSearchCriteria` και `ImageDctHashSearchCriteria` με τη μέθοδο `or()`, όπως φαίνεται στο παράδειγμα αφαίρεσης.

**Q: Είναι δυνατόν να αφαιρέσετε υδατογραφήματα χωρίς να καταστρέψετε το διάγραμμα;**  
A: Απόλυτα. Η βιβλιοθήκη απομονώνει τα αντικείμενα υδατογραφημάτων, έτσι η κλήση του `clear()` αφαιρεί μόνο τα στρώματα υδατογραφημάτων ενώ διατηρεί το αρχικό περιεχόμενο του διαγράμματος.

**Q: Υποστηρίζει το GroupDocs.Watermark πολλαπλές μορφές διαγραμμάτων;**  
A: Ναι. Μορφές όπως `.vsdx`, `.vdx` και άλλα αρχεία συμβατά με Visio υποστηρίζονται πλήρως.

**Q: Πώς να διαχειριστώ μεγάλα όγκους εγγράφων αποδοτικά;**  
A: Υλοποιήστε βρόχους επεξεργασίας παρτίδων, επαναχρησιμοποιήστε μια ενιαία παρουσία `Watermarker` όπου είναι δυνατόν, και περιορίστε τη φόρτωση σελίδων με `DiagramLoadOptions`.

**Q: Υπάρχει τρόπος να αυτοματοποιήσετε την ανίχνευση υδατογραφημάτων σε pipeline CI/CD;**  
A: Μπορείτε να ενσωματώσετε τα παρεχόμενα αποσπάσματα Java στα σενάρια κατασκευής σας (π.χ., Maven ή Gradle) για να επαληθεύσετε ότι δεν υπάρχουν μη εξουσιοδοτημένα υδατογραφήματα πριν την κυκλοφορία των artefacts.

---

**Last Updated:** 2026-02-18  
**Tested With:** GroupDocs.Watermark 24.11 for Java  
**Author:** GroupDocs