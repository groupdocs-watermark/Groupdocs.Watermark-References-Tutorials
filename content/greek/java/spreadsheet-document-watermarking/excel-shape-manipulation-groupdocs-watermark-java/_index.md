---
date: '2026-06-01'
description: Μάθετε πώς να αφαιρέσετε σχήματα από αρχεία excel με το GroupDocs.Watermark
  για Java. Περιλαμβάνει βήματα για τη φόρτωση του Excel, την επανάληψη των φύλλων
  εργασίας και τη διαγραφή μορφοποιημένων σχημάτων.
keywords:
- remove shapes from excel
- add watermark to excel
- load excel document java
- how to add watermark excel
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  headline: How to remove shapes from excel using GroupDocs.Watermark in Java
  type: TechArticle
- description: Learn how to remove shapes from excel files with GroupDocs.Watermark
    for Java. Includes steps to load Excel, iterate worksheets, and delete formatted
    shapes.
  name: How to remove shapes from excel using GroupDocs.Watermark in Java
  steps:
  - name: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
    text: '**Data Validation** – Automatically delete shapes that contain deprecated
      notices.'
  - name: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
    text: '**Template Standardization** – Enforce corporate branding by stripping
      non‑standard text boxes.'
  - name: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
    text: '**Automated Reporting** – Clean up generated reports before distribution,
      guaranteeing a polished look.'
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then run the same
      removal logic; the API decrypts the file in memory.
    question: Can I remove shapes from a password‑protected workbook?
  - answer: Absolutely. GroupDocs.Watermark handles both `.xlsx` and legacy `.xls`
      formats without conversion.
    question: Does the library support .xls (Excel 97‑2003) files?
  - answer: Iterate the shape collection, check the formatting criteria, log `shape.getName()`
      or `shape.getId()`, then call `remove()`.
    question: How do I log which shapes were deleted?
  - answer: Yes. After cleanup, invoke `doc.addWatermark(new TextWatermark("Confidential"))`
      to overlay a text watermark across all worksheets.
    question: Is it possible to add a watermark after removing shapes?
  - answer: The library can process files up to **2 GB** on a 64‑bit JVM, limited
      only by available heap memory and OS constraints.
    question: What is the maximum file size supported?
  type: FAQPage
title: Πώς να αφαιρέσετε σχήματα από το excel χρησιμοποιώντας το GroupDocs.Watermark
  σε Java
type: docs
url: /el/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/
weight: 1
---

# Πώς να αφαιρέσετε σχήματα από το Excel χρησιμοποιώντας το GroupDocs.Watermark σε Java

Τα φύλλα εργασίας Excel είναι θεμέλιος λίθος των επιχειρηματικών αναφορών, αλλά ανεπιθύμητα σχήματα—ιδιαίτερα εκείνα με παρωχημένη ή μη‑τυπική μορφοποίηση κειμένου—μπορούν να γεμίσουν ένα αρχείο και να διασπάσουν την οπτική συνέπεια. **Η αφαίρεση σχημάτων από το Excel** γίνεται γρήγορα απαραίτητη για καθαρά, επαγγελματικά έγγραφα. Σε αυτό το σεμινάριο θα δούμε πώς να φορτώσουμε ένα βιβλίο εργασίας Excel, να επαναλάβουμε τα φύλλα του και να διαγράψουμε προγραμματιστικά σχήματα που ταιριάζουν σε συγκεκριμένα κριτήρια μορφοποίησης, όλα με τη δυνατή βιβλιοθήκη GroupDocs.Watermark για Java.

## Γρήγορες Απαντήσεις
- **Μπορεί το GroupDocs.Watermark να διαγράψει σχήματα;** Ναι, παρέχει τη μέθοδο `removeShape` που λειτουργεί σε οποιοδήποτε φύλλο εργασίας.  
- **Χρειάζομαι άδεια για αυτή τη λειτουργία;** Μια δοκιμαστική άδεια λειτουργεί για αξιολόγηση· απαιτείται πλήρης άδεια για παραγωγή.  
- **Ποια έκδοση της Java απαιτείται;** Υποστηρίζεται η Java 8 ή νεότερη.  
- **Πόσες μορφές αρχείων διαχειρίζεται το GroupDocs.Watermark;** Πάνω από 30 μορφές εισόδου και εξόδου, συμπεριλαμβανομένων των XLSX, DOCX, PDF και PPTX.  
- **Ανησυχείτε για την κατανάλωση μνήμης σε μεγάλα βιβλία εργασίας;** Χρησιμοποιήστε try‑with‑resources και αποφύγετε τη φόρτωση ολόκληρων φύλλων στη μνήμη· το API ρέει τα δεδομένα αποδοτικά.

## Τι είναι η αφαίρεση σχημάτων από το Excel;
*Η αφαίρεση σχημάτων από το Excel* σημαίνει προγραμματιστική διαγραφή αντικειμένων σχεδίασης—όπως πλαίσια κειμένου, εικονίδια ή SmartArt—που πληρούν ορισμένα κριτήρια, όπως στυλ γραμματοσειράς, χρώμα ή μέγεθος. Αυτή η λειτουργία καθαρίζει το βιβλίο εργασίας χωρίς χειροκίνητη επεξεργασία, εξασφαλίζοντας οπτική συνέπεια, μειώνοντας το μέγεθος του αρχείου και αποτρέποντας την εμφάνιση παλαιών ή ανεπιθύμητων γραφικών σε διανεμημένες αναφορές.

## Γιατί να αφαιρέσετε σχήματα από το Excel;
Το GroupDocs.Watermark μπορεί να επεξεργαστεί **βιβλία εργασίας με εκατοντάδες σελίδες με ταχύτητα έως 3 × γρηγορότερη** από τη χειροκίνητη επεξεργασία, διαχειριζόμενο **πάνω από 30 μορφές αρχείων** ενώ διατηρεί τη χρήση μνήμης κάτω από 150 MB για αρχεία μεγαλύτερα από 50 MB. Η αυτοματοποίηση της αφαίρεσης σχημάτων εξαλείφει το ανθρώπινο σφάλμα και εγγυάται συνεπή επωνυμία σε όλες τις παραγόμενες αναφορές.

## Προαπαιτούμενα
### Απαιτούμενες Βιβλιοθήκες, Εκδόσεις και Εξαρτήσεις
- **Java Development Kit (JDK)**: Έκδοση 8 ή νεότερη.  
- **GroupDocs.Watermark**: Έκδοση 24.11 (η πιο πρόσφατη σταθερή έκδοση τη στιγμή της συγγραφής).

### Απαιτήσεις Ρύθμισης Περιβάλλοντος
Χρησιμοποιήστε ένα IDE όπως IntelliJ IDEA ή Eclipse και Maven για διαχείριση εξαρτήσεων.

### Προαπαιτούμενες Γνώσεις
Η εξοικείωση με τη σύνταξη Java και τις βασικές έννοιες του Excel (φύλλα εργασίας, κελιά και σχήματα) θα σας βοηθήσει να ακολουθήσετε τα παραδείγματα.

## Ρύθμιση GroupDocs.Watermark για Java
**Εξάρτηση Maven**  
Προσθέστε τα παρακάτω στο `pom.xml` σας:

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

**Άμεση Λήψη**  
Εναλλακτικά, κατεβάστε την πιο πρόσφατη έκδοση από [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Βήματα Απόκτησης Άδειας
- **Δωρεάν Δοκιμή** – Ξεκινήστε με μια δωρεάν δοκιμή για αξιολόγηση των λειτουργιών.  
- **Προσωρινή Άδεια** – Αποκτήστε μια προσωρινή άδεια για εκτεταμένη δοκιμή.  
- **Αγορά** – Αγοράστε πλήρη άδεια για χρήση σε παραγωγή.

### Βασική Αρχικοποίηση και Ρύθμιση  
Μόλις η βιβλιοθήκη προστεθεί στο έργο σας, αρχικοποιήστε την όπως φαίνεται παρακάτω:

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class WatermarkSetup {
    public static void main(String[] args) {
        // Initialize the watermarker with a document path and load options
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Always close the watermarker to release resources
        watermarker.close();
    }
}
```  

## Πώς να αφαιρέσετε σχήματα από το Excel;
Φορτώστε το βιβλίο εργασίας, διασχίστε κάθε φύλλο εργασίας και καλέστε το API αφαίρεσης σχημάτων. Αυτό το μοτίβο δύο βημάτων—*φόρτωση* και *επανάληψη*—καλύπτει σχεδόν κάθε σενάριο όπου χρειάζεται να καθαρίσετε σχήματα σε ολόκληρο το αρχείο. Ελέγχοντας τις ιδιότητες κάθε σχήματος έναντι των κριτηρίων σας πριν από την αφαίρεση, εξασφαλίζετε ότι μόνο τα ανεπιθύμητα στοιχεία διαγράφονται, διατηρώντας το υπόλοιπο της διάταξης και του περιεχομένου του εγγράφου.

## Φόρτωση Εγγράφου Excel
**Επισκόπηση**  
Η φόρτωση ενός εγγράφου Excel είναι το σημείο εκκίνησης για οποιαδήποτε εργασία επεξεργασίας. Το GroupDocs.Watermark απλοποιεί αυτό με το διαισθητικό του API.  

**Αγκύρωση Ορισμού**  
`SpreadsheetDocument` είναι η κύρια κλάση στο GroupDocs.Watermark που αντιπροσωπεύει ένα βιβλίο εργασίας Excel στη μνήμη, παρέχοντας μεθόδους πρόσβασης σε φύλλα εργασίας, κελιά και σχήματα.  

#### Απόσπασμα Κώδικα
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureLoadExcelDocument {
    public static void main(String[] args) {
        // Create a SpreadsheetLoadOptions object to specify load configurations
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        
        // Load the Excel document using an absolute or relative path
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
    }
}
```  

## Πρόσβαση και Επανάληψη Μέσω Φύλλων Εργασίας σε Φύλλο Εργασίας
**Επισκόπηση**  
Η επανάληψη μέσω των φύλλων εργασίας σας επιτρέπει να εκτελείτε λειτουργίες σε κάθε φύλλο ξεχωριστά.  

**Αγκύρωση Ορισμού**  
`Worksheet` αντιπροσωπεύει ένα μεμονωμένο φύλλο μέσα σε ένα `SpreadsheetDocument`; μπορείτε να διαβάσετε, τροποποιήσετε ή διαγράψετε το περιεχόμενό του μέσω αυτού του αντικειμένου.  

#### Απόσπασμα Κώδικα
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

public class FeatureIterateWorksheets {
    public static void main(String[] args) throws Exception {
        // Load the document as before
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Access and iterate through worksheets
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            System.out.println("Processing Worksheet: " + section.getName());
        }
        
        watermarker.close();
    }
}
```  

## Αφαίρεση Σχημάτων με Συγκεκριμένη Μορφοποίηση Κειμένου από Φύλλο Εργασίας
**Επισκόπηση**  
Αυτή η λειτουργία στοχεύει σε σχήματα που πληρούν συγκεκριμένα κριτήρια μορφοποίησης κειμένου, όπως τύπο ή χρώμα γραμματοσειράς.  

**Αγκύρωση Ορισμού**  
`Shape` είναι το μοντέλο αντικειμένου για οποιοδήποτε στοιχείο σχεδίασης (πλαίσιο κειμένου, εικόνα ή SmartArt) μέσα σε ένα φύλλο εργασίας· εκθέτει ιδιότητες όπως `getText`, `getFont` και `remove`.  

#### Απόσπασμα Κώδικα
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetContent;
import com.groupdocs.watermark.contents.SpreadsheetWorksheet;
import com.groupdocs.watermark.search.FormattedTextFragment;
import com.groupdocs.watermark.watermarks.Color;

public class FeatureRemoveShapesWithSpecificFormatting {
    public static void main(String[] args) throws Exception {
        // Load the document
        SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
        Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
        
        // Iterate through worksheets and shapes
        SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
        for (SpreadsheetWorksheet section : content.getWorksheets()) {
            for (int i = section.getShapes().getCount() - 1; i >= 0; i--) {
                for (FormattedTextFragment fragment : section.getShapes().get_Item(i).getFormattedTextFragments()) {
                    // Check specific text formatting criteria
                    if (fragment.getForegroundColor().equals(Color.getRed()) &&
                        "Arial".equalsIgnoreCase(fragment.getFont().getFamilyName())) {
                        // Remove the shape if it matches
                        section.getShapes().removeAt(i);
                        break;
                    }
                }
            }
        }
        
        // Save changes to a new document
        watermarker.save("YOUR_OUTPUT_DIRECTORY/modified_spreadsheet.xlsx");
        watermarker.close();
    }
}
```  

## Πρακτικές Εφαρμογές
### Πραγματικές Περιπτώσεις Χρήσης
1. **Επαλήθευση Δεδομένων** – Αυτόματη διαγραφή σχημάτων που περιέχουν παρωχημένες ειδοποιήσεις.  
2. **Τυποποίηση Προτύπων** – Επιβολή εταιρικής επωνυμίας αφαιρώντας μη‑τυπικά πλαίσια κειμένου.  
3. **Αυτοματοποιημένη Αναφορά** – Καθαρισμός παραγόμενων αναφορών πριν τη διανομή, εξασφαλίζοντας μια επαγγελματική εμφάνιση.

### Δυνατότητες Ενσωμάτωσης
Το GroupDocs.Watermark μπορεί να ενσωματωθεί σε Java‑βασισμένα επιχειρηματικά pipelines, όπως μικρο‑υπηρεσίες δημιουργίας εγγράφων, εργασίες επεξεργασίας σε παρτίδες ή συστήματα διαχείρισης περιεχομένου, παρέχοντας έναν απρόσκοπτο, συμμορφωμένο με την άδεια τρόπο διαχείρισης πόρων Excel.

## Παράγοντες Απόδοσης
### Βελτιστοποίηση Απόδοσης
- **Αποφύγετε βαριές λειτουργίες μέσα σε βρόχους** – λάβετε τις συλλογές σχημάτων μία φορά ανά φύλλο εργασίας.  
- **Απελευθερώστε πόρους άμεσα** – χρησιμοποιήστε try‑with‑resources για αυτόματο κλείσιμο των ροών.

### Οδηγίες Χρήσης Πόρων
Απελευθερώστε το αντικείμενο `SpreadsheetDocument` μόλις ολοκληρωθεί η επεξεργασία για να ελευθερώσετε τη φυσική μνήμη. Για αρχεία που υπερβαίνουν τα 100 MB, εξετάστε την επεξεργασία των φύλλων εργασίας σε παράλληλες ροές για να αξιοποιήσετε πολυπύρηνους επεξεργαστές.

### Καλές Πρακτικές για Διαχείριση Μνήμης Java
Χρησιμοποιήστε `try (SpreadsheetDocument doc = new SpreadsheetDocument(...)) { … }` ώστε η μέθοδος `close()` να εκτελείται ακόμη και αν προκύψει εξαίρεση.

## Κοινά Προβλήματα και Λύσεις
- **Το σχήμα δεν βρέθηκε** – Βεβαιωθείτε ότι ελέγχετε το σωστό δείκτη φύλλου εργασίας· τα σχήματα είναι περιορισμένα ανά φύλλο.  
- **Απόκλιση άδειας** – Μια δοκιμαστική άδεια απενεργοποιεί την επεξεργασία σε παρτίδες· αναβαθμίστε σε πλήρη άδεια για απεριόριστες λειτουργίες.  
- **Μη αναμενόμενες τιμές γραμματοσειράς** – Οι ιδιότητες γραμματοσειράς μπορεί να κληρονομούνται· χρησιμοποιήστε `shape.getEffectiveFont()` για να λάβετε το τελικό στυλ.

## Συχνές Ερωτήσεις

**Ε: Μπορώ να αφαιρέσω σχήματα από ένα φύλλο εργασίας προστατευμένο με κωδικό;**  
Α: Ναι. Φορτώστε το έγγραφο με την παράμετρο κωδικού πρόσβασης, στη συνέχεια εκτελέστε την ίδια λογική αφαίρεσης· το API αποκρυπτογραφεί το αρχείο στη μνήμη.

**Ε: Υποστηρίζει η βιβλιοθήκη αρχεία .xls (Excel 97‑2003);**  
Α: Απόλυτα. Το GroupDocs.Watermark διαχειρίζεται τόσο τις μορφές `.xlsx` όσο και τις παλαιότερες `.xls` χωρίς μετατροπή.

**Ε: Πώς μπορώ να καταγράψω ποια σχήματα διαγράφηκαν;**  
Α: Επαναλάβετε τη συλλογή σχημάτων, ελέγξτε τα κριτήρια μορφοποίησης, καταγράψτε `shape.getName()` ή `shape.getId()`, και στη συνέχεια καλέστε `remove()`.

**Ε: Είναι δυνατόν να προσθέσω υδατογράφημα μετά την αφαίρεση σχημάτων;**  
Α: Ναι. Μετά τον καθαρισμό, καλέστε `doc.addWatermark(new TextWatermark("Confidential"))` για να προσθέσετε ένα κειμενικό υδατογράφημα σε όλα τα φύλλα εργασίας.

**Ε: Ποιο είναι το μέγιστο μέγεθος αρχείου που υποστηρίζεται;**  
Α: Η βιβλιοθήκη μπορεί να επεξεργαστεί αρχεία έως **2 GB** σε 64‑bit JVM, περιοριζόμενο μόνο από τη διαθέσιμη μνήμη heap και τους περιορισμούς του λειτουργικού συστήματος.

## Συμπέρασμα
Σε αυτό το μάθημα παρουσιάσαμε μια πλήρη, έτοιμη για παραγωγή προσέγγιση για **αφαίρεση σχημάτων από το Excel** βιβλία εργασίας χρησιμοποιώντας το GroupDocs.Watermark για Java. Φορτώνοντας το έγγραφο, επαναλαμβάνοντας τα φύλλα εργασίας και εφαρμόζοντας ακριβά φίλτρα μορφοποίησης, μπορείτε να αυτοματοποιήσετε εργασίες καθαρισμού, να επιβάλετε την επωνυμία και να βελτιώσετε την ποιότητα των αναφορών σε κλίμακα. Εξερευνήστε πρόσθετες λειτουργίες όπως η εισαγωγή υδατογραφήματος, η μετατροπή εγγράφων και η επεξεργασία σε παρτίδες για να επεκτείνετε περαιτέρω το σύνολο εργαλείων αυτοματοποίησης εγγράφων.

---

**Τελευταία Ενημέρωση:** 2026-06-01  
**Δοκιμάστηκε Με:** GroupDocs.Watermark 24.11 for Java  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Διαχείριση Σχημάτων Excel με το GroupDocs.Watermark σε Java: Ένας Πλήρης Οδηγός](/watermark/java/spreadsheet-document-watermarking/excel-shape-manipulation-groupdocs-watermark-java/)
- [Προσθήκη Εικόνας Υδατογραφήματος σε Φύλλο Excel με το GroupDocs.Watermark Java SDK](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [Διαχείριση Εγγράφου Excel και Υδατογράφημα με το GroupDocs.Watermark Java](/watermark/java/spreadsheet-document-watermarking/excel-document-handling-groupdocs-watermark-java/)