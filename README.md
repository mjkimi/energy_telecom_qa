<h1 align="center">Energy-Telecom Web App <img src="https://github.com/blackcater/blackcater/raw/main/images/Hi.gif" height="32"/></h1> 
<h2 align="center"><a href="#test_cases" style="color: #04AA6D">->Test Cases</a> & <a href="#bug_reports" style="color: #f44336">->Bug Reports</a></h2>
  
#### External links:

:paperclip: <a href="http://www.energy-telecom.portnov.com/qa/" target="_blank">To the project</a>

:orange_book: <a href="https://online.portnov.net/energy-telecom-reqs/" target="_blank">Product Requirements</a>

---

<h3 style="color: #04AA6D"><a id="test_cases">:pencil2: Test Cases</a></h3>

> **_#1: Input field "First Name:"_**

<details open>
  <summary>Requirements</summary>

- [x] text field
- [x] accepts all characters
- [x] no more than 31 [Max = 31 chars]
- [x] required field.

</details>

| ID  | Purpose/Title          | Instruction                | Expected Result                 |
| --- | ---------------------- | -------------------------- | ------------------------------- |
| 1   | Accepts all characters | First name = 10 John\_!@#$ | accepted                        |
| 2   | input Max              | 31 characters              | accepted                        |
| 3   | input Max+1            | 32 characters              | accepted 31 chars               |
| 4   | Required field         | ""                         | rejected + "required field" msg |
| 5   | Lower boundary, 1 char | First name = f             | accepted                        |

> **_#2: Input field "Last Name:"_**

<details>
  <summary>Requirements</summary>

- [x] text field
- [x] accepts all characters
- [x] no more than 31 [Max = 31 chars]
- [x] required field.

</details>

| ID  | Purpose/Title          | Instruction              | Expected Result                 |
| --- | ---------------------- | ------------------------ | ------------------------------- |
| 6   | Accepts all characters | Last name = 10 Doe\_!@#$ | accepted                        |
| 7   | input Max              | 31 characters            | accepted                        |
| 8   | input Max+1            | 32 characters            | accepted 31 chars               |
| 9   | Required field         | ""                       | rejected + "required field" msg |
| 10  | Lower boundary, 1 char | Last name = l            | accepted                        |

> **_#3: Input field "Street Address:"_**

<details>
  <summary>Requirements</summary>

- [x] text field
- [x] accepts all characters
- [x] no more than 255 [Max = 255 chars]
- [x] required field.

</details>

| ID  | Purpose/Title          | Instruction                   | Expected Result                 |
| --- | ---------------------- | ----------------------------- | ------------------------------- |
| 11  | Accepts all characters | Str Addr = 1450 Main Blvd, #A | accepted                        |
| 12  | input Max              | 255 characters                | accepted                        |
| 13  | input Max+1            | 256 characters                | accepted 255 chars              |
| 14  | Required field         | ""                            | rejected + "required field" msg |
| 15  | Lower boundary, 1 char | Str Addr = s                  | accepted                        |

> **_#4: Input field "City:"_**

<details>
  <summary>Requirements</summary>

- [x] text field
- [x] accepts all characters
- [x] no more than 50 [Max = 50 chars]
- [x] required field.

</details>

| ID  | Purpose/Title          | Instruction         | Expected Result                 |
| --- | ---------------------- | ------------------- | ------------------------------- |
| 16  | Accepts all characters | City = Kazan@1000$% | accepted                        |
| 17  | input Max              | 50 characters       | accepted                        |
| 18  | input Max+1            | 51 characters       | accepted 50 chars               |
| 19  | Required field         | ""                  | rejected + "required field" msg |
| 20  | Lower boundary, 1 char | City = c            | accepted                        |

> **_#5: Select box "State:"_**

<details>
  <summary>Requirements</summary>

- [x] list box
- [x] all 50 states
- [x] required field.

</details>

| ID  | Purpose/Title  | Instruction                                                            | Expected Result                                                             |
| --- | -------------- | ---------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| 21  | Select 1 state | Option = CA                                                            | accepted                                                                    |
| 22  | No select      | "--"                                                                   | rejected + "required field" msg                                             |
| 23  | All 50 States  | Project Webpage > Browser DevTools<br/> > Console > copy/paste code \* | "Missing states are: [] <br/>States that need to be removed OR renamed: []" |

```javascript
*
const statesArr = ['AK','AL','AR','AZ','CA','CO','CT','DE','FL','GA','HI','IA','ID','IL','IN','KS','KY','LA','MA','MD','ME','MI','MN','MO','MS','MT','NC','ND','NE','NH','NJ','NM','NV','NY','OH','OK','OR','PA','RI','SC','SD','TN','TX','UT','VA','VT','WA','WI','WV','WY',];
const selectBox = document.getElementsByName('state');
const options = selectBox[0].options;

const ourStatesArr = Array.from(options)
  .map((el) => el.value)
  .sort();

const matched = ourStatesArr.filter((state) => statesArr.includes(state));
const difference = statesArr.filter((state) => !matched.includes(state));
const failedStates = ourStatesArr.filter((state) => !matched.includes(state));

console.log('Missing states are: ', difference);
console.log('States that need to be removed OR renamed: ', failedStates);
```

> **_#6: Input field "ZIP:"_**

<details>
  <summary>Requirements</summary>

- [x] text field
- [x] accepts 5 characters (digits-only)
- [x] required field.

</details>

| ID  | Purpose/Title              | Instruction  | Expected Result                  |
| --- | -------------------------- | ------------ | -------------------------------- |
| 24  | Existing, 5 digits         | 10012        | accepted                         |
| 25  | 4 digits                   | 1001         | rejected + "enter valid ZIP" msg |
| 26  | 6 digits                   | 100122       | accepted 10012                   |
| 27  | Non-digit/letter           | 1O012        | rejected + "enter valid ZIP" msg |
| 28  | Non-digit/spec.char.       | 1001@        | rejected + "enter valid ZIP" msg |
| 29  | Required field             | ""           | rejected + "required field" msg  |
| 30  | Paste 6 digits             | paste 100122 | accepted 10012                   |
| 31  | Paste Non-digits/letter    | 1O012        | err msg "digits only"            |
| 32  | Paste Non-digits/spec.char | 1001@        | err msg "digits only"            |

> **_#7: Input field "Email:"_**

<details>
  <summary>Requirements</summary>

- [x] text field
- [x] accepts digits, letters, some special characters
- [x] 255 characters [Max = 255 chars]
- [x] required field.

</details>

| ID  | Purpose/Title                | Instruction                 | Expected Result                    |
| --- | ---------------------------- | --------------------------- | ---------------------------------- |
| 33  | Valid email                  | email@test.com              | accepted                           |
| 34  | Missing @ sign               | emailtest.com               | rejected + "enter valid email" msg |
| 35  | Missing local-part           | @test.com                   | rejected + "enter valid email" msg |
| 36  | Missing domain-part          | email@                      | rejected + "enter valid email" msg |
| 37  | Valid spec.chars             | name+lastname-id.1@test.com | accepted                           |
| 38  | Subdomain within TLD         | email@test-me.co.jp         | accepted                           |
| 39  | Missing domain name          | email@test                  | rejected + "enter valid email" msg |
| 40  | Subdomain within local-part  | name.lastname@test.com      | accepted                           |
| 41  | Two @ signs                  | email@s@test.com            | rejected + "enter valid email" msg |
| 42  | Dot in front of local-part   | .email@test.com             | rejected + "enter valid email" msg |
| 43  | Dot at the end of local-part | email.@test.com             | rejected + "enter valid email" msg |
| 44  | Digits in local-part         | 123456@test.com             | accepted                           |
| 45  | input Max                    | 255 valid characters        | accepted                           |
| 46  | input Max+1                  | 256 valid characters        | accepted 255 chars                 |
| 47  | Empty field                  | ""                          | rejected + "enter valid email" msg |

> **_#8: Input field "Phone:"_**

<details>
  <summary>Requirements</summary>

- [x] 3 text field
- [x] accepting 3-3-4 chars (digits only)
- [x] required field.

</details>

| ID  | Purpose/Title              | Instruction     | Expected Result                           |
| --- | -------------------------- | --------------- | ----------------------------------------- |
| 48  | Accept valid 3-3-4 digits  | 111-222-3333    | accepted                                  |
| 49  | 2-2-3 digits               | 11-22-333       | rejected + "enter valid phone number" msg |
| 50  | 4-4-5 digits               | 1117-2227-33337 | accepted "111-222-3333"                   |
| 51  | Invalid input/letter       | q11-222-3333    | rejected + "enter valid phone number" msg |
| 52  | Invalid input/spec.chars.  | ----222-3333    | rejected + "enter valid phone number" msg |
| 53  | Empty field                | ""              | rejected + "enter valid phone number" msg |
| 54  | Paste all (3-3-4) digits   | 111-222-3333    | accepted msg                              |
| 55  | Paste Non-digits/letters   | aaa-bbb-cccc    | rejected + "enter valid phone number" msg |
| 56  | Paste Non-digits/spec.char | -@$-=\_)-!%^&   | rejected + "enter valid phone number" msg |
| 57  | Paste 4-4-5 digits         | 1117-2227-33337 | accepted "111-222-3333"                   |

> **_#9: Input field "Best Way To Contact Me:"_**

| ID  | Purpose/Title   | Instruction    | Expected Result |
| --- | --------------- | -------------- | --------------- |
| 58  | Option selected | select "phone" | accepted        |
| 59  | Option empty    | ""             | accepted        |

> **_#10: Input field "Referred by:"_**

| ID  | Purpose/Title | Instruction                 | Expected Result |
| --- | ------------- | --------------------------- | --------------- |
| 60  | Accept input  | Referred by = 10 John\_!@#$ | accepted        |
| 61  | Empty input   | ""                          | accepted        |

---

<h3 style="color: #f44336"><a id="bug_reports">:beetle: Bug Reports</a></h3>

| ID  | Severity   | Title                                                                                                                                        |
| --- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | minor      | "First name" field should accept up to 31 characters, not 30 as it does now.                                                                 |
| 2   | minor      | "Last name" field should accept up to 31 characters, not 30 as it does now.                                                                  |
| 3   | minor      | "Street Address" field accepts no more than 100 characters instead of 255 as per requirements                                                |
| 4   | suggestion | In Requirements for State change the requirement phrase <br/> from '...all 50 states...' <br/>to '...all 50 states in alphabetical order...' |
| 5   | suggestion | In Requirements for "State" field change 'List Box' to 'Select Box'.                                                                         |
| 6   | minor      | "State" select box: 'Other' option is excessive.                                                                                             |
| 7   | serious    | "State" select box: there should be no such states as 'OT', 'NO', 'BC' in options for US.                                                    |
| 8   | serious    | "State" select box is missing options for Hawaii - (HI) & Nevada - (NV).                                                                     |
| 9   | minor      | "State" select box option for Indiana should be 'IN', instead of 'IND'.                                                                      |
| 10  | serious    | "Email" field is not processed as a required field when it is left empty.                                                                    |
| 11  | serious    | Beginning at "First Name" field, tab order is broken when going through the form with 'Tab' key.                                             |
| 12  | serious    | "Email" field accepts more than required 255 characters.                                                                                     |
| 13  | serious    | "Phone" input fields: while typing - cursor position doesn't switch to the next "Phone" inputs.                                              |
| 14  | serious    | Digit-only "Phone" input fields accept non-digit characters when pasting them.                                                               |
| 15  | serious    | "Referred by" field: inconsistency between the field not having asterisk, but being processed as a required field.                           |
| 16  | suggestion | "Referred by" field: clarify the Requiremenets on the field being/not being required.                                                        |
| 17  | serious    | Confusing/misleading error message when user pushes "Clear" button.                                                                          |
| 18  | minor      | Inconsistency:"State" & "Best way to contact me" select boxes by default have different options values, instead of one.                      |
| 19  | serious    | "Zip" code field: allows pasting more than required 5 characters.                                                                            |
| 20  | serious    | "Zip" code field: allows pasting non-digit values (letters and/or special characters).                                                       |

<!--  s -->
