# Exercise-13-Invoice-Processing-automation-using-OCR
## Date: 20.03.2025
### Name : Thamizh.S
### Reg number : 212224040350
The aim of this project is to automate the process of extracting information from invoices using OCR, reducing manual data entry and enhancing operational efficiency. The automation will extract the following details:
- **Invoice Number**
- **Invoice Date**
- **Total Amount**
---

##  **Step-by-Step Procedure for Invoice Processing Using OCR in UiPath**

### **Step 1: Install UiPath and Required Packages**
1. **Download and Install UiPath Studio** if you haven't already.
2. **Create a New Project**:
   - Open UiPath Studio.
   - Create a new "Process" project and name it (e.g., **InvoiceProcessing**).
3. **Install Packages**:
   - Go to "Manage Packages".
   - Install the following:
     - **UiPath.PDF.Activities** (for PDF handling).
     - **UiPath.IntelligentOCR.Activities** (for OCR capabilities).
     - **UiPath.Excel.Activities** (for working with Excel).

---

### **Step 2: Read the PDF Invoice with OCR**
1. **Add the "Read PDF with OCR" Activity**:
   - In the Activities Panel, search for **"Read PDF with OCR"**.
   - Drag and drop this activity into your workflow.
2. **Set PDF File Path**:
   - In the **Properties Panel**, set the "FileName" property to the path of your invoice PDF. 
   - You can use "Select File" to browse to the PDF file.
3. **Add OCR Engine**:
   - Drag and drop an OCR Engine (like **Tesseract OCR** or **Microsoft OCR**) into the "OCR Engine" property of the "Read PDF with OCR" activity.
   - **Tesseract OCR** is recommended for beginners as it's easy to set up.

---

### **Step 3: Extract Text from PDF**
1. **Store the Extracted Text**:
   - Create a variable to store the extracted text. For example, name it `invoiceText`.
   - In the **"Output"** property of the "Read PDF with OCR" activity, set the variable to `invoiceText`. This will hold all the text extracted from the invoice.

---

### **Step 4: Extract Specific Data (Invoice Number, Date, Amount)**
1. **Use the "Matches" Activity for Data Extraction**:
   - Search for **"Matches"** in the Activities Panel.
   - Drag this activity to your workflow.
   - Set the "Input" property to the `invoiceText` variable.
2. **Add Regex Patterns for Each Data Type**:
   - **Invoice Number**: For invoice numbers in the format **INV-12345**, use the regex pattern: 
     ```regex
     INV-\d+
     ```
   - **Date**: For dates in the format **DD/MM/YYYY**, use the regex pattern:
     ```regex
     \d{2}/\d{2}/\d{4}
     ```
   - **Amount**: To extract the total amount, use the regex pattern:
     ```regex
     \$?\d+(,\d{3})*(\.\d{2})?
     ```
3. **Store the Extracted Matches**:
   - The output of the "Matches" activity will be a collection of matches.
   - Store these in separate variables like `invoiceNumber`, `invoiceDate`, and `totalAmount`.

---

### **Step 5: Write Extracted Data to Excel**
1. **Add the "Excel Application Scope" Activity**:
   - In the Activities Panel, search for **"Excel Application Scope"**.
   - Drag and drop this activity into your workflow.
   - Set the "File Path" to the location where you want to store the data.
   - If the file doesn't exist yet, provide a new name and let UiPath create the file.
2. **Write Data to Excel Using the "Write Cell" Activity**:
   - Inside the **"Excel Application Scope"**, use the **"Write Cell"** activity to write extracted data to the Excel sheet.
   - Example:
     - For Invoice Number: Write `invoiceNumber` to cell **A2**.
     - For Date: Write `invoiceDate` to cell **B2**.
     - For Total Amount: Write `totalAmount` to cell **C2**.

---

### **Step 6: Add Error Handling (Optional)**
1. **Add "Try Catch" Activity**:
   - Search for **"Try Catch"** in the Activities Panel.
   - Wrap all activities inside a **"Try Catch"** block to handle errors, like if the file cannot be found or if OCR fails to extract text.

---

### **Step 7: Test the Workflow**
1. **Run the Automation**:
   - Click the **"Run"** button to test the workflow.
   - Verify that the correct data is being extracted from the invoice and stored in the Excel file.

---

### **Step 8: Review and Adjust**
1. **Check the Output**:
   - Open the Excel file and ensure that the data (Invoice Number, Date, and Amount) is being correctly captured.
2. **Adjust OCR Settings if Needed**:
   - If the output is incorrect, try adjusting the OCR settings (e.g., change scale to 1.5 or 2.0).
   - You can also try switching OCR engines to improve accuracy.
---


### CODE:
---
### OUTPUT:

