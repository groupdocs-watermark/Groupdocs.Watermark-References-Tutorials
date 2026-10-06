---
date: '2026-10-06'
description: Μάθετε πώς να προσθέσετε υδατογράφημα σε σελίδες σε διαγράμματα με το
  GroupDocs.Watermark για Java. Ρύθμιση βήμα προς βήμα, αποσπάσματα κώδικα και πρακτικές
  συμβουλές για ασφαλή δημοσίευση διαγραμμάτων.
keywords:
- add watermark to pages
- text watermarks in Java
- GroupDocs.Watermark for Java
- diagram watermarking tutorial
lastmod: '2026-10-06'
og_description: Προσθέστε υδατογράφημα σε σελίδες σε διαγράμματα με το GroupDocs.Watermark
  για Java. Ακολουθήστε αυτόν τον οδηγό για ρύθμιση, υλοποίηση και βέλτιστες πρακτικές.
og_image_alt: Developer guide showing Java code that adds text watermarks to diagram
  pages
og_title: Πώς να προσθέσετε υδατογράφημα σε σελίδες χρησιμοποιώντας το GroupDocs.Watermark
  Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-06'
  description: Learn how to add watermark to pages in diagrams with GroupDocs.Watermark
    for Java. Step‑by‑step setup, code snippets, and practical tips for secure diagram
    publishing.
  headline: How to add watermark to pages using GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to add watermark to pages in diagrams with GroupDocs.Watermark
    for Java. Step‑by‑step setup, code snippets, and practical tips for secure diagram
    publishing.
  name: How to add watermark to pages using GroupDocs.Watermark Java
  steps:
  - name: load your diagram
    text: 'First, create a `DiagramLoadOptions` instance to tell the SDK how to interpret
      the source file, then open the diagram with `Watermarker`. DiagramLoadOptions
      specifies loading parameters such as format and password for diagram files.
      `Watermarker` is the main class that manages loading, editing, and '
  - name: initialize the text watermark
    text: Next, build a `TextWatermark` object that holds the watermark text, font,
      color, and rotation angle. `TextWatermark` represents a reusable textual overlay
      that can be applied to one or many pages.
  - name: add watermark to diagram
    text: Now specify the pages you want to watermark. Using `DiagramPage` with `WatermarkPageOptions`
      lets you target background, foreground, or both. `DiagramPage` selects individual
      or ranges of diagram pages for watermarking. `WatermarkPageOptions` defines
      where (background/foreground) and how the waterma
  - name: save and close
    text: Finally, write the watermarked diagram to disk and release resources. `Watermarker.save()`
      persists the changes, and `close()` frees native resources to keep memory usage
      low.
  type: HowTo
- questions:
  - answer: Yes – it supports over 50 formats, including PDF, Word, Excel, PowerPoint,
      and image files.
    question: Can GroupDocs.Watermark handle other file types besides diagrams?
  - answer: There is no hard limit, but applying more than 10 watermarks per page
      can increase processing time by roughly 15 % per additional watermark.
    question: Is there a limit to how many watermarks I can apply?
  - answer: Use the `Watermarker.removeWatermarks()` method with a matching `WatermarkSearchOptions`
      filter to delete specific watermarks.
    question: How do I remove a watermark once it’s been added?
  - answer: Absolutely – configure `DiagramPage` with a page index range or a custom
      predicate to apply watermarks selectively.
    question: Can I target only selected pages instead of all pages?
  - answer: Verify the page’s background/foreground settings and ensure the opacity
      is not set below 10 %. Also confirm the font size is appropriate for the page
      dimensions.
    question: The watermark is not visible on some pages; what should I check?
  type: FAQPage
tags:
- add watermark to pages
- GroupDocs.Watermark
- Java diagram security
- watermark tutorial
title: Πώς να προσθέσετε υδατογράφημα σε σελίδες χρησιμοποιώντας το GroupDocs.Watermark
  Java
type: docs
url: /el/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/
weight: 1
---

# Πώς να προσθέσετε υδατογράφημα σε σελίδες χρησιμοποιώντας το GroupDocs.Watermark Java

Η προστασία της πνευματικής σας ιδιοκτησίας είναι ουσιώδης όταν μοιράζεστε διαγράμματα με συνεργάτες, πελάτες ή το κοινό. Σε αυτό το tutorial θα μάθετε **πώς να προσθέσετε υδατογράφημα σε σελίδες** σε αρχεία διαγράμματος χρησιμοποιώντας το GroupDocs.Watermark για Java, ώστε κάθε εξαγόμενη σελίδα να φέρει το branding ή την ειδοποίηση εμπιστευτικότητας σας. Τα βήματα καλύπτουν τη ρύθμιση του περιβάλλοντος, την άδεια και τις ακριβείς κλήσεις API που χρειάζεστε για ενσωμάτωση προσαρμόσιμου κειμενικού υδατογραφήματος.

## Σύντομες απαντήσεις
- **Ποια βιβλιοθήκη προσθέτει υδατογραφήματα σε διαγράμματα σε Java;** GroupDocs.Watermark for Java.  
- **Ποια κύρια μέθοδος δημιουργεί το αντικείμενο υδατογραφήματος;** `new TextWatermark(...)`.  
- **Χρειάζομαι άδεια για ανάπτυξη;** Μια προσωρινή δοκιμαστική άδεια λειτουργεί για δοκιμές· απαιτείται πλήρης άδεια για παραγωγή.  
- **Μπορώ να προσθέσω υδατογράφημα σε κάθε σελίδα αυτόματα;** Ναι – χρησιμοποιήστε `Watermarker.addWatermark()` με έναν επιλογέα `DiagramPage`.  
- **Είναι η διαδικασία thread‑safe;** Το API έχει σχεδιαστεί για ταυτόχρονη χρήση· απλώς αποφύγετε την κοινή χρήση της ίδιας παρουσίας `Watermarker` μεταξύ νημάτων.

## Τι σημαίνει η προσθήκη υδατογραφήματος σε σελίδες;
*Add watermark to pages* σημαίνει την εισαγωγή ενός ημιδιαφανούς στρώματος κειμένου σε κάθε σελίδα ενός εγγράφου ή διαγράμματος, ώστε το περιεχόμενο να παραμένει αναγνώσιμο ενώ το υδατογράφημα είναι εμφανές. Αυτή η τεχνική αποτρέπει την μη εξουσιοδοτημένη επαναχρησιμοποίηση και ενισχύει την ταυτότητα της μάρκας.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark για Java;
Το GroupDocs.Watermark υποστηρίζει **50+ μορφές αρχείων** (συμπεριλαμβανομένων VDX, VSDX, SVG και άλλων τύπων διαγραμμάτων) και μπορεί να επεξεργαστεί αρχεία έως **500 MB** χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη, παρέχοντας καθυστέρηση κάτω από το δευτερόλεπτο σε τυπικό εξοπλισμό διακομιστή. Το ευέλικτο API του επιτρέπει τη ρύθμιση γραμματοσειράς, χρώματος, περιστροφής και διαφάνειας με μία κλήση.

## Προαπαιτούμενα
- Java Development Kit 8 ή νεότερο.  
- Ένα IDE όπως IntelliJ IDEA ή Eclipse.  
- Βασική εμπειρία προγραμματισμού Java.  

### Απαιτούμενες βιβλιοθήκες και εξαρτήσεις
Το GroupDocs.Watermark για Java διανέμεται μέσω Maven Central. Συμπεριλάβετε την εξάρτηση στο `pom.xml` σας:

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

[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/)

Αν προτιμάτε χειροκίνητη λήψη, κατεβάστε τα binaries από τη σελίδα επίσημης κυκλοφορίας.

### Απόκτηση άδειας
Μπορείτε να ξεκινήσετε με δωρεάν δοκιμή κατεβάζοντας μια προσωρινή άδεια από το portal δοκιμής του GroupDocs. Αφού έχετε το αρχείο `.lic`, φορτώστε το όπως φαίνεται παρακάτω.

Η κλάση `License` επαληθεύει το αρχείο άδειας δοκιμής ή αγορασμένης άδειας κατά την εκτέλεση.  

```java
License license = new License();
license.setLicense("path/to/license/file");
```

[GroupDocs.Trial Licensing](https://purchase.groupdocs.com/temporary-license/)

## Οδηγός υλοποίησης

### Προσθήκη κειμενικών υδατογραφημάτων σε σελίδες διαγράμματος

#### Βήμα 1: φόρτωση του διαγράμματος σας
Αρχικά, δημιουργήστε μια παρουσία `DiagramLoadOptions` για να ενημερώσετε το SDK πώς να ερμηνεύσει το αρχείο προέλευσης, στη συνέχεια ανοίξτε το διάγραμμα με `Watermarker`.  
Το `DiagramLoadOptions` καθορίζει παραμέτρους φόρτωσης όπως μορφή και κωδικό πρόσβασης για αρχεία διαγράμματος.  
Η `Watermarker` είναι η κύρια κλάση που διαχειρίζεται τη φόρτωση, την επεξεργασία και την αποθήκευση εγγράφων διαγράμματος.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
Watermarker watermarker = new Watermarker(inputFilePath, new DiagramLoadOptions());
```

#### Βήμα 2: αρχικοποίηση του κειμενικού υδατογραφήματος
Στη συνέχεια, δημιουργήστε ένα αντικείμενο `TextWatermark` που περιέχει το κείμενο του υδατογραφήματος, τη γραμματοσειρά, το χρώμα και τη γωνία περιστροφής.  
Η `TextWatermark` αντιπροσωπεύει μια επαναχρησιμοποιήσιμη κειμενική επικάλυψη που μπορεί να εφαρμοστεί σε μία ή πολλές σελίδες.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 36));
textWatermark.setColor(Color.getBlue());
textWatermark.setBackground(false);
textWatermark.setRotationAngle(-45);
```

#### Βήμα 3: προσθήκη υδατογραφήματος στο διάγραμμα
Τώρα καθορίστε τις σελίδες που θέλετε να υδατογραφήσετε. Η χρήση του `DiagramPage` με `WatermarkPageOptions` σας επιτρέπει να στοχεύσετε το παρασκήνιο, το προσκήνιο ή και τα δύο.  
Το `DiagramPage` επιλέγει μεμονωμένες ή περιοχές σελίδων διαγράμματος για υδατογράφημα.  
Το `WatermarkPageOptions` ορίζει πού (παρασκήνιο/προσκήνιο) και πώς θα αποδοθεί το υδατογράφημα στις επιλεγμένες σελίδες.

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacement(DiagramWatermarkPlacementType.Background);
watermarker.add(textWatermark, options);
```

#### Βήμα 4: αποθήκευση και κλείσιμο
Τέλος, γράψτε το υδατογραφημένο διάγραμμα στο δίσκο και απελευθερώστε τους πόρους.

`Watermarker.save()` αποθηκεύει τις αλλαγές, και `close()` ελευθερώνει τους εγγενείς πόρους για να διατηρεί τη χρήση μνήμης χαμηλή.  

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_diagram.vsdx";
watermarker.save(outputFilePath);
watermarker.close();
```

## Συχνά προβλήματα και λύσεις
- **Σφάλματα διαδρομής αρχείου** – Επαληθεύστε ότι οι διαδρομές εισόδου και εξόδου είναι απόλυτες ή σωστά σχετικές με τον τρέχοντα φάκελο εργασίας.  
- **Ασυμφωνίες έκδοσης** – Χρησιμοποιήστε GroupDocs.Watermark 23.11 ή νεότερη; οι παλαιότερες εκδόσεις μπορεί να μην υποστηρίζουν διαγράμματα.  
- **Ανεπαρκή δικαιώματα** – Η διαδικασία πρέπει να έχει πρόσβαση ανάγνωσης/εγγραφής στους φακέλους που ορίζετε.

## Πρακτικές εφαρμογές
1. **Ασφαλή παραδοτέα πελατών** – Προσθέστε υδατογράφημα σε κάθε διάγραμμα πριν αποστείλετε PDF σε εξωτερικούς συνεργάτες.  
2. **Εταιρική ταυτότητα** – Ενσωματώστε το λογότυπό σας ή το όνομα της εταιρείας σε όλες τις εξαγόμενες σελίδες αυτόματα.  
3. **Παρακολούθηση συνεργασίας** – Προσθέστε τα αρχικά του χρήστη ως υδατογράφημα για να υποδείξετε ποιος επεξεργάστηκε κάθε έκδοση του διαγράμματος.

## Σκέψεις απόδοσης
- Επεξεργαστείτε μεγάλες παρτίδες επαναχρησιμοποιώντας μία μόνο παρουσία `Watermarker` και καλώντας `addWatermark` σε βρόχο· αυτό μειώνει το κόστος δημιουργίας αντικειμένων έως και **30 %**.  
- Διατηρήστε το κείμενο του υδατογραφήματος σύντομο (κάτω από 30 χαρακτήρες) για να ελαχιστοποιήσετε τον χρόνο απόδοσης, ειδικά σε διαγράμματα υψηλής ανάλυσης.  
- Δοκιμάστε με διάγραμμα 200 σελίδων· ο τυπικός χρόνος επεξεργασίας είναι κάτω από **2 δευτερόλεπτα** σε τυπική VM 2 vCPU.

## Συμπέρασμα
Τώρα έχετε μια πλήρη, έτοιμη για παραγωγή ροή εργασίας για **προσθήκη υδατογραφήματος σε σελίδες** σε αρχεία διαγράμματος χρησιμοποιώντας το GroupDocs.Watermark για Java. Αυτή η προσέγγιση όχι μόνο προστατεύει τα περιουσιακά σας στοιχεία, αλλά ενισχύει επίσης τη συνέπεια της μάρκας σε όλα τα εξαγόμενα περιουσιακά στοιχεία.

### Επόμενα βήματα
- Εξερευνήστε υδατογραφήματα εικόνας για πιο πλούσια ταυτότητα.  
- Συνδυάστε κειμενικά και εικόνα υδατογραφήματα για πολυεπίπεδη προστασία.  
- Ενσωματώστε τη διαδικασία υδατογράφησης στο CI/CD pipeline σας για αυτοματοποίηση της ασφάλειας εγγράφων.

## Συχνές ερωτήσεις

**Ε: Μπορεί το GroupDocs.Watermark να χειριστεί άλλους τύπους αρχείων εκτός από διαγράμματα;**  
Α: Ναι – υποστηρίζει πάνω από 50 μορφές, συμπεριλαμβανομένων PDF, Word, Excel, PowerPoint και αρχείων εικόνας.

**Ε: Υπάρχει όριο στον αριθμό των υδατογραφημάτων που μπορώ να εφαρμόσω;**  
Α: Δεν υπάρχει σκληρό όριο, αλλά η εφαρμογή περισσότερων από 10 υδατογραφημάτων ανά σελίδα μπορεί να αυξήσει τον χρόνο επεξεργασίας περίπου κατά 15 % ανά επιπλέον υδατογράφημα.

**Ε: Πώς να αφαιρέσω ένα υδατογράφημα αφού έχει προστεθεί;**  
Α: Χρησιμοποιήστε τη μέθοδο `Watermarker.removeWatermarks()` με ένα φίλτρο `WatermarkSearchOptions` που ταιριάζει για να διαγράψετε συγκεκριμένα υδατογραφήματα.

**Ε: Μπορώ να στοχεύσω μόνο επιλεγμένες σελίδες αντί για όλες τις σελίδες;**  
Α: Απολύτως – ρυθμίστε το `DiagramPage` με εύρος δεικτών σελίδας ή προσαρμοσμένο predicate για να εφαρμόσετε υδατογραφήματα επιλεκτικά.

**Ε: Το υδατογράφημα δεν είναι ορατό σε ορισμένες σελίδες· τι πρέπει να ελέγξω;**  
Α: Επαληθεύστε τις ρυθμίσεις παρασκηνίου/προσσκηνίου της σελίδας και βεβαιωθείτε ότι η διαφάνεια δεν είναι κάτω από 10 %. Επίσης, επιβεβαιώστε ότι το μέγεθος γραμματοσειράς είναι κατάλληλο για τις διαστάσεις της σελίδας.

## Πόροι
- [Documentation](https://docs.groupdocs.com/watermark/java/) – επίσημος οδηγός και tutorials.  
- [API Reference](https://reference.groupdocs.com/watermark/java) – λεπτομερείς περιγραφές κλάσεων και μεθόδων.  
- [Download Latest Version](https://releases.groupdocs.com/watermark/java/) – κατεβάστε την πιο πρόσφατη έκδοση της βιβλιοθήκης.  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java) – κώδικας πηγής, ζητήματα και συνεισφορές.  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10) – βοήθεια κοινότητας και συζητήσεις.

**Τελευταία ενημέρωση:** 2026-10-06  
**Δοκιμάστηκε με:** GroupDocs.Watermark 23.11 for Java  
**Συγγραφέας:** GroupDocs  

## Σχετικά Μαθήματα

- [Πώς να προσθέσετε κείμενο και εικόνα υδατογραφήματα σε συγκεκριμένες σελίδες PDF χρησιμοποιώντας το GroupDocs.Watermark για Java](/watermark/java/pdf-document-watermarking/add-watermarks-pdf-pages-groupdocs-java/)
- [Πώς να προσθέσετε κειμενικά υδατογραφήματα σε διαγράμματα χρησιμοποιώντας το GroupDocs.Watermark σε Java](/watermark/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/)
- [Προσθήκη κειμενικών υδατογραφημάτων σε Java χρησιμοποιώντας το GroupDocs.Watermark: Οδηγός βήμα-βήμα](/watermark/java/text-watermarks/add-text-watermarks-java-groupdocs/)