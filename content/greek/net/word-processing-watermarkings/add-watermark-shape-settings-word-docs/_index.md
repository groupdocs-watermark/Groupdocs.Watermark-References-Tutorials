---
title: Προσθήκη υδατογραφήματος με ρυθμίσεις σχήματος στα Έγγραφα του Word
linktitle: Προσθήκη υδατογραφήματος με ρυθμίσεις σχήματος στα Έγγραφα του Word
second_title: GroupDocs.Watermark .NET API
description: Μάθετε πώς να προσθέτετε υδατογραφήματα με ρυθμίσεις σχήματος σε έγγραφα του Word χρησιμοποιώντας το υδατογράφημα GroupDocs για .NET. Προστατέψτε τα έγγραφά σας αποτελεσματικά.
weight: 20
url: /el/net/word-processing-watermarkings/add-watermark-shape-settings-word-docs/
---
## Εισαγωγή
Σε αυτό το σεμινάριο, θα ακολουθήσουμε τη διαδικασία προσθήκης υδατογραφήματος με ρυθμίσεις σχήματος σε έγγραφα του Word χρησιμοποιώντας το GroupDocs.Watermark για .NET.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:
1.  Εγκατεστημένο GroupDocs.Watermark για .NET. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.groupdocs.com/Watermark/net/).
2. Βασικές γνώσεις προγραμματισμού C#.
3. Κατανόηση της επεξεργασίας εγγράφων Word.

## Εισαγωγή χώρων ονομάτων
Αρχικά, πρέπει να εισαγάγετε τους απαραίτητους χώρους ονομάτων για πρόσβαση στις απαιτούμενες κλάσεις και μεθόδους.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Βήμα 1: Φορτώστε το έγγραφο
Φορτώστε το έγγραφο του Word όπου θέλετε να προσθέσετε το υδατογράφημα.
```csharp
string documentPath = "Your Document Path";
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ο κωδικός προσθήκης υδατογραφήματος πηγαίνει εδώ
}
```
## Βήμα 2: Προσθήκη υδατογραφήματος
 Στιγμιότυπο α`TextWatermark` αντικείμενο και καθορίστε το κείμενο που θέλετε να χρησιμοποιήσετε ως υδατογράφημα.
```csharp
TextWatermark watermark = new TextWatermark("Test watermark", new Font("Arial", 19));
```
## Βήμα 3: Προσαρμόστε τις ρυθμίσεις υδατογραφήματος
Ορίστε διάφορες ρυθμίσεις για το υδατογράφημα, όπως ευθυγράμμιση, γωνία περιστροφής, χρώμα και αδιαφάνεια.
```csharp
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.RotateAngle = 25.0;
watermark.ForegroundColor = Color.Red;
watermark.Opacity = 1.0;
```
## Βήμα 4: Ορίστε τις επιλογές ενότητας υδατογραφήματος
Ορίστε επιλογές για την ενότητα υδατογραφήματος, όπως το όνομα του σχήματος και το εναλλακτικό κείμενο.
```csharp
WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
options.Name = "Shape 1";
options.AlternativeText = "Test watermark";
```
## Βήμα 5: Προσθήκη υδατογραφήματος στο έγγραφο
Προσθέστε το υδατογράφημα στο έγγραφο με τις καθορισμένες επιλογές.
```csharp
watermarker.Add(watermark, options);
```
## Βήμα 6: Αποθηκεύστε το έγγραφο
Αποθηκεύστε το έγγραφο με το προστιθέμενο υδατογράφημα.
```csharp
watermarker.Save(outputFileName);
```

## συμπέρασμα
Η προσθήκη υδατογραφημάτων με ρυθμίσεις σχήματος σε έγγραφα του Word χρησιμοποιώντας το υδατογράφημα για το .NET είναι μια απλή διαδικασία. Ακολουθώντας τα βήματα που περιγράφονται σε αυτό το σεμινάριο, μπορείτε να προστατεύσετε αποτελεσματικά τα έγγραφά σας με προσαρμοσμένα υδατογραφήματα.
## Συχνές ερωτήσεις
### Μπορώ να προσθέσω πολλά υδατογραφήματα στο ίδιο έγγραφο;
Ναι, μπορείτε να προσθέσετε πολλά υδατογραφήματα με διαφορετικές ρυθμίσεις στο ίδιο έγγραφο.
### Το GroupDocs.Watermark υποστηρίζει άλλες μορφές εγγράφων εκτός από το Word;
Ναι, το GroupDocs.Watermark υποστηρίζει διάφορες μορφές εγγράφων, όπως Excel, PowerPoint, PDF και άλλα.
### Μπορώ να προσαρμόσω περαιτέρω την εμφάνιση του υδατογραφήματος;
Οπωσδήποτε, μπορείτε να προσαρμόσετε διάφορες παραμέτρους, όπως μέγεθος γραμματοσειράς, στυλ, χρώμα και θέση για να ταιριάζουν στις ανάγκες σας.
### Υπάρχει διαθέσιμη δοκιμαστική έκδοση για το GroupDocs.Watermark για .NET;
 Ναι, μπορείτε να λάβετε δωρεάν δοκιμή από[εδώ](https://releases.groupdocs.com/).
### Πού μπορώ να βρω υποστήριξη για το GroupDocs.Watermark;
 Μπορείτε να βρείτε υποστήριξη και να κάνετε ερωτήσεις στο φόρουμ του GroupDocs[εδώ](https://forum.groupdocs.com/c/watermark/19).