---
date: '2026-07-15'
description: Μάθετε πώς να προσθέσετε κειμενικό watermark σε αρχεία Excel χρησιμοποιώντας
  Java και GroupDocs.Watermark. Αυτός ο οδηγός δείχνει πώς να προσθέσετε watermark
  και να εφαρμόσετε watermark σε spreadsheet αποδοτικά.
keywords:
- add text watermark excel
- how to add watermark
- apply watermark to spreadsheet
lastmod: '2026-07-15'
og_description: Μάθετε πώς να προσθέσετε κειμενικό watermark σε αρχεία Excel χρησιμοποιώντας
  Java και GroupDocs.Watermark. Αυτός ο οδηγός δείχνει πώς να προσθέσετε watermark
  και να εφαρμόσετε watermark σε spreadsheet αποδοτικά.
og_image_alt: 'Guide: Add text watermark to Excel using Java with GroupDocs.Watermark'
og_title: Προσθήκη κειμενικού watermark σε Excel με χρήση Java – GroupDocs.Watermark
schemas:
- author: GroupDocs
  dateModified: '2026-07-15'
  description: Learn how to add text watermark to Excel files using Java and GroupDocs.Watermark.
    This guide shows how to add watermark and apply watermark to spreadsheet efficiently.
  headline: Add Text Watermark to Excel Using Java – GroupDocs.Watermark
  type: TechArticle
- description: Learn how to add text watermark to Excel files using Java and GroupDocs.Watermark.
    This guide shows how to add watermark and apply watermark to spreadsheet efficiently.
  name: Add Text Watermark to Excel Using Java – GroupDocs.Watermark
  steps:
  - name: Load the Excel Document
    text: '**Direct answer:** Initialize the `Watermarker` class with the path to
      your Excel file and appropriate load options – this prepares the document for
      watermark operations. xml <repositories> <repository> <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name> <url>https://releases.groupdo'
  - name: Create and Configure the Text Watermark
    text: '**Direct answer:** Instantiate a `TextWatermark`, set its text, font, size,
      color, and alignment, then attach it to a `SpreadsheetWatermarkOptions` object.
      java import com.groupdocs.watermark.Watermarker; import com.groupdocs.watermark.contents.SpreadsheetLoadOptions;
      // Initialize load options Spre'
  - name: Apply the Watermark to Desired Sheets
    text: '**Direct answer:** Use the `add` method on the `Watermarker` instance,
      passing the options and optionally specifying a sheet index to target a single
      worksheet. java import com.groupdocs.watermark.options.HorizontalAlignment;
      import com.groupdocs.watermark.options.VerticalAlignment; import com.group'
  - name: Save the Watermarked Workbook
    text: '**Direct answer:** Call `save` on the `Watermarker`, providing the output
      path and format; the library writes the watermarked file while preserving original
      data. java // Save the watermarked document watermarker.save("YOUR_OUTPUT_DIRECTORY/spreadsheet_watermarked.xlsx");
      // Release resources waterm'
  type: HowTo
- questions:
  - answer: It inserts customizable text watermarks into Excel files without altering
      original content.
    question: What does the library do?
  - answer: GroupDocs.Watermark for Java 24.11 or later.
    question: Which version is required?
  - answer: A free trial works for evaluation; a permanent license removes all limitations.
    question: Do I need a license?
  - answer: Yes – you can apply watermarks to specific worksheets.
    question: Can I target a single sheet?
  - answer: Yes, it processes multi‑hundred‑page workbooks using streaming, keeping
      memory usage low.
    question: Is it fast on large files?
  type: FAQPage
tags:
- add text watermark excel
- GroupDocs.Watermark
- Java spreadsheet watermark
- document security
- Excel watermarking
title: Προσθήκη κειμενικού watermark σε Excel με χρήση Java – GroupDocs.Watermark
type: docs
url: /el/java/spreadsheet-document-watermarking/java-add-customize-text-watermarks-excel/
weight: 1
---

# Προσθήκη Υδατογραφήματος Κειμένου σε Excel με Java – GroupDocs.Watermark

Στη σύγχρονη ψηφιακή εποχή, η προστασία ευαίσθητων πληροφοριών σε λογιστικά φύλλα είναι κρίσιμη. **Add text watermark excel** αρχεία εύκολα με το GroupDocs.Watermark για Java, μια βιβλιοθήκη που σας επιτρέπει να ενσωματώσετε προσαρμοσμένα υδατογραφήματα κειμένου απευθείας σε βιβλία εργασίας Excel. Αυτό το σεμινάριο σας καθοδηγεί μέσω της εγκατάστασης, της βασικής χρήσης και της προχωρημένης μορφοποίησης ώστε να ασφαλίζετε τα έγγραφα διατηρώντας τη σταθερή επωνυμία.

## Γρήγορες Απαντήσεις
- **Τι κάνει η βιβλιοθήκη;** Εισάγει προσαρμόσιμα υδατογραφήματα κειμένου σε αρχεία Excel χωρίς να τροποποιεί το αρχικό περιεχόμενο.  
- **Ποια έκδοση απαιτείται;** GroupDocs.Watermark for Java 24.11 ή νεότερη.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για αξιολόγηση· μια μόνιμη άδεια αφαιρεί όλους τους περιορισμούς.  
- **Μπορώ να στοχεύσω ένα μόνο φύλλο;** Ναι – μπορείτε να εφαρμόσετε υδατογραφήματα σε συγκεκριμένα φύλλα εργασίας.  
- **Είναι γρήγορο σε μεγάλα αρχεία;** Ναι, επεξεργάζεται βιβλία εργασίας με εκατοντάδες σελίδες χρησιμοποιώντας ροή, διατηρώντας τη χρήση μνήμης χαμηλή.

## Τι είναι το “add text watermark excel”;
**Add text watermark excel** αναφέρεται στη διαδικασία ενσωμάτωσης μιας ορατής επικάλυψης κειμένου σε ένα βιβλίο εργασίας Excel για να υποδείξει εμπιστευτικότητα, ιδιοκτησία ή επωνυμία. Αυτή η επικάλυψη αποθηκεύεται ως μέρος του αρχείου και παραμένει ορατή όταν το λογιστικό φύλλο ανοίγει σε οποιονδήποτε συμβατό προβολέα.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark για Java;
Το GroupDocs.Watermark υποστηρίζει **30+ μορφές εισόδου και εξόδου** και μπορεί να επεξεργαστεί αρχεία Excel έως **200 MB** χωρίς να φορτώνει ολόκληρο το βιβλίο εργασίας στη μνήμη, παρέχοντας απόδοση κάτω του δευτερολέπτου σε τυπικό εξοπλισμό διακομιστή. Το API του είναι πλήρως ασφαλές για νήματα, καθιστώντας το ιδανικό για αγωγούς υψηλής απόδοσης σε επιχειρήσεις.

## Προαπαιτούμενα
1. **Βιβλιοθήκες και Εξαρτήσεις**  
   - GroupDocs.Watermark for Java (Version 24.11 ή νεότερη)  
2. **Ρύθμιση Περιβάλλοντος**  
   - Ένα Java Development Kit (JDK) 8 ή νεότερο εγκατεστημένο  
3. **Απαιτήσεις Γνώσεων**  
   - Βασικές δεξιότητες προγραμματισμού Java  
   - Εξοικείωση με το Maven για διαχείριση εξαρτήσεων  

## Πώς να προσθέσετε υδατογράφημα κειμένου excel – Οδηγός Βήμα‑Βήμα
Για να ενσωματώσετε ένα υδατογράφημα κειμένου σε ένα βιβλίο εργασίας Excel, πρώτα φορτώνετε το αρχείο με το Watermarker, στη συνέχεια ορίζετε την εμφάνιση του υδατογραφήματος και τέλος το εφαρμόζετε στα επιθυμητά φύλλα πριν την αποθήκευση. Η διαδικασία είναι απλή και μπορεί να υλοποιηθεί με λίγες γραμμές κώδικα Java, όπως φαίνεται στα παρακάτω αποσπάσματα.

### Βήμα 1: Φόρτωση του Εγγράφου Excel
**Direct answer:** Αρχικοποιήστε την κλάση `Watermarker` με τη διαδρομή του αρχείου Excel και τις κατάλληλες επιλογές φόρτωσης – αυτό προετοιμάζει το έγγραφο για λειτουργίες υδατογραφήματος.  

``` 
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
```  

### Βήμα 2: Δημιουργία και Διαμόρφωση του Υδατογραφήματος Κειμένου
**Direct answer:** Δημιουργήστε ένα αντικείμενο `TextWatermark`, ορίστε το κείμενο, τη γραμματοσειρά, το μέγεθος, το χρώμα και την ευθυγράμμιση, στη συνέχεια συνδέστε το με ένα αντικείμενο `SpreadsheetWatermarkOptions`.  

``` 
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.SpreadsheetLoadOptions;

// Initialize load options
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();

// Create a watermarker instance for the Excel file
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```
```  

### Βήμα 3: Εφαρμογή του Υδατογραφήματος στα Επιθυμητά Φύλλα
**Direct answer:** Χρησιμοποιήστε τη μέθοδο `add` στο αντικείμενο `Watermarker`, περνώντας τις επιλογές και προαιρετικά καθορίζοντας έναν δείκτη φύλλου για να στοχεύσετε ένα μόνο φύλλο εργασίας.  

``` 
```java
import com.groupdocs.watermark.options.HorizontalAlignment;
import com.groupdocs.watermark.options.VerticalAlignment;
import com.groupdocs.watermark.watermarks.Color;
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Create a text watermark
TextWatermark watermark = new TextWatermark("Confidential", new Font("Segoe UI", 19));

// Set size, alignment and color of the watermark
watermark.setSizingType(TextWatermark.SIZING_TYPE.FIT_TO_PAGE);
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setVerticalAlignment(VerticalAlignment.Center);
```
```  

### Βήμα 4: Αποθήκευση του Υδατογραφημένου Βιβλίου Εργασίας
**Direct answer:** Καλέστε τη μέθοδο `save` στο `Watermarker`, παρέχοντας τη διαδρομή εξόδου και τη μορφή· η βιβλιοθήκη γράφει το υδατογραφημένο αρχείο διατηρώντας τα αρχικά δεδομένα.  

``` 
```java
// Save the watermarked document
watermarker.save("YOUR_OUTPUT_DIRECTORY/spreadsheet_watermarked.xlsx");

// Release resources
watermarker.close();
```
```  

## Εφαρμογή Εφέ Κειμένου σε Υδατογραφήματα σε Λογιστικά Φύλλα
Βελτιώστε την ορατότητα με στυλ γραμμής, διαφάνεια και περιστροφή.

### Προσαρμογή Μορφής Γραμμής
**Definition anchor:** Η κλάση `SpreadsheetTextEffects` είναι μια βοηθητική κλάση που ορίζει το πάχος της γραμμής, το στυλ παύλας και το χρώμα για υδατογραφήματα κειμένου σε λογιστικά φύλλα.  

``` 
```java
import com.groupdocs.watermark.options.SpreadsheetLineFormat;
import com.groupdocs.watermark.options.SpreadsheetDashStyle;
import com.groupdocs.watermark.options.SpreadsheetLineStyle;

// Set up text effects for the watermark
SpreadsheetTextEffects effects = new SpreadsheetTextEffects();
effects.getLineFormat().setEnabled(true);
effects.getLineFormat().setColor(Color.getRed());
effects.getLineFormat().setDashStyle(SpreadsheetDashStyle.DashDotDot);
effects.getLineFormat().setLineStyle(SpreadsheetLineStyle.Triple);
effects.getLineFormat().setWeight(1);
```
```  

### Εφαρμογή Εφέ στις Επιλογές Υδατογραφήματος
Ενσωματώστε το `SpreadsheetTextEffects` στο `SpreadsheetWatermarkOptions` για να ελέγξετε πώς το υδατογράφημα αποδίδεται σε κάθε σελίδα.

``` 
```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkShapeOptions;

// Attach effects to the watermark shape options
SpreadsheetWatermarkShapeOptions options = new SpreadsheetWatermarkShapeOptions();
options.setEffects(effects);
```
```  

## Πρακτικές Εφαρμογές
Τα λογιστικά φύλλα με υδατογράφημα κειμένου είναι χρήσιμα σε πολλές περιπτώσεις:

1. **Confidential Reports** – Σημειώστε οικονομικές καταστάσεις ως “Confidential” για να αποτρέψετε διαρροές.  
2. **Branding** – Επικάλυψη του λογότυπου ή του σλόγκαν της εταιρείας σας σε λογιστικά φύλλα που προορίζονται για πελάτες.  
3. **Legal Documentation** – Επισήμανση συμβάσεων και συμφωνιών για να διασφαλιστεί η αυθεντικότητα.  

## Σκέψεις για την Απόδοση
Κατά τη διαχείριση μεγάλων βιβλίων εργασίας Excel, ακολουθήστε τις καλύτερες πρακτικές:

- **Stream instead of load:** Το GroupDocs.Watermark επεξεργάζεται τα δεδομένα με ροή, αποφεύγοντας την πλήρη κατανομή μνήμης του εγγράφου.  
- **Close resources promptly:** Χρησιμοποιήστε try‑with‑resources ή ρητές κλήσεις `close()` για να ελευθερώσετε τους χειριστές αρχείων.  
- **Tune the JVM:** Αυξήστε το μέγεθος του heap (`-Xmx2g`) για αρχεία μεγαλύτερα από 100 MB, αλλά παρακολουθήστε τις παύσεις του GC.  

## Συμπέρασμα
Τώρα γνωρίζετε πώς να **add text watermark excel** αρχεία χρησιμοποιώντας το GroupDocs.Watermark για Java, από την βασική εισαγωγή μέχρι την προχωρημένη μορφοποίηση. Πειραματιστείτε με διαφορετικές γραμματοσειρές, χρώματα και γωνίες περιστροφής για να ταιριάζουν με την εταιρική σας ταυτότητα, και ενσωματώστε τη ροή εργασίας σε μεγαλύτερους αγωγούς επεξεργασίας εγγράφων για αυτοματοποιημένη προστασία.

## Συχνές Ερωτήσεις

**Q:** Ποιο είναι το μέγιστο μέγεθος αρχείου που υποστηρίζει το GroupDocs.Watermark;  
**A:** Η βιβλιοθήκη μπορεί να επεξεργαστεί βιβλία εργασίας Excel έως **200 MB** χωρίς μείωση της απόδοσης, χάρη στην αρχιτεκτονική ροής.

**Q:** Μπορώ να προσαρμόσω τα στυλ και τα μεγέθη γραμματοσειρών;  
**A:** Ναι – η κλάση `Font` σας επιτρέπει να ορίσετε οικογένεια, μέγεθος, στυλ (bold, italic) και χρώμα για οποιοδήποτε υδατογράφημα κειμένου.

**Q:** Είναι δυνατόν να προσθέσετε υδατογραφήματα μόνο σε συγκεκριμένα φύλλα;  
**A:** Απόλυτα. Χρησιμοποιήστε την υπερφόρτωση της μεθόδου `add` που δέχεται δείκτη ή όνομα φύλλου για να στοχεύσετε μεμονωμένα φύλλα εργασίας.

**Q:** Πώς πρέπει να διαχειριστώ σφάλματα κατά την εφαρμογή του υδατογραφήματος;  
**A:** Τυλίξτε τον κώδικά σας σε μπλοκ try‑catch και πιάστε τις εξαιρέσεις `IOException` και `WatermarkException` για να διαχειριστείτε προβλήματα πρόσβασης αρχείων και σφάλματα API με χάρη.

**Q:** Μπορούν τα υδατογραφήματα να αφαιρεθούν αργότερα αν χρειαστεί;  
**A:** Ναι – το GroupDocs.Watermark παρέχει ένα API `remove` που μπορεί να αφαιρέσει τα προηγουμένως προστιθέμενα υδατογραφήματα διατηρώντας το αρχικό περιεχόμενο.

---

**Τελευταία Ενημέρωση:** 2026-07-15  
**Δοκιμή Με:** GroupDocs.Watermark for Java 24.11  
**Συγγραφέας:** GroupDocs  

---

## Πόροι
- [GroupDocs.Watermark για Java εκδόσεις](https://releases.groupdocs.com/watermark/java/)
- [Τεκμηρίωση](https://docs.groupdocs.com/watermark/java/releases)

## Σχετικά Μαθήματα

- [Προσθήκη Υδατογραφήματος Εικόνας σε Φύλλο Excel Χρησιμοποιώντας το GroupDocs.Watermark Java SDK](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [Πώς να Προσθέσετε Συνημμένα σε Excel Χρησιμοποιώντας το GroupDocs.Watermark Java για Υδατογράφημα Λογιστικών Φύλλων](/watermark/java/spreadsheet-document-watermarking/groupdocs-watermark-java-add-attachments-excel/)
- [Μαθήματα Υδατογραφήματος Φύλλων Excel για το GroupDocs.Watermark Java](/watermark/java/spreadsheet-document-watermarking/)