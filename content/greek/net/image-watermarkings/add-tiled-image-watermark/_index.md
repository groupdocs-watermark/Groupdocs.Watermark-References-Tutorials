---
title: Προσθήκη υδατογραφήματος εικόνας με πλακάκια
linktitle: Προσθήκη υδατογραφήματος εικόνας με πλακάκια
second_title: GroupDocs.Watermark .NET API
description: Μάθετε πώς να προσθέτετε υδατογραφήματα εικόνων με πλακάκια στα έγγραφά σας χρησιμοποιώντας το GroupDocs.Watermark για .NET. Εύκολο, αποτελεσματικό και προσαρμόσιμο.
weight: 10
url: /el/net/image-watermarkings/add-tiled-image-watermark/
type: docs
---
# Προσθήκη υδατογραφήματος εικόνας με πλακάκια

## Εισαγωγή
Το GroupDocs.Watermark for .NET είναι ένα ισχυρό API που επιτρέπει στους προγραμματιστές να προσθέτουν, να αφαιρούν και να αναζητούν υδατογραφήματα σε διάφορες μορφές εγγράφων μέσω προγραμματισμού. Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στη διαδικασία προσθήκης υδατογραφήματος εικόνας με πλακάκια στα έγγραφά σας χρησιμοποιώντας το GroupDocs.Watermark για .NET.
## Προαπαιτούμενα
Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε τα εξής:
- Βασικές γνώσεις γλώσσας προγραμματισμού C#.
- Το Visual Studio είναι εγκατεστημένο στο σύστημά σας.
- GroupDocs.Watermark για τη βιβλιοθήκη .NET προστέθηκε στο έργο σας. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.groupdocs.com/Watermark/net/).

## Εισαγωγή χώρων ονομάτων
Βεβαιωθείτε ότι έχετε εισαγάγει τους απαραίτητους χώρους ονομάτων στην αρχή του αρχείου C#:
```csharp
using GroupDocs.Watermark.Watermarks;
using System;
using System.IO;
```
## Βήμα 1: Ορισμός διαδρομής εγγράφου και καταλόγου εξόδου
Καθορίστε τη διαδρομή του εγγράφου εισόδου και τον κατάλογο όπου θέλετε να αποθηκεύσετε το έγγραφο εξόδου:
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
```
 Αντικαθιστώ`"Your Document Path"` με την απόλυτη ή σχετική διαδρομή προς το έγγραφο εισόδου σας.
## Βήμα 2: Αρχικοποίηση αντικειμένου Watermarker
Δημιουργήστε ένα αντικείμενο Watermarker χρησιμοποιώντας τη διαδρομή εγγράφου εισόδου:
```csharp
using (Watermarker watermarker = new Watermarker(documentPath))
{
    // Προσθέστε υδατογράφημα εδώ
}
```
## Βήμα 3: Προσθήκη υδατογραφήματος με πλακάκια εικόνας
Δημιουργήστε ένα αντικείμενο ImageWatermark με τη διαδρομή προς το αρχείο εικόνας που θέλετε να χρησιμοποιήσετε ως υδατογράφημα:
```csharp
using (ImageWatermark watermark = new ImageWatermark("Path to Your Image"))
{
    // Διαμόρφωση επιλογών πλακιδίων
    watermark.TileOptions = new TileOptions()
    {
        TileType = TileType.Offset,
        LineSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 12
        },
        WatermarkSpacing = new MeasureValue()
        {
            MeasureType = TileMeasureType.Percent,
            Value = 10
        },
    };
    watermark.RotateAngle = -30;
    // Προσθέστε υδατογράφημα στο έγγραφο
    watermarker.Add(watermark);
    // Αποθηκεύστε το τροποποιημένο έγγραφο
    watermarker.Save(outputFileName);
}
```
 Αντικαθιστώ`"Path to Your Image"` με την πραγματική διαδρομή προς το αρχείο εικόνας υδατογραφήματος.

## συμπέρασμα
Ακολουθώντας αυτά τα βήματα, μπορείτε εύκολα να προσθέσετε ένα υδατογράφημα εικόνας με πλακάκια στα έγγραφά σας χρησιμοποιώντας το GroupDocs.Watermark για .NET. Πειραματιστείτε με διαφορετικές επιλογές και διαμορφώσεις για να επιτύχετε το επιθυμητό αποτέλεσμα.
## Συχνές ερωτήσεις
### Μπορώ να προσθέσω πολλά υδατογραφήματα σε ένα μόνο έγγραφο;
Ναι, μπορείτε να προσθέσετε πολλά υδατογραφήματα διαφορετικών τύπων σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Watermark για .NET.
### Το GroupDocs.Watermark υποστηρίζει όλες τις μορφές εγγράφων;
Το GroupDocs.Watermark υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, συμπεριλαμβανομένων των PDF, Word, Excel, PowerPoint και πολλών άλλων.
### Υπάρχει διαθέσιμη δοκιμαστική έκδοση για το GroupDocs.Watermark;
 Ναι, μπορείτε να κάνετε λήψη μιας δωρεάν δοκιμαστικής έκδοσης από[εδώ](https://releases.groupdocs.com/).
### Μπορώ να προσαρμόσω την εμφάνιση του υδατογραφήματος;
Ναι, μπορείτε να προσαρμόσετε διάφορες πτυχές του υδατογραφήματος, όπως θέση, μέγεθος, περιστροφή, διαφάνεια κ.λπ.
### Το GroupDocs.Watermark προσφέρει τεχνική υποστήριξη;
 Ναι, μπορείτε να λάβετε τεχνική υποστήριξη από το φόρουμ GroupDocs.Watermark[εδώ](https://forum.groupdocs.com/c/watermark/19).