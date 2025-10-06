---
title: Προσθήκη υδατογραφήματος σε εικόνες σχήματος στα Έγγραφα του Word
linktitle: Προσθήκη υδατογραφήματος σε εικόνες σχήματος στα Έγγραφα του Word
second_title: GroupDocs.Watermark .NET API
description: Μάθετε πώς να προσθέτετε υδατογραφήματα για να διαμορφώνετε εικόνες σε έγγραφα του Word χρησιμοποιώντας το GroupDocs.Watermark για .NET. Βελτιώστε την ασφάλεια των εγγράφων με αυτό το σεμινάριο.
weight: 17
url: /el/net/word-processing-watermarkings/add-watermark-shape-images-word-docs/
type: docs
---
# Προσθήκη υδατογραφήματος σε εικόνες σχήματος στα Έγγραφα του Word

## Εισαγωγή
Σε αυτό το σεμινάριο, θα διερευνήσουμε πώς να προσθέσετε ένα υδατογράφημα για να διαμορφώσετε εικόνες σε έγγραφα του Word χρησιμοποιώντας το GroupDocs.Watermark για .NET. Η υδατοσήμανση είναι μια κρίσιμη πτυχή της προστασίας των εγγράφων, ειδικά όταν πρόκειται για ευαίσθητες ή εμπιστευτικές πληροφορίες. Προσθέτοντας υδατογραφήματα για τη διαμόρφωση εικόνων, μπορείτε να διασφαλίσετε την ακεραιότητα και την ασφάλεια των εγγράφων σας.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:
1.  GroupDocs.Watermark για .NET: Κάντε λήψη και εγκατάσταση της βιβλιοθήκης GroupDocs.Watermark από το[σελίδα λήψης](https://releases.groupdocs.com/Watermark/net/).
2. Έγγραφο: Προετοιμάστε το έγγραφο του Word όπου θέλετε να προσθέσετε το υδατογράφημα.
3. Περιβάλλον ανάπτυξης: Ρυθμίστε το περιβάλλον ανάπτυξης .NET που προτιμάτε.
## Εισαγωγή χώρων ονομάτων
Πριν γράψετε τον κώδικα, φροντίστε να εισαγάγετε τους απαραίτητους χώρους ονομάτων:
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Βήμα 1: Φορτώστε το έγγραφο
Αρχικά, ορίστε τη διαδρομή προς το έγγραφό σας και καθορίστε το όνομα του αρχείου εξόδου:
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
## Βήμα 2: Αρχικοποίηση του Υδατοσήμανσης
 Στιγμιότυπο α`Watermarker` αντικείμενο παρέχοντας τη διαδρομή του εγγράφου και τις προαιρετικές επιλογές φόρτωσης:
```csharp
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Προσθέστε τη λογική υδατογράφησης εδώ
}
```
## Βήμα 3: Δημιουργήστε Υδατογράφημα κειμένου
Καθορίστε το υδατογράφημα κειμένου με τις επιθυμητές ιδιότητες όπως κείμενο, γραμματοσειρά, στοίχιση, περιστροφή, μέγεθος κ.λπ.:
```csharp
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;
```
## Βήμα 4: Εφαρμογή υδατογραφήματος σε εικόνες σχήματος
Επαναλάβετε τις ενότητες και τα σχήματα του εγγράφου για να αναγνωρίσετε εικόνες σχήματος και να προσθέσετε το υδατογράφημα:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingSection section in content.Sections)
{
    foreach (WordProcessingShape shape in section.Shapes)
    {
        if (shape.HeaderFooter == null && shape.Image != null)
        {
            shape.Image.Add(watermark);
        }
    }
}
```
## Βήμα 5: Αποθηκεύστε το έγγραφο
Αποθηκεύστε το έγγραφο με το προστιθέμενο υδατογράφημα στο καθορισμένο αρχείο εξόδου:
```csharp
watermarker.Save(outputFileName);
```

## συμπέρασμα
Σε αυτό το σεμινάριο, μάθαμε πώς να προσθέτουμε υδατογραφήματα για τη διαμόρφωση εικόνων σε έγγραφα του Word χρησιμοποιώντας το GroupDocs.Watermark για .NET. Ακολουθώντας τον οδηγό βήμα προς βήμα και αξιοποιώντας τις ισχυρές δυνατότητες του GroupDocs.Watermark, μπορείτε να βελτιώσετε αποτελεσματικά την ασφάλεια και την προστασία των εγγράφων σας.
## Συχνές ερωτήσεις
### Μπορώ να προσαρμόσω την εμφάνιση του κειμένου του υδατογραφήματος;
Ναι, μπορείτε να προσαρμόσετε διάφορες ιδιότητες όπως γραμματοσειρά, μέγεθος, χρώμα, γωνία περιστροφής και στοίχιση για να προσαρμόσετε το υδατογράφημα σύμφωνα με τις προτιμήσεις σας.
### Το GroupDocs.Watermark υποστηρίζει άλλες μορφές εγγράφων εκτός από το Word;
Ναι, το GroupDocs.Watermark παρέχει υποστήριξη για ένα ευρύ φάσμα μορφών εγγράφων, όπως PDF, Excel, PowerPoint και άλλα.
### Είναι δυνατή η προσθήκη πολλών υδατογραφημάτων σε ένα μόνο έγγραφο;
Οπωσδήποτε, μπορείτε να προσθέσετε πολλά υδατογραφήματα με διαφορετικό περιεχόμενο, στυλ και θέσεις στο ίδιο έγγραφο.
### Μπορώ να αφαιρέσω υδατογραφήματα από έγγραφα χρησιμοποιώντας το GroupDocs.Watermark;
Ναι, το GroupDocs.Watermark προσφέρει λειτουργίες για την αποτελεσματική ανίχνευση και αφαίρεση υδατογραφημάτων από έγγραφα.
### Παρέχει το GroupDocs.Watermark συμβατότητα μεταξύ πλατφορμών;
Ναι, το GroupDocs.Watermark είναι συμβατό με .NET Framework, .NET Core και .NET Standard, διασφαλίζοντας απρόσκοπτη ενοποίηση σε διαφορετικές πλατφόρμες.