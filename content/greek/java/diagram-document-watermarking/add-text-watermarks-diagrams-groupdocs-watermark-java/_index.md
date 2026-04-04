---
date: '2026-04-04'
description: Μάθετε πώς να δημιουργείτε υδατογράφημα κειμένου σε διαγράμματα Visio
  χρησιμοποιώντας το GroupDocs.Watermark για Java. Περιλαμβάνει εγκατάσταση, κώδικα
  και πραγματικές περιπτώσεις χρήσης.
keywords:
- create text watermark
- add watermark diagram
- groupdocs watermark java
- watermark visio diagram
title: Δημιουργία Υδατογραφήματος Κειμένου σε Διαγράμματα με το GroupDocs.Watermark
  Java
type: docs
url: /el/java/diagram-document-watermarking/add-text-watermarks-diagrams-groupdocs-watermark-java/
weight: 1
---

# Δημιουργία Υδατογραφήματος Κειμένου σε Διαγράμματα με GroupDocs.Watermark Java

Η προστασία των διαγραμμάτων σας από μη εξουσιοδοτημένη επαναχρησιμοποίηση είναι απαραίτητη στα σημερινά συνεργατικά περιβάλλοντα. Σε αυτό το tutorial θα **δημιουργήσετε υδατογράφημα κειμένου** σε διαγράμματα τύπου Visio χρησιμοποιώντας το **GroupDocs.Watermark for Java**. Θα καλύψουμε όλα τα βήματα, από τη ρύθμιση του Maven μέχρι την αποθήκευση του αρχείου με υδατογράφημα, ώστε να μπορείτε με σιγουριά να προσθέτετε σήματα εμπορικής ταυτότητας ή ασφαλείας σε κάθε σελίδα διαγράμματος.

## Γρήγορες Απαντήσεις
- **Ποια βιβλιοθήκη χρειάζομαι;** GroupDocs.Watermark for Java (Maven artifact `groupdocs-watermark`).
- **Ποιοι τύποι αρχείων υποστηρίζονται;** Visio (`.vsdx`, `.vsd`), as well as many other diagram formats.
- **Χρειάζομαι άδεια;** A temporary trial license works for development; a full license is required for production.
- **Μπορώ να προσαρμόσω τη γραμματοσειρά, το χρώμα και την περιστροφή;** Yes – the `TextWatermark` class lets you set all of those properties.
- **Πόσο χρόνο διαρκεί η διαδικασία;** Adding a text watermark to a typical diagram takes less than a second on modern hardware.

## Τι είναι η λειτουργία «δημιουργία υδατογραφήματος κειμένου»;
Η δημιουργία υδατογραφήματος κειμένου σημαίνει την προγραμματιστική επικάλυψη ημιδιαφανούς κειμένου πάνω σε μια σελίδα εγγράφου. Το υδατογράφημα μπορεί να τοποθετηθεί στο προσκήνιο ή στο παρασκήνιο, να περιστραφεί, να χρωματιστεί και να μορφοποιηθεί ώστε να ταιριάζει στις απαιτήσεις εμπορικής ταυτότητας ή ασφάλειας.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark για Java;
- **Ευρεία υποστήριξη μορφών** – works with Visio, PDF, Word, Excel, and more.
- **Ακριβής έλεγχος** – choose placement, opacity, rotation, and background/foreground rendering.
- **Εύκολη ενσωμάτωση** – Maven‑based setup and straightforward API calls keep your code clean.
- **Βελτιστοποιημένη απόδοση** – resources are released automatically when you close the `Watermarker`.

## Προαπαιτούμενα
- Java Development Kit (JDK) 8 ή νεότερο.
- Ένα IDE όπως το IntelliJ IDEA ή το Eclipse.
- Maven για διαχείριση εξαρτήσεων.

## Ρύθμιση του GroupDocs.Watermark για Java
Προσθέστε το αποθετήριο και την εξάρτηση στο `pom.xml` σας:

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

Αν προτιμάτε χειροκίνητη λήψη, κατεβάστε τα δυαδικά αρχεία από [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/) και προσθέστε τα στο classpath του έργου σας.

### Απόκτηση Άδειας
Ξεκινήστε με μια δωρεάν δοκιμαστική άδεια από [GroupDocs.Trial Licensing](https://purchase.groupdocs.com/temporary-license/). Φορτώστε το αρχείο άδειας πριν από οποιαδήποτε λειτουργία υδατογραφήματος:

```java
License license = new License();
license.setLicense("path/to/license/file");
```

## Υλοποίηση Βήμα‑βήμα

### Βήμα 1: Φόρτωση του Αρχείου Διαγράμματος
Χρησιμοποιήστε το `DiagramLoadOptions` για να ανοίξετε ένα αρχείο Visio (ή οποιαδήποτε υποστηριζόμενη μορφή διαγράμματος).

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/diagram.vsdx";
Watermarker watermarker = new Watermarker(inputFilePath, new DiagramLoadOptions());
```

### Βήμα 2: Δημιουργία του Υδατογραφήματος Κειμένου
Ρυθμίστε το κείμενο του υδατογραφήματος, τη γραμματοσειρά, το χρώμα, τη σημαία παρασκηνίου και τη γωνία περιστροφής.

```java
TextWatermark textWatermark = new TextWatermark("Test watermark", new Font("Arial", 36));
textWatermark.setColor(Color.getBlue());
textWatermark.setBackground(false);
textWatermark.setRotationAngle(-45);
```

### Βήμα 3: Ορισμός Τοποθέτησης για το Διάγραμμα
Επιλέξτε αν το υδατογράφημα θα εμφανίζεται στο παρασκήνιο ή στο προσκήνιο κάθε σελίδας διαγράμματος.

```java
DiagramShapeWatermarkOptions options = new DiagramShapeWatermarkOptions();
options.setPlacement(DiagramWatermarkPlacementType.Background);
watermarker.add(textWatermark, options);
```

### Βήμα 4: Αποθήκευση του Διαγράμματος με Υδατογράφημα
Γράψτε το αποτέλεσμα σε ένα νέο αρχείο και απελευθερώστε τους πόρους.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/watermarked_diagram.vsdx";
watermarker.save(outputFilePath);
watermarker.close();
```

## Συνηθισμένα Προβλήματα & Λύσεις
| Πρόβλημα | Λύση |
|---------|----------|
| **Αρχείο δεν βρέθηκε** | Επαληθεύστε τις απόλυτες/σχετικές διαδρομές και βεβαιωθείτε ότι το αρχείο είναι αναγνώσιμο από τη διαδικασία Java. |
| **Η άδεια δεν εφαρμόστηκε** | Επιβεβαιώστε ότι η διαδρομή του αρχείου άδειας είναι σωστή και ότι το αρχείο δεν είναι κατεστραμμένο. |
| **Το υδατογράφημα δεν είναι ορατό** | Ελέγξτε το `setBackground(false)` και τη γωνία περιστροφής· δοκιμάστε διαφορετικό χρώμα ή διαφάνεια. |
| **Μη υποστηριζόμενη έκδοση διαγράμματος** | Χρησιμοποιήστε την πιο πρόσφατη έκδοση του GroupDocs.Watermark (24.11) που προσθέτει υποστήριξη για νεότερες μορφές Visio. |

## Πρακτικές Περιπτώσεις Χρήσης
1. **Ασφάλεια Εγγράφου** – Prevent competitors from re‑using proprietary flowcharts.
2. **Συνεπής Επωνυμία** – Automatically embed company name or logo across all exported diagrams.
3. **Παρακολούθηση Συνεργασίας** – Add user initials as a watermark to identify who edited each diagram.

## Συμβουλές Απόδοσης
- Κλείστε το `Watermarker` μόλις ολοκληρώσετε για να ελευθερώσετε τους εγγενείς πόρους.
- Για επεξεργασία σε παρτίδες, επαναχρησιμοποιήστε μια μόνο παρουσία του `Watermarker` όταν είναι δυνατόν.
- Κρατήστε το κείμενο του υδατογραφήματος σύντομο· μεγάλες γραμματοσειρές αυξάνουν το χρόνο απόδοσης.

## Συμπέρασμα
Τώρα ξέρετε πώς να **δημιουργήσετε υδατογράφημα κειμένου** σε διαγράμματα Visio χρησιμοποιώντας το GroupDocs.Watermark για Java. Αυτή η προσέγγιση σας δίνει πλήρη έλεγχο πάνω στην εμφάνιση, την τοποθέτηση και το στυλ, βοηθώντας σας να προστατεύετε και να ταυτοποιείτε τα οπτικά σας περιουσιακά στοιχεία αποτελεσματικά.

### Επόμενα Βήματα
- Δοκιμάστε υδατογραφήματα εικόνας (`ImageWatermark`) για την επωνυμία λογότυπου.
- Εξερευνήστε την επιλεκτική τοποθέτηση υδατογραφήματος σε σελίδες, επαναλαμβάνοντας το `watermarker.getPages()` και εφαρμόζοντας επιλογές υπό όρους.
- Ενσωματώστε αυτή τη λογική στην αλυσίδα CI/CD σας για να ασφαλίζετε αυτόματα τα διαγράμματα πριν από τη δημοσίευση.

## Ενότητα Συχνών Ερωτήσεων
1. **Μπορώ να χρησιμοποιήσω το GroupDocs.Watermark για άλλες μορφές αρχείων;**  
   Ναι, υποστηρίζει PDF, έγγραφα Word, φύλλα Excel, παρουσιάσεις PowerPoint και πολλά άλλα.
2. **Υπάρχει όριο στον αριθμό των υδατογραφημάτων που μπορώ να προσθέσω;**  
   Δεν υπάρχει σκληρό όριο, αλλά η προσθήκη πολλών σύνθετων υδατογραφημάτων μπορεί να επηρεάσει την απόδοση.
3. **Πώς αφαιρώ ένα υδατογράφημα από ένα διάγραμμα;**  
   Το GroupDocs.Watermark παρέχει API ανίχνευσης και αφαίρεσης που μπορείτε να καλέσετε παρόμοια με τη ροή προσθήκης.
4. **Μπορούν τα υδατογραφήματα κειμένου να προστεθούν σε όλες τις σελίδες ή μόνο σε επιλεγμένες;**  
   Μπορείτε να διαμορφώσετε το `DiagramShapeWatermarkOptions` ανά σελίδα ή να εφαρμόσετε φίλτρα πριν καλέσετε το `add`.
5. **Τι πρέπει να κάνω αν το υδατογράφημα δεν εμφανίζεται όπως αναμένεται;**  
   Ελέγξτε ξανά τις ρυθμίσεις τοποθέτησης, την αντίθεση χρώματος και βεβαιωθείτε ότι το διάγραμμα δεν συμπιέζεται μετά την αποθήκευση.

## Συχνές Ερωτήσεις

**Q: Λειτουργεί η βιβλιοθήκη με αρχεία Visio 2003 (`.vsd`);**  
A: Ναι – το `DiagramLoadOptions` υποστηρίζει τόσο τις μορφές `.vsdx` όσο και τις παλαιότερες `.vsd`.

**Q: Μπορώ να αλλάξω τη διαφάνεια του υδατογραφήματος κειμένου;**  
A: Απόλυτα. Χρησιμοποιήστε το `textWatermark.setOpacity(0.5);` για να ορίσετε διαφάνεια 50 %.

**Q: Είναι δυνατόν να προσθέσετε διαφορετικά υδατογραφήματα σε διαφορετικές σελίδες διαγράμματος;**  
A: Ναι. Επαναλάβετε μέσω του `watermarker.getPages()` και εφαρμόστε διαφορετικές παρουσίες `TextWatermark` με προσαρμοσμένες επιλογές ανά σελίδα.

**Q: Υπάρχουν περιορισμοί άδειας για εμπορική χρήση;**  
A: Απαιτείται πλήρης εμπορική άδεια για παραγωγικές εγκαταστάσεις· η δοκιμαστική άδεια προορίζεται μόνο για αξιολόγηση.

**Q: Πώς μπορώ να επεξεργαστώ πολλαπλά διαγράμματα σε μια εκτέλεση;**  
A: Τυλίξτε τα παραπάνω βήματα σε έναν βρόχο που φορτώνει κάθε αρχείο, εφαρμόζει το υδατογράφημα, αποθηκεύει και κλείνει το `Watermarker` πριν προχωρήσει στο επόμενο αρχείο.

---

**Τελευταία Ενημέρωση:** 2026-04-04  
**Δοκιμάστηκε Με:** GroupDocs.Watermark 24.11 for Java  
**Συγγραφέας:** GroupDocs  

## Πόροι
- [Τεκμηρίωση](https://docs.groupdocs.com/watermark/java/)
- [Αναφορά API](https://reference.groupdocs.com/watermark/java)
- [Λήψη Τελευταίας Έκδοσης](https://releases.groupdocs.com/watermark/java/)
- [Αποθετήριο GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Δωρεάν Φόρουμ Υποστήριξης](https://forum.groupdocs.com/c/watermark/10)