# SMS/Message_Slang_Translator

## How to Run
- In Terminal or Command Prompt
```
  python sms_translator_function.py
```
- Enter Message like "Hey Hardik brb!!"
- Result would be --> Hey Hardik Be Right Back
  ```
    userInput = Hey Hardik brb!!
    output = Hey Hardik Be Right Back
  ```

## Main Working logic
```python
  def translator(user_string):
    user_string = user_string.split(" ")
    j = 0
    for _str in user_string:
        # File path which consists of Abbreviations.
        fileName = "G:\\Projects [Git]\\sms_slag_translator\\slang.txt"
        # File Access mode [Read Mode]
        accessMode = "r"
        with open(fileName, accessMode) as myCSVfile:
            # Reading file as CSV with delimiter as "=", so that abbreviation are stored in row[0] and phrases in row[1]
            dataFromFile = csv.reader(myCSVfile, delimiter="=")
            # Removing Special Characters.
            _str = re.sub('[^a-zA-Z0-9-_.]', '', _str)
            for row in dataFromFile:
                # Check if selected word matches short forms[LHS] in text file.
                if _str.upper() == row[0]:
                    # If match found replace it with its Abbreviation in text file.
                    user_string[j] = row[1]
            myCSVfile.close()
        j = j + 1
    # Replacing commas with spaces for final output.
    print(' '.join(user_string))
```
## Python Script to abbreviate slangs
This script takes input from user and finds any abbreviation available in it as described in text file, If found it will replace it with its corresponding phrase.

