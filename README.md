# IronBarcode C# Barcode Image Generator Tutorial in C#

## IronBarcode Features and Compatiblity

IronBarcode easily handles all these features:
- Read single or multiple Barcodes and QR Codes from images or PDFs.
- Image correction for skewing, orientation, noise, low resolution, contrast etc.
- Create barcodes and apply to images or PDF documents.
- Embed barcodes into HTML documents.
- Style Barcodes and add annotation text.
- QR Code Writing allows adding of logos, colors, and advanced QR alignment.

IronBarcode also has cross platform support compatibility with:
- .NET 6 and .NET 5, .NET Core, Standard, and Framework
- Windows, macOS, Linux, Docker, Azure, and AWS

Get Started creating, reading, and editing Barcodes and QR Codes with IronBarcode in C# now! https://github.com/iron-software

## Code Example:

```csharp
using IronBarCode;

// Get a free license key instantly: https://ironsoftware.com/csharp/barcode/#trial-license
IronBarCode.License.LicenseKey = "ENTER-KEY-HERE";

// Creating a barcode is as simple as:
var myBarcode = BarcodeWriter.CreateBarcode("12345", BarcodeWriterEncoding.EAN8);

// And save our barcode as in image:
myBarcode.SaveAsImage("EAN8.jpeg");

// Reading a barcode is easy with IronBarcode:
var resultFromFile = BarcodeReader.Read(@"file/barcode.png"); // From a file
var resultFromPdf = BarcodeReader.ReadPdf(@"file/mydocument.pdf"); // From PDF use ReadPdf

// After creating a barcode, we may choose to resize and save which is easily done with:
var myNewBarcode = BarcodeWriter.CreateBarcode("12345", BarcodeWriterEncoding.EAN8);
myNewBarcode.ResizeTo(400, 100);
myNewBarcode.SaveAsImage("myBarcodeResized.jpeg");

// To set more options and optimization with your Barcode Reading,
// Please utilize the BarcodeReaderOptions parameter of read:
BarcodeReaderOptions myOptionsExample = new BarcodeReaderOptions()
{
    // Choose a speed from: Faster, Balanced, Detailed, ExtremeDetail
    // There is a tradeoff in performance as more Detail is set
    Speed = ReadingSpeed.Balanced,
    // Reader will stop scanning once a barcode is found, unless set to true
    ExpectMultipleBarcodes = true,
    // By default, all barcode formats are scanned for.
    // Specifying one or more, performance will increase.
    ExpectBarcodeTypes = BarcodeEncoding.AllOneDimensional,
    // Utilizes multiple threads to reads barcodes from multiple images in parallel.
    Multithreaded = true,
    // Maximum threads for parallel. Default is 4
    MaxParallelThreads = 2,
    // The area of each image frame in which to scan for barcodes.
    // Will improve perfornace significantly and avoid unwanted results and avoid noisy parts of the image.
    CropArea = new System.Drawing.Rectangle(),
    // Special Setting for Code39 Barcodes.
    // If a Code39 barcode is detected. Try to use extended mode for the full ASCII Character Set
    UseCode39ExtendedMode = true
};
// And, apply:
var results = BarcodeReader.Read("barcode.png", myOptionsExample);
```
