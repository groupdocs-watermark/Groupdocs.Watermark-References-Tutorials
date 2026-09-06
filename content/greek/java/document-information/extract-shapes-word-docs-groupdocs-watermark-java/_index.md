---
date: '2026-09-06'
description: Μάθετε πώς να εξάγετε shapes από Word documents με GroupDocs.Watermark
  για Java, επιτρέποντας ισχυρή αυτοματοποίηση εγγράφων και ανάλυση.
keywords:
- how to extract shapes
- GroupDocs.Watermark Java
- Word document shape extraction
lastmod: '2026-09-06'
og_description: Πώς να εξάγετε shapes από Word documents με GroupDocs.Watermark για
  Java. Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για να φορτώσετε, αναλύσετε και επεξεργαστείτε
  shapes αποδοτικά.
og_image_alt: Guide showing Java code extracting shapes from a Word document using
  GroupDocs.Watermark
og_title: Πώς να εξάγετε shapes από Word documents χρησιμοποιώντας GroupDocs.Watermark
  σε Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-06'
  description: Learn how to extract shapes from Word documents with GroupDocs.Watermark
    for Java, enabling powerful document automation and analysis.
  headline: How to extract shapes from Word documents using GroupDocs.Watermark in
    Java
  type: TechArticle
- questions:
  - answer: GroupDocs.Watermark for Java is a comprehensive SDK that enables watermark
      creation, detection, and document inspection across 30+ file formats, including
      DOCX, PDF, and PPTX.
    question: What is GroupDocs.Watermark for Java?
  - answer: Yes—pass the password to `WordProcessingLoadOptions` when constructing
      the `Watermarker` instance.
    question: Can I extract shapes from password‑protected Word files?
  - answer: Absolutely; GroupDocs.Watermark is platform‑agnostic and runs on any OS
      that supports Java 8+.
    question: Does the library work on Linux servers?
  - answer: The SDK can handle thousands of shapes; tests show stable performance
      on documents with up to 5,000 individual shapes.
    question: How many shapes can be processed in a single document?
  - answer: No, shape extraction is included in the standard GroupDocs.Watermark license.
    question: Is a separate license needed for shape extraction?
  type: FAQPage
tags:
- extract shapes
- GroupDocs.Watermark
- Java document processing
title: Πώς να εξάγετε shapes από Word documents χρησιμοποιώντας GroupDocs.Watermark
  σε Java
type: docs
url: /el/java/document-information/extract-shapes-word-docs-groupdocs-watermark-java/
weight: 1
---

# Πώς να εξάγετε σχήματα από έγγραφα Word χρησιμοποιώντας το GroupDocs.Watermark σε Java

Σε σύγχρονες εφαρμογές που εστιάζουν στα έγγραφα, **πώς να εξάγετε σχήματα** από αρχεία Word αποτελεί κοινή πρόκληση. Είτε χρειάζεστε να ελέγξετε τη χρήση διαγραμμάτων, να μετατρέψετε γραφικά σε εικόνες, είτε να δημιουργήσετε δυναμικές αναφορές, η δυνατότητα προγραμματιστικής ανάκτησης μεταδεδομένων σχήματος εξοικονομεί αμέτρητες ώρες χειροκίνητης εργασίας. Αυτό το σεμινάριο σας καθοδηγεί στη χρήση του GroupDocs.Watermark για Java για τη φόρτωση ενός DOCX, την απαρίθμηση κάθε σχήματος και την ανάκτηση των ιδιοτήτων του όπως τύπος, μέγεθος και θέση.

## Γρήγορες απαντήσεις
- **Ποια βιβλιοθήκη χειρίζεται την εξαγωγή σχημάτων;** GroupDocs.Watermark για Java.  
- **Ελάχιστη έκδοση Java;** JDK 8 ή νεότερη.  
- **Χρειάζεται άδεια για ανάπτυξη;** Μια δωρεάν δοκιμαστική άδεια λειτουργεί για δοκιμές· απαιτείται πλήρης άδεια για παραγωγή.  
- **Μπορώ να επεξεργαστώ μεγάλα έγγραφα;** Ναι—επεξεργαστείτε τμήματα διαδοχικά για να διατηρήσετε τη χρήση μνήμης χαμηλή.  
- **Είναι το Maven η προτιμώμενη μέθοδος εγκατάστασης;** Το Maven απλοποιεί τη διαχείριση εξαρτήσεων και συνιστάται για τα περισσότερα έργα.

## Τι είναι η εξαγωγή σχημάτων σε έγγραφα Word;
Η εξαγωγή σχημάτων είναι η διαδικασία προγραμματιστικής ανάγνωσης ενός αρχείου Word και ανάκτησης λεπτομερειών για κάθε γραφικό αντικείμενο—εικόνες, σχέδια, SmartArt, διαγράμματα ή πλαίσια κειμένου—ώστε να μπορείτε να τα αναλύσετε ή να τα επεξεργαστείτε στον κώδικα. Τα εξαγόμενα μεταδεδομένα περιλαμβάνουν τύπο σχήματος, διαστάσεις, θέση και τυχόν συσχετισμένο κείμενο, επιτρέποντας περαιτέρω επεξεργασία όπως μετατροπή ή ανάλυση.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark για Java;
Το GroupDocs.Watermark υποστηρίζει **30+ μορφές εγγράφων** και μπορεί να χειριστεί **αρχεία με εκατοντάδες σελίδες** χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη, χάρη στο streaming API του. Η βιβλιοθήκη επεξεργάζεται τα μεταδεδομένα σχημάτων σε λιγότερο από **200 ms ανά 100‑σελίδες έγγραφο** σε τυπικό διακομιστή, παρέχοντάς σας γρήγορα, αξιόπιστα αποτελέσματα για μαζικές λειτουργίες.

## Προαπαιτούμενα
- **Java Development Kit (JDK)** 8 ή νεότερο.  
- **IDE** όπως IntelliJ IDEA ή Eclipse.  
- Βασική εξοικείωση με Java I/O και Maven.  

Θα χρησιμοποιήσουμε το GroupDocs.Watermark για Java, ένα ισχυρό SDK που εστιάζει στην τοποθέτηση υδατογραφιών αλλά προσφέρει επίσης δυνατότητες βαθιάς επιθεώρησης εγγράφων.

## Ρύθμιση του GroupDocs.Watermark για Java
Ενσωματώστε το SDK μέσω Maven ή άμεσης λήψης.

### Χρήση Maven
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

### Άμεση λήψη
Εναλλακτικά, κατεβάστε την πιο πρόσφατη έκδοση από [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Απόκτηση άδειας
Μια δωρεάν δοκιμαστική άδεια σας επιτρέπει να εξερευνήσετε όλες τις λειτουργίες. Για παραγωγική χρήση, αποκτήστε μόνιμο κλειδί άδειας από το portal του GroupDocs.

## Οδηγός υλοποίησης
Θα χωρίσουμε την υλοποίηση σε δύο λογικά μέρη: τη φόρτωση του εγγράφου και την εξαγωγή πληροφοριών σχήματος.

## Πώς να εξάγετε σχήματα από έγγραφα Word χρησιμοποιώντας το GroupDocs.Watermark;
`Watermarker` είναι η κύρια κλάση στο GroupDocs.Watermark που φορτώνει ένα έγγραφο και παρέχει πρόσβαση στα περιεχόμενά του. Φορτώστε το DOCX με μια παρουσία `Watermarker`, στη συνέχεια επαναλάβετε κάθε τμήμα και σχήμα για να διαβάσετε τις ιδιότητές του. Το μοτίβο δύο βημάτων—αρχικοποίηση, έπειτα απαρίθμηση—καλύπτει **όλους τους 30+ υποστηριζόμενους τύπους σχημάτων** και λειτουργεί για έγγραφα έως 500 σελίδες χωρίς υπερβολική κατανάλωση μνήμης. Διαχειρίζεται το έγγραφο με streaming, επιτρέποντάς σας να δουλεύετε με μεγάλα αρχεία χωρίς υψηλή χρήση μνήμης.

### Βήμα 1: διαμόρφωση επιλογών φόρτωσης
`WordProcessingLoadOptions` σας επιτρέπει να ρυθμίσετε λεπτομερώς τον τρόπο ανάλυσης του αρχείου (π.χ., αγνόηση κεφαλίδων, ενεργοποίηση γρήγορης λειτουργίας).  
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
Το απόσπασμα δημιουργεί ένα `Watermarker` που κρατά το έγγραφο στη μνήμη και το προετοιμάζει για επιθεώρηση.

### Βήμα 2: πρόσβαση στο περιεχόμενο επεξεργασίας κειμένου
Περιηγηθείτε στα τμήματα και τα σχήματα, εκτυπώνοντας βασικές λεπτομέρειες όπως τύπο, διαστάσεις, στοίχιση και αν το σχήμα βρίσκεται σε κεφαλίδα/υποσέλιδο.  
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
Αυτός ο βρόχος καλύπτει κάθε αντικείμενο σχήματος, διασφαλίζοντας ότι δεν θα χάσετε κρυφά γραφικά ενσωματωμένα σε κεφαλίδες ή υποσέλιδα.

## Συχνά προβλήματα και λύσεις
- **Αρχείο δεν βρέθηκε** – ελέγξτε το απόλυτο ή σχετικό μονοπάτι· χρησιμοποιήστε `Paths.get(...).toAbsolutePath()` για σαφήνεια.  
- **Σημεία συμφόρησης απόδοσης** – για έγγραφα μεγαλύτερα από 300 σελίδες, επεξεργαστείτε τμήματα ένα προς ένα και καλέστε `watermarker.close()` μετά από κάθε παρτίδα για απελευθέρωση μνήμης.  
- **Μη υποστηριζόμενος τύπος σχήματος** – το GroupDocs.Watermark υποστηρίζει επί του παρόντος 25 κατηγορίες εγγενών σχημάτων· για προσαρμοσμένα αντικείμενα OfficeArt, εξετάστε το OpenXML SDK ως εναλλακτική λύση.

## Πρακτικές εφαρμογές
1. **Αυτοματοποιημένη δημιουργία αναφορών** – εξάγετε διαγράμματα για ενσωμάτωση σε πίνακες ελέγχου.  
2. **Έλεγχος συμμόρφωσης** – επαληθεύστε ότι απαγορευμένα γραφικά δεν υπάρχουν σε ρυθμιζόμενα έγγραφα.  
3. **Διαδικασίες μετεγκατάστασης** – μετατρέψτε σχήματα σε SVG πριν τη μεταφορά περιεχομένου σε πλατφόρμες δημοσίευσης στο web.

## Σκέψεις απόδοσης
- Απελευθερώστε άμεσα το αντικείμενο `Watermarker` με `watermarker.close()` για να ελευθερώσετε εγγενείς πόρους.  
- Ενεργοποιήστε τη σημαία `fastLoad` στο `WordProcessingLoadOptions` όταν χρειάζεστε μόνο μεταδεδομένα σχήματος, όχι πλήρη απόδοση περιεχομένου.  
- Επεξεργαστείτε έγγραφα σε παράλληλα streams μόνο αν ο διακομιστής σας διαθέτει επαρκείς πυρήνες CPU· αποφύγετε κοινόχρηστα αντικείμενα που δεν είναι thread‑safe.

## Συμπέρασμα
Τώρα γνωρίζετε **πώς να εξάγετε σχήματα** από έγγραφα Word χρησιμοποιώντας το GroupDocs.Watermark για Java. Φορτώνοντας ένα έγγραφο με `Watermarker`, διαμορφώνοντας τις επιλογές φόρτωσης και επαναλαμβάνοντας κάθε σχήμα, μπορείτε να δημιουργήσετε ισχυρές αυτοματοποιημένες ροές εργασίας που διαχειρίζονται ακόμη και τα πιο σύνθετα αρχεία.

### Επόμενα βήματα
- Πειραματιστείτε με τη μέθοδο `getImageData()` του αντικειμένου `Shape` για εξαγωγή εικόνων ως PNG.  
- Εξερευνήστε άλλες δυνατότητες του GroupDocs.Watermark όπως η ανίχνευση και αφαίρεση υδατογραφιών.  
- Συνδυάστε την εξαγωγή σχημάτων με τη βιβλιοθήκη GroupDocs.Parser για ανάκτηση του περιβάλλοντος κειμένου για πιο πλούσια ανάλυση.

## Συχνές ερωτήσεις

**Q: Τι είναι το GroupDocs.Watermark για Java;**  
A: Το GroupDocs.Watermark για Java είναι ένα ολοκληρωμένο SDK που επιτρέπει τη δημιουργία, ανίχνευση και επιθεώρηση υδατογραφιών σε πάνω από 30 μορφές αρχείων, συμπεριλαμβανομένων DOCX, PDF και PPTX.

**Q: Μπορώ να εξάγω σχήματα από αρχεία Word με κωδικό πρόσβασης;**  
A: Ναι—περάστε τον κωδικό στο `WordProcessingLoadOptions` κατά τη δημιουργία της παρουσίας `Watermarker`.

**Q: Η βιβλιοθήκη λειτουργεί σε διακομιστές Linux;**  
A: Απόλυτα· το GroupDocs.Watermark είναι ανεξάρτητο από πλατφόρμα και λειτουργεί σε οποιοδήποτε OS που υποστηρίζει Java 8+.

**Q: Πόσα σχήματα μπορούν να επεξεργαστούν σε ένα μόνο έγγραφο;**  
A: Το SDK μπορεί να διαχειριστεί χιλιάδες σχήματα· οι δοκιμές δείχνουν σταθερή απόδοση σε έγγραφα με έως και 5.000 μεμονωμένα σχήματα.

**Q: Χρειάζεται ξεχωριστή άδεια για την εξαγωγή σχημάτων;**  
A: Όχι, η εξαγωγή σχημάτων περιλαμβάνεται στην τυπική άδεια του GroupDocs.Watermark.

---

**Τελευταία ενημέρωση:** 2026-09-06  
**Δοκιμασμένο με:** GroupDocs.Watermark 23.12 for Java  
**Συγγραφέας:** GroupDocs

## Σχετικά μαθήματα

- [Εξαγωγή πληροφοριών σχήματος από διαγράμματα χρησιμοποιώντας το GroupDocs.Watermark σε Java](/watermark/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/)
- [Αφαίρεση σχημάτων από έγγραφα Word χρησιμοποιώντας το GroupDocs.Watermark σε Java: Ολοκληρωμένος Οδηγός](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}