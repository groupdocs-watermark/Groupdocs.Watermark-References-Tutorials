---
date: '2026-11-13'
description: Μάθετε πώς να προσθέσετε διαγράμματα με υδατογράφημα κειμένου χρησιμοποιώντας
  το GroupDocs.Watermark for Java. Προστατέψτε το οπτικό σας περιεχόμενο αποτελεσματικά,
  διατηρώντας τα διαγράμματα επεξεργάσιμα και ασφαλή.
keywords:
- add text watermark diagram
- GroupDocs.Watermark for Java
- diagram watermarking
lastmod: '2026-11-13'
og_description: Προσθήκη διαγράμματος με υδατογράφημα κειμένου χρησιμοποιώντας το
  GroupDocs.Watermark for Java. Αυτός ο οδηγός δείχνει βήμα‑βήμα πώς να προστατεύσετε
  τα διαγράμματα, να ρυθμίσετε τη θέση και να αποθηκεύσετε το αποτέλεσμα αποδοτικά.
og_image_alt: 'Developer guide: adding text watermarks to diagram files with GroupDocs.Watermark
  for Java'
og_title: Προσθήκη διαγράμματος με υδατογράφημα κειμένου με το GroupDocs.Watermark
  for Java
schemas:
- author: GroupDocs
  dateModified: '2026-11-13'
  description: Learn how to add text watermark diagram using GroupDocs.Watermark for
    Java. Protect your visual content effectively while keeping diagrams editable
    and secure.
  headline: Add text watermark diagram using GroupDocs.Watermark for Java
  type: TechArticle
- description: Learn how to add text watermark diagram using GroupDocs.Watermark for
    Java. Protect your visual content effectively while keeping diagrams editable
    and secure.
  name: Add text watermark diagram using GroupDocs.Watermark for Java
  steps:
  - name: load diagram document
    text: '**Definition anchor**: `DiagramLoadOptions` configures how GroupDocs.Watermark
      reads diagram files, allowing you to specify page ranges or rendering settings.
      Specify the file path and initialise the load options:'
  - name: create and configure the text watermark
    text: '**Definition anchor**: `TextWatermark` represents the textual overlay that
      will be rendered on each selected diagram shape. Instantiate the watermark with
      your chosen text, font, size, and color:'
  - name: set watermark placement options
    text: '**Definition anchor**: `DiagramShapeWatermarkOptions` lets you decide whether
      the watermark appears on the background, foreground, or specific shapes within
      the diagram. Configure the placement type and any rotation or opacity settings:'
  - name: add the watermark and save the diagram
    text: '**Definition anchor**: `Watermarker` is the core class that applies watermarks
      to supported documents and writes the output file. Apply the `textWatermark`
      to the loaded diagram using the previously defined `options`, then save the
      result to a new location:'
  type: HowTo
- questions:
  - answer: A size between 12 pt and 24 pt works well; choose larger sizes for high‑resolution
      diagrams to ensure readability without obscuring details.
    question: What is the best font size for watermarks on diagrams?
  - answer: Yes, call `textWatermark.setColor(java.awt.Color)` with any RGB value
      to match your branding.
    question: Can I change the watermark color?
  - answer: Iterate over a directory, reuse the same `Watermarker` object for each
      file, and call `watermarker.add(textWatermark, options)` inside the loop.
    question: How do I process a batch of diagram files?
  - answer: Review [documentation](https://docs.groupdocs.com/watermark/java/) for
      the full list of supported diagram formats; the library handles VSX, SVG, and
      many proprietary formats.
    question: Are there any format limitations?
  - answer: Visit the [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)
      for community assistance or open a support ticket through your account portal.
    question: Where can I get help if I run into issues?
  type: FAQPage
tags:
- add text watermark diagram
- GroupDocs.Watermark
- Java diagram processing
- document security
title: Προσθήκη διαγράμματος με υδατογράφημα κειμένου χρησιμοποιώντας το GroupDocs.Watermark
  for Java
type: docs
url: /el/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# Προσθήκη υδατογραφήματος κειμένου σε διάγραμμα χρησιμοποιώντας το GroupDocs.Watermark για Java

Η προστασία των εγγράφων διαγράμματος από μη εξουσιοδοτημένη χρήση είναι κρίσιμη, και η **προσθήκη υδατογραφήματος κειμένου σε διάγραμμα** είναι ένας απλός αλλά ισχυρός τρόπος για να το επιτύχετε. Σε αυτόν τον οδηγό θα μάθετε πώς να φορτώνετε αρχεία διαγράμματος, να δημιουργείτε ένα προσαρμόσιμο υδατογράφημα κειμένου, να το τοποθετείτε ακριβώς πάνω σε σχήματα διαγράμματος και να αποθηκεύετε το προστατευμένο αρχείο — όλα με το GroupDocs.Watermark για Java.

## Γρήγορες απαντήσεις
- **Ποια βιβλιοθήκη διαχειρίζεται υδατογραφήματα διαγράμματος;** GroupDocs.Watermark for Java.
- **Ποια είναι η ελάχιστη έκδοση Java;** JDK 8 ή νεότερη.
- **Χρειάζομαι άδεια για ανάπτυξη;** Μια προσωρινή άδεια λειτουργεί για όλες τις δυνατότητες κατά τη δοκιμή.
- **Μπορώ να προσθέσω υδατογράφημα σε πολλά αρχεία σε batch;** Ναι, χρησιμοποιήστε το ίδιο αντικείμενο Watermarker σε βρόχο.
- **Ανησυχεί η χρήση μνήμης για μεγάλα διαγράμματα;** Επαναχρησιμοποιήστε αντικείμενα και κλείστε το Watermarker για να ελευθερώσετε πόρους.

## Τι είναι η προσθήκη υδατογραφήματος κειμένου σε διάγραμμα;
`add text watermark diagram` αναφέρεται στη διαδικασία ενσωμάτωσης αναγνώσιμου κειμένου (όπως «Confidential» ή το όνομα μιας εταιρείας) απευθείας στα αρχεία διαγράμματος, ώστε το υδατογράφημα να γίνεται μέρος του οπτικού περιεχομένου και να μην μπορεί να αφαιρεθεί χωρίς να τροποποιηθεί το ίδιο το διάγραμμα.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark για Java;
Το GroupDocs.Watermark υποστηρίζει **πάνω από 50 μορφές εισόδου και εξόδου**, συμπεριλαμβανομένων των Visio (.vsdx), SVG και άλλων δημοφιλών τύπων διαγράμματος. Μπορεί να επεξεργαστεί διαγράμματα με εκατοντάδες σελίδες χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη, προσφέροντας **μείωση 30 % της χρήσης CPU** σε σύγκριση με πολλούς ανταγωνιστές όταν διαχειρίζεται αρχεία μεγαλύτερα από 100 MB.

## Προαπαιτούμενα
- **GroupDocs.Watermark for Java** έκδοση 24.11 ή νεότερη (η βιβλιοθήκη ενημερώνεται μηνιαίως με διορθώσεις ασφαλείας).  
- **Java Development Kit (JDK)** 8 ή νεότερο.  
- Ένα IDE όπως το IntelliJ IDEA ή το Eclipse.  
- Maven για διαχείριση εξαρτήσεων (προαιρετικό αλλά συνιστάται).

## Ρύθμιση του GroupDocs.Watermark για Java
Για να ξεκινήσετε, προσθέστε τη βιβλιοθήκη στο Maven project σας:

**Ρύθμιση Maven**  
Προσθέστε την ακόλουθη διαμόρφωση στο αρχείο `pom.xml`:

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

Αν προτιμάτε χειροκίνητη λήψη, αποκτήστε τα τελευταία binaries από [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Απόκτηση άδειας
- **Δωρεάν δοκιμή** – εξερευνήστε όλες τις δυνατότητες για 30 ημέρες.  
- **Προσωρινή άδεια** – αφαιρεί όλους τους περιορισμούς δοκιμής ενώ αναπτύσσετε.  
- **Πλήρης άδεια** – απαιτείται για παραγωγικές εγκαταστάσεις.

## Οδηγός υλοποίησης

### Πώς να προσθέσετε υδατογράφημα κειμένου σε διάγραμμα χρησιμοποιώντας το GroupDocs.Watermark για Java;
Πρώτα, φορτώστε το αρχείο διαγράμματος χρησιμοποιώντας το `DiagramLoadOptions`. Στη συνέχεια, δημιουργήστε ένα `TextWatermark` με το επιθυμητό κείμενο, γραμματοσειρά, μέγεθος και χρώμα. Έπειτα, διαμορφώστε το `DiagramShapeWatermarkOptions` για να ελέγξετε τη θέση, την περιστροφή και τη διαφάνεια. Τέλος, εφαρμόστε το υδατογράφημα με το `Watermarker.add` και αποθηκεύστε το τροποποιημένο διάγραμμα σε νέο αρχείο. Αυτή η άμεση απάντηση σας δίνει τη γενική ροή πριν από οποιαδήποτε λεπτομερή εξήγηση.

#### Βήμα 1: φόρτωση εγγράφου διαγράμματος
**Αγκύρωση ορισμού**: Το `DiagramLoadOptions` διαμορφώνει τον τρόπο με τον οποίο το GroupDocs.Watermark διαβάζει αρχεία διαγράμματος, επιτρέποντάς σας να καθορίσετε περιοχές σελίδων ή ρυθμίσεις απόδοσης.

Καθορίστε τη διαδρομή του αρχείου και αρχικοποιήστε τις επιλογές φόρτωσης:

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

#### Βήμα 2: δημιουργία και διαμόρφωση του υδατογραφήματος κειμένου
**Αγκύρωση ορισμού**: Το `TextWatermark` αντιπροσωπεύει την κειμενική επικάλυψη που θα αποδοθεί σε κάθε επιλεγμένο σχήμα διαγράμματος.

Δημιουργήστε το υδατογράφημα με το επιλεγμένο κείμενο, γραμματοσειρά, μέγεθος και χρώμα:

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

#### Βήμα 3: ορισμός επιλογών τοποθέτησης υδατογραφήματος
**Αγκύρωση ορισμού**: Το `DiagramShapeWatermarkOptions` σας επιτρέπει να αποφασίσετε αν το υδατογράφημα θα εμφανίζεται στο φόντο, στο προσκήνιο ή σε συγκεκριμένα σχήματα μέσα στο διάγραμμα.

Διαμορφώστε τον τύπο τοποθέτησης και τυχόν ρυθμίσεις περιστροφής ή διαφάνειας:

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

#### Βήμα 4: προσθήκη του υδατογραφήματος και αποθήκευση του διαγράμματος
**Αγκύρωση ορισμού**: Το `Watermarker` είναι η κεντρική κλάση που εφαρμόζει υδατογραφήματα σε υποστηριζόμενα έγγραφα και γράφει το αρχείο εξόδου.

Εφαρμόστε το `textWatermark` στο φορτωμένο διάγραμμα χρησιμοποιώντας τις προηγουμένως ορισμένες `options`, στη συνέχεια αποθηκεύστε το αποτέλεσμα σε νέα θέση:

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

### Πρακτικές εφαρμογές
Η προσθήκη υδατογραφήματος κειμένου σε διαγράμματα είναι χρήσιμη σε πολλές πραγματικές περιπτώσεις:

- **Προστασία πνευματικής ιδιοκτησίας** – εμποδίζει τους ανταγωνιστές από την επαναχρησιμοποίηση ιδιόκτητων ροών διαδικασιών.  
- **Ενίσχυση εμπορικού σήματος** – ενσωματώστε το όνομα ή το λογότυπο της εταιρείας σας σε κάθε εξαγόμενο διάγραμμα.  
- **Νομική συμμόρφωση** – σημειώστε εμπιστευτικά σχέδια με το «Do Not Distribute».  
- **Ακαδημαϊκή ακεραιότητα** – επισημάνετε τις υποβολές των φοιτητών με μοναδικά αναγνωριστικά.

Μπορείτε να ενσωματώσετε αυτή τη ροή εργασίας σε συστήματα διαχείρισης εγγράφων, pipelines CI/CD ή υπηρεσίες επεξεργασίας παρτίδων για να αυτοματοποιήσετε την προσθήκη υδατογραφήματος σε χιλιάδες αρχεία.

### Σκέψεις απόδοσης
Για βέλτιστη απόδοση με μεγάλες συλλογές διαγραμμάτων:

- **Επαναχρησιμοποίηση αντικειμένων** – δημιουργήστε ένα μόνο αντικείμενο `Watermarker` και επεξεργαστείτε τα αρχεία σε βρόχο.  
- **Άμεσο κλείσιμο πόρων** – πάντα καλέστε `watermarker.close()` μετά την αποθήκευση για να ελευθερώσετε τη φυσική μνήμη.  
- **Ροή μεγάλων αρχείων** – χρησιμοποιήστε το `DiagramLoadOptions` για να φορτώνετε σελίδες κατά απαίτηση αντί για ολόκληρο το αρχείο.

## Συχνές ερωτήσεις

**Q: Ποιο είναι το καλύτερο μέγεθος γραμματοσειράς για υδατογραφήματα σε διαγράμματα;**  
A: Ένα μέγεθος μεταξύ 12 pt και 24 pt λειτουργεί καλά· επιλέξτε μεγαλύτερα μεγέθη για διαγράμματα υψηλής ανάλυσης ώστε να εξασφαλίζεται η αναγνωσιμότητα χωρίς να κρύβονται λεπτομέρειες.

**Q: Μπορώ να αλλάξω το χρώμα του υδατογραφήματος;**  
A: Ναι, καλέστε `textWatermark.setColor(java.awt.Color)` με οποιαδήποτε τιμή RGB για να ταιριάζει με το branding σας.

**Q: Πώς επεξεργάζομαι μια παρτίδα αρχείων διαγράμματος;**  
A: Επανάληψη σε έναν φάκελο, επαναχρησιμοποίηση του ίδιου αντικειμένου `Watermarker` για κάθε αρχείο, και κλήση του `watermarker.add(textWatermark, options)` μέσα στον βρόχο.

**Q: Υπάρχουν περιορισμοί μορφής;**  
A: Εξετάστε την [τεκμηρίωση](https://docs.groupdocs.com/watermark/java/) για την πλήρη λίστα των υποστηριζόμενων μορφών διαγράμματος· η βιβλιοθήκη διαχειρίζεται VSX, SVG και πολλές ιδιόκτητες μορφές.

**Q: Πού μπορώ να λάβω βοήθεια αν αντιμετωπίσω προβλήματα;**  
A: Επισκεφθείτε το [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10) για βοήθεια από την κοινότητα ή ανοίξτε ένα ticket υποστήριξης μέσω του portal λογαριασμού σας.

## Πόροι
- **Τεκμηρίωση**: [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **Αναφορά API**: [Java API Reference](https://reference.groupdocs.com/watermark/java)  
- **Λήψη**: [Get GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **Αποθετήριο GitHub**: [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Δωρεάν φόρουμ υποστήριξης**: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Προσωρινή άδεια**: [Acquire Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**Τελευταία ενημέρωση:** 2026-11-13  
**Δοκιμάστηκε με:** GroupDocs.Watermark for Java 24.11  
**Συγγραφέας:** GroupDocs

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## Σχετικά Μαθήματα

- [Πώς να προσθέσετε υδατογραφήματα κειμένου σε Java με το GroupDocs.Watermark: Ένας πλήρης οδηγός](/watermark/java/text-watermarks/add-text-watermark-java-groupdocs/)
- [Πώς να προσθέσετε υδατογραφήματα κειμένου και εικόνας σε συγκεκριμένες σελίδες PDF χρησιμοποιώντας το GroupDocs.Watermark για Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [Πώς να προσθέσετε υδατογραφήματα κειμένου σε εικόνες εγγράφων Word χρησιμοποιώντας το GroupDocs.Watermark για Java](/watermark/java/image-watermarks/add-watermarks-word-images-groupdocs-java/)