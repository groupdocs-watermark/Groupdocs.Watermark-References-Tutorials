---
date: '2026-07-01'
description: Μάθετε πώς να watermark αρχεία Excel χρησιμοποιώντας Java με GroupDocs.Watermark,
  συμπεριλαμβανομένων βήμα‑βήμα οδηγιών για την προσθήκη watermark σε Excel με Java.
keywords:
- how to watermark excel
- java add excel watermark
- GroupDocs.Watermark
- Excel WordArt watermark
schemas:
- author: GroupDocs
  dateModified: '2026-07-01'
  description: Learn how to watermark Excel files using Java with GroupDocs.Watermark,
    including step‑by‑step instructions to java add excel watermark.
  headline: How to Watermark Excel with WordArt – GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to watermark Excel files using Java with GroupDocs.Watermark,
    including step‑by‑step instructions to java add excel watermark.
  name: How to Watermark Excel with WordArt – GroupDocs.Watermark Java
  steps:
  - name: Load the Excel Document
    text: Instantiate a `Watermarker` object with the path to your `.xlsx` file and
      a `SpreadsheetLoadOptions` instance. This tells the library to treat the file
      as a spreadsheet and prepares it for watermarking.
  - name: Create a TextWatermark
    text: Create a `TextWatermark` object, passing the WordArt text (e.g., “CONFIDENTIAL”)
      and a `Font` that defines size, style, and color. GroupDocs.Watermark automatically
      converts this text into a WordArt drawing.
  - name: Configure Modern WordArt Options
    text: Use `SpreadsheetWatermarkModernWordArtOptions` to specify the target worksheet
      (by index or name), rotation angle, opacity, and scaling. Setting `setRotateAngle(45)`
      and `setOpacity(0.3)` yields a subtle diagonal watermark that doesn’t obscure
      cell content.
  - name: Add the Watermark and Save
    text: Call `watermarker.add(watermark, options)` to apply the WordArt to the selected
      sheet, then invoke `watermarker.save("output.xlsx")`. The `save` method writes
      a new workbook while leaving the original untouched.
  type: HowTo
- questions:
  - answer: Yes – iterate over each sheet index and call `watermarker.add(watermark,
      options)` with the corresponding `SpreadsheetWatermarkModernWordArtOptions`.
    question: Can I apply the same WordArt watermark to all worksheets in a workbook?
  - answer: No – the watermark is added as a drawing layer, leaving all cell data,
      formulas, and pivot configurations untouched.
    question: Does the watermark affect Excel formulas or pivot tables?
  - answer: The library supports **50+ formats**, including CSV, XLS, ODS, and even
      PDF, enabling cross‑format watermarking with the same API.
    question: What file formats can GroupDocs.Watermark handle besides XLSX?
  - answer: Adjust the `Color` property of the `Font` object when creating the `TextWatermark`,
      e.g., `new Color(0, 120, 215)` for a corporate blue.
    question: How do I change the watermark color to match my corporate palette?
  - answer: Absolutely – add each watermark sequentially with its own options; they
      will be layered in the order of insertion.
    question: Is it possible to add multiple watermarks (e.g., logo + text) to the
      same sheet?
  type: FAQPage
title: Πώς να watermark Excel με WordArt – GroupDocs.Watermark Java
type: docs
url: /el/java/spreadsheet-document-watermarking/groupdocs-watermark-java-wordart-excel/
weight: 1
---

# Πώς να προσθέσετε υδατογράφημα σε Excel με WordArt – GroupDocs.Watermark Java

Η ενσωμάτωση ενός υδατογραφήματος σε ένα βιβλίο εργασίας Excel είναι ένας αξιόπιστος τρόπος προστασίας εμπιστευτικών δεδομένων, ενίσχυσης της επωνυμίας ή ένδειξης της κατάστασης του εγγράφου. Σε αυτόν τον οδηγό θα μάθετε **πώς να προσθέσετε υδατογράφημα σε αρχεία Excel** χρησιμοποιώντας τη βιβλιοθήκη GroupDocs.Watermark για Java, με σύγχρονο στυλ WordArt που φαίνεται επαγγελματικό σε οποιοδήποτε φύλλο. Θα περάσουμε από τις προαπαιτούμενες ρυθμίσεις, τις ακριβείς κλήσεις API, συμβουλές απόδοσης και κοινές παγίδες, ώστε να υλοποιήσετε τη λύση γρήγορα και με σιγουριά.

## Γρήγορες Απαντήσεις
- **Μπορώ να προσθέσω υδατογράφημα WordArt χωρίς να γράψω XML;** Ναι – το GroupDocs.Watermark διαχειρίζεται όλες τις λεπτομέρειες χαμηλού επιπέδου για εσάς.  
- **Ποια έκδοση της βιβλιοθήκης απαιτείται;** Η έκδοση 24.11 ή νεότερη υποστηρίζει το σύγχρονο WordArt API.  
- **Χρειάζομαι άδεια για ανάπτυξη;** Μια δωρεάν δοκιμαστική άδεια λειτουργεί για δοκιμές· απαιτείται πλήρης άδεια για παραγωγή.  
- **Θα επηρεάσει το υδατογράφημα τους τύπους;** Όχι – το υδατογράφημα αποδίδεται ως επίπεδο σχεδίασης, αφήνοντας τα δεδομένα των κελιών ανέπαφα.  
- **Η διαδικασία είναι thread‑safe;** Ναι, εφόσον κάθε νήμα χρησιμοποιεί τη δική του παρουσία `Watermarker`.

## Τι είναι «πώς να προσθέσετε υδατογράφημα σε excel»;
**«How to watermark excel»** αναφέρεται στη διαδικασία προγραμματιστικής εισαγωγής μιας οπτικής επικάλυψης σε ένα βιβλίο εργασίας Excel για να υποδείξει ιδιοκτησία, εμπιστευτικότητα ή κατάσταση έκδοσης. Χρησιμοποιώντας το GroupDocs.Watermark, μπορείτε να εφαρμόσετε αυτήν την επικάλυψη με μία κλήση μεθόδου χωρίς να τροποποιήσετε τα υποκείμενα δεδομένα.

## Γιατί να χρησιμοποιήσετε υδατογραφήματα WordArt στο Excel;
Τα υδατογραφήματα WordArt προσφέρουν μια σύγχρονη, στιλιζαρισμένη εμφάνιση που ξεχωρίζει περισσότερο από απλό κείμενο ή εικόνα. Το GroupDocs.Watermark υποστηρίζει **50+ μορφές εισόδου και εξόδου** και μπορεί να επεξεργαστεί αρχεία Excel έως **500 MB** χωρίς να φορτώσει ολόκληρο το βιβλίο στη μνήμη, παρέχοντας τόσο οπτική επίδραση όσο και υψηλή απόδοση.

## Προαπαιτούμενα
- **Java Development Kit (JDK) 8+** εγκατεστημένο στο σύστημά σας.  
- **GroupDocs.Watermark for Java** έκδοση 24.11 ή νεότερη (λήψη από τη σελίδα επίσημης κυκλοφορίας).  
- Ένα IDE όπως **IntelliJ IDEA** ή **Eclipse** για επεξεργασία και κατασκευή του έργου.  
- Ένα **προσωρινό ή πλήρες κλειδί άδειας** για την ενεργοποίηση των λειτουργιών υδατογραφήματος.

### Απαιτούμενες Βιβλιοθήκες και Εξαρτήσεις
Προσθέστε το αποθετήριο Maven του GroupDocs.Watermark και την εξάρτηση στο `pom.xml` σας:

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

Μπορείτε επίσης να αποκτήσετε το JAR απευθείας από τη σελίδα [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) εάν προτιμάτε χειροκίνητη εγκατάσταση.

## Πώς να προσθέσετε υδατογράφημα WordArt σε φύλλο εργασίας Excel χρησιμοποιώντας το GroupDocs.Watermark Java;
`SpreadsheetLoadOptions` καθορίζει τις επιλογές φόρτωσης για αρχεία λογιστικών φύλλων.  
`TextWatermark` αντιπροσωπεύει ένα κειμενικό υδατογράφημα που μπορεί να αποδοθεί ως WordArt.  
`SpreadsheetWatermarkModernWordArtOptions` διαμορφώνει την εμφάνιση του WordArt και το φύλλο προορισμού.  
Η μέθοδος `add` εφαρμόζει το υδατογράφημα στο έγγραφο.  
Η μέθοδος `save` γράφει το τροποποιημένο βιβλίο σε αρχείο.

Φορτώστε το βιβλίο εργασίας Excel με `SpreadsheetLoadOptions`, δημιουργήστε ένα `TextWatermark` που περιέχει το επιθυμητό κείμενο WordArt, διαμορφώστε `SpreadsheetWatermarkModernWordArtOptions` ώστε να στοχεύει το πρώτο φύλλο, και τέλος καλέστε `add` ακολουθούμενο από `save`. Αυτή η ροή απαιτεί μόνο τέσσερις κλήσεις API και διατηρεί αυτόματα τύπους, διαγράμματα και μορφοποίηση κελιών ενώ αποδίδει το υδατογράφημα ως διανυσματικό γραφικό.

## Βήμα‑βήμα Υλοποίηση

### Βήμα 1: Φόρτωση του Εγγράφου Excel
Δημιουργήστε ένα αντικείμενο `Watermarker` με τη διαδρομή προς το αρχείο `.xlsx` και μια παρουσία `SpreadsheetLoadOptions`. Αυτό ενημερώνει τη βιβλιοθήκη ότι το αρχείο είναι λογιστικό φύλλο και το προετοιμάζει για υδατογράφημα.

### Βήμα 2: Δημιουργία TextWatermark
Δημιουργήστε ένα αντικείμενο `TextWatermark`, περνώντας το κείμενο WordArt (π.χ., “CONFIDENTIAL”) και ένα `Font` που ορίζει μέγεθος, στυλ και χρώμα. Το GroupDocs.Watermark μετατρέπει αυτόματα το κείμενο σε σχεδίαση WordArt.

### Βήμα 3: Διαμόρφωση Modern WordArt Options
Χρησιμοποιήστε το `SpreadsheetWatermarkModernWordArtOptions` για να ορίσετε το φύλλο προορισμού (με δείκτη ή όνομα), γωνία περιστροφής, διαφάνεια και κλίμακα. Η ρύθμιση `setRotateAngle(45)` και `setOpacity(0.3)` δημιουργεί ένα διακριτικό διαγώνιο υδατογράφημα που δεν καλύπτει το περιεχόμενο των κελιών.

### Βήμα 4: Προσθήκη του Υδατογραφήματος και Αποθήκευση
Καλέστε `watermarker.add(watermark, options)` για να εφαρμόσετε το WordArt στο επιλεγμένο φύλλο, στη συνέχεια εκτελέστε `watermarker.save("output.xlsx")`. Η μέθοδος `save` γράφει ένα νέο βιβλίο ενώ αφήνει το αρχικό ανέπαφο.

## Πώς να διαμορφώσετε τις επιλογές WordArt για βέλτιστη εμφάνιση;
`WordArtOptions` περιέχει ιδιότητες στυλ για το υδατογράφημα WordArt.  
Ορίστε τις ιδιότητες `fontFamily`, `fontSize`, `color`, `rotateAngle` και `opacity` ώστε να ταιριάζουν με τις οδηγίες της επωνυμίας σας. Για ισορροπημένη εμφάνιση, ένα μέγεθος γραμματοσειράς **36 pt**, ημιδιαφανής διαφάνεια **0.25** και περιστροφή **-30°** λειτουργούν καλά σε τυπικά φύλλα A4.

## Πώς να εξασφαλίσετε απόδοση κατά την υδατογράφημα μεγάλων αρχείων Excel;
`Watermarker` είναι η κύρια κλάση που φορτώνει και αποθηκεύει έγγραφα.  
Επαναχρησιμοποιήστε μία ενιαία παρουσία `Watermarker` ανά αρχείο, κλείστε την άμεσα με `watermarker.close()`, και αποφύγετε τη φόρτωση ολόκληρου του βιβλίου στη μνήμη ενεργοποιώντας τη λειτουργία streaming (`setEnableStreaming(true)`). Αυτή η προσέγγιση διατηρεί τη χρήση μνήμης κάτω από **100 MB** ακόμη και για βιβλία με εκατοντάδες φύλλα. Επιπλέον, επεξεργαστείτε κάθε φύλλο ξεχωριστά όταν χρειάζεται υδατογράφημα μόνο σε υποσύνολο, μειώνοντας περαιτέρω τη μνήμη.

## Πρακτικές Εφαρμογές
1. **Ασφάλεια Εγγράφου** – Αποτρέψτε την μη εξουσιοδοτημένη διανομή οικονομικών μοντέλων προσθέτοντας σήμα “CONFIDENTIAL” WordArt.  
2. **Ενίσχυση Επωνυμίας** – Προσθέστε το λογότυπο της εταιρείας σας ως στιλιζαρισμένο κείμενο σε κάθε αναφορά προς πελάτες.  
3. **Έλεγχος Έκδοσης** – Εμφανίστε την κατάσταση “DRAFT” ή “FINAL” απευθείας στο φύλλο, καθιστώντας σαφές ποια έκδοση εξετάζεται.

## Παράγοντες Απόδοσης
- **Διαχείριση Πόρων** – Πάντα κλείστε το `Watermarker` για απελευθέρωση χειριστών αρχείων.  
- **Επεξεργασία σε Παρτίδες** – Όταν εφαρμόζετε το ίδιο υδατογράφημα σε πολλά βιβλία, επαναχρησιμοποιήστε την παρουσία `TextWatermark` για μείωση του κόστους δημιουργίας αντικειμένων.  
- **Μεγάλα Αρχεία** – Για αρχεία μεγαλύτερα από **200 MB**, ενεργοποιήστε το streaming και επεξεργαστείτε φύλλα ξεχωριστά για χαμηλή χρήση heap.

## Κοινά Προβλήματα και Λύσεις
- **Το υδατογράφημα δεν εμφανίζεται** – Ελέγξτε ότι ο δείκτης φύλλου ταιριάζει με το φύλλο-στόχο· το προεπιλεγμένο είναι το πρώτο φύλλο (`0`).  
- **Παραμορφωμένο κείμενο** – Βεβαιωθείτε ότι η επιλεγμένη γραμματοσειρά είναι εγκατεστημένη στον διακομιστή· η έλλειψη γραμματοσειρών προκαλεί εναλλακτική απόδοση.  
- **Σφάλματα Άδειας** – `License.setLicense` καταχωρεί ένα αρχείο άδειας για πλήρη λειτουργικότητα. Χρησιμοποιήστε έγκυρο κλειδί δοκιμής για δοκιμές· οι παραγωγικές εγκαταστάσεις πρέπει να καταχωρήσουν μόνιμη άδεια μέσω `License.setLicense("path/to/license.lic")`.

## Συχνές Ερωτήσεις

**Ε: Μπορώ να εφαρμόσω το ίδιο υδατογράφημα WordArt σε όλα τα φύλλα ενός βιβλίου;**  
Α: Ναι – επαναλάβετε για κάθε δείκτη φύλλου και καλέστε `watermarker.add(watermark, options)` με τις αντίστοιχες `SpreadsheetWatermarkModernWordArtOptions`.

**Ε: Επηρεάζει το υδατογράφημα τους τύπους ή τους πίνακες Pivot του Excel;**  
Α: Όχι – το υδατογράφημα προστίθεται ως επίπεδο σχεδίασης, αφήνοντας όλα τα δεδομένα κελιών, τύπους και ρυθμίσεις Pivot ανέπαφα.

**Ε: Ποιες μορφές αρχείων μπορεί να διαχειριστεί το GroupDocs.Watermark εκτός από XLSX;**  
Α: Η βιβλιοθήκη υποστηρίζει **50+ μορφές**, συμπεριλαμβανομένων CSV, XLS, ODS και ακόμη PDF, επιτρέποντας υδατογράφημα διαφόρων τύπων με το ίδιο API.

**Ε: Πώς αλλάζω το χρώμα του υδατογραφήματος ώστε να ταιριάζει με την εταιρική μου παλέτα;**  
Α: Ρυθμίστε την ιδιότητα `Color` του αντικειμένου `Font` κατά τη δημιουργία του `TextWatermark`, π.χ., `new Color(0, 120, 215)` για εταιρικό μπλε.

**Ε: Είναι δυνατόν να προσθέσω πολλαπλά υδατογραφήματα (π.χ., λογότυπο + κείμενο) στο ίδιο φύλλο;**  
Α: Απόλυτα – προσθέστε κάθε υδατογράφημα διαδοχικά με τις δικές του επιλογές· θα στρωθούν με τη σειρά εισαγωγής.

## Συμπέρασμα
Τώρα έχετε μια πλήρη, έτοιμη για παραγωγή μέθοδο **πώς να προσθέσετε υδατογράφημα σε Excel** χρησιμοποιώντας το GroupDocs.Watermark για Java, με σύγχρονο στυλ WordArt, βέλτιστες πρακτικές απόδοσης και συμβουλές αντιμετώπισης προβλημάτων. Πειραματιστείτε με διαφορετικές γραμματοσειρές, χρώματα και γωνίες περιστροφής για να ταιριάξετε την επωνυμία σας, και σκεφτείτε την επέκταση της προσέγγισης για επεξεργασία πολλαπλών βιβλίων σε μια ενιαία εργασία.

---

**Τελευταία Ενημέρωση:** 2026-07-01  
**Δοκιμασμένο Με:** GroupDocs.Watermark 24.11 for Java  
**Συγγραφέας:** GroupDocs  

**Πόροι**  
- [Documentation](https://docs.groupdocs.com/watermark/java/)  
- [API Reference](https://reference.groupdocs.com/watermark/java)  
- [Download GroupDocs.Watermark for Java](https://releases.groupdocs.com/watermark/java/)  
- [GitHub Repository](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/watermark/10)  
- [Temporary License Acquisition](https://purchase.groupdocs.com/temporary-license/)

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

// Initialize load options and watermarker.
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx", loadOptions);
```

```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

// Configure font and watermark text.
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 8));
```

```java
import com.groupdocs.watermark.options.SpreadsheetWatermarkModernWordArtOptions;

// Apply watermark to the first sheet.
SpreadsheetWatermarkModernWordArtOptions options = new SpreadsheetWatermarkModernWordArtOptions();
options.setWorksheetIndex(0);
```

```java
// Add watermark and save the watermarked file.
watermarker.add(textWatermark, options);
watermarker.save("YOUR_OUTPUT_DIRECTORY/watermarked_spreadsheet.xlsx");
// Release resources.
watermarker.close();
```

## Σχετικά Μαθήματα

- [How to Add a Text Watermark to Excel Sheets Using GroupDocs.Watermark for Java](/watermark/java/spreadsheet-document-watermarking/add-text-watermark-excel-groupdocs-watermark-java/)
- [Add Image Watermark to Excel Spreadsheet Using GroupDocs.Watermark Java SDK](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [Excel Spreadsheet Watermarking Tutorials for GroupDocs.Watermark Java](/watermark/java/spreadsheet-document-watermarking/)