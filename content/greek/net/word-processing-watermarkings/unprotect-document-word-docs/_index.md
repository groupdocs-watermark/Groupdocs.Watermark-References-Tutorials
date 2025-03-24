---
title: Κατάργηση προστασίας εγγράφου στα Έγγραφα του Word
linktitle: Κατάργηση προστασίας εγγράφου στα Έγγραφα του Word
second_title: GroupDocs.Watermark .NET API
description: Μάθετε πώς να καταργείτε εύκολα τα έγγραφα του Word χρησιμοποιώντας το GroupDocs.Watermark για .NET. Ακολουθήστε τον βήμα προς βήμα οδηγό μας.
weight: 38
url: /el/net/word-processing-watermarkings/unprotect-document-word-docs/
---
## Εισαγωγή
Το GroupDocs.Watermark για .NET είναι ένα ισχυρό API που επιτρέπει στους προγραμματιστές να εργάζονται με υδατογραφήματα σε διάφορες μορφές εγγράφων, συμπεριλαμβανομένων των εγγράφων του Word. Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στη διαδικασία κατάργησης προστασίας ενός εγγράφου του Word χρησιμοποιώντας το GroupDocs.Watermark για .NET. Είτε είστε έμπειρος προγραμματιστής είτε μόλις ξεκινάτε με την ανάπτυξη .NET, αυτός ο οδηγός βήμα προς βήμα θα σας βοηθήσει να ολοκληρώσετε την εργασία αποτελεσματικά.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:
1.  GroupDocs.Watermark για .NET: Πρέπει να έχετε εγκατεστημένο το GroupDocs.Watermark για .NET API στο περιβάλλον ανάπτυξης σας. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.groupdocs.com/Watermark/net/).
2. Περιβάλλον ανάπτυξης: Βεβαιωθείτε ότι έχετε ρυθμίσει ένα κατάλληλο περιβάλλον ανάπτυξης για την ανάπτυξη .NET, συμπεριλαμβανομένου του Visual Studio ή οποιουδήποτε άλλου συμβατού IDE.
3. Έγγραφο Word: Έχετε έτοιμο στο σύστημα αρχείων σας ένα έγγραφο του Word που θέλετε να καταργήσετε την προστασία.

## Εισαγωγή χώρων ονομάτων
Πριν βουτήξετε στον κώδικα, πρέπει να εισαγάγετε τους απαραίτητους χώρους ονομάτων στο έργο σας .NET. Αυτό σας επιτρέπει να έχετε απρόσκοπτη πρόσβαση στις λειτουργίες που παρέχονται από το GroupDocs.Watermark για .NET.
```csharp
using GroupDocs.Watermark.Contents.WordProcessing;
using GroupDocs.Watermark.Options.WordProcessing;
using System.IO;
using System;
```
## Βήμα 1: Καθορίστε τη διαδρομή εγγράφου
Καθορίστε τη διαδρομή προς το έγγραφο του Word που θέλετε να καταργήσετε την προστασία.
```csharp
string documentPath = "Your Document Path";
```
 Αντικαθιστώ`"Your Document Path"` με την πραγματική διαδρομή προς το έγγραφο του Word.
## Βήμα 2: Ορισμός ονόματος αρχείου εξόδου
Καθορίστε τον κατάλογο όπου θέλετε να αποθηκεύσετε το μη προστατευμένο έγγραφο και δώστε ένα όνομα για το αρχείο εξόδου.
```csharp
string outputFileName = Path.Combine("Your Document Directory", Path.GetFileName(documentPath));
```
 Αντικαθιστώ`"Your Document Directory"` με τη διαδρομή καταλόγου όπου θέλετε να αποθηκεύσετε το αρχείο εξόδου.
## Βήμα 3: Φόρτωση εγγράφου με επιλογές
 Δημιουργήστε ένα παράδειγμα του`WordProcessingLoadOptions` για να φορτώσετε το έγγραφο του Word με συγκεκριμένες επιλογές.
```csharp
var loadOptions = new WordProcessingLoadOptions();
```
## Βήμα 4: Καταργήστε την προστασία του εγγράφου
 Στιγμιότυπο το`Watermarker` κλάση με τις επιλογές διαδρομής εγγράφου και φόρτωσης. Στη συνέχεια, λάβετε το περιεχόμενο του εγγράφου ως WordProcessingContent και καταργήστε την προστασία του.
```csharp
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
    WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
    content.Unprotect();
    watermarker.Save(outputFileName);
}
```

## συμπέρασμα
Ακολουθώντας αυτά τα βήματα, μπορείτε εύκολα να καταργήσετε την προστασία ενός εγγράφου του Word χρησιμοποιώντας το GroupDocs.Watermark για .NET. Αυτό το API παρέχει έναν απλό τρόπο χειρισμού υδατογραφημάτων και αποτελεσματικής προστασίας των εγγράφων σας.
## Συχνές ερωτήσεις
### Είναι το GroupDocs.Watermark για .NET συμβατό με όλες τις εκδόσεις του .NET;
Ναι, το GroupDocs.Watermark για .NET είναι συμβατό με .NET Framework 2.0 και νεότερες εκδόσεις, συμπεριλαμβανομένων των .NET Core και .NET Standard.
### Μπορώ να εφαρμόσω υδατογραφήματα σε έγγραφα σε άλλες μορφές εκτός από το Word;
Απολύτως! Το GroupDocs.Watermark για .NET υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, συμπεριλαμβανομένων των PDF, Excel, PowerPoint και άλλων.
### Υπάρχει διαθέσιμη δοκιμαστική έκδοση για το GroupDocs.Watermark για .NET;
 Ναι, μπορείτε να λάβετε μια δωρεάν δοκιμαστική έκδοση από[εδώ](https://releases.groupdocs.com/).
### Πώς μπορώ να λάβω τεχνική υποστήριξη για το GroupDocs.Watermark για .NET;
 Μπορείτε να επισκεφθείτε το[Φόρουμ GroupDocs.Watermark](https://forum.groupdocs.com/c/watermark/19) για τεχνική βοήθεια και κοινοτική υποστήριξη.
### Μπορώ να αγοράσω μια προσωρινή άδεια χρήσης για το GroupDocs.Watermark για .NET;
 Ναι, μπορείτε να αγοράσετε μια προσωρινή άδεια από[εδώ](https://purchase.groupdocs.com/temporary-license/).