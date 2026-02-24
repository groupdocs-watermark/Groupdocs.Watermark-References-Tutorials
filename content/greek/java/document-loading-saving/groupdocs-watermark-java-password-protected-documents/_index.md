---
date: '2026-02-24'
description: Μάθετε πώς να φορτώνετε έγγραφα προστατευμένα με κωδικό πρόσβασης χρησιμοποιώντας
  το GroupDocs.Watermark Maven για Java. Αυτός ο οδηγός παρέχει βήμα-βήμα οδηγίες,
  πρακτικά παραδείγματα και συμβουλές αντιμετώπισης προβλημάτων.
keywords:
- load password-protected documents in Java
- GroupDocs Watermark Java
- manage watermarks encrypted documents
title: Πώς να φορτώσετε έγγραφα με προστασία κωδικού πρόσβασης με το GroupDocs.Watermark
  Maven σε Java
type: docs
url: /el/java/document-loading-saving/groupdocs-watermark-java-password-protected-documents/
weight: 1
---

# Πώς να φορτώσετε έγγραφα με κωδικό πρόσβασης χρησιμοποιώντας το GroupDocs.Watermark Maven σε Java

Σε αυτό το tutorial θα ανακαλύψετε **πώς να φορτώνετε έγγραφα με κωδικό πρόσβασης** χρησιμοποιώντας την ενσωμάτωση **GroupDocs.Watermark Maven** για Java. Θα περάσουμε από κάθε βήμα—από την προσθήκη της εξάρτησης Maven μέχρι την αποθήκευση του επεξεργασμένου αρχείου—ώστε να μπορείτε να προστατεύετε εμπιστευτικό περιεχόμενο ενώ ταυτόχρονα εφαρμόζετε ή αφαιρείτε υδατογραφήματα.

## Γρήγορες Απαντήσεις
- **Ποια βιβλιοθήκη προσθέτει υποστήριξη Maven;** Πακέτο GroupDocs.Watermark Maven.  
- **Μπορώ να ανοίξω ένα έγγραφο με κωδικό πρόσβασης;** Ναι, ορίστε τον κωδικό μέσω του `LoadOptions`.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για αξιολόγηση· απαιτείται πλήρης ή προσωρινή άδεια για παραγωγή.  
- **Ποιοι τύποι αρχείων υποστηρίζονται;** DOCX, PDF, PPTX και πολλά άλλα.  
- **Είναι ο κώδικας thread‑safe;** Η παρουσία `Watermarker` δεν μοιράζεται μεταξύ νημάτων· δημιουργήστε μια νέα παρουσία ανά έγγραφο.

## Τι είναι το GroupDocs.Watermark Maven;
Το GroupDocs.Watermark Maven παρέχει έναν βολικό τρόπο να συμπεριλάβετε το Watermark SDK στα Java projects σας μέσω του τυπικού συστήματος κατασκευής Maven. Με την δήλωση του αποθετηρίου και της εξάρτησης στο `pom.xml`, το Maven αυτόματα λύνει όλες τις απαιτούμενες JAR, διατηρώντας το project σας οργανωμένο και ενημερωμένο.

## Γιατί να φορτώσετε ένα έγγραφο με κωδικό πρόσβασης;
Οι επιχειρήσεις συχνά αποθηκεύουν ευαίσθητες συμβάσεις, νομικές αναφορές ή οικονομικές εκθέσεις σε κρυπτογραφημένα αρχεία. Η φόρτωση αυτών των αρχείων με τον σωστό κωδικό πρόσβασης σας επιτρέπει να:
1. **Εφαρμόσετε εταιρική επωνυμία** χωρίς να εκθέσετε το αρχικό περιεχόμενο.  
2. **Αφαιρέσετε παλαιά υδατογραφήματα** πριν την αρχειοθέτηση.  
3. **Αυτοματοποιήσετε ελέγχους συμμόρφωσης** σε ασφαλές περιβάλλον.

## Προαπαιτούμενα
- Java Development Kit (JDK) 8 ή νεότερο.  
- Maven 3.5 ή νεότερο (ή η δυνατότητα προσθήκης JAR χειροκίνητα).  
- Βασικές γνώσεις Java και εξοικείωση με Maven.  

## Ρύθμιση του GroupDocs.Watermark Maven

### Maven Repository and Dependency
Προσθέστε το αποθετήριο GroupDocs και την εξάρτηση Watermark στο `pom.xml`:

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

### Direct Download (if you prefer not to use Maven)
Μπορείτε επίσης να κατεβάσετε τα JAR απευθείας από τη σελίδα των επίσημων εκδόσεων: [GroupDocs.Watermark για εκδόσεις Java](https://releases.groupdocs.com/watermark/java/).

### Licensing
Ξεκινήστε με μια δωρεάν δοκιμή για να εξερευνήσετε το API. Για παραγωγικά φορτία εργασίας, ζητήστε προσωρινή ή πλήρη άδεια εδώ: [σελίδα αγοράς](https://purchase.groupdocs.com/temporary-license/).

## Οδηγός Υλοποίησης: Φόρτωση Εγγράφου με Κωδικό Πρόσβασης

Παρακάτω υπάρχει ένα σύντομο, βήμα‑βήμα παράδειγμα που δείχνει πώς να ανοίξετε ένα κρυπτογραφημένο αρχείο DOCX, να εργαστείτε με υδατογραφήματα και να αποθηκεύσετε το αποτέλεσμα.

### Step 1: Configure Load Options with the Document Password
Δημιουργήστε μια παρουσία `LoadOptions` και παρέχετε τον κωδικό που προστατεύει το αρχείο σας.

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.LoadOptions;

public class LoadPasswordProtectedDocument {
    public static void run() {
        // Create LoadOptions and set the password for the protected document
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setPassword("P@$$w0rd");
```

### Step 2: Define the Path to Your Encrypted File
Καθορίστε πού βρίσκεται το πηγαίο έγγραφο στο δίσκο.

```java
        // Define file path for your document
        String filePath = "YOUR_DOCUMENT_DIRECTORY/protected-document.docx";
```

### Step 3: Instantiate the Watermarker with Load Options
Περάστε τόσο τη διαδρομή του αρχείου όσο και τις ρυθμισμένες `LoadOptions` στον κατασκευαστή `Watermarker`.

```java
        // Create Watermarker instance with the document path and LoadOptions
        Watermarker watermarker = new Watermarker(filePath, loadOptions);
```

### Step 4: (Optional) Manage Watermarks
Σε αυτό το σημείο μπορείτε να προσθέσετε, επεξεργαστείτε ή αφαιρέσετε υδατογραφήματα. Για συντομία θα προχωρήσουμε απευθείας στην αποθήκευση.

### Step 5: Save the Processed Document
Επιλέξτε μια τοποθεσία εξόδου και γράψτε τις αλλαγές.

```java
        // Save changes to a specified output directory
        String outputPath = "YOUR_OUTPUT_DIRECTORY/protected-document-output.docx";
        watermarker.save(outputPath);
```

### Step 6: Release Resources
Πάντα κλείστε το `Watermarker` για να ελευθερώσετε τους εγγενείς πόρους.

```java
        // Close the Watermarker instance to release resources
        watermarker.close();
    }
}
```

## Συχνά Προβλήματα & Λύσεις
| Συμπτωμα | Πιθανή Αιτία | Διόρθωση |
|---------|--------------|-----|
| `Invalid password` exception | Λάθος πληκτρολόγηση κωδικού ή λανθασμένη κωδικοποίηση | Ελέγξτε ξανά τη συμβολοσειρά κωδικού· βεβαιωθείτε ότι ταιριάζει ακριβώς με το case και τους ειδικούς χαρακτήρες του εγγράφου. |
| `File not found` error | Λανθασμένο `filePath` ή έλλειψη δικαιωμάτων ανάγνωσης | Επαληθεύστε την απόλυτη διαδρομή και επιβεβαιώστε ότι η JVM έχει πρόσβαση ανάγνωσης. |
| `OutOfMemoryError` on large files | Φόρτωση τεράστιων εγγράφων χωρίς streaming | Επεξεργαστείτε τα έγγραφα σε μικρότερες παρτίδες ή αυξήστε το heap της JVM (`-Xmx` flag). |

## Πρακτικές Περιπτώσεις Χρήσης
- **Συστήματα Διαχείρισης Εγγράφων:** Ασφαλής επανα-υδατογράφημα συμβάσεων πριν την αρχειοθέτηση.  
- **Νομικές Εταιρείες:** Εφαρμόστε την επωνυμία της εταιρείας σε κρυπτογραφημένα αρχεία υποθέσεων χωρίς να εκθέσετε εμπιστευτικά δεδομένα.  
- **Οικονομική Αναφορά:** Προσθέστε σφραγίδες συμμόρφωσης σε οικονομικές καταστάσεις με κωδικό πρόσβασης.  

## Συμβουλές Απόδοσης
- Επαναχρησιμοποιήστε την ίδια παρουσία `LoadOptions` όταν επεξεργάζεστε πολλά αρχεία με τον ίδιο κωδικό.  
- Κλείστε άμεσα κάθε `Watermarker` για να αποφύγετε διαρροές μνήμης.  
- Για μαζικές λειτουργίες, σκεφτείτε ένα thread pool όπου κάθε νήμα εργάζεται σε ξεχωριστό έγγραφο.

## Συμπέρασμα
Τώρα έχετε ένα πλήρες, έτοιμο για παραγωγή παράδειγμα για τη φόρτωση ενός **εγγράφου με κωδικό πρόσβασης** με το **GroupDocs.Watermark Maven** σε Java. Ενσωματώστε αυτό το απόσπασμα στη μεγαλύτερη ροή εργασίας σας, πειραματιστείτε με λειτουργίες υδατογραφήματος και διατηρήστε τα εμπιστευτικά σας περιουσιακά στοιχεία ασφαλή και με επωνυμία.

## Συχνές Ερωτήσεις

**Ε: Πώς να διαχειριστώ έναν λανθασμένο κωδικό πρόσβασης κατά την εκτέλεση;**  
Α: Τυλίξτε τη δημιουργία του `Watermarker` σε μπλοκ try‑catch για `InvalidPasswordException` και ζητήστε από τον χρήστη να εισάγει ξανά τον κωδικό.

**Ε: Είναι η άδεια υποχρεωτική για εκδόσεις ανάπτυξης;**  
Α: Μια δοκιμαστική άδεια λειτουργεί για ανάπτυξη και δοκιμές, αλλά απαιτείται πλήρης ή προσωρινή άδεια για παραγωγικές εγκαταστάσεις.

**Ε: Ποιοι τύποι εγγράφων μπορώ να φορτώσω με κωδικό πρόσβασης;**  
Α: Το SDK υποστηρίζει DOCX, PDF, PPTX, XLSX και πολλούς άλλους τύπους—οι περισσότεροι από αυτούς μπορούν να ανοιχτούν με κωδικό.

**Ε: Μπορώ να επεξεργαστώ πολλά έγγραφα παράλληλα;**  
Α: Ναι, εφόσον κάθε νήμα δημιουργεί τη δική του παρουσία `Watermarker`; η κλάση δεν είναι thread‑safe.

**Ε: Πού μπορώ να βρω πιο προχωρημένα παραδείγματα υδατογράφησης;**  
Α: Η επίσημη τεκμηρίωση και η αναφορά API περιέχουν λεπτομερείς οδηγούς για προσθήκη κειμένου, εικόνας και σχήματος ως υδατογραφήματα.

---

**Τελευταία ενημέρωση:** 2026-02-24  
**Δοκιμή με:** GroupDocs.Watermark 24.11 for Java  
**Συγγραφέας:** GroupDocs  

**Πόροι**  
- [Τεκμηρίωση](https://docs.groupdocs.com/watermark/java/)  
- [Αναφορά API](https://reference.groupdocs.com/watermark/java)  
- [Λήψη GroupDocs.Watermark](https://releases.groupdocs.com/watermark/java/)  
- [Αποθετήριο GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)  
- [Δωρεάν Φόρουμ Υποστήριξης](https://forum.groupdocs.com/c/watermark/10)  
- [Αίτηση για Προσωρινή Άδεια](https://purchase.groupdocs.com/temporary-license/)