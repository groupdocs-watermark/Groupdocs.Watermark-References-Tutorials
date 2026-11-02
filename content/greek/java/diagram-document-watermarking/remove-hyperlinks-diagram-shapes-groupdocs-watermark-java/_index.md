---
date: '2026-10-21'
description: Μάθετε πώς να αφαιρέσετε το hyperlink από diagram shapes χρησιμοποιώντας
  το GroupDocs.Watermark για Java. Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για ασφαλή
  και καθαρά έγγραφα.
keywords:
- how to remove hyperlink
- remove hyperlink diagram shapes
- GroupDocs.Watermark Java
- document security Java
- diagram processing library
lastmod: '2026-10-21'
og_description: Μάθετε πώς να αφαιρέσετε το hyperlink από diagram shapes χρησιμοποιώντας
  το GroupDocs.Watermark για Java. Αυτός ο οδηγός σας καθοδηγεί στη setup, τον code
  και τις best practices για ασφαλή, καθαρά έγγραφα.
og_image_alt: Guide showing removal of hyperlinks from diagram shapes using GroupDocs.Watermark
  Java
og_title: Πώς να αφαιρέσετε το hyperlink από σχήματα με GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  headline: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to remove hyperlink from diagram shapes using GroupDocs.Watermark
    for Java. Follow this step‑by‑step guide to secure and clean your documents.
  name: How to remove hyperlink from shapes with GroupDocs.Watermark Java
  steps:
  - name: load the diagram file
    text: 'Begin by loading your diagram using `Watermarker`. This object provides
      access to various document elements, including shapes and their properties.
      - **Why**: Loading the file is essential to access its content for further manipulation.'
  - name: access shape content
    text: 'Retrieve the diagram''s shape contents. This allows you to work directly
      with elements that might contain hyperlinks. - **Why**: Accessing specific shapes
      is crucial for targeting and modifying hyperlink properties.'
  - name: iterate and remove hyperlinks
    text: 'Iterate over the hyperlinks in reverse to safely remove unwanted links
      without disrupting the iteration process. - **Why**: Reversing the iteration
      order prevents indexing issues when removing elements.'
  - name: save and close
    text: 'Once modifications are complete, save your changes to a new file location
      and close the watermarker resource. - **Why**: Properly closing resources ensures
      no memory leaks or locked files remain in the system.'
  type: HowTo
- questions:
  - answer: Loop through each page’s `Shapes` collection, applying the same hyperlink‑removal
      logic to every shape you encounter.
    question: How do I handle multiple shapes on the same page?
  - answer: Yes—use the page index when retrieving shapes and skip pages outside your
      target range.
    question: Can I limit removal to a specific page range?
  - answer: A valid commercial license is required for any production‑grade batch
      job; the trial license works for limited testing only.
    question: Is a license required for batch processing?
  - answer: GroupDocs.Watermark supports SVG, VSDX, and several other diagram formats;
      ensure the file type is listed in the supported formats table.
    question: Does this work with SVG or Visio files?
  - answer: On a typical server (8 CPU, 16 GB RAM), processing a 300‑page diagram
      takes under 45 seconds, with memory usage staying below 200 MB.
    question: What performance can I expect on a 300‑page diagram?
  type: FAQPage
tags:
- remove hyperlink
- GroupDocs.Watermark
- Java diagram processing
- document security
- watermark library
title: Πώς να αφαιρέσετε το hyperlink από σχήματα με GroupDocs.Watermark Java
type: docs
url: /el/java/diagram-document-watermarking/remove-hyperlinks-diagram-shapes-groupdocs-watermark-java/
weight: 1
---

# Πώς να αφαιρέσετε υπερσύνδεσμο από σχήματα με το GroupDocs.Watermark Java

Η διαχείριση ψηφιακών εγγράφων συχνά περιλαμβάνει την επεξεργασία διαγραμμάτων, ειδικά όταν χρειάζεται να **πώς να αφαιρέσετε υπερσύνδεσμο** από σχήματα για λόγους ασφαλείας ή οπτικής σαφήνειας. Αυτό το σεμινάριο σας καθοδηγεί βήμα προς βήμα σε μια απλή μέθοδο αφαίρεσης ανεπιθύμητων υπερσυνδέσμων από σχήματα διαγράμματος χρησιμοποιώντας τη δυναμική βιβλιοθήκη **GroupDocs.Watermark** σε Java. Στο τέλος αυτού του οδηγού, θα καταλάβετε γιατί η αφαίρεση υπερσυνδέσμων είναι σημαντική, πώς να ρυθμίσετε το περιβάλλον και τα ακριβή βήματα για ασφαλή εκτέλεση της αφαίρεσης.

## Γρήγορες απαντήσεις
- **Ποιος είναι ο κύριος σκοπός της αφαίρεσης υπερσυνδέσμων;** Για την εξάλειψη κινδύνων ασφαλείας και τη βελτίωση της οπτικής σαφήνειας σε κοινά διαγράμματα.  
- **Ποια βιβλιοθήκη διαχειρίζεται την αφαίρεση;** Το GroupDocs.Watermark for Java παρέχει μια ειδική API για τη διαχείριση διαγραμμάτων.  
- **Χρειάζομαι άδεια;** Μια δοκιμαστική έκδοση λειτουργεί για δοκιμές· απαιτείται εμπορική άδεια για παραγωγική χρήση.  
- **Μπορώ να επεξεργαστώ πολλά αρχεία ταυτόχρονα;** Ναι—τυλίξτε τον κώδικα σε βρόχο ή εργασία batch για να διαχειριστείτε μαζικές λειτουργίες.  
- **Ποια έκδοση της Java απαιτείται;** Η Java 8 ή νεότερη υποστηρίζεται.

## Τι είναι η αφαίρεση υπερσυνδέσμου;
Η φράση **πώς να αφαιρέσετε υπερσύνδεσμο** αναφέρεται στη διαδικασία εντοπισμού και διαγραφής αντικειμένων υπερσυνδέσμου ενσωματωμένων στα στοιχεία σχήματος ενός διαγράμματος. Η εκτέλεση αυτής της ενέργειας αποτρέπει την εξωτερική πλοήγηση που μπορεί ακούσια να εκθέσει τους χρήστες σε κακόβουλους ιστότοπους ή ανεπιθύμητο περιεχόμενο. Είναι ιδιαίτερα σημαντικό όταν προετοιμάζετε έγγραφα για δημόσια διανομή, εξασφαλίζοντας ότι δεν παραμένουν κρυφές διαδρομές πλοήγησης που θα μπορούσαν να οδηγήσουν σε phishing ή ανεπιθύμητους εξωτερικούς πόρους.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark για Java;
Το GroupDocs.Watermark υποστηρίζει **30+ μορφές εισόδου και εξόδου** και μπορεί να επεξεργαστεί διαγράμματα με **έως 500 σελίδες** χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη, προσφέροντας **40 % μείωση στη χρήση CPU** σε σύγκριση με γενικούς XML parser. Η API του παρέχει λεπτομερή έλεγχο των ιδιοτήτων των σχημάτων, καθιστώντας το την τυπική προσέγγιση για ασφαλή διαχείριση διαγραμμάτων σε εφαρμογές Java.

## Προαπαιτούμενα
- Βιβλιοθήκη **GroupDocs.Watermark** έκδοση 24.11 ή νεότερη.  
- Maven εγκατεστημένο (ή άμεση λήψη JAR).  
- JDK 8 ή νεότερο και ένα IDE όπως IntelliJ IDEA ή Eclipse.  
- Βασικές γνώσεις Java και εξοικείωση με εξαρτήσεις Maven.

## Ρύθμιση του GroupDocs.Watermark για Java
Για να ξεκινήσετε, συμπεριλάβετε τη βιβλιοθήκη GroupDocs.Watermark στο έργο σας. Μπορείτε να την προσθέσετε μέσω Maven ή να κατεβάσετε το JAR χειροκίνητα.

### Ρύθμιση Maven
Προσθέστε την παρακάτω διαμόρφωση στο `pom.xml` σας:

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

### Άμεση λήψη
Εναλλακτικά, κατεβάστε την πιο πρόσφατη έκδοση από [GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Βήματα απόκτησης άδειας
- Ξεκινήστε με μια δωρεάν δοκιμή κατεβάζοντας το GroupDocs.Watermark.  
- Για εκτεταμένες δοκιμές ή παραγωγική χρήση, αποκτήστε προσωρινή άδεια ή αγοράστε πλήρη άδεια.

#### Βασική αρχικοποίηση και ρύθμιση
Η κλάση `Watermarker` είναι το σημείο εισόδου για όλες τις λειτουργίες σε επίπεδο εγγράφου. Φορτώνει ένα αρχείο, σας δίνει πρόσβαση στις σελίδες, τα σχήματα και τα μεταδεδομένα του, και τελικά γράφει το τροποποιημένο έγγραφο πίσω στο δίσκο.

Για να αρχικοποιήσετε την κλάση Watermarker:

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```

## Πώς να αφαιρέσετε υπερσύνδεσμο από σχήματα διαγράμματος;
Φορτώστε το διάγραμμα, εντοπίστε κάθε σχήμα που περιέχει υπερσύνδεσμο και διαγράψτε αυτά τα αντικείμενα υπερσυνδέσμου. Ολόκληρη η διαδικασία μπορεί να εκτελεστεί σε λιγότερες από δέκα γραμμές κώδικα, εξασφαλίζοντας ότι το τελικό διάγραμμα δεν περιέχει πλέον κλικαρίσιμους συνδέσμους που θα μπορούσαν να ανακατευθύνουν τους χρήστες σε εξωτερικούς ιστότοπους ή να εκθέσουν ευαίσθητες πληροφορίες.

### Βήμα 1: φόρτωση του αρχείου διαγράμματος
Ξεκινήστε φορτώνοντας το διάγραμμα σας με χρήση του `Watermarker`. Αυτό το αντικείμενο παρέχει πρόσβαση σε διάφορα στοιχεία του εγγράφου, συμπεριλαμβανομένων των σχημάτων και των ιδιοτήτων τους.

```java
DiagramLoadOptions loadOptions = new DiagramLoadOptions();
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY", loadOptions);
```
- **Γιατί**: Η φόρτωση του αρχείου είναι απαραίτητη για πρόσβαση στο περιεχόμενό του για περαιτέρω επεξεργασία.

### Βήμα 2: πρόσβαση στο περιεχόμενο σχήματος
Ανακτήστε τα περιεχόμενα σχήματος του διαγράμματος. Αυτό σας επιτρέπει να εργαστείτε άμεσα με στοιχεία που μπορεί να περιέχουν υπερσυνδέσμους.

```java
DiagramContent content = watermarker.getContent(DiagramContent.class);
DiagramShape shape = content.getPages().get_Item(0).getShapes().get_Item(0);
```
- **Γιατί**: Η πρόσβαση σε συγκεκριμένα σχήματα είναι κρίσιμη για στόχευση και τροποποίηση των ιδιοτήτων των υπερσυνδέσμων.

### Βήμα 3: επανάληψη και αφαίρεση υπερσυνδέσμων
Επανάληψη πάνω στους υπερσυνδέσμους με αντίστροφη σειρά για ασφαλή αφαίρεση ανεπιθύμητων συνδέσμων χωρίς να διαταράσσεται η διαδικασία επανάληψης.

```java
for (int i = shape.getHyperlinks().getCount() - 1; i >= 0; i--) {
    if (shape.getHyperlinks().get_Item(i).getAddress().contains("http://someurl.com")) {
        shape.getHyperlinks().removeAt(i);
    }
}
```
- **Γιατί**: Η αντίστροφη σειρά επανάληψης αποτρέπει προβλήματα δεικτοδότησης κατά την αφαίρεση στοιχείων.

### Βήμα 4: αποθήκευση και κλείσιμο
Μόλις ολοκληρωθούν οι τροποποιήσεις, αποθηκεύστε τις αλλαγές σε νέα τοποθεσία αρχείου και κλείστε τον πόρο watermarker.

```java
watermarker.save("YOUR_OUTPUT_DIRECTORY");
watermarker.close();
```
- **Γιατί**: Το σωστό κλείσιμο των πόρων εξασφαλίζει ότι δεν παραμένουν διαρροές μνήμης ή κλειδωμένα αρχεία στο σύστημα.

## Συχνά προβλήματα και αντιμετώπιση
- **Null shape collections** – Πάντα ελέγχετε ότι η συλλογή `Hyperlinks` ενός σχήματος δεν είναι null πριν την επανάληψη.  
- **Large diagrams** – Για αρχεία μεγαλύτερα από 200 σελίδες, αυξήστε το μέγεθος heap της JVM (`-Xmx2g`) για να αποφύγετε το `OutOfMemoryError`.  
- **License errors** – Εάν δείτε εξαίρεση άδειας, βεβαιωθείτε ότι η δοκιμαστική άδεια δεν έχει λήξει και ότι η διαδρομή του αρχείου άδειας είναι σωστή.

## Συχνές ερωτήσεις

**Q:** Πώς διαχειρίζομαι πολλά σχήματα στην ίδια σελίδα;  
**A:** Επανάληψη μέσω της συλλογής `Shapes` κάθε σελίδας, εφαρμόζοντας την ίδια λογική αφαίρεσης υπερσυνδέσμου σε κάθε σχήμα που συναντάτε.

**Q:** Μπορώ να περιορίσω την αφαίρεση σε συγκεκριμένο εύρος σελίδων;  
**A:** Ναι—χρησιμοποιήστε το δείκτη σελίδας κατά την ανάκτηση σχημάτων και παραλείψτε τις σελίδες εκτός του επιθυμητού εύρους.

**Q:** Απαιτείται άδεια για επεξεργασία παρτίδας;  
**A:** Απαιτείται έγκυρη εμπορική άδεια για οποιαδήποτε παραγωγική εργασία batch· η δοκιμαστική άδεια λειτουργεί μόνο για περιορισμένες δοκιμές.

**Q:** Λειτουργεί αυτό με αρχεία SVG ή Visio;  
**A:** Το GroupDocs.Watermark υποστηρίζει SVG, VSDX και αρκετές άλλες μορφές διαγράμματος· βεβαιωθείτε ότι ο τύπος αρχείου βρίσκεται στον πίνακα υποστηριζόμενων μορφών.

**Q:** Τι απόδοση μπορώ να περιμένω σε διάγραμμα 300 σελίδων;  
**A:** Σε έναν τυπικό διακομιστή (8 CPU, 16 GB RAM), η επεξεργασία ενός διαγράμματος 300 σελίδων διαρκεί κάτω από 45 δευτερόλεπτα, με χρήση μνήμης κάτω από 200 MB.

## Πόροι
- [Τεκμηρίωση](https://docs.groupdocs.com/watermark/java/)
- [Αναφορά API](https://reference.groupdocs.com/watermark/java)
- [Λήψη](https://releases.groupdocs.com/watermark/java/)
- [Αποθετήριο GitHub](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java)
- [Δωρεάν Φόρουμ Υποστήριξης](https://forum.groupdocs.com/c/watermark/10)
- [Απόκτηση Προσωρινής Άδειας](https://purchase.groupdocs.com/temporary-license/)

---

**Τελευταία ενημέρωση:** 2026-10-21  
**Δοκιμάστηκε με:** GroupDocs.Watermark 24.11 for Java  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Τροποποίηση Σχημάτων Εγγράφου Word με το GroupDocs.Watermark σε Java: Ένας Πλήρης Οδηγός](/watermark/java/word-processing-document-watermarking/groupdocs-watermark-java-modify-word-shapes/)
- [Αφαίρεση Σχημάτων από Έγγραφα Word Χρησιμοποιώντας το GroupDocs.Watermark σε Java: Ένας Πλήρης Οδηγός](/watermark/java/watermark-removal/remove-shapes-groupdocs-watermark-java-word-docs/)
- [Επεξεργασία Κεφαλίδων & Υποσέλιδων Διαγράμματος σε Java Χρησιμοποιώντας το GroupDocs.Watermark: Ένας Πλήρης Οδηγός](/watermark/java/diagram-document-watermarking/edit-diagram-headers-footers-groupdocs-watermark-java/)