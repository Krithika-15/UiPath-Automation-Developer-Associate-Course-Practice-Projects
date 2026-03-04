# Email Address Extraction Bot

This UiPath project demonstrates **two different ways to extract an email address from a sentence** using **basic string methods**.  
Both approaches are built as separate sequences and are invoked from the **Main.xaml** to showcase multiple solutions.

---

## 📌 Inputs Used
- Please use the following address to contact me hemma.watson@localcompany.com on the company email. (for Approach 1)
- Please use the following address to contact me john.doe@localcompany.com on the company email. (for Approach 2)

---

## 🧠 What This Project Covers
- String handling in UiPath using **Assign** activities
- Using **IndexOf** and **Substring** to extract specific text
- Validation using **If** condition (email exists or not)
- Modular design using **2 sequences** + **Invoke Workflow File**
- Printing final output using **Log Message**

---

## 📂 Project Structure
- **Main.xaml**
  - Invokes both extraction workflows (Way 1 and Way 2)

- **EmailExtractingUsing@.xaml**
  - Extracts email by locating the `@` symbol and slicing around it

- **EmailExtractionUsingWords.xaml**
  - Extracts email using start/end keywords like `"me "` and `" on"` 

---

## ✅ Approach 1 – Find “@” and Extract Email
**Logic**
1. Store the input sentence in a variable (e.g., `InputData`)
2. Find the position of `@` using:
   - `InputData.IndexOf("@")`
3. Use an **If** condition:
   - If index is `-1` → `@` not found → log “No email found”
   - Else → Extract the email (using substring logic around `@`)
4. Log the extracted email

**Key Activities / Methods**
- Assign
- `IndexOf()`
- If
- Substring
- Log Message

---

## ✅ Approach 2 – Use Start Keyword and End Keyword 
**Logic**
1. `StartIndex = InputData.IndexOf("me ") + "me ".Length`
   - Starts extraction right after the word **"me "**
2. `EndIndex = InputData.IndexOf(" on")`
   - Stops extraction before the word **" on"**
3. `EmailAddress = InputData.Substring(StartIndex, EndIndex - StartIndex)`
4. Log the extracted email

**Why it works**
- The email is positioned between known words:
  - **me [email] on**
- So we can reliably slice the email part using start & end indexes.

**Key Activities / Methods**
- Assign
- `IndexOf()`
- `Substring(startIndex, length)`
- Log Message

---

## ▶️ How to Run
1. Open the project in **UiPath Studio**
2. Run **Main.xaml**
3. Output will be visible in the **Output panel** as log messages

---

## 🛠 Skills Demonstrated
- String manipulation using `.NET` methods inside UiPath
- Index calculation using `IndexOf`
- Text extraction using `Substring`
- Workflow modularization using **Invoke Workflow File**
- Debug-friendly output using **Log Message**

---

## 📌 Output Example
- hemma.watson@localcompany.com
- john.doe@localcompany.com


---

## 🔖 Notes
- Approach 2 depends on the sentence containing `"me "` and `" on"` exactly.
- For dynamic/unpredictable text, Approach 1 (or Regex) is usually more flexible.

---