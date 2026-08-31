---
date: '2026-08-31'
description: Μάθετε πώς να προσθέσετε watermark σε διαγράμματα χρησιμοποιώντας το
  GroupDocs.Watermark for Java. Αυτός ο οδηγός καλύπτει τη ρύθμιση, τη δημιουργία
  text watermark, τις επιλογές τοποθέτησης και την αποθήκευση των προστατευμένων αρχείων.
keywords:
- how to add watermark
- text watermark Java
- diagram watermarking
- GroupDocs.Watermark
lastmod: '2026-08-31'
og_description: Μάθετε πώς να προσθέσετε watermark σε διαγράμματα χρησιμοποιώντας
  το GroupDocs.Watermark for Java. Ακολουθήστε βήμα‑βήμα οδηγίες για να προστατεύσετε
  το οπτικό σας περιεχόμενο με text watermarks.
og_image_alt: Guide showing how to add watermark to diagram files using GroupDocs.Watermark
  for Java
og_title: Πώς να προσθέσετε watermark σε διαγράμματα με το GroupDocs.Watermark for
  Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-31'
  description: Learn how to add watermark to diagrams using GroupDocs.Watermark for
    Java. This guide covers setup, text watermark creation, placement options, and
    saving the protected files.
  headline: How to add watermark to diagrams with GroupDocs.Watermark for Java
  type: TechArticle
- description: Learn how to add watermark to diagrams using GroupDocs.Watermark for
    Java. This guide covers setup, text watermark creation, placement options, and
    saving the protected files.
  name: How to add watermark to diagrams with GroupDocs.Watermark for Java
  steps:
  - name: load the diagram document
    text: First, specify the file location and initialise the load options. **Definition
      anchor:** `DiagramLoadOptions` specifies how a diagram file is parsed, including
      page‑size handling and shape extraction.
  - name: create and configure the text watermark
    text: Instantiate a `TextWatermark` object and set its visual properties. **Definition
      anchor:** `TextWatermark` represents a textual overlay that can be styled with
      font, size, color, and opacity before being applied to a document.
  - name: configure watermark placement options
    text: Define where the watermark should appear within the diagram shapes. **Definition
      anchor:** `DiagramShapeWatermarkOptions` lets you target specific diagram elements
      (e.g., background pages, individual shapes) for watermark insertion.
  - name: add the watermark and save the document
    text: Apply the configured watermark to the loaded diagram and write the protected
      file to disk. **Definition anchor:** `Watermarker` is the core class that orchestrates
      loading, watermarking, and saving operations for supported file types.
  type: HowTo
- questions:
  - answer: A size between 14 pt and 24 pt balances readability and unobtrusiveness
      for most diagram dimensions.
    question: What is the best font size for a diagram watermark?
  - answer: Yes – use `textWatermark.setColor(Color.BLUE)` (or any `java.awt.Color`)
      to customise the hue.
    question: Can I change the watermark colour?
  - answer: Iterate over your file collection and reuse a single `Watermarker` per
      thread, calling `watermarker.add()` for each document before saving.
    question: How do I process a large batch of diagrams?
  - answer: GroupDocs.Watermark supports over 50 formats, including Visio (.vsdx),
      SVG, PNG, and JPEG. See the full list in the official [documentation](https://docs.groupdocs.com/watermark/java/).
    question: Are there any format limitations?
  - answer: 'Post questions on the community forum: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10).'
    question: Where can I get help if I encounter issues?
  type: FAQPage
tags:
- watermark
- GroupDocs.Watermark
- Java diagram
- text watermark
- document protection
title: Πώς να προσθέσετε watermark σε διαγράμματα με το GroupDocs.Watermark for Java
type: docs
url: /el/java/diagram-document-watermarking/groupdocs-watermark-java-add-text-watermarks-diagrams/
weight: 1
---

# Πώς να προσθέσετε υδατογράφημα σε διαγράμματα με GroupDocs.Watermark για Java

Η προστασία των εγγράφων διαγραμμάτων από μη εξουσιοδοτημένη χρήση είναι ουσιώδης για κάθε οργανισμό που μοιράζεται οπτικά περιουσιακά στοιχεία. Σε αυτό το ολοκληρωμένο tutorial θα ανακαλύψετε **πώς να προσθέσετε υδατογράφημα** σε διαγράμματα χρησιμοποιώντας το GroupDocs.Watermark για Java, από τη ρύθμιση του έργου έως την τελική αποθήκευση του εγγράφου. Ο οδηγός είναι γραμμένος για προγραμματιστές εξοικειωμένους με τη Java και στοχεύει να σας προσφέρει μια σαφή, έτοιμη για παραγωγή λύση.

## Γρήγορες απαντήσεις
- **Ποια βιβλιοθήκη διαχειρίζεται υδατογραφήματα διαγραμμάτων;** GroupDocs.Watermark for Java.
- **Ελάχιστη έκδοση Java;** JDK 8 or higher.
- **Μπορώ να επεξεργαστώ μαζικά πολλά διαγράμματα;** Yes – the API provides batch methods.
- **Χρειάζομαι άδεια για ανάπτυξη;** A temporary license removes all restrictions.
- **Πού αποθηκεύονται τα αρχεία με υδατογράφημα;** To any path you specify via `watermarker.save()`.

## Τι σημαίνει η προσθήκη υδατογραφήματος σε διαγράμματα;
Η προσθήκη υδατογραφήματος σημαίνει ενσωμάτωση ημιδιαφανούς κειμένου (ή εικόνων) σε ένα αρχείο διαγράμματος ώστε το οπτικό περιεχόμενο να μεταφέρει πληροφορίες ιδιοκτησίας. Το υδατογράφημα γίνεται μέρος του αρχείου και δεν μπορεί να αφαιρεθεί χωρίς να τροποποιηθεί το ίδιο το έγγραφο. Συνήθως αποδίδεται με μειωμένη διαφάνεια ώστε το υποκείμενο διάγραμμα να παραμένει αναγνώσιμο ενώ το υδατογράφημα παραμένει ορατό.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark για Java;
Το GroupDocs.Watermark υποστηρίζει **πάνω από 50 μορφές εισόδου και εξόδου** — συμπεριλαμβανομένων των Visio (.vsdx), SVG και κοινών τύπων εικόνας — και μπορεί να επεξεργαστεί διαγράμματα με έως και **500 σελίδες** χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη, παρέχοντας γρήγορες, χαμηλής μνήμης λειτουργίες για μεγάλης κλίμακας έργα. Η βιβλιοθήκη παρέχει επίσης APIs για μαζική επεξεργασία, προσαρμοσμένη περιστροφή και ρυθμίσεις χρώματος, καθιστώντας την κατάλληλη για επιχειρησιακά επίπεδα αγωγών εγγράφων.

## Προαπαιτούμενα
- **GroupDocs.Watermark for Java** ≥ 24.11 (λήψη από την επίσημη σελίδα releases).  
- **Java Development Kit (JDK)** 8 ή νεότερο.  
- Ένα IDE όπως το IntelliJ IDEA ή το Eclipse.  
- Maven για διαχείριση εξαρτήσεων (προαιρετικό αλλά συνιστάται).  

## Ρύθμιση του GroupDocs.Watermark για Java
### Ρύθμιση Maven
Προσθέστε την ακόλουθη εξάρτηση στο αρχείο `pom.xml` σας:

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
Αποκτήστε το πιο πρόσφατο JAR από την επίσημη σελίδα releases: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Απόκτηση άδειας
- **Δωρεάν δοκιμή** – αξιολογήστε όλες τις λειτουργίες χωρίς κόστος.  
- **Προσωρινή άδεια** – αφαιρεί περιορισμούς χρήσης κατά την ανάπτυξη.  
- **Εμπορική άδεια** – απαιτείται για παραγωγικές εγκαταστάσεις.

## Πώς να προσθέσετε υδατογράφημα σε διαγράμματα χρησιμοποιώντας το GroupDocs.Watermark για Java;
Η διαδικασία αποτελείται από τέσσερα κύρια βήματα: φόρτωση του πηγαίου διαγράμματος σε μια παρουσία `Watermarker`, δημιουργία ενός `TextWatermark` με την επιθυμητή εμφάνιση, ρύθμιση του πού θα εμφανιστεί το υδατογράφημα χρησιμοποιώντας `DiagramShapeWatermarkOptions`, και τέλος αποθήκευση του τροποποιημένου αρχείου στην επιθυμητή τοποθεσία. Κάθε βήμα παρουσιάζεται με σύντομα αποσπάσματα κώδικα παρακάτω.

### Βήμα 1: φόρτωση του εγγράφου διαγράμματος
Πρώτα, καθορίστε τη θέση του αρχείου και αρχικοποιήστε τις επιλογές φόρτωσης.

```java
String inputPath = "YOUR_DOCUMENT_DIRECTORY";
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker(inputPath, loadOptions);
```

**Αγκύρωση ορισμού:** `DiagramLoadOptions` καθορίζει πώς γίνεται η ανάλυση ενός αρχείου διαγράμματος, συμπεριλαμβανομένου του χειρισμού μεγέθους σελίδας και της εξαγωγής σχημάτων.

### Βήμα 2: δημιουργία και ρύθμιση του κειμενικού υδατογραφήματος
Δημιουργήστε ένα αντικείμενο `TextWatermark` και ορίστε τις οπτικές του ιδιότητες.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark 1", new Font("Calibri", 19));
```

**Αγκύρωση ορισμού:** `TextWatermark` αντιπροσωπεύει μια κειμενική επικάλυψη που μπορεί να μορφοποιηθεί με γραμματοσειρά, μέγεθος, χρώμα και διαφάνεια πριν εφαρμοστεί σε ένα έγγραφο.

### Βήμα 3: ρύθμιση επιλογών τοποθέτησης υδατογραφήματος
Ορίστε πού θα εμφανιστεί το υδατογράφημα εντός των σχημάτων του διαγράμματος.

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacementType(DiagramWatermarkPlacementType.SeparateBackgrounds);
```

**Αγκύρωση ορισμού:** `DiagramShapeWatermarkOptions` σας επιτρέπει να στοχεύσετε συγκεκριμένα στοιχεία του διαγράμματος (π.χ. σελίδες φόντου, μεμονωμένα σχήματα) για εισαγωγή υδατογραφήματος.

### Βήμα 4: προσθήκη του υδατογραφήματος και αποθήκευση του εγγράφου
Εφαρμόστε το ρυθμισμένο υδατογράφημα στο φορτωμένο διάγραμμα και γράψτε το προστατευμένο αρχείο στο δίσκο.

```java
watermarker.add(textWatermark, options);
String outputPath = "YOUR_OUTPUT_DIRECTORY";
watermarker.save(outputPath);
watermarker.close();
```

**Αγκύρωση ορισμού:** `Watermarker` είναι η κεντρική κλάση που συντονίζει τις λειτουργίες φόρτωσης, υδατογράφησης και αποθήκευσης για υποστηριζόμενους τύπους αρχείων.

## Πρακτικές εφαρμογές
Η ενσωμάτωση υδατογραφημάτων είναι πολύτιμη σε πολλές πραγματικές περιπτώσεις:

- **Προστασία πνευματικής ιδιοκτησίας:** Αποτρέψτε τους ανταγωνιστές από την επαναχρησιμοποίηση ιδιόκτητων διαγραμμάτων ροής.  
- **Ενίσχυση μάρκας:** Εμφανίστε το όνομα της εταιρείας σας σε όλα τα εξαγόμενα διαγράμματα.  
- **Νομική συμμόρφωση:** Σημειώστε τα εμπιστευτικά σχέδια με “Confidential – Do Not Distribute.”  
- **Ακαδημαϊκή ακεραιότητα:** Επισήμανση των υποβολών των φοιτητών με μοναδικά αναγνωριστικά.

Μπορείτε να ενσωματώσετε αυτή τη ροή εργασίας σε συστήματα διαχείρισης εγγράφων, CI pipelines ή υπηρεσίες μαζικής επεξεργασίας για να αυτοματοποιήσετε την προστασία χιλιάδων αρχείων.

## Σκέψεις απόδοσης
- **Βελτιστοποίηση μνήμης:** Επαναχρησιμοποιήστε τις παρουσίες `Watermarker` όπου είναι δυνατόν και κλείστε τις με `watermarker.close()` για απελευθέρωση των εγγενών πόρων.  
- **Διαχείριση μεγάλων αρχείων:** Η βιβλιοθήκη επεξεργάζεται τις σελίδες κατά απαίτηση, έτσι ακόμη και διαγράμματα 300 σελίδων παραμένουν κάτω από 200 MB χρήσης heap σε μια τυπική JVM 8 GB.  
- **Ασφάλεια νήματος:** Κάθε νήμα πρέπει να εργάζεται με τη δική του παρουσία `Watermarker`; το API δεν είναι παγκοσμίως συγχρονισμένο.

## Συχνές ερωτήσεις

**Q:** Ποιο είναι το καλύτερο μέγεθος γραμματοσειράς για υδατογράφημα διαγράμματος;  
**A:** Ένα μέγεθος μεταξύ 14 pt και 24 pt εξισορροπεί την αναγνωσιμότητα και την μη ενοχλητικότητα για τις περισσότερες διαστάσεις διαγράμματος.

**Q:** Μπορώ να αλλάξω το χρώμα του υδατογραφήματος;  
**A:** Ναι – χρησιμοποιήστε `textWatermark.setColor(Color.BLUE)` (ή οποιοδήποτε `java.awt.Color`) για να προσαρμόσετε την απόχρωση.

**Q:** Πώς επεξεργάζομαι μια μεγάλη δέσμη διαγραμμάτων;  
**A:** Επανάληψη πάνω στη συλλογή αρχείων σας και επαναχρησιμοποίηση ενός μόνο `Watermarker` ανά νήμα, καλώντας `watermarker.add()` για κάθε έγγραφο πριν την αποθήκευση.

**Q:** Υπάρχουν περιορισμοί μορφής;  
**A:** Το GroupDocs.Watermark υποστηρίζει πάνω από 50 μορφές, συμπεριλαμβανομένων των Visio (.vsdx), SVG, PNG και JPEG. Δείτε την πλήρη λίστα στην επίσημη [documentation](https://docs.groupdocs.com/watermark/java/).

**Q:** Πού μπορώ να λάβω βοήθεια αν αντιμετωπίσω προβλήματα;  
**A:** Δημοσιεύστε ερωτήσεις στο φόρουμ της κοινότητας: [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10).

## Πόροι
- **Τεκμηρίωση:** [GroupDocs.Watermark Documentation](https://docs.groupdocs.com/watermark/java/)  
- **Αναφορά API:** [Java API Reference](https://reference.groupdocs.com/watermark/java)  
- **Λήψη:** [Get GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- **Αποθετήριο GitHub:** [GroupDocs Watermark Java](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- **Δωρεάν φόρουμ υποστήριξης:** [GroupDocs Forum](https://forum.groupdocs.com/c/watermark/10)  
- **Προσωρινή άδεια:** [Acquire Temporary License](https://purchase.groupdocs.com/temporary-license/)  

Εφαρμόστε τα παραπάνω βήματα για να προστατεύσετε τα διαγράμματα σας με ένα επαγγελματικό κειμενικό υδατογράφημα. Πειραματιστείτε με διαφορετικές γραμματοσειρές, χρώματα και επιλογές τοποθέτησης ώστε να ταιριάζουν με τις οδηγίες της μάρκας σας, και σκεφτείτε την αυτοματοποίηση της διαδικασίας για μεγάλες βιβλιοθήκες εγγράφων.

---

**Τελευταία ενημέρωση:** 2026-08-31  
**Δοκιμάστηκε με:** GroupDocs.Watermark 24.11 for Java  
**Συγγραφέας:** GroupDocs

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.DiagramLoadOptions;
```

## Σχετικά μαθήματα

- [Οδηγός προσθήκης υδατογραφημάτων σε διαγράμματα χρησιμοποιώντας το GroupDocs.Watermark για Java](/watermark/java/diagram-document-watermarking/add-watermarks-groupdocs-diagrams-java/)
- [Πώς να προσθέσετε κειμενικό υδατογράφημα σε PDF χρησιμοποιώντας το GroupDocs.Watermark για Java: Οδηγός βήμα προς βήμα](/watermark/java/pdf-document-watermarking/add-text-watermark-pdf-groupdocs-java/)
- [Πώς να προσθέσετε κειμενικά υδατογραφήματα σε εικόνες εγγράφων Word χρησιμοποιώντας το GroupDocs.Watermark για Java](/watermark/java/image-watermarks/add-watermarks-word-images-groupdocs-java/)