---
title: Προσθήκη υδατογραφήματος κειμένου
linktitle: Προσθήκη υδατογραφήματος κειμένου
second_title: GroupDocs.Watermark .NET API
description: Μάθετε πώς να προσθέτετε υδατογραφήματα κειμένου στα έγγραφά σας χρησιμοποιώντας το υδατογράφημα Groupdocs για .NET με αυτόν τον αναλυτικό οδηγό.
weight: 11
url: /el/net/watermarking-basics/add-text-watermark/
---
## Εισαγωγή
Το GroupDocs.Watermark for .NET είναι μια ισχυρή βιβλιοθήκη που επιτρέπει στους προγραμματιστές να προσθέτουν, να αναζητούν και να αφαιρούν υδατογραφήματα από διάφορες μορφές εγγράφων σε εφαρμογές .NET. Σε αυτό το σεμινάριο, θα επικεντρωθούμε στην προσθήκη ενός υδατογραφήματος κειμένου σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Watermark.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:
1. Βασικές γνώσεις γλώσσας προγραμματισμού C#.
2. Το Visual Studio είναι εγκατεστημένο στο σύστημά σας.
3.  Εγκαταστάθηκε το GroupDocs.Watermark για τη βιβλιοθήκη .NET. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.groupdocs.com/Watermark/net/).

## Εισαγωγή χώρων ονομάτων
Αρχικά, πρέπει να εισαγάγετε τους απαραίτητους χώρους ονομάτων στο έργο σας C#.
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Βήμα 1: Ορισμός διαδρομής εγγράφου και καταλόγου εξόδου
Καθορίστε τη διαδρομή προς το έγγραφο εισόδου και τον κατάλογο εξόδου όπου θα αποθηκευτεί το υδατογραφημένο έγγραφο.
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Αντικαθιστώ`"Your Document Path"` με την απόλυτη ή σχετική διαδρομή προς το έγγραφο εισόδου σας, για παράδειγμα:`@"C:\Docs\document.pdf"`. Επίσης, καθορίστε τον κατάλογο στον οποίο θέλετε να αποθηκεύσετε το υδατογραφημένο έγγραφο.
## Βήμα 2: Προσθήκη υδατογραφήματος κειμένου
 Στιγμιότυπο το`Watermarker` κλάση με τη διαδρομή εγγράφου εισόδου. Στη συνέχεια, δημιουργήστε ένα`TextWatermark` αντικείμενο με τις επιθυμητές ρυθμίσεις κειμένου και γραμματοσειράς.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    TextWatermark watermark = new TextWatermark("top secret", new Font("Arial", 36));
    watermark.ForegroundColor = Color.Red;
    watermark.HorizontalAlignment = HorizontalAlignment.Center;
    watermark.VerticalAlignment = VerticalAlignment.Center;
    watermarker.Add(watermark);
    watermarker.Save(outputFileName);
}
```

## συμπέρασμα
Σε αυτό το σεμινάριο, μάθαμε πώς να προσθέτουμε ένα υδατογράφημα κειμένου σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Watermark για .NET. Με το διαισθητικό API του, οι προγραμματιστές μπορούν εύκολα να χειριστούν υδατογραφήματα σε διάφορες μορφές εγγράφων.
## Συχνές ερωτήσεις
### Είναι το GroupDocs.Watermark για .NET συμβατό με όλες τις μορφές εγγράφων;
Το GroupDocs.Watermark υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, όπως PDF, Microsoft Word, Excel, PowerPoint και πολλά άλλα.
### Μπορώ να προσαρμόσω την εμφάνιση του υδατογραφήματος κειμένου;
Ναι, μπορείτε να προσαρμόσετε διάφορες ιδιότητες, όπως γραμματοσειρά, χρώμα, στοίχιση και αδιαφάνεια του υδατογραφήματος κειμένου.
### Το GroupDocs.Watermark παρέχει υποστήριξη για την αφαίρεση υδατογραφημάτων από έγγραφα;
Ναι, το GroupDocs.Watermark προσφέρει λειτουργικότητα για αναζήτηση και αφαίρεση υδατογραφημάτων από έγγραφα.
### Μπορώ να δοκιμάσω το GroupDocs.Watermark για .NET πριν το αγοράσω;
 Ναι, μπορείτε να κάνετε λήψη μιας δωρεάν δοκιμαστικής έκδοσης από[εδώ](https://releases.groupdocs.com/).
### Πώς μπορώ να λάβω τεχνική υποστήριξη για το GroupDocs.Watermark;
 Μπορείτε να λάβετε τεχνική υποστήριξη μεταβαίνοντας στο[Φόρουμ GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19).