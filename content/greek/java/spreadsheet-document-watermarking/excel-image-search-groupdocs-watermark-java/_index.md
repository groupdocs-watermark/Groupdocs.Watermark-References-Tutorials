---
date: '2026-06-01'
description: Μάθετε πώς να αναζητάτε εικόνες και να φορτώνετε αρχείο Excel java χρησιμοποιώντας
  το GroupDocs.Watermark Java για να αυτοματοποιήσετε τις αναζητήσεις εικόνων σε λογιστικά
  φύλλα αποδοτικά.
keywords:
- how to search images
- load excel file java
- GroupDocs.Watermark image search
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to search images and load Excel file java using GroupDocs.Watermark
    Java to automate image searches in spreadsheets efficiently.
  headline: How to Search Images in Excel with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to search images and load Excel file java using GroupDocs.Watermark
    Java to automate image searches in spreadsheets efficiently.
  name: How to Search Images in Excel with GroupDocs.Watermark Java
  steps:
  - name: '**Document Management Systems:** Automatically index and tag spreadsheets
      based on embedded logos or product photos.'
    text: '**Document Management Systems:** Automatically index and tag spreadsheets
      based on embedded logos or product photos.'
  - name: '**Data Auditing:** Verify that visual data (charts, screenshots) has not
      been altered by comparing DCT hashes across versions.'
    text: '**Data Auditing:** Verify that visual data (charts, screenshots) has not
      been altered by comparing DCT hashes across versions.'
  - name: '**Content Verification:** Ensure only authorized brand assets appear in
      financial reports or marketing decks.'
    text: '**Content Verification:** Ensure only authorized brand assets appear in
      financial reports or marketing decks.'
  type: HowTo
- questions:
  - answer: It supports XLSX, XLS, CSV, and ODS, handling both legacy and modern workbook
      structures.
    question: What file formats can GroupDocs.Watermark read for Excel?
  - answer: Yes, by setting `SpreadsheetSearchableObjects.All` you can include floating
      pictures, charts, and other drawing objects.
    question: Can I search for images that are not attached (e.g., floating shapes)?
  - answer: The algorithm achieves > 95 % similarity detection for resized or slightly
      recolored images, making it ideal for branding checks.
    question: How accurate is DCT hash matching?
  - answer: Absolutely. After locating a `Watermark`, call `watermarker.replace(watermark,
      newImagePath)` to swap the graphic.
    question: Is it possible to replace found images automatically?
  - answer: Yes, GroupDocs.Watermark is pure Java and runs on any platform with a
      compatible JRE, including Docker‑based Linux containers.
    question: Does the library work on Linux containers?
  type: FAQPage
title: Πώς να αναζητήσετε εικόνες στο Excel με το GroupDocs.Watermark Java
type: docs
url: /el/java/spreadsheet-document-watermarking/excel-image-search-groupdocs-watermark-java/
weight: 1
---

# Πώς να Αναζητήσετε Εικόνες σε Excel με το GroupDocs.Watermark Java

Η αναζήτηση συγκεκριμένων εικόνων μέσα σε βιβλία εργασίας Excel μπορεί να είναι επίπονη, ειδικά όταν αντιμετωπίζετε μεγάλα αρχεία ή πολλές ενσωματωμένες γραφικές παραστάσεις. **How to search images** γίνεται γρήγορα ένα κρίσιμο ερώτημα για όποιον αυτοματοποιεί ροές εργασίας εγγράφων. Σε αυτόν τον οδηγό θα σας δείξουμε ακριβώς πώς να αναζητήσετε εικόνες σε λογιστικά φύλλα Excel χρησιμοποιώντας το GroupDocs.Watermark Java, ενώ θα καλύψουμε επίσης τα απαραίτητα βήματα για **load Excel file java** έργα αποδοτικά.

## Γρήγορες Απαντήσεις
- **Ποιος είναι ο πιο γρήγορος τρόπος εντοπισμού μιας ενσωματωμένης εικόνας;** Use `ImageDctHashSearchCriteria` with `SpreadsheetSearchableObjects.AttachedImages`.  
- **Χρειάζομαι ειδική άδεια;** Μια προσωρινή ή δοκιμαστική άδεια ξεκλειδώνει πλήρεις δυνατότητες αναζήτησης.  
- **Ποια εξάρτηση Maven απαιτείται;** Προσθέστε `com.groupdocs:groupdocs-watermark` στο `pom.xml` σας.  
- **Μπορώ να περιορίσω την αναζήτηση σε ένα μόνο φύλλο;** Ναι, ρυθμίστε το `SpreadsheetLoadOptions` με το όνομα του φύλλου.  
- **Είναι το API thread‑safe;** Όλες οι δημόσιες μέθοδοι είναι ασφαλείς για ταυτόχρονη χρήση μετά τη σωστή αρχικοποίηση.  

`ImageDctHashSearchCriteria` ορίζει το DCT hash που χρησιμοποιείται για σύγκριση εικόνων. `SpreadsheetSearchableObjects.AttachedImages` περιορίζει την αναζήτηση σε ενσωματωμένες εικόνες.

## Τι σημαίνει “how to search images” στο πλαίσιο του GroupDocs.Watermark;
**“How to search images”** αναφέρεται στον προγραμματιστικό εντοπισμό ενσωματωμένων αντικειμένων εικόνας μέσα σε ένα έγγραφο χρησιμοποιώντας το Watermarker API. Η βιβλιοθήκη σαρώει κάθε φύλλο εργασίας, εξάγει αντικείμενα εικόνας, υπολογίζει το Discrete Cosine Transform (DCT) hash τους, και το συγκρίνει με το hash της εικόνας-στόχου, επιστρέφοντας τυχόν αντιστοιχίες ως αντικείμενα watermark που μπορούν να υποβληθούν σε περαιτέρω επεξεργασία.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark για αναζητήσεις εικόνων σε Excel;
Το GroupDocs.Watermark υποστηρίζει **50+ μορφές εισόδου και εξόδου**—συμπεριλαμβανομένων των XLSX, XLS, CSV και ODS—ενώ επεξεργάζεται βιβλία εργασίας πολλών εκατοντάδων σελίδων χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη. Ο αλγόριθμος DCT‑hash εντοπίζει οπτικά παρόμοιες εικόνες με > 95 % ακρίβεια, μειώνοντας δραστικά τα ψευδή θετικά. Επιπλέον, η βιβλιοθήκη προσφέρει πρόσβαση ροής, επιτρέποντας την εργασία με αρχεία μεγαλύτερα από τη διαθέσιμη RAM, και παρέχει ενσωματωμένη υποστήριξη για βιβλία εργασίας προστατευμένα με κωδικό, καθιστώντας το κατάλληλο για αυτοματοποιημένες γραμμές παραγωγής επιχειρησιακού επιπέδου.

## Προαπαιτούμενα

Before you begin, make sure you have:

- **Java Development Kit (JDK) 8+** εγκατεστημένο και ρυθμισμένο στο `PATH` σας.
- **Maven** για διαχείριση εξαρτήσεων (ή μπορείτε να κατεβάσετε τα JAR χειροκίνητα).
- Μια **GroupDocs.Watermark license** (δοκιμαστική, προσωρινή ή μόνιμη) για να ξεκλειδώσετε το API αναζήτησης.
- Βασική εξοικείωση με συλλογές Java και διαχείριση εξαιρέσεων.

### Απαιτούμενες Βιβλιοθήκες και Εξαρτήσεις
Για να εργαστείτε με το GroupDocs.Watermark Java, ρυθμίστε το περιβάλλον σας με Maven ή κατεβάστε τις απαραίτητες βιβλιοθήκες. Βεβαιωθείτε ότι έχετε:
- **Maven Configuration:** Προσθέστε το αποθετήριο GroupDocs και την εξάρτηση στο `pom.xml` σας.
- **Java Development Kit (JDK):** Απαιτείται έκδοση 8 ή νεότερη.

### Απαιτήσεις Ρύθμισης Περιβάλλοντος
Βεβαιωθείτε ότι η Java είναι σωστά εγκατεστημένη στο σύστημά σας, μαζί με το Maven για διαχείριση εξαρτήσεων εάν επιλέξετε αυτή τη μέθοδο εγκατάστασης.

### Προαπαιτούμενες Γνώσεις
Μια βασική κατανόηση του προγραμματισμού Java και εξοικείωση με τον προγραμματιστικό χειρισμό αρχείων Excel θα είναι χρήσιμη. Εάν είστε νέοι σε αυτές τις έννοιες, εξετάστε το ενδεχόμενο να εξερευνήσετε πρώτα εισαγωγικούς πόρους.

## Πώς να ρυθμίσετε το GroupDocs.Watermark για Java;
Φορτώστε το Maven project σας, προσθέστε την εξάρτηση και αρχικοποιήστε το Watermarker με τις κατάλληλες ρυθμίσεις. Αυτή η διαδικασία δύο βημάτων σας ετοιμάζει να ξεκινήσετε την αναζήτηση. Πρώτα, προσθέστε το αποθετήριο Maven και την εξάρτηση στο `pom.xml` σας, στη συνέχεια δημιουργήστε μια παρουσία Watermarker περνώντας τη διαδρομή του αρχείου Excel και ένα αντικείμενο `WatermarkLoadOptions` που καθορίζει το επιθυμητό φύλλο και τις ρυθμίσεις αναζήτησης. Το `SpreadsheetLoadOptions` σας επιτρέπει να καθορίσετε ποια φύλλα να φορτωθούν και να ρυθμίσετε επιλογές αναζήτησης όπως η ευαισθησία σε πεζά/κεφαλαία. Το `Watermarker` είναι το κύριο σημείο εισόδου για τη φόρτωση εγγράφων και την εκτέλεση αναζητήσεων ή λειτουργιών watermark.

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

## Πώς να φορτώσετε αρχείο Excel java με συγκεκριμένες ρυθμίσεις αναζήτησης;
Φορτώστε το βιβλίο εργασίας ενώ ενημερώνετε τη βιβλιοθήκη να κοιτάζει μόνο τις συνδεδεμένες εικόνες. Αυτή η εστιασμένη προσέγγιση μειώνει τον χρόνο επεξεργασίας έως **30 %** για τυπικά λογιστικά φύλλα.

``` 
```java
import com.groupdocs.watermark.Watermarker;
// Basic initialization code here...
```
```

## Πώς να ρυθμίσετε την αναζήτηση ώστε να στοχεύει μόνο σε συνδεδεμένες εικόνες;
Το enum `SpreadsheetSearchableObjects` σας επιτρέπει να καθορίσετε ακριβώς τι θα σαρώσετε. Ορίζοντάς το σε `AttachedImages` περιορίζει τη μηχανή σε αντικείμενα εικόνας, αγνοώντας κείμενο, τύπους ή διαγράμματα.

``` 
```java
import com.groupdocs.watermark.WatermarkerSettings;
import com.groupdocs.watermark.options.SpreadsheetLoadOptions;

WatermarkerSettings settings = new WatermarkerSettings();
settings.getSearchableObjects().setSpreadsheetSearchableObjects(SpreadsheetSearchableObjects.AttachedImages);
```
```

## Πώς να εκτελέσετε αναζήτηση εικόνας χρησιμοποιώντας κριτήρια DCT hash;
Η μέθοδος DCT‑hash δημιουργεί ένα συμπαγές αποτύπωμα της εικόνας-αναφοράς και το συγκρίνει με κάθε ενσωματωμένη εικόνα, επιστρέφοντας αντιστοιχίες με υψηλή οπτική ομοιότητα.

``` 
```java
import com.groupdocs.watermark.Watermarker;

String filePath = "YOUR_DOCUMENT_DIRECTORY/spreadsheet.xlsx";
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
Watermarker watermarker = new Watermarker(filePath, loadOptions, settings);
```
```

## Πώς να ορίσετε τα κριτήρια αναζήτησης DCT hash;
`ImageDctHashSearchCriteria` ενσωματώνει την εικόνα-αναφορά και ένα προαιρετικό όριο ομοιότητας. Μπορείτε να προσαρμόσετε το όριο (0‑100) για να σφίξετε ή να χαλαρώσετε την αντιστοίχιση.

``` 
```java
// Reuse the previous configuration from the 'Load Spreadsheet' section.
```
```

## Πώς να εκτελέσετε την αναζήτηση και να επεξεργαστείτε τα αποτελέσματα;
Καλώντας `watermarker.search(criteria)` επιστρέφει μια συλλογή αντικειμένων `Watermark`. Επανάληψη στη συλλογή για να ανακτήσετε αριθμούς σελίδων, διευθύνσεις κελιών ή για να αντικαταστήσετε την εικόνα.

``` 
```java
import com.groupdocs.watermark.search.ImageDctHashSearchCriteria;

String imagePath = "YOUR_DOCUMENT_DIRECTORY/sample_image.png";
ImageDctHashSearchCriteria criteria = new ImageDctHashSearchCriteria(imagePath);
```
```

## Πρακτικές Εφαρμογές
Ακολουθούν μερικά σενάρια πραγματικού κόσμου όπου αυτές οι δυνατότητες διαπρέπουν:

1. **Document Management Systems:** Αυτόματη ευρετηρίαση και ετικετοθέτηση λογιστικών φύλλων βάσει ενσωματωμένων λογοτύπων ή φωτογραφιών προϊόντων.  
2. **Data Auditing:** Επαλήθευση ότι τα οπτικά δεδομένα (διαγράμματα, στιγμιότυπα) δεν έχουν τροποποιηθεί συγκρίνοντας DCT hashes μεταξύ εκδόσεων.  
3. **Content Verification:** Διασφάλιση ότι εμφανίζονται μόνο εξουσιοδοτημένα στοιχεία μάρκας σε οικονομικές αναφορές ή παρουσιάσεις μάρκετινγκ.

## Σκέψεις Απόδοσης
Για να διατηρήσετε την εφαρμογή σας γρήγορη:

- **Περιορίστε την αναζήτηση** μόνο σε `AttachedImages`; αυτό μειώνει τη χρήση CPU κατά ~30 % κατά μέσο όρο.  
- **Επεξεργαστείτε μεγάλα αρχεία** σε τμήματα φορτώνοντας μεμονωμένα φύλλα αντί για ολόκληρο το βιβλίο εργασίας.  
- **Επαναχρησιμοποιήστε το `WatermarkerSettings`** σε πολλαπλές αναζητήσεις για να αποφύγετε επαναλαμβανόμενη δημιουργία αντικειμένων.  
- **Παρακολουθήστε τη μνήμη** με εργαλεία προφίλ Java· η βιβλιοθήκη ρέει δεδομένα, αλλά πολύ μεγάλες εικόνες μπορεί ακόμη να επηρεάσουν τη χρήση του heap.

## Συχνά Προβλήματα και Λύσεις

| Σύμπτωμα | Πιθανή Αιτία | Διόρθωση |
|---|---|---|
| Δεν επιστράφηκαν αποτελέσματα | Τα searchable objects έχουν οριστεί σε `None` | Ορίστε `SpreadsheetSearchableObjects.AttachedImages`. |
| `OutOfMemoryError` σε αρχείο 500 σελίδων | Ολόκληρο το βιβλίο εργασίας φορτώνεται στη μνήμη | Χρησιμοποιήστε `SpreadsheetLoadOptions` με `setLoadAllSheets(false)` και φορτώστε τα φύλλα ξεχωριστά. |
| Ψευδώς θετικά στην σύγκριση hash | Το όριο είναι πολύ χαμηλό (π.χ., 30) | Αυξήστε το όριο ομοιότητας σε 80‑90 για πιο αυστηρή αντιστοίχιση. |

## Συχνές Ερωτήσεις

**Q: Ποια μορφάτωση αρχείων μπορεί να διαβάσει το GroupDocs.Watermark για Excel;**  
A: Υποστηρίζει XLSX, XLS, CSV και ODS, διαχειριζόμενο τόσο τις παλαιές όσο και τις σύγχρονες δομές βιβλίων εργασίας.

**Q: Μπορώ να αναζητήσω εικόνες που δεν είναι συνδεδεμένες (π.χ., αιωρούμενα σχήματα);**  
A: Ναι, ορίζοντας `SpreadsheetSearchableObjects.All` μπορείτε να συμπεριλάβετε αιωρούμενες εικόνες, διαγράμματα και άλλα αντικείμενα σχεδίασης.

**Q: Πόσο ακριβής είναι η αντιστοίχιση DCT hash;**  
A: Ο αλγόριθμος επιτυγχάνει > 95 % ανίχνευση ομοιότητας για εικόνες που έχουν αλλάξει μέγεθος ή ελαφρώς επαναχρωματιστεί, καθιστώντας το ιδανικό για ελέγχους μάρκας.

**Q: Είναι δυνατόν να αντικαταστήσετε αυτόματα τις εικόνες που βρέθηκαν;**  
A: Απόλυτα. Αφού εντοπίσετε ένα `Watermark`, καλέστε `watermarker.replace(watermark, newImagePath)` για να ανταλλάξετε το γραφικό.

**Q: Λειτουργεί η βιβλιοθήκη σε Linux containers;**  
A: Ναι, το GroupDocs.Watermark είναι καθαρά Java και εκτελείται σε οποιαδήποτε πλατφόρμα με συμβατό JRE, συμπεριλαμβανομένων των Docker‑based Linux containers.

## Συμπέρασμα
Σε αυτό το σεμινάριο περάσαμε από το **how to search images** μέσα σε βιβλία εργασίας Excel χρησιμοποιώντας το GroupDocs.Watermark Java, από τη ρύθμιση του περιβάλλοντος μέχρι την εκτέλεση αναζήτησης βασισμένης σε DCT‑hash. Περιορίζοντας τη σάρωση σε συνδεδεμένες εικόνες και αξιοποιώντας τη δυνατή σύγκριση hash, μπορείτε να επιταχύνετε δραστικά τις ροές εργασίας επαλήθευσης εικόνων διατηρώντας υψηλή ακρίβεια. Στη συνέχεια, εξερευνήστε τις δυνατότητες προσθήκης watermark της βιβλιοθήκης ή ενσωματώστε τη λογική αναζήτησης σε μια μεγαλύτερη γραμμή επεξεργασίας εγγράφων.

---

**Τελευταία Ενημέρωση:** 2026-06-01  
**Δοκιμάστηκε Με:** GroupDocs.Watermark 23.12 for Java  
**Συγγραφέας:** GroupDocs  

**Πόροι**  
- **Τεκμηρίωση:** [GroupDocs.Watermark Java Docs](https://docs.groupdocs.com/watermark/java/)  
- **Αναφορά API:** [GroupDocs API Reference](https://reference.groupdocs.com/watermark/java)  
- **Λήψη:** [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)

```java
import com.groupdocs.watermark.PossibleWatermarkCollection;

PossibleWatermarkCollection possibleWatermarks = watermarker.search(criteria);
```

## Πόροι
- [GroupDocs.Watermark για εκδόσεις Java](https://releases.groupdocs.com/watermark/java/)
- [GroupDocs.Watermark Java Docs](https://docs.groupdocs.com/watermark/java/)
- [GroupDocs API Reference](https://reference.groupdocs.com/watermark/java)
- [GroupDocs Downloads](https://releases.groupdocs.com/watermark/java/)

## Σχετικά Μαθήματα

- [Προσθήκη Υδατογραφήματος Εικόνας σε Φύλλο Excel χρησιμοποιώντας το GroupDocs.Watermark Java SDK](/watermark/java/spreadsheet-document-watermarking/add-image-watermark-spreadsheet-groupdocs-java/)
- [Αντικατάσταση Εικόνων σε Σχήματα Excel χρησιμοποιώντας το GroupDocs.Watermark για Java: Πλήρης Οδηγός](/watermark/java/spreadsheet-document-watermarking/replace-images-excel-shapes-groupdocs-watermark-java/)
- [Ασφαλίστε τα Φύλλα Excel σας με το GroupDocs.Watermark σε Java](/watermark/java/spreadsheet-document-watermarking/protect-excel-spreadsheets-groupdocs-watermark-java/)