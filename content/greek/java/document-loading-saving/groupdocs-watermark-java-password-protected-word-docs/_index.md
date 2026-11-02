---
date: '2025-12-23'
description: Μάθετε πώς να φορτώνετε έγγραφα Word προστατευμένα με κωδικό μέσω του
  GroupDocs.Watermark Java, να εφαρμόζετε υδατογραφήματα και να διαχειρίζεστε ασφαλή
  αρχεία αποδοτικά.
keywords:
- load password-protected Word documents
- GroupDocs.Watermark Java setup
- watermarking secured files
title: Πώς να φορτώσετε έγγραφα Word με προστασία κωδικού και να προσθέσετε υδατογραφήματα
  χρησιμοποιώντας το GroupDocs.Watermark Java
type: docs
url: /el/java/document-loading-saving/groupdocs-watermark-java-password-protected-word-docs/
weight: 1
---

# Πώς να φορτώσετε έγγραφα Word με προστασία κωδικού και να προσθέσετε υδατογραφήματα χρησιμοποιώντας το GroupDocs.Watermark Java

Στις σύγχρονες επιχειρηματικές ροές εργασίας, συχνά χρειάζεται να **φορτώνετε αρχεία Word με προστασία κωδικού**, να τα επεξεργάζεστε και να εφαρμόζετε υδατογραφήματα branding πριν τα μοιραστείτε. Αυτό το εκπαιδευτικό υλικό σας καθοδηγεί σε όλη τη διαδικασία με το **GroupDocs.Watermark Java**, από τη ρύθμιση της βιβλιοθήκης μέχρι την αποθήκευση του εγγράφου με υδατογράφημα.

## Γρήγορες Απαντήσεις
- **Μπορεί το GroupDocs.Watermark να ανοίξει κρυπτογραφημένα αρχεία Word;** Ναι, απλώς παρέχετε τον κωδικό μέσω `WordProcessingLoadOptions`.
- **Χρειάζομαι άδεια για ανάπτυξη;** Μια άδεια δοκιμής λειτουργεί για αξιολόγηση· απαιτείται πλήρης άδεια για παραγωγή.
- **Ποιες συντεταγμένες Maven απαιτούνται;** `com.groupdocs:groupdocs-watermark:24.11` (ή νεότερη).
- **Είναι δυνατόν να επεξεργαστείτε μαζικά πολλαπλά προστατευμένα έγγραφα;** Απόλυτα – δημιουργήστε ένα `Watermarker` για κάθε αρχείο μέσα σε βρόχο.
- **Ποιες εκδόσεις Java υποστηρίζονται;** Java 8 και άνω.

## Τι σημαίνει “Φόρτωση Word με προστασία κωδικού”;
Η φόρτωση ενός εγγράφου Word με προστασία κωδικού σημαίνει το άνοιγμα ενός αρχείου `.docx` που έχει κρυπτογραφηθεί με κωδικό, η αποκρυπτογράφησή του στη μνήμη και, στη συνέχεια, η εκτέλεση λειτουργιών όπως η προσθήκη υδατογραφημάτων. Χωρίς τον σωστό κωδικό, το αρχείο παραμένει μη προσβάσιμο.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark Java;
**GroupDocs.Watermark Java** προσφέρει ένα απλό API για τη διαχείριση μιας ευρείας γκάμας μορφών εγγράφων, συμπεριλαμβανομένων των κρυπτογραφημένων αρχείων Word. Απομακρύνει τις λεπτομέρειες χαμηλού επιπέδου, σας επιτρέπει να προσθέτετε κείμενο ή εικόνα ως υδατογραφήματα με λίγες μόνο γραμμές κώδικα και εξασφαλίζει υψηλή απόδοση ακόμη και με μεγάλα έγγραφα.

## Προαπαιτούμενα
- Java 8+ (IntelliJ IDEA, Eclipse ή οποιοδήποτε IDE προτιμάτε)
- Maven εγκατεστημένο για διαχείριση εξαρτήσεων
- Πρόσβαση σε άδεια **GroupDocs.Watermark Java** (δοκιμαστική ή επί πληρωμή)
- Ένα έγγραφο Word με προστασία κωδικού για δοκιμή

## Ρύθμιση του GroupDocs.Watermark για Java

### Ρύθμιση Maven
Προσθέστε το αποθετήριο και την εξάρτηση στο αρχείο `pom.xml` σας:

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

### Άμεση Λήψη
Αν προτιμάτε χειροκίνητη εγκατάσταση, κατεβάστε το πιο πρόσφατο JAR από την επίσημη πηγή: [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Βήματα Απόκτησης Άδειας
1. **Δωρεάν Δοκιμή** – Λάβετε μια προσωρινή άδεια για να εξερευνήσετε όλες τις δυνατότητες.  
2. **Αγορά** – Αποκτήστε πλήρη άδεια για απεριόριστη χρήση σε παραγωγή.

## Πώς να φορτώσετε έγγραφα Word με προστασία κωδικού

### Βήμα 1: Εισαγωγή Απαιτούμενων Πακέτων
```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.WordProcessingLoadOptions;
```

### Βήμα 2: Ρύθμιση Επιλογών Φόρτωσης με Κωδικό
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/protected-document.docx"; // Replace with your document path.
WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
loadOptions.setPassword("P@$$w0rd"); // Set the correct password here.
```
*Η κλήση `setPassword` ενημερώνει το GroupDocs.Watermark πώς να αποκρυπτογραφήσει το αρχείο ώστε να μπορείτε να το επεξεργαστείτε.*

### Βήμα 3: Αρχικοποίηση Watermarker
```java
Watermarker watermarker = new Watermarker(filePath, loadOptions);
```
*Η δημιουργία μιας παρουσίας `Watermarker` σας δίνει πλήρη έλεγχο στο περιεχόμενο του εγγράφου και στα υδατογραφήματα.*

### Βήμα 4: Προσθήκη Κειμενικού Υδατογραφήματος
```java
import com.groupdocs.watermark.watermarks.Font;
import com.groupdocs.watermark.watermarks.TextWatermark;

TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 12));
watermarker.add(watermark);
```
*Εδώ δημιουργούμε ένα απλό κειμενικό υδατογράφημα. Μπορείτε να προσαρμόσετε τη γραμματοσειρά, το μέγεθος, το χρώμα, την περιστροφή και τη θέση.*

### Βήμα 5: Αποθήκευση και Κλείσιμο
```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/protected-document.docx";
watermarker.save(outputFilePath);
watermarker.close();
```
*Η αποθήκευση γράφει το νέο υδατογράφημα σε ένα νέο αρχείο, και το κλείσιμο απελευθερώνει όλους τους εγγενείς πόρους.*

## Συνηθισμένα Προβλήματα και Λύσεις
- **Λάθος κωδικός** – Επαληθεύστε τον κωδικό με τον κάτοχο του εγγράφου· ένας μη ταιριαστός κωδικός προκαλεί `WrongPasswordException`.
- **Προβλήματα διαδρομής αρχείου** – Χρησιμοποιήστε απόλυτες διαδρομές ή βεβαιωθείτε ότι ο τρέχων φάκελος δείχνει στο σωστό φάκελο.
- **Απουσία εξαρτήσεων Maven** – Ελέγξτε ξανά τις ενότητες `<repositories>` και `<dependencies>`· εκτελέστε `mvn clean install` για να ανανεώσετε την τοπική κρυφή μνήμη.

## Πρακτικές Εφαρμογές
1. **Νομικά γραφεία** – Προσθέστε εμπιστευτικά υδατογραφήματα σε φακέλους υποθέσεων πριν τα μοιραστείτε με πελάτες.  
2. **Εκπαιδευτικά ιδρύματα** – Προστατέψτε τις σημειώσεις διαλέξεων προσθέτοντας υδατογραφήματα, ενώ επιτρέπετε στους φοιτητές να βλέπουν το περιεχόμενο.  
3. **Επιχειρήσεις** – Ασφαλίστε εσωτερικές αναφορές με εταιρικά υδατογραφήματα branding, ακόμη και όταν τα αρχεία είναι προστατευμένα με κωδικό.

## Συμβουλές Απόδοσης
- **Μειώστε το μέγεθος του εγγράφου** πριν τη φόρτωση για να μειώσετε την κατανάλωση μνήμης.  
- **Επαναχρησιμοποιήστε παρουσίες Watermarker** μόνο όταν επεξεργάζεστε ένα μόνο έγγραφο· δημιουργήστε νέες παρουσίες για κάθε αρχείο σε σενάρια μαζικής επεξεργασίας.  
- **Κλείστε τους πόρους άμεσα** (`watermarker.close()`) για να αποφύγετε διαρροές μνήμης.

## Συχνές Ερωτήσεις

**Ε: Μπορεί το GroupDocs.Watermark να διαχειριστεί άλλες προστατευμένες μορφές (π.χ., PDF);**  
Α: Ναι, η βιβλιοθήκη υποστηρίζει PDF, παρουσιάσεις και λογιστικά φύλλα με προστασία κωδικού, χρησιμοποιώντας τις αντίστοιχες κλάσεις επιλογών φόρτωσης.

**Ε: Τι συμβαίνει αν προσπαθήσω να φορτώσω ένα έγγραφο χωρίς να δώσω κωδικό;**  
Α: Η βιβλιοθήκη ρίχνει `WrongPasswordException`. Πάντα ορίστε τον κωδικό στο `WordProcessingLoadOptions` όταν το αρχείο είναι κρυπτογραφημένο.

**Ε: Είναι δυνατόν να προσθέσω υδατογραφήματα εικόνας αντί για κείμενο;**  
Α: Απόλυτα. Χρησιμοποιήστε την κλάση `ImageWatermark` και καθορίστε τη διαδρομή της εικόνας, τη διαφάνεια και τη θέση.

**Ε: Πώς αφαιρώ ένα υδατογράφημα που προστέθηκε προηγουμένως;**  
Α: Ανακτήστε το αντικείμενο υδατογραφήματος μέσω `watermarker.getWatermarks()` και καλέστε `watermarker.remove(watermark)`.

**Ε: Υποστηρίζει το API έγγραφα πολλαπλών γλωσσών;**  
Α: Ναι, οι χαρακτήρες Unicode υποστηρίζονται πλήρως, επιτρέποντας υδατογραφήματα σε οποιαδήποτε γλώσσα.

## Πόροι
- [Τεκμηρίωση GroupDocs Watermark](https://docs.groupdocs.com/watermark/java/)
- [Αναφορά API](https://reference.groupdocs.com/watermark/java)
- [Λήψη Τελευταίας Έκδοσης](https://releases.groupdocs.com/watermark/java/)
- [Αποθετήριο GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Δωρεάν Φόρουμ Υποστήριξης](https://forum.groupdocs.com/c/watermark/10)
- [Απόκτηση Προσωρινής Άδειας](https://purchase.groupdocs.com/temporary-license/)

---

**Τελευταία Ενημέρωση:** 2025-12-23  
**Δοκιμάστηκε Με:** GroupDocs.Watermark 24.11 for Java  
**Συγγραφέας:** GroupDocs