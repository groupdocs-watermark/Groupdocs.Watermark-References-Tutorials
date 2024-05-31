---
title: Προσθήκη υδατογραφήματος σε όλα τα συνημμένα σε PDF
linktitle: Προσθήκη υδατογραφήματος σε όλα τα συνημμένα σε PDF
second_title: GroupDocs.Watermark .NET API
description: Μάθετε πώς να προσθέτετε υδατογραφήματα σε συνημμένα PDF χρησιμοποιώντας το GroupDocs.Watermark για .NET. Ασφαλίστε εύκολα τα έγγραφά σας με προσαρμοσμένα υδατογραφήματα.
type: docs
weight: 16
url: /el/net/pdf-watermarking-attachments/add-watermark-all-attachments-pdf/
---
## Εισαγωγή
Η προσθήκη υδατογραφημάτων σε συνημμένα PDF μπορεί να είναι ένα κρίσιμο βήμα στη διαχείριση εγγράφων, ειδικά όταν διασφαλίζεται η ασφάλεια ή η επωνυμία. Το GroupDocs.Watermark for .NET προσφέρει μια ολοκληρωμένη λύση για την απρόσκοπτη ενσωμάτωση υδατογραφημάτων σε αρχεία PDF. Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στη διαδικασία προσθήκης υδατογραφήματος σε όλα τα συνημμένα σε ένα έγγραφο PDF χρησιμοποιώντας το GroupDocs.Watermark για .NET.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:
1.  GroupDocs.Watermark για .NET: Εάν δεν το έχετε κάνει ήδη, κάντε λήψη και εγκαταστήστε το GroupDocs.Watermark για .NET από το[δικτυακός τόπος](https://releases.groupdocs.com/Watermark/net/).
2. Περιβάλλον ανάπτυξης: Ρυθμίστε ένα κατάλληλο περιβάλλον ανάπτυξης με το Visual Studio ή οποιοδήποτε άλλο IDE συμβατό με .NET.
3. Έγγραφο PDF: Προετοιμάστε το έγγραφο PDF στο οποίο θέλετε να προσθέσετε υδατογραφήματα, μαζί με τα συνημμένα που θέλετε να υδατογραφήσετε.

## Εισαγωγή χώρων ονομάτων
Πριν βουτήξετε στον κώδικα, βεβαιωθείτε ότι έχετε εισαγάγει τους απαραίτητους χώρους ονομάτων για πρόσβαση στο GroupDocs.Watermark για λειτουργίες .NET:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Βήμα 1: Ορισμός διαδρομής εγγράφου και καταλόγου εξόδου
Αρχικά, ορίστε τη διαδρομή προς το εισερχόμενο έγγραφο PDF και τον κατάλογο όπου θα αποθηκευτεί το υδατογραφημένο έγγραφο:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
## Βήμα 2: Αρχικοποιήστε τις επιλογές φόρτωσης και το υδατογράφημα
Στη συνέχεια, αρχικοποιήστε τις επιλογές φόρτωσης για το έγγραφο PDF και δημιουργήστε ένα υδατογράφημα κειμένου:
```csharp
var loadOptions = new PdfLoadOptions();
TextWatermark watermark = new TextWatermark("This is WaterMark on Attachment", new Font("Arial", 19));
```
## Βήμα 3: Φορτώστε το έγγραφο και τα συνημμένα
Φορτώστε το έγγραφο PDF και επαναλάβετε τα συνημμένα του:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    PdfContent pdfContent = watermarker.GetContent<PdfContent>();
    foreach (PdfAttachment attachment in pdfContent.Attachments)
    {
```
## Βήμα 4: Ελέγξτε την υποστήριξη συνημμένων
Ελέγξτε εάν το συνημμένο αρχείο υποστηρίζεται από το GroupDocs.Watermark:
```csharp
        IDocumentInfo info = attachment.GetDocumentInfo();
        if (info.FileType != FileType.Unknown && !info.IsEncrypted)
        {
```
## Βήμα 5: Προσθήκη υδατογραφήματος στα συνημμένα
Φορτώστε το συνημμένο έγγραφο και προσθέστε το υδατογράφημα:
```csharp
            using (Watermarker attachedWatermarker = attachment.CreateWatermarker())
            {
                attachedWatermarker.Add(watermark);
                attachedWatermarker.Save();
            }
        }
    }
```
## Βήμα 6: Αποθήκευση αλλαγών
Τέλος, αποθηκεύστε τις αλλαγές στο υδατογραφημένο έγγραφο PDF:
```csharp
    watermarker.Save(outputFileName);
}
```

## συμπέρασμα
Σε αυτό το σεμινάριο, εξερευνήσαμε πώς να προσθέτουμε υδατογραφήματα σε όλα τα συνημμένα σε ένα έγγραφο PDF χρησιμοποιώντας το GroupDocs.Watermark για .NET. Ακολουθώντας τον οδηγό βήμα προς βήμα, μπορείτε να ενσωματώσετε απρόσκοπτα υδατογραφήματα στα αρχεία PDF σας, διασφαλίζοντας την ασφάλεια των εγγράφων και την επωνυμία.
## Συχνές ερωτήσεις
### Μπορώ να προσαρμόσω την εμφάνιση του υδατογραφήματος;
Ναι, μπορείτε να προσαρμόσετε διάφορες πτυχές, όπως κείμενο, γραμματοσειρά, μέγεθος, χρώμα και θέση του υδατογραφήματος σύμφωνα με τις απαιτήσεις σας.
### Το GroupDocs.Watermark υποστηρίζει άλλες μορφές εγγράφων εκτός από το PDF;
Ναι, το GroupDocs.Watermark υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, συμπεριλαμβανομένων των Microsoft Word, Excel, PowerPoint, Visio, Outlook και Images.
### Υπάρχει διαθέσιμη δοκιμαστική έκδοση για το GroupDocs.Watermark;
Ναι, μπορείτε να εξερευνήσετε τις δυνατότητες του GroupDocs.Watermark κατεβάζοντας τη δωρεάν δοκιμαστική έκδοση από τον ιστότοπο.
### Μπορώ να προσθέσω πολλά υδατογραφήματα σε ένα μόνο έγγραφο;
Οπωσδήποτε, το GroupDocs.Watermark σάς επιτρέπει να προσθέτετε πολλά υδατογραφήματα, όπως κείμενο, εικόνα και σχολιασμό ταυτόχρονα, για να βελτιώσετε την ασφάλεια των εγγράφων και την επωνυμία.
### Είναι διαθέσιμη τεχνική υποστήριξη για τους χρήστες του GroupDocs.Watermark;
Ναι, το GroupDocs παρέχει ολοκληρωμένη τεχνική υποστήριξη μέσω φόρουμ και αποκλειστικών καναλιών υποστήριξης για να βοηθήσει τους χρήστες με τυχόν απορίες ή προβλήματα που μπορεί να αντιμετωπίσουν.