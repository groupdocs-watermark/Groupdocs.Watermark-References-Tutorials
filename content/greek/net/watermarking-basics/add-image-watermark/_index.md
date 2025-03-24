---
title: Προσθήκη υδατογραφήματος εικόνας
linktitle: Προσθήκη υδατογραφήματος εικόνας
second_title: GroupDocs.Watermark .NET API
description: Προσθέστε εύκολα υδατογραφήματα εικόνας στα έγγραφά σας χρησιμοποιώντας το GroupDocs.Watermark για .NET. Προστατέψτε την πνευματική σας ιδιοκτησία με ευκολία.
weight: 10
url: /el/net/watermarking-basics/add-image-watermark/
---
## Εισαγωγή
Σε αυτό το σεμινάριο, θα εμβαθύνουμε στη διαδικασία προσθήκης υδατογραφήματος εικόνας στα έγγραφά σας χρησιμοποιώντας το GroupDocs.Watermark για .NET. Η υδατογράφηση εγγράφων είναι απαραίτητη για την προστασία της πνευματικής ιδιοκτησίας και της επωνυμίας. Με το GroupDocs.Watermark για .NET, μπορείτε να ενσωματώσετε απρόσκοπτα υδατογραφήματα σε διάφορες μορφές εγγράφων όπως Word, Excel, PowerPoint, PDF και πολλά άλλα.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:
1.  GroupDocs.Watermark for .NET Library: Κατεβάστε και εγκαταστήστε τη βιβλιοθήκη GroupDocs.Watermark για .NET από τη[δικτυακός τόπος](https://releases.groupdocs.com/Watermark/net/).
2. Έγγραφο: Έχετε έτοιμο το έγγραφο στο οποίο θέλετε να προσθέσετε το υδατογράφημα.
3. Εικόνα για υδατογράφημα: Προετοιμάστε το αρχείο εικόνας που θέλετε να χρησιμοποιήσετε ως υδατογράφημα.

## Εισαγωγή χώρων ονομάτων
```csharp
using System;
using System.IO;
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.Spreadsheet;
using GroupDocs.Watermark.Watermarks;
```
## Βήμα 1: Αρχικοποίηση διαδρομής εγγράφου και καταλόγου εξόδου
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Αντικαθιστώ`"Your Document Path"`με την απόλυτη ή σχετική διαδρομή προς το έγγραφό σας και`"Your Document Directory"` με τον κατάλογο όπου θέλετε να αποθηκεύσετε το υδατογραφημένο έγγραφο.
## Βήμα 2: Ανοίξτε τη ροή εγγράφων και αρχικοποιήστε το υδατοσήμανση
```csharp
using (FileStream stream = File.Open(documentPath, FileMode.Open, FileAccess.ReadWrite))
{
    using (Watermarker watermarker = new Watermarker(stream))
    {
        // Η διαδικασία υδατογράφησης θα πάει εδώ
    }
}
```
 Ανοίξτε τη ροή εγγράφων χρησιμοποιώντας`FileStream` και αρχικοποιήστε το`Watermarker` αντικείμενο.
## Βήμα 3: Προσθήκη υδατογραφήματος εικόνας
```csharp
using (ImageWatermark watermark = new ImageWatermark(Constants.LogoPng))
{
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
}
```
 Δημιουργήστε ένα`ImageWatermark` αντικείμενο με τη διαδρομή προς το αρχείο εικόνας που θέλετε να χρησιμοποιήσετε ως υδατογράφημα. Ορίστε την οριζόντια και κάθετη στοίχιση του υδατογραφήματος.
## Βήμα 4: Αποθήκευση υδατογραφημένου εγγράφου
```csharp
watermarker.Save(outputFileName);
```
Αποθηκεύστε το υδατογραφημένο έγγραφο στον καθορισμένο κατάλογο εξόδου με το επιθυμητό όνομα αρχείου.

## συμπέρασμα
Συμπερασματικά, το GroupDocs.Watermark for .NET παρέχει μια ολοκληρωμένη λύση για την εύκολη προσθήκη υδατογραφημάτων σε διάφορες μορφές εγγράφων. Ακολουθώντας τα βήματα που περιγράφονται σε αυτό το σεμινάριο, μπορείτε να προσθέσετε αποτελεσματικά υδατογραφήματα εικόνας στα έγγραφά σας και να προστατεύσετε την πνευματική σας ιδιοκτησία.
## Συχνές ερωτήσεις
### Μπορώ να προσθέσω υδατογραφήματα κειμένου χρησιμοποιώντας το GroupDocs.Watermark για .NET;
Ναι, το GroupDocs.Watermark for .NET υποστηρίζει την προσθήκη υδατογραφημάτων εικόνας και κειμένου σε έγγραφα.
### Είναι το GroupDocs.Watermark για .NET συμβατό με διαφορετικές μορφές εγγράφων;
Οπωσδήποτε, το GroupDocs.Watermark για .NET υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, όπως Word, Excel, PowerPoint, PDF και άλλα.
### Το GroupDocs.Watermark για .NET παρέχει επιλογές προσαρμογής για υδατογραφήματα;
Ναι, μπορείτε να προσαρμόσετε διάφορες πτυχές του υδατογραφήματος όπως η θέση, το μέγεθος, η αδιαφάνεια και η περιστροφή.
### Μπορώ να αφαιρέσω υδατογραφήματα από έγγραφα χρησιμοποιώντας το GroupDocs.Watermark για .NET;
Ναι, το GroupDocs.Watermark για .NET προσφέρει λειτουργικότητα για τον εντοπισμό και την αφαίρεση υδατογραφημάτων από έγγραφα.
### Υπάρχει διαθέσιμη δοκιμαστική έκδοση για το GroupDocs.Watermark για .NET;
 Ναι, μπορείτε να επωφεληθείτε από μια δωρεάν δοκιμαστική έκδοση από τον ιστότοπο για να εξερευνήσετε τις δυνατότητες πριν από την αγορά[εδώ](https://releases.groupdocs.com/).