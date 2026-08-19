---
date: '2026-08-19'
description: Μάθετε πώς να προστατεύετε διαγράμματα πνευματικής ιδιοκτησίας χρησιμοποιώντας
  το GroupDocs.Watermark για Java. Οδηγός βήμα‑βήμα για τη load, detect image watermark,
  search και remove watermarks από αρχεία .vsdx.
keywords:
- intellectual property diagrams
- detect image watermark
- GroupDocs.Watermark Java
- diagram watermark management
- Java watermark API
lastmod: '2026-08-19'
og_description: Ανακαλύψτε πώς να προστατεύετε διαγράμματα πνευματικής ιδιοκτησίας
  χρησιμοποιώντας το GroupDocs.Watermark για Java. Μάθετε να load αρχεία .vsdx, detect
  image watermark και remove unwanted watermarks efficiently.
og_image_alt: Java code snippet showing watermark detection in diagram files
og_title: Προστασία διαγραμμάτων πνευματικής ιδιοκτησίας με GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to protect intellectual property diagrams using GroupDocs.Watermark
    for Java. Step‑by‑step guide to load, detect image watermark, search and remove
    watermarks from .vsdx files.
  headline: Protect intellectual property diagrams with GroupDocs.Watermark
  type: TechArticle
- description: Learn how to protect intellectual property diagrams using GroupDocs.Watermark
    for Java. Step‑by‑step guide to load, detect image watermark, search and remove
    watermarks from .vsdx files.
  name: Protect intellectual property diagrams with GroupDocs.Watermark
  steps:
  - name: '**Java Development Kit (JDK) 8+** – the code uses standard Java 8 APIs.'
    text: '**Java Development Kit (JDK) 8+** – the code uses standard Java 8 APIs.'
  - name: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
    text: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
  - name: '**GroupDocs.Watermark for Java** – either via Maven or a manual JAR download.'
    text: '**GroupDocs.Watermark for Java** – either via Maven or a manual JAR download.'
  type: HowTo
- questions:
  - answer: Yes, combine criteria with `OrSearchCriteria` (e.g., `new OrSearchCriteria(textCriteria,
      imageCriteria)`) to retrieve both types at once.
    question: Can I search for both text and image watermarks in a single call?
  - answer: No. The library isolates watermark objects, so shapes, connectors, and
      formatting remain unchanged after `clear()`.
    question: Will removing watermarks corrupt the diagram layout?
  - answer: GroupDocs.Watermark handles `.vsdx`, `.vdx`, `.vsx`, and several older
      Visio formats, covering over **30** diagram types.
    question: Which diagram formats are supported?
  - answer: Use Java’s `ExecutorService` to run watermark detection/removal in parallel
      batches, and reuse a single `Watermarker` configuration object to reduce overhead.
    question: How do I process thousands of diagrams efficiently?
  - answer: Absolutely. Add the Java snippets to your build scripts (Maven/Gradle)
      and run them as a pre‑deployment verification step to ensure no prohibited watermarks
      are present.
    question: Is it possible to integrate this into a CI/CD pipeline?
  type: FAQPage
tags:
- watermark diagrams
- GroupDocs.Watermark
- Java document processing
- intellectual property protection
title: Προστασία διαγραμμάτων πνευματικής ιδιοκτησίας με GroupDocs.Watermark
type: docs
url: /el/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# Προστασία διαγραμμάτων πνευματικής ιδιοκτησίας με το GroupDocs.Watermark

Η προστασία διαγραμμάτων πνευματικής ιδιοκτησίας είναι ένα κρίσιμο βήμα για κάθε οργανισμό που μοιράζεται περιουσιακά στοιχεία σχεδίασης, διαγράμματα ροής ή αρχιτεκτονικά σχέδια. Με το GroupDocs.Watermark για Java μπορείτε προγραμματιστικά να φορτώσετε αρχεία διαγράμματος (όπως `.vsdx`), να εντοπίσετε περιπτώσεις υδατογραφημάτων εικόνας, να αναζητήσετε υδατογραφήματα κειμένου και να τα αφαιρέσετε με ασφάλεια χωρίς να καταστρέψετε το αρχικό σχέδιο. Αυτό το σεμινάριο σας καθοδηγεί σε όλη τη διαδικασία—από τη ρύθμιση του περιβάλλοντος μέχρι την επεξεργασία μεγάλων βιβλιοθηκών διαγραμμάτων σε παρτίδες—ώστε να ενσωματώσετε αξιόπιστη προστασία IP απευθείας στις εφαρμογές Java.

## Γρήγορες απαντήσεις
- **Ποια βιβλιοθήκη διαχειρίζεται τα υδατογραφήματα διαγραμμάτων;** GroupDocs.Watermark για Java.  
- **Μπορώ να εντοπίσω υδατογράφημα εικόνας καθώς και κειμένου;** Ναι, το API παρέχει `ImageDctHashSearchCriteria` για εντοπισμό εικόνας και `TextSearchCriteria` για κείμενο.  
- **Χρειάζομαι εμπορική άδεια για την εκτέλεση του κώδικα;** Μια δοκιμαστική άδεια λειτουργεί για ανάπτυξη· απαιτείται πληρωμένη άδεια για παραγωγή.  
- **Υποστηρίζεται η επεξεργασία σε παρτίδες;** Απόλυτα—επαναλάβετε τη διαδικασία σε έναν φάκελο και εφαρμόστε την ίδια λογική υδατογραφημάτων σε κάθε αρχείο.  
- **Θα παραμείνει αμετάβλητη η αρχική διάταξη του διαγράμματος μετά την αφαίρεση;** Η βιβλιοθήκη διαγράφει μόνο τα αντικείμενα υδατογραφημάτων, διατηρώντας όλα τα σχήματα, συνδέσμους και μορφοποίηση.

## Τι είναι τα διαγράμματα πνευματικής ιδιοκτησίας;
Τα διαγράμματα πνευματικής ιδιοκτησίας είναι οπτικές αναπαραστάσεις—όπως διαγράμματα ροής, μοντέλα UML, σχήματα δικτύων ή αρχιτεκτονικά σχέδια—που περιέχουν ιδιόκτητες πληροφορίες που ανήκουν σε άτομο ή οργανισμό. Αυτά τα διαγράμματα συχνά μεταφέρουν εμπιστευτικές διαδικασίες, σχέδια ή στρατηγικές, καθιστώντας τα πολύτιμα περιουσιακά στοιχεία που απαιτούν προστασία έναντι μη εξουσιοδοτημένων αντιγραφών, διανομής ή τροποποίησης. Θεωρώντας τα ως πνευματική ιδιοκτησία, μπορείτε να εφαρμόσετε νομικές και τεχνικές προστασίες, συμπεριλαμβανομένου του υδατογραφημένου, για να διατηρήσετε τον έλεγχο της χρήσης και διάδοσής τους.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark για Java;
Το GroupDocs.Watermark υποστηρίζει **50+ μορφές εισόδου και εξόδου** (συμπεριλαμβανομένων `.vsdx`, `.vdx`, `.vsx`) και μπορεί να επεξεργαστεί διαγράμματα εκατοντάδων σελίδων χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη, μειώνοντας την κατανάλωση RAM έως **70 %** σε σύγκριση με απλές προσεγγίσεις ροής αρχείου. Το API προσφέρει επίσης ενσωματωμένη σύγκριση εικόνας‑hash χωρίς OCR, επιτρέποντας αξιόπιστες λειτουργίες `detect image watermark` σε λιγότερο από **200 ms** ανά διάγραμμα σε έναν τυπικό διακομιστή 2.5 GHz.

## Προαπαιτούμενα
1. **Java Development Kit (JDK) 8+** – ο κώδικας χρησιμοποιεί τυπικά API Java 8.  
2. **IDE** – IntelliJ IDEA, Eclipse ή οποιοσδήποτε επεξεργαστής προτιμάτε.  
3. **GroupDocs.Watermark για Java** – είτε μέσω Maven είτε με χειροκίνητη λήψη JAR.  

### Απαιτούμενες βιβλιοθήκες και εξαρτήσεις
Μπορείτε να προσθέσετε τη βιβλιοθήκη μέσω Maven ή να κατεβάσετε τα JAR απευθείας.

#### Ρύθμιση Maven
Προσθέστε τις εγγραφές αποθετηρίου και εξάρτησης στο αρχείο `pom.xml` σας:

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

#### Άμεση λήψη
Αν προτιμάτε χειροκίνητη εγκατάσταση, κατεβάστε την τελευταία έκδοση από [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Απόκτηση άδειας
- **Δωρεάν δοκιμή:** Ιδανική για αξιολόγηση των δυνατοτήτων του API.  
- **Προσωρινή άδεια:** Χρησιμοποιήστε για βραχυπρόθεσμο testing χωρίς περιορισμούς λειτουργιών.  
- **Αγορά:** Απαιτείται για παραγωγικές εγκαταστάσεις και για ξεκλείδωμα premium μορφών.

## Πώς να αρχικοποιήσετε το Watermarker;
Η δημιουργία ενός αντικειμένου `Watermarker` είναι το πρώτο βήμα σε οποιαδήποτε ροή εργασίας υδατογραφημάτων. Η κλάση `Watermarker` φορτώνει ένα αρχείο διαγράμματος στη μνήμη και παρέχει μεθόδους για αναζήτηση, προσθήκη και αφαίρεση υδατογραφημάτων. Με τη διόρθωση της διαδρομής του διαγράμματος και προαιρετικά `DiagramLoadOptions`, λαμβάνετε ένα αντικείμενο που λειτουργεί ως κεντρικό σημείο για όλες τις επόμενες λειτουργίες, εξασφαλίζοντας συνεπή διαχείριση του εγγράφου καθ' όλη τη διαδικασία.

```java
Watermarker watermarker = new Watermarker(inputFilePath, loadOptions);
```

## Πώς να φορτώσετε ένα έγγραφο διαγράμματος;
Η φόρτωση ενός διαγράμματος με `DiagramLoadOptions` σας δίνει λεπτομερή έλεγχο του τρόπου ανάλυσης του αρχείου. Το `DiagramLoadOptions` επιτρέπει να καθορίσετε αν θα φορτωθούν μόνο οι ορατές σελίδες, αν θα διατηρηθούν κρυφά στρώματα και πώς θα διαχειριστούν οι ενσωματωμένες γραμματοσειρές. Η ρύθμιση αυτών των επιλογών μπορεί να βελτιώσει δραστικά την απόδοση για μεγάλα διαγράμματα και εξασφαλίζει ότι μόνο τα απαραίτητα τμήματα του αρχείου θα υποβληθούν σε επεξεργασία, μειώνοντας τη χρήση μνήμης και επιταχύνοντας τον εντοπισμό υδατογραφημάτων.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
loadOptions.setLoadHiddenLayers(false);
Watermarker watermarker = new Watermarker("sample.vsdx", loadOptions);
```

## Πώς να εντοπίσετε υδατογράφημα εικόνας σε ένα διάγραμμα;
Η ανίχνευση υδατογραφημάτων εικόνας βασίζεται στην κλάση `ImageDctHashSearchCriteria`, η οποία υπολογίζει ένα αντιληπτικό hash μιας εικόνας αναφοράς και το συγκρίνει με κάθε ενσωματωμένη εικόνα στο διάγραμμα. Αυτή η μέθοδος είναι γρήγορη και ανεκτική σε μικρές οπτικές διαφορές, επιτρέποντας τον εντοπισμό λογοτύπων ή άλλων γραφικών υδατογραφημάτων ακόμη και αν έχουν αλλάξει το μέγεθος ή τροποποιηθεί ελαφρώς. Ρυθμίζοντας το όριο ομοιότητας, μπορείτε να ισορροπήσετε την ευαισθησία εντοπισμού με τα ψευδώς θετικά αποτελέσματα.

```java
ImageDctHashSearchCriteria criteria = new ImageDctHashSearchCriteria("logo.png");
PossibleWatermarkCollection watermarks = watermarker.search(criteria);
```

## Πώς να αναζητήσετε υδατογραφήματα κειμένου;
Η αναζήτηση υδατογραφημάτων κειμένου χρησιμοποιεί την κλάση `TextSearchCriteria`. Αυτή η κλάση σαρώει όλα τα κειμενικά στρώματα του διαγράμματος, συμπεριλαμβανομένων εκείνων μέσα σε σχήματα, συνδέσμους και ομάδες, και επιστρέφει τυχόν αντιστοιχίες που περιέχουν τη συγκεκριμένη συμβολοσειρά ή το μοτίβο. Η αναζήτηση είναι εξ ορισμού μη ευαίσθητη σε πεζά/κεφαλαία και μπορεί να βελτιωθεί με κανονικές εκφράσεις, επιτρέποντάς σας να εντοπίσετε υδατογραφήματα που μπορεί να είναι περιστρεφόμενα, μερικώς κρυμμένα ή ενσωματωμένα σε σύνθετες δομές διαγράμματος.

```java
TextSearchCriteria textCriteria = new TextSearchCriteria("Confidential");
PossibleWatermarkCollection textWatermarks = watermarker.search(textCriteria);
```

## Πώς να αφαιρέσετε υδατογραφήματα από ένα διάγραμμα;
Η αφαίρεση υδατογραφημάτων πραγματοποιείται καλώντας τη μέθοδο `clear()` σε κάθε αντικείμενο `Watermark` που επιστρέφεται από μια λειτουργία αναζήτησης. Η μέθοδος `clear()` διαγράφει μόνο τα οπτικά στοιχεία του υδατογραφήματος, αφήνοντας ανέπαφα τα υποκείμενα αντικείμενα του διαγράμματος—όπως σχήματα, συνδέσμους και μορφοποίηση. Μετά τον καθαρισμό, αποθηκεύετε το έγγραφο χρησιμοποιώντας τη μέθοδο `save`, παράγοντας μια καθαρή έκδοση του διαγράμματος που διατηρεί την αρχική του διάταξη και λειτουργικότητα.

```java
for (Watermark wm : watermarks) {
    wm.clear();
}
watermarker.save("cleaned.vsdx");
```

## Πρακτικές εφαρμογές
- **Ενσωμάτωση λογισμικού επιχείρησης:** Ενσωματώστε την επικύρωση υδατογραφημάτων σε συστήματα διαχείρισης εγγράφων για αυτόματη επιβολή πολιτικών IP.  
- **Συστήματα διαχείρισης περιεχομένου (CMS):** Σαρώστε διαγράμματα που ανεβάζουν χρήστες για μη εξουσιοδοτημένα λογότυπα πριν από τη δημοσίευση.  
- **Διαχείριση νομικών εγγράφων:** Εντοπίστε και αφαιρέστε εμπιστευτικά υδατογραφήματα κατά την προετοιμασία πακέτων αποδεικτικών στοιχείων.  

## Συχνά προβλήματα και αντιμετώπιση
- **Εξαίρεση έλλειψης άδειας:** Βεβαιωθείτε ότι το αρχείο δοκιμαστικής ή πληρωμένης άδειας έχει αναφερθεί σωστά μέσω `License.setLicense("license_path")`.  
- **Μείωση ταχύτητας σε μεγάλα διαγράμματα:** Ενεργοποιήστε `loadOptions.setLoadHiddenLayers(false)` και εξετάστε την επεξεργασία διαγραμμάτων σε παράλληλα streams.  
- **Ψευδώς θετικά αποτελέσματα εικόνας:** Ρυθμίστε την ανοχή του DCT hash με `criteria.setSimilarityThreshold(0.85)` για μείωση τυχαίων αντιστοιχίσεων.  

## Συχνές ερωτήσεις

**Ε: Μπορώ να αναζητήσω τόσο κείμενο όσο και υδατογράφημα εικόνας με μία κλήση;**  
Α: Ναι, συνδυάστε κριτήρια με `OrSearchCriteria` (π.χ., `new OrSearchCriteria(textCriteria, imageCriteria)`) για να λάβετε και τους δύο τύπους ταυτόχρονα.

**Ε: Θα καταστρέψει η αφαίρεση των υδατογραφημάτων τη διάταξη του διαγράμματος;**  
Α: Όχι. Η βιβλιοθήκη απομονώνει τα αντικείμενα υδατογραφημάτων, έτσι σχήματα, συνδέσμοι και μορφοποίηση παραμένουν αμετάβλητα μετά το `clear()`.

**Ε: Ποιες μορφές διαγραμμάτων υποστηρίζονται;**  
Α: Το GroupDocs.Watermark διαχειρίζεται `.vsdx`, `.vdx`, `.vsx` και αρκετές παλαιότερες μορφές Visio, καλύπτοντας πάνω από **30** τύπους διαγραμμάτων.

**Ε: Πώς μπορώ να επεξεργαστώ χιλιάδες διαγράμματα αποδοτικά;**  
Α: Χρησιμοποιήστε το `ExecutorService` της Java για να εκτελέσετε τον εντοπισμό/αφαίρεση υδατογραφημάτων σε παράλληλες παρτίδες και επαναχρησιμοποιήστε ένα ενιαίο αντικείμενο ρύθμισης `Watermarker` για μείωση του κόστους.

**Ε: Είναι δυνατόν να ενσωματωθεί αυτό σε μια διαδικασία CI/CD;**  
Α: Απόλυτα. Προσθέστε τα αποσπάσματα Java στα σενάρια κατασκευής (Maven/Gradle) και εκτελέστε τα ως βήμα προ-ανάπτυξης για να διασφαλίσετε ότι δεν υπάρχουν απαγορευμένα υδατογραφήματα.

---

**Τελευταία ενημέρωση:** 2026-08-19  
**Δοκιμασμένο με:** GroupDocs.Watermark 23.12 για Java  
**Συγγραφέας:** GroupDocs

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

## Σχετικά Μαθήματα

- [Οδηγός προσθήκης υδατογραφημάτων σε διαγράμματα χρησιμοποιώντας το GroupDocs.Watermark για Java](/watermark/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/)
- [Προσθήκη υδατογραφημάτων κειμένου σε διαγράμματα χρησιμοποιώντας το GroupDocs.Watermark για Java&#58; Ένας ολοκληρωμένος οδηγός](/watermark/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/)
- [Επεξεργασία κεφαλίδων & υποσέλιδων διαγράμματος σε Java χρησιμοποιώντας το GroupDocs.Watermark&#58; Ένας ολοκληρωμένος οδηγός](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)