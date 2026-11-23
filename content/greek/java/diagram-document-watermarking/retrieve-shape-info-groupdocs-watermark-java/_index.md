---
date: '2026-02-13'
description: Μάθετε πώς να εξάγετε σχήματα και να εξάγετε εικόνα από σχήμα με το GroupDocs.Watermark
  για Java, ανακτώντας λεπτομερείς πληροφορίες διαγράμματος αποδοτικά.
keywords:
- extract shape information Java
- GroupDocs.Watermark diagram processing
- Java diagram manipulation
title: Πώς να εξάγετε σχήματα από διαγράμματα χρησιμοποιώντας το GroupDocs.Watermark
  σε Java
type: docs
url: /el/java/diagram-document-watermarking/retrieve-shape-info-groupdocs-watermark-java/
weight: 1
---

# Πώς να Εξάγετε Σχήματα από Διαγράμματα Χρησιμοποιώντας το GroupDocs.Watermark σε Java

Όταν χρειάζεται να **πώς να εξάγετε σχήματα** από ένα διάγραμμα τύπου Visio προγραμματιστικά, η βιβλιοθήκη GroupDocs.Watermark σας προσφέρει έναν καθαρό, Java‑first τρόπο για να αντλήσετε κάθε λεπτομέρεια — διαστάσεις, θέσεις, ενσωματωμένες εικόνες και ακόμη και το κείμενο μέσα σε κάθε σχήμα. Σε αυτό το tutorial θα δείτε ακριβώς **πώς να εξάγετε σχήματα**, γιατί είναι σημαντικό, και κώδικα βήμα‑βήμα που μπορείτε να αντιγράψετε στο έργο σας.

## Γρήγορες Απαντήσεις
- **Ποια βιβλιοθήκη διαχειρίζεται την εξαγωγή σχημάτων;** GroupDocs.Watermark for Java  
- **Ποια έκδοση Java απαιτείται;** JDK 8 ή νεότερη  
- **Μπορώ να λάβω δεδομένα εικόνας από ένα σχήμα;** Ναι — χρησιμοποιήστε `shape.getImage()`  
- **Είναι προσβάσιμο το κείμενο μέσα σε σχήμα;** Απόλυτα, μέσω `shape.getText()`  
- **Χρειάζεται άδεια για παραγωγή;** Απαιτείται έγκυρη άδεια GroupDocs.Watermark  

## Εισαγωγή

Η διαχείριση σύνθετων διαγραμμάτων συχνά απαιτεί πρόσβαση σε λεπτομερείς πληροφορίες για τα στοιχεία τους, όπως σχήματα και εικόνες. Αν έχετε χρειαστεί ποτέ να ανακτήσετε προγραμματιστικά δεδομένα όπως διαστάσεις, θέσεις ή κείμενο που σχετίζονται με σχήματα διαγράμματος χρησιμοποιώντας Java, αυτό το tutorial είναι για εσάς. Εκμεταλλευόμενοι τη δύναμη της βιβλιοθήκης GroupDocs.Watermark, μπορείτε να απλοποιήσετε αυτή τη διαδικασία σε μια εφαρμογή Java. Σε αυτόν τον οδηγό, θα περάσουμε από **πώς να εξάγετε σχήματα** από ένα αρχείο διαγράμματος και επίσης θα δείξουμε πώς να **εξάγετε εικόνα από σχήμα** και **εξάγετε κείμενο από σχήμα**.

## Τι είναι το «πώς να εξάγετε σχήματα»;

Η εξαγωγή σχημάτων σημαίνει ανάγνωση των εσωτερικών αντικειμένων του διαγράμματος (σελίδες, σχήματα, εικόνες, κείμενο) ώστε να μπορείτε να τα αναλύσετε, να τα μετασχηματίσετε ή να τα επαναχρησιμοποιήσετε σε άλλες εφαρμογές — ιδανικό για αυτοματοποίηση, αναφορές ή ενσωμάτωση με εργαλεία CAD.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark για εξαγωγή σχημάτων;

- **Πλήρης υποστήριξη μορφών** – λειτουργεί με VSDX, VDX και πολλούς άλλους τύπους διαγραμμάτων.  
- **Πλούσιο μοντέλο αντικειμένων** – παρέχει άμεση πρόσβαση στη γεωμετρία, τις εικόνες και το κείμενο των σχημάτων.  
- **Χωρίς εξωτερικές εξαρτήσεις** – καθαρά Java, εύκολο στην ενσωμάτωση σε έργα Maven.  

## Προαπαιτούμενα

- **GroupDocs.Watermark for Java** (έκδοση 24.11 ή νεότερη)  
- Java Development Kit (JDK) 8 ή νεότερη  
- Maven για διαχείριση εξαρτήσεων  
- Ένα IDE όπως IntelliJ IDEA ή Eclipse  

## Ρύθμιση του GroupDocs.Watermark για Java

Προσθέστε τη βιβλιοθήκη στο `pom.xml` του Maven:

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

Μπορείτε επίσης να κατεβάσετε τα τελευταία binaries από [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

### Βήματα Απόκτησης Άδειας
- **Δωρεάν Δοκιμή:** Κατεβάστε ένα πακέτο δοκιμής για να αξιολογήσετε το API.  
- **Προσωρινή Άδεια:** Ζητήστε ένα προσωρινό κλειδί για εκτεταμένη δοκιμή.  
- **Αγορά:** Αποκτήστε πλήρη άδεια για χρήση σε παραγωγή.

### Βασική Αρχικοποίηση και Ρύθμιση

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.contents.DiagramContent;
import com.groupdocs.watermark.options.DiagramLoadOptions;

DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

## Πώς να Εξάγετε Σχήματα – Οδηγός Υλοποίησης

### Φόρτωση και Ανάκτηση Περιεχομένου

```java
// Create load options if necessary
DiagramLoadOptions diagramLoadOptions = new DiagramLoadOptions();
// Initialize watermarker with your document path
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vsdx", diagramLoadOptions);
```

```java
// Retrieve content of the diagram file as a DiagramContent object
DiagramContent content = watermarker.getContent(DiagramContent.class);
```

### Επανάληψη μέσω Σχημάτων

```java
for (DiagramPage page : content.getPages()) {
    // Process each shape in the current page
}
```

```java
for (DiagramShape shape : page.getShapes()) {
    if (shape.getImage() != null) {
        // Access and print image-related properties
        System.out.println("Image Width: " + shape.getImage().getWidth());
        System.out.println("Image Height: " + shape.getImage().getHeight());
        System.out.println("Image Size: " + shape.getImage().getData().length);
    }
    
    // Print other shape attributes
    System.out.println("Shape Name: " + shape.getName());
    System.out.println("X Position: " + shape.getX());
    System.out.println("Y Position: " + shape.getY());
    System.out.println("Width: " + shape.getWidth());
    System.out.println("Height: " + shape.getHeight());
    System.out.println("Rotation Angle: " + shape.getRotationAngle());
    System.out.println("Text: " + (shape.getText() != null ? shape.getText() : "No text"));
    System.out.println("Shape ID: " + shape.getId());
}
```

### Πώς να εξάγετε εικόνα από σχήμα

Η κλήση `shape.getImage()` επιστρέφει ένα αντικείμενο που περιέχει το ακατέργαστο bitmap, τις διαστάσεις του και τον πίνακα byte. Χρησιμοποιήστε τις ιδιότητες που φαίνονται παραπάνω για να αποθηκεύσετε την εικόνα στο δίσκο ή να τη δώσετε σε άλλη διαδικασία επεξεργασίας.

### Πώς να εξάγετε κείμενο από σχήμα

Η μέθοδος `shape.getText()` επιστρέφει το απλό κείμενο μέσα στο σχήμα. Αν το σχήμα δεν περιέχει κείμενο, η μέθοδος επιστρέφει `null`. Ο δείγματος βρόχος ήδη εκτυπώνει το κείμενο, και μπορείτε να το επεξεργαστείτε περαιτέρω — για παράδειγμα, δημιουργώντας ένα ευρετήριο όλων των ετικετών σχημάτων.

## Συμβουλές Επίλυσης Προβλημάτων
- Επαληθεύστε τη διαδρομή του αρχείου και τα δικαιώματα ανάγνωσης.  
- Βεβαιωθείτε ότι χρησιμοποιείτε υποστηριζόμενη μορφή διαγράμματος (VSDX, VDX κ.λπ.).  
- Αν ένα σχήμα εμφανίζεται χωρίς τα αναμενόμενα δεδομένα, ελέγξτε τις σημειώσεις έκδοσης της βιβλιοθήκης για ιδιαιτερότητες μορφής.

## Πρακτικές Εφαρμογές

1. **Ανάλυση Διαγράμματος:** Αυτόματος έλεγχος διαγραμμάτων για συμμόρφωση ελέγχοντας μεγέθη σχημάτων ή ελλιπείς ετικέτες.  
2. **Οπτικοποίηση Δεδομένων:** Εισαγωγή εξαγόμενων διαστάσεων σε πίνακα αναφορών για οπτικοποίηση πυκνότητας διάταξης.  
3. **Ενσωμάτωση CAD:** Συνδυασμός δεδομένων σχημάτων με API CAD για συγχρονισμό προδιαγραφών σχεδίασης μεταξύ εργαλείων.  

## Σκέψεις για την Απόδοση

- **Κλείσιμο πόρων:** Καλέστε `watermarker.close()` όταν τελειώσετε για να ελευθερώσετε εγγενείς πόρους.  
- **Διαχείριση μνήμης:** Μεγάλα διαγράμματα μπορούν να καταναλώσουν σημαντικό heap· παρακολουθήστε τη μνήμη και αυξήστε το `-Xmx` αν χρειάζεται.  
- **Επεξεργασία παρτίδων:** Επεξεργαστείτε αρχεία σε παρτίδες και επαναχρησιμοποιήστε ένα ενιαίο αντικείμενο `Watermarker` όταν είναι δυνατόν.

## Συμπέρασμα

Ακολουθώντας αυτόν τον οδηγό, τώρα γνωρίζετε **πώς να εξάγετε σχήματα**, πώς να **εξάγετε εικόνα από σχήμα**, και πώς να **εξάγετε κείμενο από σχήμα** χρησιμοποιώντας το GroupDocs.Watermark για Java. Αυτές οι τεχνικές ανοίγουν το δρόμο για αυτοματοποιημένη ανάλυση διαγραμμάτων, αναφορές και ενσωμάτωση με άλλα συστήματα μηχανικής. Στο επόμενο βήμα, εξερευνήστε το πλήρες API ελέγχοντας την [τεκμηρίωση](https://docs.groupdocs.com/watermark/java/) και δοκιμάστε να συνδυάσετε την εξαγωγή σχημάτων με προσαρμοσμένη επιχειρηματική λογική.

## Ενότητα Συχνών Ερωτήσεων

1. **Τι είναι το GroupDocs.Watermark;**  
   - Μια ολοκληρωμένη βιβλιοθήκη Java σχεδιασμένη για υδατογράφημα και εξαγωγή πληροφοριών από διάφορες μορφές εγγράφων, συμπεριλαμβανομένων των διαγραμμάτων.  

2. **Μπορώ να χρησιμοποιήσω αυτή τη βιβλιοθήκη για επεξεργασία όλων των τύπων αρχείων διαγράμματος;**  
   - Ναι, αλλά βεβαιωθείτε ότι η μορφή αρχείου υποστηρίζεται ελέγχοντας το [API Reference](https://reference.groupdocs.com/watermark/java/).  

3. **Πώς εξάγω διαστάσεις και θέσεις σχημάτων από ένα διάγραμμα χρησιμοποιώντας Java και GroupDocs.Watermark;**  
   - Φορτώστε το διάγραμμα, αποκτήστε πρόσβαση στο `DiagramContent`, στη συνέχεια επαναλάβετε τα σχήματα για να λάβετε ιδιότητες όπως πλάτος, ύψος, X και Y.  

4. **Μπορεί το GroupDocs.Watermark να εξάγει εικόνες ενσωματωμένες σε σχήματα διαγράμματος με Java;**  
   - Ναι, παρέχει μεθόδους για πρόσβαση στα δεδομένα εικόνας εντός σχημάτων, συμπεριλαμβανομένου του μεγέθους και των εικονοστοιχείων, χρήσιμα για ανάλυση ή τροποποίηση.  

5. **Ποια είναι τα προαπαιτούμενα για την εξαγωγή πληροφοριών σχημάτων διαγράμματος σε Java;**  
   - Java JDK 8+, ρύθμιση Maven, βιβλιοθήκη GroupDocs.Watermark (24.11+), και βασικές γνώσεις Java είναι απαραίτητα για την υλοποίηση.  

---

**Τελευταία ενημέρωση:** 2026-02-13  
**Δοκιμή με:** GroupDocs.Watermark 24.11 for Java  
**Συγγραφέας:** GroupDocs