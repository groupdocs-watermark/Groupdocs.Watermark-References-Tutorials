---
date: '2026-09-26'
description: Μάθετε πώς να μετατρέψετε ένα έγγραφο σε εικόνα και να δημιουργήσετε
  thumbnails με Java χρησιμοποιώντας το GroupDocs.Watermark. Ο οδηγός βήμα-βήμα καλύπτει
  το setup, τα preview streams και τα performance tips.
keywords:
- convert document to image
- java generate thumbnails
- GroupDocs.Watermark Java
- document preview generation
- Java watermarking library
lastmod: '2026-09-26'
og_description: Μάθετε πώς να μετατρέψετε ένα έγγραφο σε εικόνα και να δημιουργήσετε
  thumbnails με Java χρησιμοποιώντας το GroupDocs.Watermark. Αυτός ο οδηγός σας καθοδηγεί
  μέσω του installation, του stream handling και του performance optimisation για
  γρήγορη δημιουργία preview creation.
og_image_alt: Guide showing how to convert document to image with GroupDocs.Watermark
  in Java
og_title: Μετατροπή εγγράφου σε εικόνα με GroupDocs.Watermark Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-26'
  description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  headline: Convert document to image with GroupDocs.Watermark Java
  type: TechArticle
- description: Learn how to convert document to image and java generate thumbnails
    using GroupDocs.Watermark. Step-by-step guide covers setup, preview streams, and
    performance tips.
  name: Convert document to image with GroupDocs.Watermark Java
  steps:
  - name: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
    text: '**Document browsers** – Show a grid of PNG thumbnails so users can skim
      large PDFs without opening them.'
  - name: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
    text: '**Search result snippets** – Attach a preview image to search index entries
      for richer UI.'
  - name: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
    text: '**Email attachments** – Embed a small preview of attached PDFs in the body
      of an email.'
  - name: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
    text: '**Mobile apps** – Reduce bandwidth by sending 200 KB PNG previews instead
      of full PDFs.'
  - name: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
    text: '**Compliance portals** – Render legally‑required watermarked versions of
      contracts as images for audit trails.'
  type: HowTo
- questions:
  - answer: 'Yes. Pass the password to the `Watermarker` constructor: `new Watermarker("file.pdf",
      "password")`.'
    question: Can I generate previews for password‑protected PDFs?
  - answer: PNG, JPEG, BMP, and TIFF are available. PNG is recommended for lossless
      thumbnails.
    question: Which image formats are supported for the preview output?
  - answer: The library imposes no hard limit; you can preview documents with thousands
      of pages, limited only by storage space and I/O throughput.
    question: How many pages can be processed in a single call?
  - answer: A single licence file can be reused across multiple instances as long
      as the total usage complies with the licence terms.
    question: Do I need a separate licence for each server instance?
  - answer: Yes. Set `previewOptions.setPages(new int[]{1})` to limit generation to
      the first page.
    question: Is there a way to generate a single combined thumbnail (e.g., first
      page only)?
  type: FAQPage
tags:
- convert document
- generate thumbnails
- GroupDocs.Watermark
- Java document processing
- preview generation
title: Μετατροπή εγγράφου σε εικόνα με GroupDocs.Watermark Java
type: docs
url: /el/java/advanced-features/groupdocs-watermark-java-document-previews/
weight: 1
---

# Μετατροπή εγγράφου σε εικόνα με το GroupDocs.Watermark Java

Generating lightweight image previews of multi‑page documents is a common requirement for portals, content‑management systems, and cloud storage services. By **convert document to image** you give end‑users a fast visual cue without the overhead of loading the full file. The GroupDocs.Watermark Java library not only adds watermarks but also provides a high‑performance preview engine that can **java generate thumbnails** for every page in a single pass.

In this tutorial you will learn how to set up the library, create custom page streams, release resources safely, and finally produce image previews for each page of a source document. The instructions are written for developers familiar with Java and object‑oriented concepts, and they include best‑practice tips for handling large batches of files.

## Γρήγορες απαντήσεις
- **Τι είναι το πρώτο βήμα;** Προσθέστε την εξάρτηση Maven του GroupDocs.Watermark και αρχικοποιήστε ένα `Watermarker` με τη διαδρομή του πηγαίου αρχείου.  
- **Πώς δημιουργούνται οι εικόνες προεπισκόπησης;** Υλοποιήστε το `ICreatePageStream` για να ανοίξετε ένα ρεύμα εξόδου για κάθε σελίδα, στη συνέχεια καλέστε το `generatePreview()` με τις κατάλληλες επιλογές.  
- **Χρειάζομαι άδεια;** Μια δοκιμαστική έκδοση λειτουργεί για βασικά σενάρια, αλλά μια πλήρης άδεια αφαιρεί τα υδατογραφήματα και ξεκλειδώνει την επεξεργασία παρτίδων.  
- **Μπορώ να επεξεργαστώ PDF μεγαλύτερα από 200 σελίδες;** Ναι – η βιβλιοθήκη μεταδίδει τις σελίδες, έτσι η χρήση μνήμης παραμένει χαμηλή ακόμη και για αρχεία 500 σελίδων.  
- **Ποιοι μορφές εικόνας υποστηρίζονται;** PNG, JPEG, BMP και TIFF είναι διαθέσιμα έτοιμα.

## Τι είναι η μετατροπή εγγράφου σε εικόνα;
Η φράση **convert document to image** περιγράφει τη διαδικασία απόδοσης κάθε σελίδας ενός πηγαίου αρχείου (PDF, DOCX, PPTX κ.λπ.) σε μια ραστερ εικόνα όπως PNG ή JPEG. Αυτή η μετατροπή είναι χρήσιμη για γκαλερί μικρογραφιών, παράθυρα προεπισκόπησης και προβολείς εγγράφων φιλικούς προς τα κινητά.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Watermark για τη δημιουργία προεπισκοπήσεων;
Το GroupDocs.Watermark υποστηρίζει **30+ μορφές εισόδου** και μπορεί να δημιουργήσει προεπισκοπήσεις για έγγραφα έως **500 σελίδες** χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη. Εσωτερικά επεξεργάζεται τις σελίδες διαδοχικά, κάτι που διατηρεί τη χρήση της στοίβας Java κάτω από 50 MB ακόμη και για μεγάλα PDF. Η βιβλιοθήκη προσφέρει επίσης ενσωματωμένη βελτιστοποίηση εικόνας, επιτρέποντάς σας να καθορίσετε DPI, βάθος χρώματος και επίπεδο συμπίεσης, με αποτέλεσμα μικρογραφίες που είναι συνήθως **70 % μικρότερες** από την αδική ραστεροποίηση.

## Προαπαιτούμενα
- **Java Development Kit (JDK) 11 or newer** – η βιβλιοθήκη είναι μεταγλωττισμένη για Java 8+, αλλά το JDK 11 παρέχει μακροπρόθεσμη υποστήριξη και καλύτερη απόδοση.
- **Maven 3.6+** – για διαχείριση εξαρτήσεων.
- **GroupDocs.Watermark for Java version 24.11** – η πιο πρόσφατη σταθερή έκδοση τη στιγμή της συγγραφής.
- **Basic knowledge of Java I/O streams** – θα δημιουργείτε αντικείμενα `FileOutputStream` για κάθε σελίδα προεπισκόπησης.
- **A licence key** (optional for production) – η δοκιμαστική έκδοση περιορίζει το μέγεθος προεπισκόπησης στα 5 MB ανά έγγραφο.

## Πώς να ρυθμίσετε το GroupDocs.Watermark για Java

Για να ρυθμίσετε το GroupDocs.Watermark, πρώτα προσθέστε το αποθετήριο Maven και στη συνέχεια συμπεριλάβετε τη βιβλιοθήκη ως εξάρτηση στο `pom.xml` του έργου σας. Αυτό εξασφαλίζει ότι το Maven μπορεί να κατεβάσει τα σωστά αρχεία και κάνει τις κλάσεις διαθέσιμες στο classpath για μεταγλώττιση και εκτέλεση.

### Προσθήκη της εξάρτησης Maven
Η βιβλιοθήκη διανέμεται μέσω Maven Central. Προσθέστε το παρακάτω απόσπασμα στο `pom.xml` σας μέσα στο μπλοκ `<dependencies>`:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-watermark</artifactId>
    <version>24.11</version>
</dependency>
```

> **Συμβουλή:** Keep the version number in a property (`<groupdocs.watermark.version>24.11</groupdocs.watermark.version>`) so you can upgrade easily.

### Άμεση λήψη (εναλλακτική)
Αν προτιμάτε χειροκίνητη εγκατάσταση, μπορείτε να κατεβάσετε το JAR από τη σελίδα επίσημων εκδόσεων: [Εκδόσεις GroupDocs.Watermark για Java](https://releases.groupdocs.com/watermark/java/).

## Πώς να αποκτήσετε και να εφαρμόσετε άδεια
Η εφαρμογή άδειας στο GroupDocs.Watermark αφαιρεί τους περιορισμούς της δοκιμαστικής έκδοσης και απενεργοποιεί την προεπιλεγμένη επικάλυψη υδατογραφήματος. Τοποθετήστε το αρχείο άδειας σε μια γνωστή θέση και κατευθύνετε το API σε αυτό, ή ενσωματώστε τη διαδρομή άδειας απευθείας στον κώδικα πριν από οποιαδήποτε άλλη κλήση. Μόλις φορτωθεί, όλες οι επόμενες λειτουργίες εκτελούνται σε πλήρη λειτουργία.

- **Ζητήστε δωρεάν δοκιμή** from the GroupDocs portal – it provides a 30‑day licence file.
- **Δημιουργήστε προσωρινή άδεια** via the online licence generator for evaluation environments.
- **Αγοράστε εμπορική άδεια** for unlimited production use and priority support.

Τοποθετήστε το αρχείο άδειας (`GroupDocs.Watermark.lic`) στη ρίζα του έργου σας ή καθορίστε τη διαδρομή του προγραμματιστικά με `Watermarker.setLicense("path/to/license.file")`.

## Πώς να αρχικοποιήσετε το Watermarker
Αρχικοποιήστε το `Watermarker` παρέχοντας τη διαδρομή του πηγαίου εγγράφου, προαιρετικά συμπεριλαμβάνοντας κωδικό πρόσβασης για προστατευμένα αρχεία. Ο κατασκευαστής επικυρώνει τη μορφή και προετοιμάζει εσωτερικούς αναλυτές, επιτρέποντάς σας να καλέσετε αμέσως μεθόδους προεπισκόπησης ή υδατογραφήματος. Μετά τη δημιουργία, διατηρήστε μια αναφορά για επαναχρησιμοποίηση του αντικειμένου σε πολλαπλές λειτουργίες εάν χρειάζεται.

Η κλάση `Watermarker` είναι το βασικό αντικείμενο του GroupDocs.Watermark που φορτώνει ένα έγγραφο και εκθέτει λειτουργίες όπως η εισαγωγή υδατογραφήματος και η δημιουργία προεπισκοπήσεων.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
```

- **`inputDocumentPath`** – απόλυτη ή σχετική διαδρομή προς το πηγαίο αρχείο.
- Ο κατασκευαστής επικυρώνει τη μορφή του αρχείου και προετοιμάζει εσωτερικούς αναλυτές.

> **Ορισμός άγκυρας:** `Watermarker` is the entry point for all document‑processing actions in GroupDocs.Watermark for Java.

## Πώς να δημιουργήσετε ρεύματα σελίδων για τη δημιουργία προεπισκοπήσεων
Δημιουργήστε προσαρμοσμένα ρεύματα σελίδων υλοποιώντας το interface `ICreatePageStream`, το οποίο η βιβλιοθήκη καλεί για κάθε σελίδα που αποδίδει. Η υλοποίησή σας πρέπει να δημιουργεί ένα νέο `OutputStream` — συνήθως ένα `FileOutputStream` — που δείχνει σε ένα μοναδικά ονομασμένο αρχείο βάσει του αριθμού σελίδας. Αυτή η προσέγγιση απομονώνει την έξοδο κάθε σελίδας και αποτρέπει την επικάλυψη δεδομένων.

Για να **java generate thumbnails**, πρέπει να παρέχετε ένα ρεύμα για κάθε σελίδα όπου θα γραφτεί η αποδοθείσα εικόνα. Υλοποιήστε το interface `ICreatePageStream`; η βιβλιοθήκη καλεί την υλοποίησή σας για κάθε σελίδα που επεξεργάζεται.
```text
public class FeatureCreatePageStream implements ICreatePageStream {
    private final String outputDir;
    private final String fileNameTemplate; // e.g. "preview_page_{0}.png"

    public FeatureCreatePageStream(String outputDir, String fileNameTemplate) {
        this.outputDir = outputDir;
        this.fileNameTemplate = fileNameTemplate;
    }

    @Override
    public OutputStream createPageStream(int pageNumber) throws IOException {
        String fileName = fileNameTemplate.replace("{0}", String.valueOf(pageNumber));
        return new FileOutputStream(Paths.get(outputDir, fileName).toFile());
    }
}
```

- **`fileNameTemplate`** σας επιτρέπει να ενσωματώσετε τον αριθμό σελίδας απευθείας στο όνομα του αρχείου, καθιστώντας την επεξεργασία παρτίδας απλή.
- Η μέθοδος επιστρέφει ένα νέο `OutputStream` για κάθε σελίδα, εξασφαλίζοντας ότι οι προηγούμενες σελίδες δεν επηρεάζουν τις επόμενες εγγραφές.

> **Ορισμός άγκυρας:** `ICreatePageStream` is a callback interface that lets you define how output streams are created for each preview page.

## Πώς να απελευθερώσετε τα ρεύματα σελίδων μετά τη δημιουργία προεπισκοπήσεων
Μετά τη γραφή μιας εικόνας σελίδας, η βιβλιοθήκη καλεί το `IReleasePageStream` ώστε να μπορείτε να κλείσετε και να καθαρίσετε το σχετικό ρεύμα εξόδου. Υλοποιήστε αυτήν την κλήση επιστροφής για να απελευθερώσετε με ασφάλεια τους χειριστές αρχείων, να αδειάσετε τις προσωρινές μνήμες και να εκτελέσετε τυχόν πρόσθετη καταγραφή. Η σωστή εκκαθάριση αποτρέπει διαρροές περιγραφέων και εξασφαλίζει ότι οι επόμενες σελίδες μπορούν να επεξεργαστούν χωρίς παρεμβολές.

Η σωστή εκκαθάριση πόρων αποτρέπει διαρροές χειριστών αρχείων και κρατά το JVM από το να εξαντλήσει τους περιγραφείς. Υλοποιήστε το `IReleasePageStream` για να κλείσετε τα ρεύματα μόλις η βιβλιοθήκη υποδείξει ότι η σελίδα ολοκληρώθηκε.
```text
public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(OutputStream stream) throws IOException {
        stream.close();
    }
}
```

> **Ορισμός άγκυρας:** `IReleasePageStream` is a callback interface that lets you define custom logic for disposing of page‑specific output resources.

## Πώς να δημιουργήσετε προεπισκοπήσεις εγγράφου (convert document to image)
Δημιουργήστε προεπισκοπήσεις καλώντας το `generatePreview()` στο αντικείμενο `Watermarker`, παρέχοντας ένα αντικείμενο `PreviewOptions` που ορίζει την ανάλυση, τη μορφή εικόνας και το εύρος σελίδων. Η μέθοδος επαναλαμβάνει για κάθε σελίδα, χρησιμοποιεί τους δημιουργούς ρευμάτων σας για να γράψει τη ραστερ εικόνα και στη συνέχεια απελευθερώνει τα ρεύματα. Αυτή η διαδικασία παράγει ένα σύνολο αρχείων εικόνας που αντιπροσωπεύουν τις σελίδες του εγγράφου.

Με το `Watermarker`, `FeatureCreatePageStream` και `FeatureReleasePageStream` έτοιμα, μπορείτε να καλέσετε τη μηχανή προεπισκόπησης. Η μέθοδος `generatePreview()` επαναλαμβάνει για κάθε σελίδα, καλεί τους δημιουργούς ρευμάτων, γράφει την εικόνα και τελικά απελευθερώνει τα ρεύματα.
```text
Watermarker watermarker = new Watermarker("YOUR_DOCUMENT_DIRECTORY/diagram.vdx");
ICreatePageStream createPageStream = new FeatureCreatePageStream("output/previews", "preview_page_{0}.png");
IReleasePageStream releasePageStream = new FeatureReleasePageStream();

PreviewOptions previewOptions = new PreviewOptions();
previewOptions.setResolution(150); // DPI, higher = sharper but larger files
previewOptions.setImageFormat(ImageFormat.Png); // PNG is lossless and web‑friendly

watermarker.generatePreview(previewOptions, createPageStream, releasePageStream);
```

- **`Resolution`** ελέγχει το DPI· 150 DPI είναι μια καλή ισορροπία για μικρογραφίες ιστού.
- **`ImageFormat`** μπορεί να είναι PNG, JPEG, BMP ή TIFF ανάλογα με τις απαιτήσεις σας.
- Η μέθοδος επεξεργάζεται τις σελίδες διαδοχικά, έτσι η κατανάλωση μνήμης παραμένει χαμηλή ακόμη και για έγγραφα με εκατοντάδες σελίδες.

> **Ορισμός άγκυρας:** `generatePreview()` is the API call that renders each page of the loaded document into an image using the streams you supplied.

## Πρακτικές εφαρμογές της μετατροπής εγγράφου σε εικόνα
Η δημιουργία προεπισκοπήσεων εικόνας ανοίγει πολλές δυνατότητες:

1. **Document browsers** – Εμφανίστε ένα πλέγμα PNG μικρογραφιών ώστε οι χρήστες να περιηγηθούν γρήγορα σε μεγάλα PDF χωρίς να τα ανοίξουν.
2. **Search result snippets** – Προσθέστε μια εικόνα προεπισκόπησης στις εγγραφές του ευρετηρίου αναζήτησης για πιο πλούσιο UI.
3. **Email attachments** – Ενσωματώστε μια μικρή προεπισκόπηση των συνημμένων PDF στο σώμα ενός email.
4. **Mobile apps** – Μειώστε το εύρος ζώνης στέλνοντας PNG προεπισκοπήσεις 200 KB αντί για πλήρη PDF.
5. **Compliance portals** – Δημιουργήστε νομικά απαιτούμενες υδατογραφημένες εκδόσεις συμβάσεων ως εικόνες για γραμμές ελέγχου.

## Σκέψεις απόδοσης όταν κάνετε java generate thumbnails
Όταν ασχολείστε με μαζική επεξεργασία, κρατήστε αυτές τις συμβουλές βελτιστοποίησης στο μυαλό:

- **Stream buffering** – Τυλίξτε το `FileOutputStream` σε ένα `BufferedOutputStream` για ελαχιστοποίηση του I/O του δίσκου.
- **Parallel batch execution** – Χρησιμοποιήστε το `ForkJoinPool` της Java για να επεξεργαστείτε πολλαπλά έγγραφα ταυτόχρονα· κάθε εργασία πρέπει να δημιουργεί το δικό της αντικείμενο `Watermarker` για να αποφύγετε προβλήματα ασφαλείας νήματος.
- **Limit DPI for thumbnails** – 72–150 DPI είναι επαρκές για τις περισσότερες περιπτώσεις UI· υψηλότερο DPI πρέπει να διατηρείται για προεπισκοπήσεις έτοιμες για εκτύπωση.
- **Reuse licence objects** – Η φόρτωση του αρχείου άδειας μία φορά ανά JVM μειώνει το κόστος.
- **Monitor memory** – Η βιβλιοθήκη κρατά μόνο την τρέχουσα σελίδα στη μνήμη. Για εξαιρετικά μεγάλα αρχεία, σκεφτείτε να αυξήσετε ελαφρώς τη στοίβα JVM (π.χ., `-Xmx512m`) για να αντιμετωπίσετε περιστασιακές αυξήσεις.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε
| Σύμπτωμα | Πιθανή αιτία | Διόρθωση |
|---------|--------------|-----|
| `OutOfMemoryError` κατά τη δημιουργία προεπισκόπησης | Χρήση του `ImageFormat.Jpeg` με 300 DPI σε PDF 1000 σελίδων | Μειώστε το DPI ή μεταβείτε σε PNG με χαμηλότερο βάθος χρώματος |
| Κενά αρχεία προεπισκόπησης | `FeatureCreatePageStream` επιστρέφει το ίδιο `FileOutputStream` για κάθε σελίδα | Βεβαιωθείτε ότι δημιουργείται νέο ρεύμα ανά `pageNumber` |
| Οι εικόνες προεπισκόπησης είναι περιστραμμένες | Το πηγαίο PDF περιέχει μεταδεδομένα περιστροφής που δεν τηρούνται | Καλέστε `previewOptions.setRotatePages(true)` (αν είναι διαθέσιμο) |
| Εμφανίζεται προειδοποίηση άδειας | Το αρχείο άδειας δεν βρέθηκε ή η διαδρομή είναι λανθασμένη | Επαληθεύστε ότι το `Watermarker.setLicense("path/to/license.file")` εκτελείται πριν από οποιεσδήποτε άλλες κλήσεις API |

## Συχνές ερωτήσεις
**Q: Μπορώ να δημιουργήσω προεπισκοπήσεις για PDF με κωδικό πρόσβασης;**  
A: Ναι. Περνάτε τον κωδικό πρόσβασης στον κατασκευαστή `Watermarker`: `new Watermarker("file.pdf", "password")`.

**Q: Ποιες μορφές εικόνας υποστηρίζονται για την έξοδο προεπισκόπησης;**  
A: Διατίθενται PNG, JPEG, BMP και TIFF. Το PNG συνιστάται για μη απωλεστικές μικρογραφίες.

**Q: Πόσες σελίδες μπορούν να επεξεργαστούν σε μία κλήση;**  
A: Η βιβλιοθήκη δεν επιβάλλει σκληρό όριο· μπορείτε να προεπισκοπήσετε έγγραφα με χιλιάδες σελίδες, περιορισμένο μόνο από τον χώρο αποθήκευσης και τη διαύγεια I/O.

**Q: Χρειάζομαι ξεχωριστή άδεια για κάθε instance του διακομιστή;**  
A: Ένα μόνο αρχείο άδειας μπορεί να επαναχρησιμοποιηθεί σε πολλαπλά instances, εφόσον η συνολική χρήση συμμορφώνεται με τους όρους της άδειας.

**Q: Υπάρχει τρόπος να δημιουργήσετε μια ενιαία συνδυαστική μικρογραφία (π.χ., μόνο την πρώτη σελίδα);**  
A: Ναι. Ορίστε `previewOptions.setPages(new int[]{1})` για να περιορίσετε τη δημιουργία στην πρώτη σελίδα.

## Συμπέρασμα
Τώρα έχετε μια πλήρη, έτοιμη για παραγωγή ροή εργασίας για **convert document to image** και **java generate thumbnails** χρησιμοποιώντας το GroupDocs.Watermark. Με τη διαμόρφωση προσαρμοσμένων χειριστών ρεύματος σελίδων, διατηρείτε τη χρήση μνήμης χαμηλή, και με την προσαρμογή των `PreviewOptions` ελέγχετε την ποιότητα εικόνας και το μέγεθος αρχείου. Αυτές οι τεχνικές σας επιτρέπουν να ενσωματώσετε γρήγορες, υψηλής ποιότητας προεπισκοπήσεις σε οποιαδήποτε εφαρμογή βασισμένη σε Java — είτε είναι μια διαδικτυακή πύλη, ένας πελάτης επιφάνειας εργασίας ή μια cloud‑native μικροϋπηρεσία.

---

**Τελευταία ενημέρωση:** 2026-09-26  
**Δοκιμή με:** GroupDocs.Watermark 24.11 for Java  
**Συγγραφέας:** GroupDocs

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

```java
import com.groupdocs.watermark.Watermarker;

public class FeatureInitializeWatermarker {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        // Initialize Watermarker with the specified document
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        System.out.println("Watermarker initialized.");
    }
}
```

```java
import java.io.FileOutputStream;
import com.groupdocs.watermark.options.ICreatePageStream;
import java.io.OutputStream;

public class FeatureCreatePageStream implements ICreatePageStream {
    private final String fileNameTemplate;

    public FeatureCreatePageStream(String outputDirectory) {
        this.fileNameTemplate = outputDirectory + "/page%s.png";
    }

    @Override
    public OutputStream createPageStream(int pageNumber) {
        String fileName = String.format(this.fileNameTemplate, pageNumber);
        try {
            return new FileOutputStream(fileName);
        } catch (Exception ex) 
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.options.IReleasePageStream;
import java.io.OutputStream;

public class FeatureReleasePageStream implements IReleasePageStream {
    @Override
    public void releasePageStream(int pageNumber, OutputStream pageStream) {
        try 
        {
            pageStream.close();
        } catch (Exception ex)
        {
            throw new RuntimeException(ex);
        }
    }
}
```

```java
import com.groupdocs.watermark.Watermarker;
import com.groupdocs.watermark.options.PreviewOptions;

public class FeatureGenerateDocumentPreview {
    public static void main(String[] args) {
        String inputDocumentPath = "YOUR_DOCUMENT_DIRECTORY/diagram.vdx";
        
        Watermarker watermarker = new Watermarker(inputDocumentPath);
        
        FeatureCreatePageStream createPageStream = new FeatureCreatePageStream("YOUR_OUTPUT_DIRECTORY");
        FeatureReleasePageStream releasePageStream = new FeatureReleasePageStream();
        
        PreviewOptions previewOptions = new PreviewOptions(createPageStream, releasePageStream);
        
        watermarker.generatePreview(previewOptions);
        
        watermarker.close();
    }
}
```

## Σχετικά Μαθήματα

- [Πώς να ανακτήσετε πληροφορίες εγγράφου χρησιμοποιώντας το GroupDocs.Watermark για Java&#58; Οδηγός βήμα προς βήμα](/watermark/java/document-information/retrieve-document-info-groupdocs-watermark-java/)
- [Προχωρημένα μαθήματα χαρακτηριστικών υδατογράφησης για το GroupDocs.Watermark Java](/watermark/java/advanced-features/)
- [Πώς να προσθέσετε υδατογράφημα εικόνας σε Java χρησιμοποιώντας το GroupDocs.Watermark&#58; Οδηγός βήμα προς βήμα](/watermark/java/image-watermarks/add-image-watermark-java-groupdocs/)