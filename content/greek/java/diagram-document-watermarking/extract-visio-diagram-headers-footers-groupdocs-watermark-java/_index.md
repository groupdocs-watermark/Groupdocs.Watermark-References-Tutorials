---
date: '2026-05-22'
description: Μάθετε πώς να εξάγετε τις κεφαλίδες και τα υποσέλιδα Visio με το GroupDocs.Watermark
  για Java, συμπεριλαμβανομένων των λεπτομερειών για τη γραμματοσειρά, το κείμενο,
  το χρώμα και τα περιθώρια.
keywords:
- how to extract visio
- GroupDocs Watermark Java
- Visio diagram extraction
schemas:
- author: GroupDocs
  dateModified: '2026-05-22'
  description: Learn how to extract Visio headers and footers with GroupDocs.Watermark
    for Java, including font, text, color, and margin details.
  headline: How to Extract Visio Headers & Footers using GroupDocs Java
  type: TechArticle
- description: Learn how to extract Visio headers and footers with GroupDocs.Watermark
    for Java, including font, text, color, and margin details.
  name: How to Extract Visio Headers & Footers using GroupDocs Java
  steps:
  - name: '**Document Analysis:** Automatically compare header/footer styles across
      thousands of diagrams to enforce branding guidelines.'
    text: '**Document Analysis:** Automatically compare header/footer styles across
      thousands of diagrams to enforce branding guidelines.'
  - name: '**Compliance Audits:** Verify that required legal notices appear in every
      Visio file before publishing.'
    text: '**Compliance Audits:** Verify that required legal notices appear in every
      Visio file before publishing.'
  - name: '**Dynamic Reporting:** Pull header text to populate metadata fields in
      a content‑management system.'
    text: '**Dynamic Reporting:** Pull header text to populate metadata fields in
      a content‑management system.'
  - name: '**Migration Projects:** Convert legacy Visio diagrams to modern formats
      while preserving visual consistency.'
    text: '**Migration Projects:** Convert legacy Visio diagrams to modern formats
      while preserving visual consistency.'
  type: HowTo
- questions:
  - answer: Yes. Pass the password to the `Watermarker` constructor; the SDK will
      decrypt the file internally before extracting metadata.
    question: Can I extract headers/footers from password‑protected Visio files?
  - answer: It supports both VSDX and VSD, covering Visio versions from 2003 onward.
    question: Does the library support Visio 2013 (VSDX) and older VSD formats?
  - answer: Iterate through `watermarker.getPages()`; each page exposes its own `HeaderFooter`
      collection, allowing page‑specific extraction.
    question: How do I handle diagrams that contain multiple pages with different
      headers?
  - answer: Ensure the diagram actually contains a footer on that page; use `hasFooter()`
      checks before accessing properties.
    question: What if I encounter a `NullPointerException` while reading a footer?
  - answer: Yes – after retrieving the objects, you can use any JSON library (e.g.,
      Jackson) to serialize the font, color, and margin fields.
    question: Is there a way to export the extracted data to JSON?
  type: FAQPage
title: Πώς να εξάγετε κεφαλίδες & υποσέλιδα Visio χρησιμοποιώντας το GroupDocs Java
type: docs
url: /el/java/diagram-document-watermarking/extract-visio-diagram-headers-footers-groupdocs-watermark-java/
weight: 1
---

# Πώς να εξάγετε κεφαλίδες & υποσέλιδα Visio χρησιμοποιώντας το GroupDocs Java

Η εξαγωγή κεφαλίδων και υποσέλιδων από διαγράμματα Microsoft Visio μπορεί να είναι μια επίπονη χειροκίνητη εργασία, ειδικά όταν χρειάζεστε ακριβείς ρυθμίσεις γραμματοσειράς, χρώματα ή τιμές περιθωρίων. **How to extract Visio** κεφαλίδες και υποσέλιδα γίνεται αβίαρο με το GroupDocs.Watermark for Java, μια βιβλιοθήκη που διαβάζει τα μεταδεδομένα του διαγράμματος χωρίς να αποδίδει ολόκληρο το αρχείο. Σε αυτόν τον οδηγό θα ανακαλύψετε πώς να αντλήσετε πληροφορίες γραμματοσειράς, περιεχόμενο κειμένου, χρώματα και ρυθμίσεις περιθωρίων προγραμματιστικά, και θα αποκτήσετε έτοιμα αποσπάσματα κώδικα που ταιριάζουν σε οποιοδήποτε έργο Java.

## Γρήγορες Απαντήσεις
- **Τι καλύπτει το σεμινάριο;** Εξαγωγή δεδομένων γραμματοσειράς, κειμένου, χρώματος και περιθωρίου από κεφαλίδες/υποσέλιδα Visio με το GroupDocs.Watermark for Java.  
- **Ποια έκδοση της βιβλιοθήκης απαιτείται;** GroupDocs.Watermark 24.11 ή νεότερη.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για αξιολόγηση· απαιτείται μόνιμη άδεια για παραγωγή.  
- **Μπορώ να επεξεργαστώ μεγάλα διαγράμματα;** Ναι – το API ρέει δεδομένα, έτσι η χρήση μνήμης παραμένει χαμηλή ακόμη και για αρχεία με εκατοντάδες σελίδες.  
- **Είναι ο κώδικας συμβατός με Maven;** Απόλυτα – η βιβλιοθήκη προστίθεται μέσω μιας εξάρτησης Maven.

## Τι είναι το GroupDocs.Watermark for Java;
Το GroupDocs.Watermark for Java είναι ένα SDK βασισμένο σε Java που επιτρέπει την ανάγνωση, προσθήκη και αφαίρεση υδατογραφιών, καθώς και την εξαγωγή μεταδεδομένων εγγράφων από πάνω από 100 μορφές αρχείων, συμπεριλαμβανομένων των διαγραμμάτων Visio. Παρέχει μια υψηλού επιπέδου κλάση `Watermarker` που αφαιρεί την πολυπλοκότητα της διαχείρισης αρχείων, επιτρέποντάς σας να εστιάσετε στη λογική της επιχείρησης αντί στην χαμηλού επιπέδου ανάλυση.

## Πώς να εξάγετε κεφαλίδες & υποσέλιδα Visio;
Φορτώστε το αρχείο Visio με μια παρουσία `Watermarker` και καλέστε τις κατάλληλες μεθόδους λήψης κεφαλίδας/υποσέλιδου – η βιβλιοθήκη επιστρέφει πλούσια αντικείμενα που περιέχουν ιδιότητες γραμματοσειράς, κειμένου, χρώματος και περιθωρίου. Η διαδικασία συνήθως περιλαμβάνει τρεις γραμμές κώδικα: δημιουργία του `Watermarker`, πρόσβαση στη συλλογή `HeaderFooter` και ανάγνωση των επιθυμητών χαρακτηριστικών. Αυτή η προσέγγιση εκτελείται σε χρόνο O(1) σε σχέση με το μέγεθος του αρχείου, επειδή το SDK διαβάζει μόνο τις απαιτούμενες ενότητες XML.

### Προαπαιτούμενα
- **GroupDocs.Watermark for Java** ≥ 24.11 (διαθέσιμο για λήψη από την επίσημη σελίδα εκδόσεων).  
- Java 8 ή νεότερη εγκατεστημένη στο μηχάνημά σας.  
- Maven ή Gradle για διαχείριση εξαρτήσεων.  
- Βασική εξοικείωση με τη σύνταξη Java και τις αντικειμενοστραφείς έννοιες.

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

Εναλλακτικά, κατεβάστε τη βιβλιοθήκη απευθείας από [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Απόκτηση Άδειας
- **Free Trial** – ξεκινήστε αμέσως χωρίς πιστωτική κάρτα.  
- **Temporary License** – ζητήστε κλειδί 30‑ημέρας μέσω της πύλης GroupDocs.  
- **Full License** – αγοράστε για απεριόριστη χρήση παραγωγής και προτεραιότητα υποστήριξης.

### Βασική Αρχικοποίηση
Η κλάση `Watermarker` είναι το σημείο εισόδου για όλες τις λειτουργίες· φορτώνει το διάγραμμα στη μνήμη και εκθέτει τα API κεφαλίδας/υποσέλιδου.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Χαρακτηριστικό 1: Εξαγωγή Πληροφοριών Γραμματοσειράς Κεφαλίδας και Υποσέλιδου
### Επισκόπηση
Αυτή η λειτουργία επιστρέφει ένα αντικείμενο `FontInfo` που περιέχει το όνομα οικογένειας, το μέγεθος, τις σημαίες στυλ (έντονη, πλάγια, υπογράμμιση, διακριτή γραμμή) και άλλες τυπογραφικές λεπτομέρειες για κάθε τμήμα κεφαλίδας/υποσέλιδου.

Η κλάση `FontInfo` περιλαμβάνει την οικογένεια γραμματοσειράς, το μέγεθος, το στυλ και άλλα τυπογραφικά χαρακτηριστικά για μια κεφαλίδα ή υποσέλιδο.

#### Υλοποίηση Βήμα‑βήμα
**Αρχικοποίηση Watermarker**

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

**Εξαγωγή Ρυθμίσεων Γραμματοσειράς**

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);

// Extract font attributes
String fontFamilyName = content.getHeaderFooter().getFont().getFamilyName();
float fontSize = content.getHeaderFooter().getFont().getSize();
boolean isBold = content.getHeaderFooter().getFont().getBold();
boolean isItalic = content.getHeaderFooter().getFont().getItalic();
boolean isUnderline = content.getHeaderFooter().getFont().getUnderline();
boolean isStrikeout = content.getHeaderFooter().getFont().getStrikeout();

watermarker.close(); // Always close the watermarker to free resources
```

## Χαρακτηριστικό 2: Εξαγωγή Περιεχομένου Κειμένου από Κεφαλίδες και Υποσέλιδα
### Επισκόπηση
Μπορείτε να ανακτήσετε το ακατέργαστο περιεχόμενο συμβολοσειράς από κάθε περιοχή κεφαλίδας/υποσέλιδου, κάτι που είναι χρήσιμο για ευρετηρίαση, αναζήτηση ή αυτόματη δημιουργία αναφορών.

Το αντικείμενο `HeaderFooter` παρέχει τη μέθοδο `getText()` για την ανάκτηση του ακατέργαστου περιεχομένου συμβολοσειράς από μια κεφαλίδα ή υποσέλιδο.

#### Υλοποίηση Βήμα‑βήμα
**Εξαγωγή Κειμένου Κεφαλίδας & Υποσέλιδου**

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);

// Extract header texts
String headerLeftText = content.getHeaderFooter().getHeaderLeft();
String headerCenterText = content.getHeaderFooter().getHeaderCenter();
String headerRightText = content.getHeaderFooter().getHeaderRight();

// Extract footer texts
String footerLeftText = content.getHeaderFooter().getFooterLeft();
String footerCenterText = content.getHeaderFooter().getFooterCenter();
String footerRightText = content.getHeaderFooter().getFooterRight();

watermarker.close(); // Remember to close the watermarker
```

## Χαρακτηριστικό 3: Εξαγωγή Χρώματος Κειμένου από Κεφαλίδες και Υποσέλιδα
### Επισκόπηση
Το SDK αναφέρει το χρώμα του κειμένου ως ακέραιο ARGB, επιτρέποντας ακριβή αντιστοίχιση χρώματος ή μετατροπή σε HEX για εμφάνιση UI.

Η κλάση `ColorInfo` αντιπροσωπεύει το χρώμα του κειμένου ως ακέραιο ARGB, επιτρέποντας μετατροπή σε μορφές HEX ή RGB.

#### Υλοποίηση Βήμα‑βήμα
**Εξαγωγή Χρώματος Κειμένου**

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);

// Get text color as ARGB integer
int textColorArgb = content.getHeaderFooter().getTextColor().toArgb();

watermarker.close(); // Close to release resources
```

## Χαρακτηριστικό 4: Εξαγωγή Περιθωρίων Κεφαλίδας και Υποσέλιδου
### Επισκόπηση
Οι τιμές περιθωρίων (πάνω, κάτω, αριστερά, δεξιά) εκτίθενται σε σημεία, επιτρέποντάς σας να αναπαράγετε την αρχική διάταξη κατά τη δημιουργία νέων διαγραμμάτων ή PDF.

Η κλάση `MarginInfo` περιέχει τις τιμές περιθωρίων πάνω, κάτω, αριστερά και δεξιά, μετρημένες σε σημεία.

#### Υλοποίηση Βήμα‑βήμα
**Εξαγωγή Ρυθμίσεων Περιθωρίου**

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);

// Get margins
float footerMargin = content.getHeaderFooter().getFooterMargin();
float headerMargin = content.getHeaderFooter().getHeaderMargin();

watermarker.close(); // Closing is crucial for resource management
```

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark for Java;
Το GroupDocs.Watermark for Java παρέχει μια ολοκληρωμένη, υψηλής απόδοσης λύση για τη διαχείριση ενός ευρέος φάσματος μορφών εγγράφων, συμπεριλαμβανομένου του Visio, χωρίς να απαιτείται εγκατάσταση του Microsoft Office. Προσφέρει εκτενή υποστήριξη μορφών, γρήγορη επεξεργασία και ένα απλό API που επιτρέπει στους προγραμματιστές να εξάγουν και να χειρίζονται στοιχεία εγγράφων όπως κεφαλίδες, υποσέλιδα και υδατογραφήματα αποδοτικά, καθιστώντας το ιδανικό για αυτοματοποίηση σε επιχειρησιακό επίπεδο.

- **Ευρεία υποστήριξη μορφών:** Διαχειρίζεται πάνω από 120 τύπους αρχείων, συμπεριλαμβανομένων των VSDX, VDX και παλαιότερων μορφών VSD.  
- **Υψηλή απόδοση:** Επεξεργάζεται αρχεία έως 500 MB χωρίς να φορτώνει ολόκληρο το έγγραφο στη μνήμη, επιτυγχάνοντας χρόνους εξαγωγής κάτω από 2 δευτερόλεπτα σε τυπική CPU 2.5 GHz.  
- **Χωρίς εξωτερικές εξαρτήσεις:** Λειτουργεί αποκλειστικά σε Java, έτσι δεν χρειάζεστε εγκατεστημένο Microsoft Office ή Visio στον διακομιστή.  
- **Thread‑safe API:** Επιτρέπει ταυτόχρονη επεξεργασία πολλαπλών διαγραμμάτων, ιδανικό για εργασίες παρτίδας σε επιχειρησιακές γραμμές.

## Πρακτικές Εφαρμογές
Η αξιοποίηση αυτών των δυνατοτήτων εξαγωγής μπορεί να βελτιώσει αρκετά σενάρια πραγματικού κόσμου:

1. **Ανάλυση Εγγράφων:** Αυτόματη σύγκριση στυλ κεφαλίδας/υποσέλιδου σε χιλιάδες διαγράμματα για την επιβολή οδηγιών branding.  
2. **Έλεγχοι Συμμόρφωσης:** Επαλήθευση ότι οι απαιτούμενες νομικές ειδοποιήσεις εμφανίζονται σε κάθε αρχείο Visio πριν τη δημοσίευση.  
3. **Δυναμική Αναφορά:** Ανάκτηση κειμένου κεφαλίδας για τη συμπλήρωση πεδίων μεταδεδομένων σε σύστημα διαχείρισης περιεχομένου.  
4. **Έργα Μετανάστευσης:** Μετατροπή παλαιών διαγραμμάτων Visio σε σύγχρονες μορφές διατηρώντας την οπτική συνέπεια.

## Σκέψεις Απόδοσης
- **Απελευθέρωση πόρων:** Πάντα καλέστε `watermarker.close()` μετά την ολοκλήρωση για να ελευθερώσετε τους χειριστές αρχείων.  
- **Συμβουλή παρτίδας επεξεργασίας:** Επαναχρησιμοποιήστε μια ενιαία παρουσία `Watermarker` για πολλαπλά αρχεία όταν μοιράζονται το ίδιο πλαίσιο αδειών.  
- **Προφίλ μνήμης:** Χρησιμοποιήστε το Java VisualVM ή παρόμοια εργαλεία για την παρακολούθηση της χρήσης heap, ειδικά όταν διαχειρίζεστε διαγράμματα μεγαλύτερα από 200 MB.

## Συχνές Ερωτήσεις
**Q: Μπορώ να εξάγω κεφαλίδες/υποσέλιδα από αρχεία Visio προστατευμένα με κωδικό;**  
A: Ναι. Περνάτε τον κωδικό στον κατασκευαστή `Watermarker`; το SDK θα αποκρυπτογραφήσει το αρχείο εσωτερικά πριν εξάγει τα μεταδεδομένα.

**Q: Υποστηρίζει η βιβλιοθήκη Visio 2013 (VSDX) και παλαιότερες μορφές VSD;**  
A: Υποστηρίζει τόσο VSDX όσο και VSD, καλύπτοντας εκδόσεις Visio από το 2003 και μετά.

**Q: Πώς να διαχειριστώ διαγράμματα που περιέχουν πολλαπλές σελίδες με διαφορετικές κεφαλίδες;**  
A: Επανάληψη μέσω `watermarker.getPages()`· κάθε σελίδα εκθέτει τη δική της συλλογή `HeaderFooter`, επιτρέποντας εξαγωγή ανά σελίδα.

**Q: Τι γίνεται αν αντιμετωπίσω `NullPointerException` κατά την ανάγνωση ενός υποσέλιδου;**  
A: Βεβαιωθείτε ότι το διάγραμμα περιέχει πραγματικά υποσέλιδο σε αυτή τη σελίδα· χρησιμοποιήστε ελέγχους `hasFooter()` πριν την πρόσβαση στις ιδιότητες.

**Q: Υπάρχει τρόπος εξαγωγής των δεδομένων σε JSON;**  
A: Ναι – μετά την ανάκτηση των αντικειμένων, μπορείτε να χρησιμοποιήσετε οποιαδήποτε βιβλιοθήκη JSON (π.χ., Jackson) για τη σειριοποίηση των πεδίων γραμματοσειράς, χρώματος και περιθωρίου.

## Συμπέρασμα
Τώρα έχετε έναν πλήρη, έτοιμο για παραγωγή οδηγό για **how to extract Visio** κεφαλίδες και υποσέλιδα χρησιμοποιώντας το GroupDocs.Watermark for Java. Ακολουθώντας τα παραπάνω βήματα μπορείτε προγραμματιστικά να διαβάζετε στυλ γραμματοσειράς, συμβολοσειρές κειμένου, χρώματα και περιθώρια διάταξης, επιτρέποντας ισχυρά σενάρια αυτοματοποίησης σε διαχείριση εγγράφων, συμμόρφωση και έργα μετανάστευσης. Για πιο λεπτομερείς πληροφορίες, εξερευνήστε την επίσημη τεκμηρίωση και τους συνδέσμους αναφοράς API παρακάτω.

---

**Τελευταία Ενημέρωση:** 2026-05-22  
**Δοκιμάστηκε Με:** GroupDocs.Watermark 24.11 for Java  
**Συγγραφέας:** GroupDocs  

**Πόροι**

- **Documentation:** Εξερευνήστε περισσότερα στο [GroupDocs Documentation](https://docs.groupdocs.com/watermark/java/)
- **Documentation (lowercase):** Εξερευνήστε περισσότερα στο [GroupDocs documentation](https://docs.groupdocs.com/watermark/java/)
- **API Reference:** Βυθιστείτε πιο βαθιά με [API References](https://reference.groupdocs.com/watermark/java)
- **Download Library:** Λάβετε την πιο πρόσφατη έκδοση από το [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)
- **Support Forum:** Λάβετε βοήθεια στο [free support forum](https://forum.groupdocs.com/c/watermark/10)

## Σχετικά Μαθήματα

- [Edit Diagram Headers & Footers in Java Using GroupDocs.Watermark: A Comprehensive Guide](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)
- [Remove Hyperlinks from Diagram Shapes using GroupDocs.Watermark Java for Enhanced Document Security](/watermark/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/)
- [Diagram Watermarking Tutorials for GroupDocs.Watermark Java](/watermark/java/diagram-document-watermarking/)