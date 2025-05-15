# Aim:
To extract key information such as Invoice Number, Invoice Date, and Due Date from scanned invoice PDFs by applying OCR and Regex techniques, and to store the extracted data in an Excel file using UiPath automation.

# Software Required:
```
1.UiPath Studio – For designing and running automation workflows.
2.PDF Reader or Scanner – To read invoice PDFs.
3.Microsoft Excel – To store extracted data.
4.OCR Engine (e.g., UiPath OCR activities, Google OCR, Microsoft OCR) – To convert scanned PDF images to text.
```

# Procedure:
# 1.Read PDF using OCR:
    Use UiPath’s Read PDF with OCR activity to extract the invoice text and store it in a variable (pdfText).
# 2.Extract Data using Regex:
    Use Assign activities with Regular Expressions to extract:
              invoiceNumber from the text pattern near "Invoice Number"
              invoiceDate from the text pattern near "Invoice Date"
              dueDate from the text pattern near "Due Date"
              Example Regex Assign it using assign activity:
                 invoiceNumber = System.Text.RegularExpressions.Regex.Match(pdfText, "Invoice Number[:\s]*([A-Za-z0-9\-]+)").Groups(1).Value
                 invoiceDate = System.Text.RegularExpressions.Regex.Match(pdfText, "Invoice Date[:\s]*([0-9\/\-]+)").Groups(1).Value
                 dueDate = System.Text.RegularExpressions.Regex.Match(pdfText, "Due Date[:\s]*([0-9\/\-]+)").Groups(1).Value
# 3.Build Data Table:
    Use Build Data Table activity to create a table with columns: InvoiceNumber, InvoiceDate, DueDate.
# 4.Add Data Row:
    Use Add Data Row activity to add the extracted values {invoiceNumber, invoiceDate, dueDate} into the DataTable.
# 5.Write Data to Excel:
    Use Write Range activity to save the DataTable into an Excel file with headers.

# Workflow:
![Screenshot 2025-05-15 175832](https://github.com/user-attachments/assets/ec009a24-f1cb-4e95-811c-4911f9fd4faf)
![Screenshot 2025-05-15 175845](https://github.com/user-attachments/assets/b158ec0c-7d86-4845-937d-04df015e20ad)
![Screenshot 2025-05-15 175850](https://github.com/user-attachments/assets/727e86f6-ff9e-40e2-96e0-2b0f4ecd08ee)

# Output:
![Screenshot 2025-05-15 175808](https://github.com/user-attachments/assets/31e5465e-8207-42a3-8565-e9c335db3a5a)
![Screenshot 2025-05-15 175744](https://github.com/user-attachments/assets/cf93c01f-0e94-419b-a8fc-8821d20df5b7)

# Result:
```
1.Successfully extracted Invoice Number, Invoice Date, and Due Date from scanned invoice PDFs.
2.Extracted data stored accurately in Excel in tabular format with columns matching the extracted fields.
3.The automation reduces manual data entry and increases data processing speed and accuracy.
```




