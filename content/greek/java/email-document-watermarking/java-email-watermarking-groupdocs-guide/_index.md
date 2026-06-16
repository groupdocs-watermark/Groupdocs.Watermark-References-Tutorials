---
date: '2026-06-16'
description: Μάθετε πώς να προσθέτετε υδατογράφημα σε έγγραφα email χρησιμοποιώντας
  το GroupDocs.Watermark for Java. Αυτό το step-by-step tutorial καλύπτει τη ρύθμιση,
  την προσθήκη υδατογραφήματος σε email και τις βέλτιστες πρακτικές.
keywords:
- how to watermark email
- add watermark to email
- GroupDocs Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-16'
  description: Learn how to watermark email documents using GroupDocs.Watermark for
    Java. This step‑by‑step tutorial covers setup, adding watermark to email, and
    best practices.
  headline: How to Watermark Email with GroupDocs.Watermark for Java – A Complete
    Guide
  type: TechArticle
- description: Learn how to watermark email documents using GroupDocs.Watermark for
    Java. This step‑by‑step tutorial covers setup, adding watermark to email, and
    best practices.
  name: How to Watermark Email with GroupDocs.Watermark for Java – A Complete Guide
  steps:
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Email Load Options and Watermarker:**'
    text: '**Initialize Email Load Options and Watermarker:**'
  - name: '**Import Required Packages:**'
    text: '**Import Required Packages:**'
  - name: '**Read Image File and Convert to Byte Array:**'
    text: '**Read Image File and Convert to Byte Array:**'
  - name: '**Import Classes for Handling Email Contents:**'
    text: '**Import Classes for Handling Email Contents:**'
  - name: '**Add Embedded Image to the Email:**'
    text: '**Add Embedded Image to the Email:**'
  - name: '**Save and Close Watermarker:**'
    text: '**Save and Close Watermarker:**'
  - name: '**Internal Document Security** – Prevent accidental data leaks by branding
      every internal memo with a confidential watermark.'
    text: '**Internal Document Security** – Prevent accidental data leaks by branding
      every internal memo with a confidential watermark.'
  - name: '**Email Marketing** – Reinforce brand identity by automatically adding
      your logo to every campaign email.'
    text: '**Email Marketing** – Reinforce brand identity by automatically adding
      your logo to every campaign email.'
  - name: '**Legal Correspondence** – Attach a “Confidential – Attorney‑Client Privilege”
      watermark to legal emails to satisfy compliance audits.'
    text: '**Legal Correspondence** – Attach a “Confidential – Attorney‑Client Privilege”
      watermark to legal emails to satisfy compliance audits.'
  type: HowTo
- questions:
  - answer: GroupDocs.Watermark only modifies the HTML body; plain‑text parts remain
      unchanged, which is standard practice for email branding.
    question: Can I watermark both HTML and plain‑text parts of an email?
  - answer: Yes, because the watermark becomes part of the email’s HTML content, it
      is retained in all subsequent forwards.
    question: Does the watermark survive when the email is forwarded?
  - answer: You can save as EML, MSG, or MHT. The API also supports PDF conversion
      if you need a printable version.
    question: What file formats can I export the watermarked email to?
  - answer: A free trial license works for development and testing. Production deployments
      require a purchased license to remove evaluation watermarks.
    question: Is a license required for development environments?
  - answer: Attachments are streamed unchanged; only the email body is processed,
      so attachment size does not affect watermarking performance.
    question: How does GroupDocs.Watermark handle large attachments?
  type: FAQPage
title: Πώς να προσθέσετε υδατογράφημα σε email με το GroupDocs.Watermark for Java
  – Ένας πλήρης οδηγός
type: docs
url: /el/java/email-document-watermarking/java-email-watermarking-groupdocs-guide/
weight: 1
---

# Πώς να προσθέσετε υδατογράφημα σε email με το GroupDocs.Watermark για Java – Ένας πλήρης οδηγός

## Εισαγωγή

Αν χρειάζεται να προστατέψετε την ακεραιότητα των επικοινωνιών σας μέσω email, **how to watermark email** είναι μια κρίσιμη δυνατότητα. Η προσθήκη ενός οπτικού αναγνωριστικού απευθείας μέσα στο email αποτρέπει την μη εξουσιοδοτημένη προώθηση και την παραποίηση, ενώ διατηρεί το αρχικό μήνυμα αναγνώσιμο. Σε αυτό το tutorial θα μάθετε πώς να ενσωματώσετε το GroupDocs.Watermark για Java στην εφαρμογή σας, να φορτώσετε ένα αρχείο email, να ενσωματώσετε μια εικόνα ως υδατογράφημα και να αποθηκεύσετε το υδατογραφημένο μήνυμα — χωρίς να αλλάξετε τη δομή του αρχικού email.

**Τι θα μάθετε:**
- Εγκατάσταση και διαμόρφωση του GroupDocs.Watermark για Java.  
- Φόρτωση ενός εγγράφου email (EML, MSG ή MHT) στο API.  
- Μετατροπή μιας εικόνας σε byte array και ενσωμάτωσή της ως υδατογράφημα.  
- Αποθήκευση του τροποποιημένου email διατηρώντας τα συνημμένα και το περιεχόμενο HTML.  

Στο τέλος, θα μπορείτε να **add watermark to email** αρχεία προγραμματιστικά, καθιστώντας τις εξερχόμενες επικοινωνίες σας ασφαλώς επωνυμοποιημένες.

## Γρήγορες Απαντήσεις
- **Ποια βιβλιοθήκη απαιτείται;** GroupDocs.Watermark for Java (v24.11+).  
- **Ποιοι τύποι email υποστηρίζονται;** EML, MSG, και MHT αρχεία – πάνω από 30 + τύπους συνολικά.  
- **Μπορώ να χρησιμοποιήσω PNG υδατογραφήματα;** Ναι, τα PNG και JPEG υποστηρίζονται πλήρως.  
- **Χρειάζομαι άδεια για ανάπτυξη;** Μια δωρεάν δοκιμή λειτουργεί για δοκιμές· απαιτείται άδεια παραγωγής για εμπορική χρήση.  
- **Πόση επιπλέον μνήμη καταναλώνει η υδ.σφραγίδωση;** Συνήθως κάτω από 15 MB για ένα email 5 MB όταν χρησιμοποιούνται συμπιεσμένες εικόνες.

## Τι είναι η Υδ.σφραγίδωση Email;
Η υδ.σφραγίδωση email είναι η διαδικασία ενσωμάτωσης ενός οπτικού στοιχείου—όπως λογότυπο ή αποποίηση ευθύνης—απευθείας στο σώμα ενός αρχείου email. Το υδατογράφημα γίνεται μέρος του περιεχομένου HTML, διασφαλίζοντας ότι οι παραλήπτες βλέπουν το branding ανεξάρτητα από τον πελάτη email που χρησιμοποιούν.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark για Java;
Το GroupDocs.Watermark υποστηρίζει **50+ input and output formats**, συμπεριλαμβανομένων των EML, MSG και MHT, και μπορεί να επεξεργαστεί email έως **200 MB** χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη. Το API του προσφέρει λειτουργίες thread‑safe, επιτρέποντας την υδ.σφραγίδωση εκατοντάδων email ανά λεπτό σε έναν τυπικό server 4‑πυρήνων.

## Προαπαιτούμενα

- **Java Development Kit (JDK) 8+** εγκατεστημένο και ρυθμισμένο στο IDE σας.  
- **Maven** ή άλλο εργαλείο κατασκευής για διαχείριση εξαρτήσεων.  
- Πρόσβαση σε φάκελο όπου μπορείτε να διαβάσετε τα πηγαία email και να γράψετε τα υδατογραφημένα αποτελέσματα.  
- Βασικές γνώσεις Java (file I/O, streams, και αντικειμενοστραφείς έννοιες).  

## Ρύθμιση του GroupDocs.Watermark για Java

### Χρήση Maven
Add the following dependency to your `pom.xml` file:

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
Alternatively, download the latest JAR from the official release page:  
[GroupDocs.Watermark for Java releases](https://releases.groupdocs.com/watermark/java/).

#### Βήματα Απόκτησης Άδειας
- **Free Trial:** Κατεβάστε μια δοκιμαστική άδεια για να εξερευνήσετε το API.  
- **Temporary License:** Για εκτεταμένη αξιολόγηση, ζητήστε ένα προσωρινό κλειδί μέσω του portal αγοράς: [GroupDocs' purchase page](https://purchase.groupdocs.com/temporary-license).  
- **Full License:** Αγοράστε μια άδεια παραγωγής για απεριόριστη ανάπτυξη.

### Βασική Αρχικοποίηση και Ρύθμιση
`Watermarker` is the main class that manages loading, editing, and saving documents.  
`EmailLoadOptions` configures how an email file is interpreted when loading.  

```java
import com.groupdocs.watermark.Watermarker;

// Initialize GroupDocs.Watermark with your document path
String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
Watermarker watermarker = new Watermarker(emailFilePath);
```

## Οδηγός Υλοποίησης

### Φόρτωση Εγγράφου Email

#### Επισκόπηση
Loading the email is the first step before any watermark can be applied. GroupDocs.Watermark abstracts the file format, letting you work with a unified `Watermarker` object.

#### Άμεση Απάντηση
Create a `Watermarker` instance with `EmailLoadOptions`, point it at your `.eml` or `.msg` file, and the API will parse the HTML body, attachments, and metadata—all in a single call. This operation typically completes in under 200 ms for a 2 MB email.

#### Υλοποίηση Βήμα‑βήμα
1. **Import Necessary Classes:**  
   ```java
   import com.groupdocs.watermark.Watermarker;
   import com.groupdocs.watermark.options.EmailLoadOptions;
   ```  

2. **Initialize Email Load Options and Watermarker:**  
   ```java
   EmailLoadOptions loadOptions = new EmailLoadOptions();
   String emailFilePath = "YOUR_DOCUMENT_DIRECTORY/message.msg";
   Watermarker watermarker = new Watermarker(emailFilePath, loadOptions);
   ```  

#### Ορισμός Άγκυρας
`EmailLoadOptions` is a configuration class that tells GroupDocs.Watermark how to interpret the source email file (e.g., whether to preserve embedded images).  

### Ανάγνωση Αρχείου Εικόνας σε Byte Array

#### Επισκόπηση
To embed a watermark, the image must be supplied as a byte array so the API can insert it into the email’s HTML.

#### Άμεση Απάντηση
Read the image file with a `FileInputStream`, convert the stream to a byte array using `IOUtils.toByteArray`, and keep the array in memory—this enables the watermark to be inserted without writing temporary files to disk.

#### Υλοποίηση Βήμα‑βήμα
1. **Import Required Packages:**  
   ```java
   import java.io.File;
   import java.io.FileInputStream;
   import java.io.InputStream;
   ```  

2. **Read Image File and Convert to Byte Array:**  
   ```java
   File imageFile = new File("YOUR_DOCUMENT_DIRECTORY/sample.jpg");
   byte[] imageBytes = new byte[(int) imageFile.length()];
   InputStream imageInputStream = new FileInputStream(imageFile);
   imageInputStream.read(imageBytes);
   imageInputStream.close();
   ```  

#### Ορισμός Άγκυρας
`FileInputStream` is a standard Java I/O class that reads raw bytes from a file on the filesystem.

### Προσθήκη Ενσωματωμένης Εικόνας στο Email

#### Επισκόπηση
Embedding the image as a Content‑ID (CID) reference ensures the watermark appears inline within the HTML body of the email.

#### Άμεση Απάντηση
Generate a unique CID, add the image bytes to the `Watermarker` using `addImageWatermark`, and reference the CID in the HTML body. The API automatically updates the MIME parts so the email remains RFC‑compatible.

#### Υλοποίηση Βήμα‑βήμα
1. **Import Classes for Handling Email Contents:**  
   ```java
   import com.groupdocs.watermark.contents.EmailContent;
   import com.groupdocs.watermark.contents.EmailEmbeddedObject;
   ```  

2. **Add Embedded Image to the Email:**  
   ```java
   EmailContent content = watermarker.getContent(EmailContent.class);
   content.getEmbeddedObjects().add(imageBytes, "sample.jpg");
   
   EmailEmbeddedObject embeddedObject = content.getEmbeddedObjects().get_Item(content.getEmbeddedObjects().getCount() - 1);
   content.setHtmlBody("<html><body>This is an embedded image: <img src=\"cid:" + embeddedObject.getContentId() + "\"></body></html>");
   ```  

#### Ορισμός Άγκυρας
`addImageWatermark` is a method of `Watermarker` that inserts an image watermark into the document’s visual layer.  
`Content‑ID (CID)` is a MIME header that allows an email client to display embedded resources like images directly within the message body.

### Αποθήκευση Υδατογραφημένου Εγγράφου Email

#### Επισκόπηση
After the watermark is applied, you must persist the changes to a new file.

#### Άμεση Απάντηση
Call `watermarker.save("output.eml", SaveOptions.create())` and then `watermarker.close()` to release all file handles and memory buffers. The saved file retains the original attachments and metadata while showing the new watermark.

#### Υλοποίηση Βήμα‑βήμα
1. **Save and Close Watermarker:**  
   ```java
   String outputFilePath = "YOUR_OUTPUT_DIRECTORY/message.msg";
   watermarker.save(outputFilePath);
   watermarker.close();
   ```  

#### Ορισμός Άγκυρας
`SaveOptions` defines the output format and compression settings for the resulting email file.

## Πρακτικές Εφαρμογές

1. **Internal Document Security** – Αποτρέψτε τυχαίες διαρροές δεδομένων επισημαίνοντας κάθε εσωτερική σημείωση με ένα εμπιστευτικό υδατογράφημα.  
2. **Email Marketing** – Ενισχύστε την ταυτότητα της μάρκας προσθέτοντας αυτόματα το λογότυπό σας σε κάθε email καμπάνιας.  
3. **Legal Correspondence** – Προσθέστε ένα υδατογράφημα “Confidential – Attorney‑Client Privilege” στα νομικά email για να ικανοποιήσετε ελέγχους συμμόρφωσης.  

## Σκέψεις Απόδοσης
- **Βελτιστοποίηση Μεγέθους Εικόνας:** Χρησιμοποιήστε PNG‑8 ή JPEG‑2000 για να διατηρήσετε το byte array κάτω από 100 KB χωρίς αισθητή απώλεια ποιότητας.  
- **Διαχείριση Πόρων:** Πάντα κλείστε τα streams (`FileInputStream`, `watermarker`) σε block `finally` ή χρησιμοποιήστε try‑with‑resources για αποφυγή διαρροών μνήμης.  
- **Επεξεργασία σε Παρτίδες:** Για μαζική υδ.σφραγίδωση, επεξεργαστείτε τα email ασύγχρονα με το `CompletableFuture` της Java για μέγιστη αξιοποίηση CPU.  

## Συνηθισμένα Προβλήματα και Λύσεις

| Πρόβλημα | Αιτία | Λύση |
|----------|-------|------|
| **Η εικόνα δεν εμφανίζεται** | Το CID δεν αναφέρεται σωστά στο HTML | Επαληθεύστε ότι η ετικέτα `<img src="cid:yourCid">` ταιριάζει με το CID που χρησιμοποιείται στο `addImageWatermark`. |
| **Το email καταστρέφεται** | Αποθήκευση με λανθασμένο `SaveOptions` | Χρησιμοποιήστε `SaveOptions.create().setPreserveOriginalHeaders(true)` για να διατηρήσετε τα αρχικά headers ανέπαφα. |
| **Σφάλμα έλλειψης μνήμης** | Μεγάλο email (>200 MB) φορτώνεται πλήρως στη μνήμη | Ενεργοποιήστε τη λειτουργία streaming μέσω `EmailLoadOptions.setLoadMode(LoadMode.Stream)` πριν την αρχικοποίηση του `Watermarker`. |

## Συχνές Ερωτήσεις

**Q: Μπορώ να υδατογραφήσω τόσο το HTML όσο και τα plain‑text μέρη ενός email;**  
A: Το GroupDocs.Watermark τροποποιεί μόνο το σώμα HTML· τα plain‑text μέρη παραμένουν αμετάβλητα, κάτι που είναι η τυπική πρακτική για branding email.

**Q: Διατηρείται το υδατογράφημα όταν προωθείται το email;**  
A: Ναι, επειδή το υδατογράφημα γίνεται μέρος του περιεχομένου HTML του email, παραμένει σε όλες τις επόμενες προωθήσεις.

**Q: Σε ποιες μορφές αρχείων μπορώ να εξάγω το υδατογραφημένο email;**  
A: Μπορείτε να αποθηκεύσετε ως EML, MSG ή MHT. Το API υποστηρίζει επίσης μετατροπή σε PDF εάν χρειάζεστε εκτυπώσιμη έκδοση.

**Q: Απαιτείται άδεια για περιβάλλοντα ανάπτυξης;**  
A: Μια δωρεάν δοκιμαστική άδεια λειτουργεί για ανάπτυξη και δοκιμές. Οι παραγωγικές εγκαταστάσεις απαιτούν αγορά άδειας για την αφαίρεση των υδατογραφημάτων αξιολόγησης.

**Q: Πώς διαχειρίζεται το GroupDocs.Watermark μεγάλα συνημμένα;**  
A: Τα συνημμένα μεταφέρονται αμετάβλητα· μόνο το σώμα του email υποβάλλεται σε επεξεργασία, οπότε το μέγεθος των συνημμένων δεν επηρεάζει την απόδοση της υδ.σφραγίδωσης.

## Συμπέρασμα

Τώρα έχετε μια πλήρη, έτοιμη για παραγωγή ροή εργασίας για **how to watermark email** αρχεία χρησιμοποιώντας το GroupDocs.Watermark για Java. Ακολουθώντας τα παραπάνω βήματα, μπορείτε να ενσωματώσετε λογότυπα, ειδοποιήσεις εμπιστευτικότητας ή οποιαδήποτε προσαρμοσμένη εικόνα σε κάθε εξερχόμενο email, εξασφαλίζοντας συνεπές branding και ενισχυμένη ασφάλεια. Εξερευνήστε πρόσθετες δυνατότητες όπως υδατογραφήματα κειμένου, δυναμικές ημερομηνίες ή επεξεργασία σε παρτίδες για να επεκτείνετε περαιτέρω τη λύση σας.

---

**Τελευταία ενημέρωση:** 2026-06-16  
**Δοκιμάστηκε με:** GroupDocs.Watermark for Java 24.11  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Υδατογράφημα Εγγράφου Email σε Java : Διαχείριση με GroupDocs.Watermark](/watermark/java/email-document-watermarking/groupdocs-watermark-java-email-management/)
- [Επεξεργασία Συνημμένων Email σε Java με GroupDocs.Watermark : Ένας Πλήρης Οδηγός](/watermark/java/email-document-watermarking/java-email-attachment-processing-groupdocs-watermark/)
- [Οδηγός Υδ.σφραγίδωσης Java : Ασφαλή Έγγραφα με GroupDocs.Watermark API](/watermark/java/getting-started/java-watermark-groupdocs-guide/)


{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}