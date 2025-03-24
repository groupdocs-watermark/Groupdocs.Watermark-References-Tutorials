---
title: Αντικαταστήστε το κείμενο σχήματος με μορφοποιημένο κείμενο στα Έγγραφα του Word
linktitle: Αντικαταστήστε το κείμενο σχήματος με μορφοποιημένο κείμενο στα Έγγραφα του Word
second_title: GroupDocs.Watermark .NET API
description: Μάθετε πώς να αντικαθιστάτε κείμενο σχήματος με μορφοποιημένο κείμενο σε έγγραφα Word χρησιμοποιώντας το GroupDocs.Watermark για .NET. Οι δυνατότητες επεξεργασίας εγγράφων σας χωρίς κόπο.
weight: 34
url: /el/net/word-processing-watermarkings/replace-shape-text-formatted-text-word-docs/
---
## Εισαγωγή
Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στη διαδικασία αντικατάστασης κειμένου σχήματος με μορφοποιημένο κείμενο σε έγγραφα του Word χρησιμοποιώντας το GroupDocs.Watermark για .NET. Αυτή η βιβλιοθήκη παρέχει ισχυρές δυνατότητες για εργασία με υδατογραφήματα, συμπεριλαμβανομένης της αντικατάστασης κειμένου μέσα σε σχήματα.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:
1.  GroupDocs.Watermark για .NET: Βεβαιωθείτε ότι έχετε εγκαταστήσει και ρυθμίσει το GroupDocs.Watermark για .NET. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.groupdocs.com/Watermark/net/).
2. Διαδρομή εγγράφου: Θα πρέπει να έχετε τη διαδρομή προς το έγγραφο του Word όπου θέλετε να αντικαταστήσετε το κείμενο.

## Εισαγωγή χώρων ονομάτων
Πριν γράψετε τον κώδικα, εισαγάγετε τους απαραίτητους χώρους ονομάτων:
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Βήμα 1: Φορτώστε το έγγραφο
 Φορτώστε το έγγραφο του Word χρησιμοποιώντας το`Watermarker` τάξη:
```csharp
string documentPath = "Your Document Path";
var loadOptions = new WordProcessingLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    // Ο κωδικός σας συνεχίζεται εδώ...
}
```
## Βήμα 2: Λήψη περιεχομένου και αντικατάσταση κειμένου
Μόλις φορτωθεί το έγγραφο, λάβετε το περιεχόμενο και αντικαταστήστε το κείμενο σε σχήματα:
```csharp
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
foreach (WordProcessingShape shape in content.Sections[0].Shapes)
{
    if (shape.Text.Contains("Some text"))
    {
        shape.FormattedTextFragments.Clear();
        shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
    }
}
```
## Βήμα 3: Αποθηκεύστε το έγγραφο
Αφού αντικαταστήσετε το κείμενο, αποθηκεύστε το τροποποιημένο έγγραφο:
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
watermarker.Save(outputFileName);
```

## συμπέρασμα
Η αντικατάσταση του κειμένου σχήματος με μορφοποιημένο κείμενο στα έγγραφα του Word γίνεται εύκολα με το GroupDocs για .NET. Ακολουθώντας τα βήματα που περιγράφονται σε αυτό το σεμινάριο, μπορείτε να διαχειριστείτε και να χειριστείτε αποτελεσματικά το κείμενο στα έγγραφά σας.

## Συχνές ερωτήσεις
### Μπορώ να αντικαταστήσω κείμενο σε άλλους τύπους εγγράφων χρησιμοποιώντας το GroupDocs.Watermark για .NET;
Ναι, το GroupDocs υποστηρίζει διάφορες μορφές εγγράφων όπως PDF, Excel, PowerPoint και άλλα.
### Είναι το GroupDocs.Watermark συμβατό με .NET Core;
Ναι, το GroupDocs.Watermark υποστηρίζει τόσο .NET Framework όσο και .NET Core.
### Το GroupDocs.Watermark παρέχει υποστήριξη για την προσθήκη εικόνων ως υδατογραφημάτων;
Οπωσδήποτε, το GroupDocs.Watermark σάς επιτρέπει να προσθέτετε υδατογραφήματα κειμένου και εικόνας στα έγγραφά σας.
### Μπορώ να προσαρμόσω την εμφάνιση των υδατογραφημάτων που προστέθηκαν χρησιμοποιώντας το GroupDocs.Watermark;
Ναι, έχετε τον πλήρη έλεγχο της εμφάνισης, της θέσης και άλλων ιδιοτήτων των υδατογραφημάτων.
### Υπάρχει διαθέσιμη δοκιμαστική έκδοση για το GroupDocs.Watermark για .NET;
 Ναι, μπορείτε να κάνετε λήψη μιας δωρεάν δοκιμής από[εδώ](https://releases.groupdocs.com/).