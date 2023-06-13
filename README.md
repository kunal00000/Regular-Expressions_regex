# Regular-Expressions_regex

1. [Whitespaces](#whitespace)
2. [Phone Number (various formats)](#phone-numbers)
  1. [Validating phone numbers in various formats](#validate-phone)
  2. [Normalizing phone numbers to a consistent format:](#normalise-phone)
3. [Email Addresses](#email-addresses)
  1. [Validating email addresses:](#validate-email)
  2. [Extracting domain names from email addresses:](#extract-domain)
4. [URLs](#urls)
  1. [Validating URLs:](#validate-url)
  2. [Extract Protocol](#extract-protocol)
  3. [Extract Domain](#extract-domain)
  4. [Extract Path](#extract-path)
  5. [Extract Query Parameters](#extract-params)
5. [Data Extraction](#data-extraction)
  1. [To extract dates:](#extract-dates)
  2. [To extract time:](#extract-times)
  3. [To extract address:](#extract-address)
  4. [To extract values from XML:](#extract-xml)
6. [Credit Card](#credit-card)
  1. [Validating credit card numbers:](#validate-credit)
  2. [Extracting credit card expiration dates:](#extract-expiry-date)
  3. [Matching CVV (Card Verification Value) codes:](#extract-cvv) 

<a id="whitespace"></a>
### Whitespace
- Regex:
  ```
  \s+
  ```

<a id="phone-numbers"></a>
### Phone Numbers
<a id="validate-phone"></a>
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
    - 
<a id="normalise-phone"></a>
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
<a id="validate-email"></a>
- Validating email addresses:
  - Regex pattern:
    ```
    ^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
    ```
  - Example formats:
    - john.doe@example.com
    - jane_smith123@gmail.com
<a id="extract-domain"></a>
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
<a id="validate-url"></a>
- Validating URLs:
    - Regex pattern:
      ```
      https?:\/\/[\w.-]+\.[\w.-]+[^\s]*
      ```
    - Example formats:
      - https://www.example.com
      - http://ftp.example.com/file.txt

<a id="extract-comp"></a>
- Extracting different components of a URL(https://www.example.com/path/file.html?param1=value1&param2=value2):
<a id="extract-protocol"></a>
  - Extracting protocol:
    - Regex pattern:
      ```
      ^(https?):\/\/
      ```
    - Example format:
      - https://
      - http://
  <a id="extract-domain"></a>
  - Extracting domain:
    - Regex pattern:
      ```
      (https?):\/\/([a-zA-Z0-9.-]+)
      ```
    - Example format:
      - www.example.com
      - www.google.com
  <a id="extract-path"></a>
  - Extracting path:
    - Regex pattern:
      ```
      (https?):\/\/[a-zA-Z0-9.-]+(\/[^?\s]*)?
      ```
    - Example format:
      - /path/file.html
  <a id="extract-params"></a>
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
<a id="extract-dates"></a>
  - To extract dates:
    ```
    (\d{1,2})\/(\d{1,2})\/(\d{4})
    ```
    - Example:
      - Extract "12/31/2023" from a text.
  <a id="extract-times"></a>
  - To extract times:
    ```
    ([01]\d|2[0-3]):([0-5]\d)
    ```
    - Example:
      - Extract "18:45" from a text.
  <a id="extract-address"></a>
  - To extract addresses:
    ```
    \d+\s[A-Za-z]+\s[A-Za-z]+,\s[A-Za-z]+\s\d+
    ```
    - Example:
      - Extract "123 Main St, New York 10001" from a text.
     
- Extracting values from structured data formats:
  <a id="extract-xml"></a>
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
<a id="validate-credit"></a>
- Validating credit card numbers:
  - Regex Pattern: 
    ```
    ^(?:\d{4}[ -]?){3}\d{4}$
    ```
    - Example Credit Card Numbers:
      - 4111 1111 1111 1111
      - 5555-5555-5555-4444
      - 3782822463100058
<a id="extract-expiry-date"></a>
- Extracting credit card expiration dates:
  - Regex Pattern:
    ```
    (?:0[1-9]|1[0-2])\/20[2-9][0-9]
    ```
    - Example Expiration Dates:
      - 12/2023
      - 05/2025
      - 09/2030
<a id="extract-cvv"></a>
- Matching CVV (Card Verification Value) codes:
  - Regex Pattern:
    ```
    ^\d{3,4}$
    ```
    - Example CVV Codes:
      - 123
      - 7890
      - 4321
