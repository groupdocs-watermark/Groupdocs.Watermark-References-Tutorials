---
date: 2026-11-13
description: Μάθετε πώς να εξάγετε metadata, να εμφανίσετε τα υποστηριζόμενα formats
  και να ανακτήσετε document information χρησιμοποιώντας το GroupDocs.Watermark for
  Java.
keywords:
- how to extract metadata
- list supported formats
- extract document metadata
- retrieve document info
- extract slide background
lastmod: 2026-11-13
og_description: Πώς να εξάγετε metadata χρησιμοποιώντας το GroupDocs.Watermark for
  Java. Μάθετε πώς να εμφανίσετε τα υποστηριζόμενα formats, να ανακτήσετε document
  info και να εξάγετε slide backgrounds σε λίγα λεπτά.
og_image_alt: Guide showing metadata extraction and format listing with GroupDocs.Watermark
  for Java
og_title: Πώς να εξάγετε metadata με το GroupDocs.Watermark for Java
schemas:
- author: GroupDocs
  dateModified: '2026-11-13'
  description: Learn how to extract metadata, list supported formats, and retrieve
    document information using GroupDocs.Watermark for Java.
  headline: How to extract metadata with GroupDocs.Watermark for Java
  type: TechArticle
- questions:
  - answer: Yes, provide the password when opening the document; the API will decrypt
      it in memory and then read the metadata.
    question: Can I extract metadata from password‑protected documents?
  - answer: The core extraction features are compatible with Android API 21+ when
      bundled as a standard JAR.
    question: Does the library work on Android?
  - answer: Use the `getCustomProperties()` method on the `DocumentInfo` object; it
      returns a map of key‑value pairs you can iterate over.
    question: How do I handle custom metadata fields?
  - answer: Wrap the extraction logic in a loop and reuse a single `Watermark` instance;
      the SDK is designed for high‑throughput scenarios.
    question: Is there a way to batch‑process many files?
  - answer: GroupDocs.Watermark offers perpetual, subscription, and temporary licenses;
      the temporary license is ideal for evaluation and CI pipelines.
    question: What licensing options are available?
  type: FAQPage
tags:
- metadata extraction
- GroupDocs.Watermark
- Java document processing
- supported formats
title: Πώς να εξάγετε metadata με το GroupDocs.Watermark for Java
type: docs
url: /el/java/document-information/
weight: 14
---

# Πώς να εξάγετε μεταδεδομένα με το GroupDocs.Watermark για Java

Σε αυτόν τον οδηγό θα ανακαλύψετε **πώς να εξάγετε μεταδεδομένα** από ένα ευρύ φάσμα τύπων εγγράφων χρησιμοποιώντας το GroupDocs.Watermark για Java. Είτε χρειάζεστε να διαβάσετε τον τύπο αρχείου, τον αριθμό σελίδων, τα στοιχεία του δημιουργού ή προσαρμοσμένες ιδιότητες, η βιβλιοθήκη σας παρέχει προγραμματιστική πρόσβαση σε αυτές τις πληροφορίες ώστε να μπορείτε να λαμβάνετε έξυπνες αποφάσεις σχετικά με την τοποθέτηση υδατογραφήματος, τη δρομολόγηση εγγράφων ή τους ελέγχους συμμόρφωσης. Ο οδηγός δείχνει επίσης πώς να εμφανίσετε τις υποστηριζόμενες μορφές, να εξάγετε δεδομένα φόντου διαφάνειας και να ανακτήσετε άλλες χρήσιμες χαρακτηριστικές πληροφορίες εγγράφου.

## Γρήγορες απαντήσεις
- **Μπορώ να εξάγω μεταδεδομένα από αρχεία PDF και Word;** Ναι, το API διαβάζει μεταδεδομένα από πάνω από 70 κοινές μορφές.  
- **Χρειάζομαι άδεια για ανάπτυξη;** Μια δωρεάν προσωρινή άδεια λειτουργεί για δοκιμές· απαιτείται πλήρης άδεια για παραγωγή.  
- **Ποια έκδοση της Java απαιτείται;** Υποστηρίζεται η Java 8 ή νεότερη.  
- **Η βιβλιοθήκη είναι thread‑safe;** Οι βασικές κλάσεις εξαγωγής έχουν σχεδιαστεί για ταυτόχροντη χρήση.  
- **Πόσες μορφές αναγνωρίζονται;** Πάνω από 70 μορφές εισόδου και εξόδου αναγνωρίζονται αμέσως.

## Τι είναι η εξαγωγή μεταδεδομένων;
Η εξαγωγή μεταδεδομένων είναι η διαδικασία ανάγνωσης ενσωματωμένων πληροφοριών—όπως δημιουργός, ημερομηνία δημιουργίας, αριθμός σελίδων και προσαρμοσμένες ιδιότητες—από ένα αρχείο εγγράφου χωρίς να αλλάζει το περιεχόμενό του. Επιτρέπει αυτοματοποιημένες ροές εργασίας που εξαρτώνται από χαρακτηριστικά εγγράφου. Συνήθως περιλαμβάνει ιδιότητες όπως τίτλος, λέξεις‑κλειδιά και χρονικές σφραγίδες τροποποίησης, που μπορούν να αξιοποιηθούν για ευρετηρίαση και αναφορές συμμόρφωσης.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark για Java;
Το GroupDocs.Watermark για Java υποστηρίζει **70+ μορφές αρχείων**, συμπεριλαμβανομένων PDF, DOCX, PPTX, XLSX και τύπων εικόνων, και μπορεί να επεξεργαστεί έγγραφα έως 500 MB χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη. Το API του επιστρέφει τα μεταδεδομένα σε ένα ενιαίο, συνεπές αντικείμενο, μειώνοντας την ανάγκη για μορφο‑συγκεκριμένους αναλυτές και μειώνοντας τον χρόνο ανάπτυξης έως και 40 %.

## Προαπαιτούμενα
- Java 8 ή νεότερη εγκατεστημένη στο μηχάνημά σας.  
- Maven ή Gradle για τη διαχείριση της εξάρτησης `groupdocs-watermark`.  
- Ένα προσωρινό ή πλήρες αρχείο άδειας GroupDocs.Watermark.

## Πώς να εξάγετε μεταδεδομένα βήμα προς βήμα

### Πώς να ανακτήσω βασικές πληροφορίες εγγράφου;
Η κλάση `Watermark` αντιπροσωπεύει ένα έγγραφο και παρέχει πρόσβαση στα μεταδεδομένα του. Η μέθοδος `getDocumentInfo()` εξάγει το αντικείμενο μεταδεδομένων από το φορτωμένο έγγραφο. Φορτώστε το έγγραφο με την κλάση `Watermark`, στη συνέχεια καλέστε `getDocumentInfo()` για να λάβετε ένα αντικείμενο που περιέχει τύπο αρχείου, μέγεθος, αριθμό σελίδων και ημερομηνία δημιουργίας. Αυτή η ενιαία κλήση επιστρέφει όλα τα βασικά μεταδεδομένα σε λιγότερο από ένα δευτερόλεπτο για τυπικά αρχεία κάτω από 100 MB. Το επιστρεφόμενο αντικείμενο `DocumentInfo` περιλαμβάνει επίσης τον δημιουργό του εγγράφου, την ημερομηνία τελευταίας τροποποίησης και τυχόν ενσωματωμένες προσαρμοσμένες ιδιότητες, παρέχοντας μια ολοκληρωμένη επισκόπηση.

### Πώς μπορώ να εμφανίσω όλες τις υποστηριζόμενες μορφές αρχείων;
Η βοηθητική κλάση `SupportedFormats` παρέχει έναν κατάλογο όλων των τύπων αρχείων που μπορεί να επεξεργαστεί το SDK. Χρησιμοποιήστε το εργαλείο `SupportedFormats` που παρέχεται από το SDK. Επιστρέφει μια συλλογή αναγνωριστικών μορφών που μπορείτε να εμφανίσετε ή να επικυρώσετε πριν από τη μεταφόρτωση αρχείων, εξασφαλίζοντας συμβατότητα και αποτρέποντας σφάλματα χρόνου εκτέλεσης. Κάθε καταχώρηση περιλαμβάνει το όνομα της μορφής, την τυπική επέκταση αρχείου και μια σύντομη περιγραφή των δυνατοτήτων της, βοηθώντας τους προγραμματιστές να επικυρώσουν τις εισόδους πριν από την επεξεργασία.

### Πώς να εξάγω λεπτομέρειες φόντου διαφάνειας από αρχείο PowerPoint;
Το `SlideInfo` είναι ένα αντικείμενο που περιγράφει τις οπτικές ιδιότητες μιας διαφάνειας, όπως η εικόνα φόντου και οι διαστάσεις της. Η μέθοδος `getSlides()` επιστρέφει μια συλλογή αντικειμένων `SlideInfo` για κάθε διαφάνεια στην παρουσίαση. Το αντικείμενο `SlideInfo` εκθέτει τις διαστάσεις της εικόνας φόντου, το μέγεθος αρχείου και το βάθος χρώματος. Πρόσβαση σε αυτό μέσω της συλλογής `getSlides()`, στη συνέχεια επαναλάβετε κάθε διαφάνεια για να διαβάσετε τις ιδιότητες φόντου—χρήσιμο για δυναμική στυλιζάρισμα ή δημιουργία μικρογραφιών. Αυτές οι λεπτομέρειες μπορούν να χρησιμοποιηθούν για δημιουργία μικρογραφιών, εφαρμογή συνεπούς στυλ ή αντικατάσταση φόντων προγραμματιστικά σε πολλαπλές παρουσιάσεις.

## Συχνά προβλήματα και λύσεις
- **Missing metadata:** Ορισμένα παλαιότερα αρχεία μπορεί να μην περιέχουν τυπικές ιδιότητες. Σε αυτήν την περίπτωση, ενεργοποιήστε τη σημαία `extractCustomProperties` για να αντλήσετε τυχόν πεδία ορισμένα από τον χρήστη.  
- **Large files cause timeouts:** Αυξήστε τη ρύθμιση `maxMemory` του SDK ή επεξεργαστείτε το έγγραφο σε λειτουργία streaming για να αποφύγετε τη φόρτωση ολόκληρου του αρχείου στη μνήμη RAM.  
- **Unsupported format error:** Επαληθεύστε τη μορφή έναντι του καταλόγου που επιστρέφεται από το `SupportedFormats` πριν επιχειρήσετε την εξαγωγή.

## Συχνές ερωτήσεις

**Q: Μπορώ να εξάγω μεταδεδομένα από έγγραφα προστατευμένα με κωδικό;**  
A: Ναι, παρέχετε τον κωδικό πρόσβασης κατά το άνοιγμα του εγγράφου· το API θα το αποκρυπτογραφήσει στη μνήμη και στη συνέχεια θα διαβάσει τα μεταδεδομένα.

**Q: Η βιβλιοθήκη λειτουργεί σε Android;**  
A: Οι βασικές λειτουργίες εξαγωγής είναι συμβατές με το Android API 21+ όταν συσκευάζονται ως τυπικό JAR.

**Q: Πώς να διαχειριστώ προσαρμοσμένα πεδία μεταδεδομένων;**  
A: Χρησιμοποιήστε τη μέθοδο `getCustomProperties()` στο αντικείμενο `DocumentInfo`; επιστρέφει έναν χάρτη ζευγών κλειδί‑τιμή που μπορείτε να επαναλάβετε.

**Q: Υπάρχει τρόπος να επεξεργαστώ μαζικά πολλά αρχεία;**  
A: Τυλίξτε τη λογική εξαγωγής σε έναν βρόχο και επαναχρησιμοποιήστε μια ενιαία παρουσία της `Watermark`; το SDK έχει σχεδιαστεί για σενάρια υψηλής διαπερατότητας.

**Q: Ποιες επιλογές αδειών είναι διαθέσιμες;**  
A: Το GroupDocs.Watermark προσφέρει δια βίου, συνδρομητικές και προσωρινές άδειες· η προσωρινή άδεια είναι ιδανική για αξιολόγηση και pipelines CI.

## Διαθέσιμα μαθήματα

### [Εξαγωγή Πληροφοριών Εγγράφου Χρησιμοποιώντας το GroupDocs.Watermark για Java&#58; Πλήρης Οδηγός](./extract-document-info-groupdocs-watermark-java/)
Μάθετε πώς να εξάγετε αποδοτικά μεταδεδομένα εγγράφου όπως τύπο αρχείου, αριθμό σελίδων και μέγεθος χρησιμοποιώντας το GroupDocs.Watermark για Java. Αυτός ο οδηγός καλύπτει τη ρύθμιση, την υλοποίηση και πρακτικές εφαρμογές.

### [Εξαγωγή Διαστάσεων Σελίδας PDF σε Java Χρησιμοποιώντας το GroupDocs.Watermark&#58; Πλήρης Οδηγός](./get-pdf-page-dimensions-groupdocs-watermark-java/)
Μάθετε πώς να εξάγετε τις διαστάσεις σελίδας PDF με το GroupDocs.Watermark για Java. Ο οδηγός καλύπτει τη ρύθμιση, παραδείγματα κώδικα και πρακτικές εφαρμογές.

### [Εξαγωγή Σχημάτων από Έγγραφα Word Χρησιμοποιώντας το GroupDocs.Watermark σε Java](./extract-shapes-word-docs-groupdocs-watermark-java/)
Μάθετε πώς να εξάγετε και να αναλύσετε σχήματα από έγγραφα Word χρησιμοποιώντας το GroupDocs.Watermark για Java, ενισχύοντας την αυτοματοποίηση και τη διαχείριση εγγράφων.

### [Πώς να Εξάγετε Πληροφορίες Φόντου Διαφάνειας Χρησιμοποιώντας το GroupDocs.Watermark για Java](./groupdocs-watermark-java-extract-slide-backgrounds/)
Μάθετε πώς να εξάγετε λεπτομέρειες φόντου διαφάνειας όπως διαστάσεις εικόνας και μέγεθος αρχείου χρησιμοποιώντας το GroupDocs.Watermark για Java. Ιδανικό για προσαρμογή, ανάλυση ή τεκμηρίωση.

### [Πώς να Εμφανίσετε Υποστηριζόμενες Μορφές Αρχείων Χρησιμοποιώντας το GroupDocs.Watermark για Java&#58; Πλήρης Οδηγός](./groupdocs-watermark-java-list-supported-formats/)
Μάθετε πώς να εμφανίσετε αποδοτικά τις υποστηριζόμενες μορφές αρχείων με το GroupDocs.Watermark σε Java, εξασφαλίζοντας συμβατότητα μεταξύ διαφόρων τύπων εγγράφων.

### [Πώς να Ανακτήσετε Πληροφορίες Εγγράφου Χρησιμοποιώντας το GroupDocs.Watermark για Java&#58; Οδηγός Βήμα‑Βήμα](./retrieve-document-info-groupdocs-watermark-java/)
Μάθετε πώς να ανακτήσετε αποδοτικά πληροφορίες εγγράφου όπως τύπο αρχείου, αριθμό σελίδων και μέγεθος χρησιμοποιώντας το GroupDocs.Watermark για Java. Ακολουθήστε τον λεπτομερή οδηγό με παραδείγματα κώδικα.

### [Πώς να Ανακτήσετε Ιδιότητες Ενότητας σε Έγγραφα Word Χρησιμοποιώντας το GroupDocs.Watermark για Java](./groupdocs-java-word-section-properties-retrieval/)
Μάθετε πώς να ανακτήσετε και να διαχειριστείτε ιδιότητες ενοτήτων σε έγγραφα Word χρησιμοποιώντας το GroupDocs.Watermark για Java. Ιδανικό για προγραμματιστές που θέλουν να βελτιώσουν τη διαχείριση εγγράφων.

## Πρόσθετοι πόροι

- [Τεκμηρίωση GroupDocs.Watermark για Java](https://docs.groupdocs.com/watermark/java/)
- [Αναφορά API GroupDocs.Watermark για Java](https://reference.groupdocs.com/watermark/java/)
- [Λήψη GroupDocs.Watermark για Java](https://releases.groupdocs.com/watermark/java/)
- [Φόρουμ GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark)
- [Δωρεάν Υποστήριξη](https://forum.groupdocs.com/)
- [Προσωρινή Άδεια](https://purchase.groupdocs.com/temporary-license/)

---

**Τελευταία ενημέρωση:** 2026-11-13  
**Δοκιμή με:** GroupDocs.Watermark 23.12 for Java  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Πώς να Εμφανίσετε Υποστηριζόμενες Μορφές Αρχείων Χρησιμοποιώντας το GroupDocs.Watermark για Java: Πλήρης Οδηγός](/watermark/java/document-information/groupdocs-watermark-java-list-supported-formats/)
- [Πώς να Ανακτήσετε Πληροφορίες Εγγράφου Χρησιμοποιώντας το GroupDocs.Watermark για Java: Οδηγός Βήμα‑Βήμα](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Εξαγωγή Πληροφοριών Εγγράφου Χρησιμοποιώντας το GroupDocs.Watermark για Java: Πλήρης Οδηγός](/watermark/java/document-information/extract-document-info-groupdocs-watermark-java/)