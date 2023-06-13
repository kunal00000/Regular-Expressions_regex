# Regular-Expressions_regex

1. [Whitespaces](#whitespace)
2. [Phone Number (various formats)](#phone-numbers)
3. [Email Addresses](#email-addresses)
4. [URLs](#urls)
5. [Data Extraction](#data-extraction)
6. [Credit Card](#credit-card)

<a id="whitespace"></a>
### Whitespace
- Regex:
  ```
  \s+
  ```

<a id="phone-numbers"></a>
### Phone Numbers
- Validating phone numbers in different formats-
  - Regex pattern:
    ```
    ^(?:\+\d{1,3}\s?)?(?:\(\d{1,4}\)\s?)?(?:\d{1,4}[\s-])?\d{1,10}$
    ```
  - Example formats:
    - +1 (123) 456-7890
    - 5551234567
    - (999) 9999-9999
    - +1 5551234567
    - +1 (416) 555 7890
    - +33 123456789
    - +91 9876543210

- Normalizing phone numbers to a consistent format:

  - Regex pattern:
    ```
    ^(\+?\d{1,3}\s?)?(\(?\d{1,4}\)?\s?)?(\d{1,})[-\s]?(\d{1,})$
    ```
  - Example formats:
    - +1 (123) 456-7890 (normalizes to +11234567890)
    - 555 123 4567 (normalizes to 5551234567)
    - +55 (11) 98765-4321 (normalizes to 5511987654321)
    - +86 10 1234 5678 (normalizes to +861012345678
    - +91 98765 43210 (normalizes to +919876543210)

<a id="email-addresses"></a>
### Email Addresses
- Validating email addresses:
  - Regex pattern:
    ```
    ^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
    ```
  - Example formats:
    - john.doe@example.com
    - jane_smith123@gmail.com

- Extracting domain names from email addresses:
  - Regex pattern:
    ```
    @[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
    ```
  - Example formats:
    - john.doe@example.com (extracts example.com)
    - jane_smith123@gmail.com (extracts gmail.com)

<a id="urls"></a>
### URLs

- Validating URLs:
    - Regex pattern:
      ```
      https?:\/\/[\w.-]+\.[\w.-]+[^\s]*
      ```
    - Example formats:
      - https://www.example.com
      - http://ftp.example.com/file.txt

- Extracting different components of a URL(https://www.example.com/path/file.html?param1=value1&param2=value2):

  - Extracting protocol:
    - Regex pattern:
      ```
      ^(https?):\/\/
      ```
    - Example format:
      - https://
      - http://
  
  - Extracting domain:
    - Regex pattern:
      ```
      (https?):\/\/([a-zA-Z0-9.-]+)
      ```
    - Example format:
      - www.example.com
      - www.google.com
    
  - Extracting path:
    - Regex pattern:
      ```
      (https?):\/\/[a-zA-Z0-9.-]+(\/[^?\s]*)?
      ```
    - Example format:
      - /path/file.html
  
  - Extracting query parameters:
    - Regex pattern:
      ```
      (https?):\/\/[a-zA-Z0-9.-]+(\/[^?\s]*)?(\?[^#\s]*)?$
      ```
    - Example format:
      - ?param1=value1&param2=value2
    - Extracted Groups:
      - https
      - /path/file.html
      - ?param1=value1&param2=value2

<a id="data-extraction"></a>
### Data Extraction

- Extracting specific patterns from unstructured text:
  - To extract dates:
    ```
    (\d{1,2})\/(\d{1,2})\/(\d{4})
    ```
    - Example:
      - Extract "12/31/2023" from a text.
     
  - To extract times:
    ```
    ([01]\d|2[0-3]):([0-5]\d)
    ```
    - Example:
      - Extract "18:45" from a text.
  
  - To extract addresses:
    ```
    \d+\s[A-Za-z]+\s[A-Za-z]+,\s[A-Za-z]+\s\d+
    ```
    - Example:
      - Extract "123 Main St, New York 10001" from a text.
     
- Extracting values from structured data formats:
  - To extract values from XML:
    ```
    <(.*?)>([^<]+)<\/\1>
    ```
    - Example:
      - Extract values between XML tags, such as
      ```
      # data
      <person>
        <name>John Doe</name>
        <age>25</age>
        <email>johndoe@example.com</email>
      </person>

      # Expected  Results 
      name John Doe
      age 25
      email johndoe@example.com
      ```

<a id="credit-card"></a>
### Credit Card
- Validating credit card numbers:
  - Regex Pattern: 
    ```
    ^(?:\d{4}[ -]?){3}\d{4}$
    ```
    - Example Credit Card Numbers:
      - 4111 1111 1111 1111
      - 5555-5555-5555-4444
      - 3782822463100058

- Extracting credit card expiration dates:
  - Regex Pattern:
    ```
    (?:0[1-9]|1[0-2])\/20[2-9][0-9]
    ```
    - Example Expiration Dates:
      - 12/2023
      - 05/2025
      - 09/2030

- Matching CVV (Card Verification Value) codes:
  - Regex Pattern:
    ```
    ^\d{3,4}$
    ```
    - Example CVV Codes:
      - 123
      - 7890
      - 4321
