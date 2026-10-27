---
date: '2026-10-27'
description: Μάθετε πώς να διαγράψετε υδατογράφημα κειμένου από αρχεία διαγραμμάτων
  χρησιμοποιώντας το GroupDocs.Watermark for Java και να ανιχνεύσετε αποτελεσματικά
  υδατογράφημα εικόνας. Οδηγός βήμα‑βήμα για προγραμματιστές.
keywords:
- delete text watermark
- detect image watermark
- GroupDocs.Watermark Java
lastmod: '2026-10-27'
og_description: Διαγράψτε υδατογράφημα κειμένου από αρχεία διαγραμμάτων με το GroupDocs.Watermark
  for Java. Μάθετε να ανιχνεύετε υδατογράφημα εικόνας, να κάνετε search και να αφαιρείτε
  υδατογραφήματα με code snippets.
og_image_alt: Diagram file with watermark management using GroupDocs.Watermark for
  Java
og_title: Διαγραφή υδατογραφήματος κειμένου σε αρχεία διαγραμμάτων με Java γρήγορα
schemas:
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to delete text watermark from diagram files using GroupDocs.Watermark
    for Java and detect image watermark efficiently. Step‑by‑step guide for developers.
  headline: How to delete text watermark in diagrams with Java
  type: TechArticle
- description: Learn how to delete text watermark from diagram files using GroupDocs.Watermark
    for Java and detect image watermark efficiently. Step‑by‑step guide for developers.
  name: How to delete text watermark in diagrams with Java
  steps:
  - name: '**Java Development Kit (JDK)** 8 or higher.'
    text: '**Java Development Kit (JDK)** 8 or higher.'
  - name: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
    text: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
  - name: '**GroupDocs.Watermark for Java** – the library JAR(s) must be on your classpath.'
    text: '**GroupDocs.Watermark for Java** – the library JAR(s) must be on your classpath.'
  - name: '**Install the library** – ensure the Maven repository and dependency entries
      are present, or place the JAR files in `libs/` and add them to your project’s
      build path.'
    text: '**Install the library** – ensure the Maven repository and dependency entries
      are present, or place the JAR files in `libs/` and add them to your project’s
      build path.'
  - name: '**Initialize the API** – create a `Watermarker` instance; this object is
      the entry point for loading diagrams and performing watermark operations.'
    text: '**Initialize the API** – create a `Watermarker` instance; this object is
      the entry point for loading diagrams and performing watermark operations.'
  - name: '**Enterprise software integration** – embed watermark management into document‑centric
      business applications to protect proprietary diagrams.'
    text: '**Enterprise software integration** – embed watermark management into document‑centric
      business applications to protect proprietary diagrams.'
  - name: '**Content Management Systems (CMS)** – automate detection of unauthorized
      logos before publishing user‑generated diagrams.'
    text: '**Content Management Systems (CMS)** – automate detection of unauthorized
      logos before publishing user‑generated diagrams.'
  - name: '**Legal document handling** – add or delete watermarks at different stages
      of a case file workflow, ensuring compliance with confidentiality policies.'
    text: '**Legal document handling** – add or delete watermarks at different stages
      of a case file workflow, ensuring compliance with confidentiality policies.'
  type: HowTo
- questions:
  - answer: Yes – combine `TextSearchCriteria` and `ImageDctHashSearchCriteria` with
      the `or()` operator to locate both types in a single pass.
    question: Can I search for both text and images simultaneously?
  - answer: Absolutely. The API isolates watermark objects and removes them, leaving
      the original diagram structure intact.
    question: Is it possible to delete watermarks without damaging the diagram?
  - answer: Yes – it supports over 20 formats, including `.vsdx`, `.vdx`, `.drawio`,
      and `.svg`, enabling broad‑range diagram management.
    question: Does GroupDocs.Watermark support multiple diagram formats?
  - answer: Use batch processing loops, reuse a single `Watermarker` instance where
      possible, and tune `LoadOptions` to stream pages instead of loading whole files.
    question: How do I handle large volumes of documents efficiently?
  - answer: Yes – the library is headless and can be called from Maven, Gradle, or
      any build script to validate diagram assets automatically.
    question: Can I integrate watermark detection into a CI/CD pipeline?
  type: FAQPage
tags:
- watermark management
- GroupDocs.Watermark
- Java diagram processing
title: Πώς να διαγράψετε υδατογράφημα κειμένου σε διαγράμματα με Java
type: docs
url: /el/java/diagram-document-watermarking/manage-watermarks-groupdocs-java-diagrams/
weight: 1
---

# Πώς να διαγράψετε το κείμενο υδατογράφημα σε διαγράμματα με Java

Η διαχείριση των υδατογραφημάτων σε έγγραφα είναι απαραίτητη για την προστασία της πνευματικής ιδιοκτησίας και τη διατήρηση της ακεραιότητας των εγγράφων. Σε αυτό το εκπαιδευτικό υλικό θα μάθετε πώς να **διαγράψετε το κείμενο υδατογράφημα** από αρχεία διαγραμμάτων όπως `.vsdx` χρησιμοποιώντας το GroupDocs.Watermark για Java, καθώς και πώς να **ανιχνεύσετε υδατογράφημα εικόνας** όταν χρειάζεται. Είτε δημιουργείτε μια επιχειρησιακή γραμμή επεξεργασίας εγγράφων είτε αυτοματοποιείτε μια απλή εργασία batch, αυτές οι τεχνικές σας δίνουν λεπτομερή έλεγχο πάνω στα υδατογραφήματα διαγραμμάτων.

**Τι θα μάθετε**
- Ρύθμιση της βιβλιοθήκης GroupDocs.Watermark
- Φόρτωση εγγράφου διαγράμματος με συγκεκριμένες επιλογές
- Αναζήτηση και διαγραφή υδατογραφημάτων κειμένου
- Ανίχνευση υδατογραφημάτων εικόνας και αφαίρεσή τους
- Συμβουλές βέλτιστης πρακτικής για επεξεργασία μεγάλης κλίμακας

Έτοιμοι να ξεκινήσετε; Ας ετοιμάσουμε πρώτα το περιβάλλον σας.

## Γρήγορες απαντήσεις
- **Μπορώ να διαγράψω ταυτόχρονα υδατογραφήματα κειμένου και εικόνας;** Ναι – συνδυάστε `TextSearchCriteria` και `ImageDctHashSearchCriteria` με συνθήκη `or()`.  
- **Φορτώνει η βιβλιοθήκη ολόκληρο το διάγραμμα στη μνήμη;** Όχι – κάνει ροή των σελίδων, επιτρέποντας αρχεία έως 500 MB χωρίς πλήρη κατανάλωση μνήμης.  
- **Ποιες μορφές διαγράμματος υποστηρίζονται;** Πάνω από 20 μορφές, συμπεριλαμβανομένων `.vsdx`, `.vdx` και `.drawio`.  
- **Απαιτείται άδεια για παραγωγική χρήση;** Απαιτείται έγκυρη άδεια GroupDocs.Watermark για μη‑δοκιμαστική χρήση.  
- **Μπορώ να το εκτελέσω σε CI/CD pipeline;** Απόλυτα – το API είναι headless και λειτουργεί σε Windows, Linux και macOS.

## Τι είναι η διαγραφή κειμένου υδατογραφήματος;
Η διαγραφή κειμένου υδατογραφήματος σημαίνει την αφαίρεση αντικειμένων επικάλυψης βασισμένων σε κείμενο που προστέθηκαν σε ένα έγγραφο για να υποδείξουν ιδιοκτησία, εμπιστευτικότητα ή κατάσταση πρόχειρου. Στο GroupDocs.Watermark αυτή η λειτουργία εκτελείται εντοπίζοντας τα αντικείμενα υδατογραφήματος με κριτήρια αναζήτησης και στη συνέχεια καλώντας `clear()` στη συλλογή που προκύπτει.

## Γιατί να ανιχνεύσετε υδατογράφημα εικόνας;
Η ανίχνευση υδατογραφήματος εικόνας σας επιτρέπει να εντοπίσετε λογότυπα ή σφραγίδες που έχουν ενσωματωθεί σε ένα διάγραμμα. Αυτό είναι κρίσιμο για ελέγχους συμμόρφωσης, προστασία εμπορικού σήματος και αυτοματοποιημένη διαχείριση περιεχομένου. Το GroupDocs.Watermark χρησιμοποιεί αντιληπτικό hashing (DCT) για γρήγορη και ακριβή σύγκριση εικόνων.

## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:
1. **Java Development Kit (JDK)** 8 ή νεότερο.  
2. **IDE** – IntelliJ IDEA, Eclipse ή οποιονδήποτε επεξεργαστή προτιμάτε.  
3. **GroupDocs.Watermark for Java** – τα JAR της βιβλιοθήκης πρέπει να βρίσκονται στο classpath σας.  

### Απαιτούμενες βιβλιοθήκες και εξαρτήσεις
Μπορείτε να προσθέσετε τη βιβλιοθήκη μέσω Maven ή να κατεβάσετε τα JAR χειροκίνητα.

#### Ρύθμιση Maven
Προσθέστε την παρακάτω διαμόρφωση στο αρχείο `pom.xml` σας:

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
Εναλλακτικά, κατεβάστε την πιο πρόσφατη έκδοση από [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Απόκτηση άδειας
- **Δωρεάν δοκιμή** – δοκιμάστε όλες τις λειτουργίες χωρίς κλειδί άδειας.  
- **Προσωρινή άδεια** – ζητήστε κλειδί περιορισμένου χρόνου για αξιολόγηση.  
- **Αγορά** – αποκτήστε μόνιμη ή συνδρομητική άδεια για παραγωγική χρήση.

## Ρύθμιση GroupDocs.Watermark για Java
1. **Εγκατάσταση της βιβλιοθήκης** – βεβαιωθείτε ότι το αποθετήριο Maven και οι εξαρτήσεις είναι παρούσες, ή τοποθετήστε τα JAR στο φάκελο `libs/` και προσθέστε τα στη διαδρομή κατασκευής του έργου σας.  
2. **Αρχικοποίηση του API** – δημιουργήστε ένα αντικείμενο `Watermarker`; αυτό το αντικείμενο είναι το σημείο εισόδου για τη φόρτωση διαγραμμάτων και την εκτέλεση λειτουργιών υδατογραφήματος.

## Πώς να διαγράψετε κείμενο υδατογράφημα σε διαγράμματα με Java
Για να διαγράψετε ένα κείμενο υδατογράφημα, φορτώστε το διάγραμμα με `Watermarker`, δημιουργήστε ένα `TextSearchCriteria` που ταιριάζει με το κείμενο του υδατογραφήματος, ανακτήστε τη συλλογή `PossibleWatermarkCollection` που ταιριάζει και καλέστε `clear()` σε αυτήν. Αυτό αφαιρεί μόνο τις καθορισμένες επικάλυψεις κειμένου ενώ διατηρεί το υπόλοιπο του διαγράμματος αμετάβλητο.

Η κλάση `Watermarker` αντιπροσωπεύει ένα μοναδικό έγγραφο στη μνήμη και παρέχει μεθόδους για φόρτωση, αναζήτηση και τροποποίηση υδατογραφημάτων.

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
- **Παράμετροι:**  
  - `inputFilePath`: Διαδρομή προς το αρχείο `.vsdx`.  
  - `loadOptions`: Διαμορφώνει τον τρόπο φόρτωσης του εγγράφου (π.χ., εύρος σελίδων, κωδικός πρόσβασης).

## Πώς να ανιχνεύσετε υδατογράφημα εικόνας σε αρχείο διαγράμματος;
Η ανίχνευση υδατογραφήματος εικόνας περιλαμβάνει τη δημιουργία ενός `ImageDctHashSearchCriteria` με μια εικόνα αναφοράς, έπειτα τη χρήση του `Watermarker` για την αναζήτηση στο διάγραμμα. Το API δημιουργεί αντιληπτικό hash για κάθε ενσωματωμένη εικόνα και το συγκρίνει με την αναφορά, επιστρέφοντας ταιριάσματα με βαθμολογίες ομοιότητας ώστε να μπορείτε να εντοπίσετε και να αφαιρέσετε ανεπιθύμητα λογότυπα ή σφραγίδες.

`ImageDctHashSearchCriteria` δημιουργεί hash της εικόνας αναφοράς και το συγκρίνει με τις εικόνες ενσωματωμένες στο διάγραμμα, επιστρέφοντας ταιριάσματα με βαθμολογία ομοιότητας.

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
- **Κύριες μέθοδοι:**  
  - `TextSearchCriteria` – δημιουργεί κριτήρια για υδατογραφήματα κειμένου.  
  - `PossibleWatermarkCollection` – περιέχει τα αποτελέσματα οποιασδήποτε λειτουργίας αναζήτησης.

## Πώς να αφαιρέσετε τα υδατογραφήματα μόλις εντοπιστούν;
Μόλις εντοπιστούν τα υδατογραφήματα, μπορείτε να τα αφαιρέσετε καλώντας τη μέθοδο `clear()` στη `PossibleWatermarkCollection` που επιστράφηκε από την αναζήτηση. Αυτή η λειτουργία διαγράφει τα αντικείμενα υδατογραφήματος ενώ διατηρεί όλα τα άλλα στοιχεία του διαγράμματος, εξασφαλίζοντας ότι το αρχικό περιεχόμενο παραμένει αμετάβλητο.

`clear()` αφαιρεί κάθε υδατογράφημα στη συλλογή ενώ διατηρεί το υπόλοιπο περιεχόμενο του διαγράμματος.

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
- **Κύρια μέθοδος:** `clear()` – διαγράφει όλα τα υδατογραφήματα στη δοθείσα συλλογή χωρίς να τροποποιεί άλλα στοιχεία του διαγράμματος.

## Πρακτικές εφαρμογές
1. **Ενσωμάτωση σε επιχειρησιακό λογισμικό** – ενσωματώστε τη διαχείριση υδατογραφημάτων σε εφαρμογές που εστιάζουν σε έγγραφα για προστασία ιδιόκτητων διαγραμμάτων.  
2. **Συστήματα Διαχείρισης Περιεχομένου (CMS)** – αυτοματοποιήστε την ανίχνευση μη εξουσιοδοτημένων λογοτύπων πριν από τη δημοσίευση διαγραμμάτων που δημιουργούνται από χρήστες.  
3. **Διαχείριση νομικών εγγράφων** – προσθέστε ή διαγράψτε υδατογραφήματα σε διαφορετικά στάδια της ροής εργασίας ενός φακέλου υπόθεσης, διασφαλίζοντας τη συμμόρφωση με πολιτικές εμπιστευτικότητας.

## Συνηθισμένα προβλήματα και αντιμετώπιση
- **Μεγάλα αρχεία** – αυξήστε τη ρύθμιση `maxMemory` στο `LoadOptions` εάν αντιμετωπίσετε `OutOfMemoryError`.  
- **Διαγράμματα με κωδικό πρόσβασης** – παρέχετε τον κωδικό στο `LoadOptions` για να ανοίξετε το αρχείο.  
- **Απουσία αντιστοιχίσεων hash εικόνας** – βεβαιωθείτε ότι η εικόνα αναφοράς έχει επαρκή ανάλυση· εικόνες χαμηλής ανάλυσης μπορεί να παράγουν αδύναμα hashes.

## Συχνές ερωτήσεις

**Ε: Μπορώ να αναζητήσω ταυτόχρονα κείμενο και εικόνες;**  
Α: Ναι – συνδυάστε `TextSearchCriteria` και `ImageDctHashSearchCriteria` με τον τελεστή `or()` για να εντοπίσετε και τους δύο τύπους σε μία διαδρομή.

**Ε: Είναι δυνατόν να διαγράψω υδατογραφήματα χωρίς να καταστρέψω το διάγραμμα;**  
Α: Απόλυτα. Το API απομονώνει τα αντικείμενα υδατογραφήματος και τα αφαιρεί, αφήνοντας την αρχική δομή του διαγράμματος αμετάβλητη.

**Ε: Υποστηρίζει το GroupDocs.Watermark πολλαπλές μορφές διαγράμματος;**  
Α: Ναι – υποστηρίζει πάνω από 20 μορφές, συμπεριλαμβανομένων `.vsdx`, `.vdx`, `.drawio` και `.svg`, επιτρέποντας ευρεία διαχείριση διαγραμμάτων.

**Ε: Πώς να διαχειριστώ μεγάλο όγκο εγγράφων αποδοτικά;**  
Α: Χρησιμοποιήστε βρόχους επεξεργασίας batch, επαναχρησιμοποιήστε ένα ενιαίο αντικείμενο `Watermarker` όπου είναι δυνατόν, και ρυθμίστε το `LoadOptions` ώστε να κάνει ροή των σελίδων αντί να φορτώνει ολόκληρα αρχεία.

**Ε: Μπορώ να ενσωματώσω την ανίχνευση υδατογραφήματος σε CI/CD pipeline;**  
Α: Ναι – η βιβλιοθήκη είναι headless και μπορεί να κληθεί από Maven, Gradle ή οποιοδήποτε script κατασκευής για αυτόματη επικύρωση περιουσιακών στοιχείων διαγράμματος.

---

**Τελευταία ενημέρωση:** 2026-10-27  
**Δοκιμασμένο με:** GroupDocs.Watermark 23.6 for Java  
**Συγγραφέας:** GroupDocs

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

## Σχετικά Tutorials

- [How to Add Text Watermarks to Diagrams Using GroupDocs.Watermark in Java](/watermark/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/)
- [Guide to Adding Watermarks to Diagrams Using GroupDocs.Watermark for Java](/watermark/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/)
- [How to Retrieve Document Information Using GroupDocs.Watermark for Java: A Step-by-Step Guide](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)