---
title: Προσθήκη υδατογραφήματος σε τεχνουργήματα εικόνας σε PDF
linktitle: Προσθήκη υδατογραφήματος σε τεχνουργήματα εικόνας σε PDF
second_title: GroupDocs.Watermark .NET API
description: Προστατέψτε τα αρχεία PDF σας με εξατομικευμένα υδατογραφήματα χρησιμοποιώντας το GroupDocs.Watermark για .NET. Προσθέστε εύκολα υδατογραφήματα κειμένου ή εικόνας σε τεχνουργήματα εικόνας σε έγγραφα PDF.
type: docs
weight: 18
url: /el/net/pdf-watermarking-attachments/add-watermark-image-artifacts-pdf/
---
## Εισαγωγή
Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στη διαδικασία προσθήκης υδατογραφήματος σε τεχνουργήματα εικόνας σε ένα έγγραφο PDF χρησιμοποιώντας το GroupDocs.Watermark για .NET. Ακολουθώντας αυτά τα βήματα, μπορείτε να προστατεύσετε αποτελεσματικά τα αρχεία PDF σας με εξατομικευμένα υδατογραφήματα.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:
1.  GroupDocs.Watermark για .NET: Λήψη και εγκατάσταση της βιβλιοθήκης GroupDocs.Watermark για .NET από[εδώ](https://releases.groupdocs.com/Watermark/net/).
2. Διαδρομή εγγράφου: Έχετε τη διαδρομή προς το έγγραφο PDF όπου θέλετε να προσθέσετε το υδατογράφημα.
3. Κατάλογος εξόδου: Δημιουργήστε έναν κατάλογο όπου θα αποθηκευτεί το υδατογραφημένο έγγραφο.

## Εισαγωγή χώρων ονομάτων
```csharp
using GroupDocs.Watermark.Common;
using GroupDocs.Watermark.Contents.Pdf;
using GroupDocs.Watermark.Options.Pdf;
using GroupDocs.Watermark.Watermarks;
using System.IO;
using System;
```
## Βήμα 1: Φορτώστε το έγγραφο και αρχικοποιήστε τον υδατοσήμανση
```csharp
string documentPath = "Your Document Path";
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, Path.GetFileName(documentPath));
var loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker(documentPath, loadOptions))
{
```
## Βήμα 2: Λάβετε περιεχόμενο PDF και προσθέστε υδατογράφημα
```csharp
	PdfContent pdfContent = watermarker.GetContent<PdfContent>();
	// Αρχικοποίηση υδατογραφήματος εικόνας ή κειμένου
	TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));
	watermark.HorizontalAlignment = HorizontalAlignment.Center;
	watermark.VerticalAlignment = VerticalAlignment.Center;
	watermark.RotateAngle = 45;
	watermark.SizingType = SizingType.ScaleToParentDimensions;
	watermark.ScaleFactor = 1;
	foreach (PdfPage page in pdfContent.Pages)
	{
		foreach (PdfArtifact artifact in page.Artifacts)
		{
			if (artifact.Image != null)
			{
				// Προσθέστε υδατογράφημα στην εικόνα
				artifact.Image.Add(watermark);
			}
		}
	}
```
## Βήμα 3: Αποθηκεύστε το υδατογραφημένο έγγραφο
```csharp
	watermarker.Save(outputFileName);
}
```

## συμπέρασμα
Με το GroupDocs.Watermark για .NET, η προσθήκη υδατογραφημάτων σε τεχνουργήματα εικόνας σε έγγραφα PDF γίνεται μια απρόσκοπτη διαδικασία. Ακολουθώντας αυτό το σεμινάριο, μπορείτε να προστατεύσετε αποτελεσματικά τα αρχεία PDF σας με προσαρμοσμένα υδατογραφήματα, διασφαλίζοντας την ασφάλεια και την αυθεντικότητά τους.
## Συχνές ερωτήσεις
### Μπορώ να προσθέσω υδατογραφήματα εικόνας και κειμένου στο έγγραφο PDF μου;
Ναι, το GroupDocs.Watermark για .NET υποστηρίζει την ταυτόχρονη προσθήκη υδατογραφημάτων εικόνας και κειμένου.
### Υπάρχει κάποιος περιορισμός στον αριθμό των υδατογραφημάτων που μπορώ να προσθέσω σε ένα έγγραφο;
Όχι, μπορείτε να προσθέσετε πολλά υδατογραφήματα σε ένα έγγραφο χωρίς περιορισμούς.
### Μπορώ να προσαρμόσω την εμφάνιση και τη θέση του υδατογραφήματος;
Απολύτως, έχετε τον πλήρη έλεγχο της εμφάνισης, της θέσης και των ιδιοτήτων του υδατογραφήματος.
### Το GroupDocs.Watermark για .NET υποστηρίζει άλλες μορφές εγγράφων εκτός από το PDF;
Ναι, υποστηρίζει διάφορες μορφές εγγράφων, όπως Word, Excel, PowerPoint και άλλα.
### Υπάρχει τρόπος να αφαιρέσω τα υδατογραφήματα από ένα έγγραφο;
Ναι, το GroupDocs.Watermark for .NET παρέχει μεθόδους αφαίρεσης υδατογραφημάτων από έγγραφα, εάν χρειάζεται.