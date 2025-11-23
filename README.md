# Windows-basic-commands-batchscript
Ex08-Windows-basic-commands-batchscript

# AIM:
To execute Windows basic commands and batch scripting

# DESIGN STEPS:

### Step 1:

Navigate to any Windows environment installed on the system or installed inside a virtual environment like virtual box/vmware 

### Step 2:

Write the Windows commands / batch file . Save each script in a file with a .bat extension. Ensure you have the necessary permissions to perform the operations. Adapt paths as needed based on your system configuration.
### Step 3:

Execute the necessary commands/batch file for the desired output. 




# WINDOWS COMMANDS:
## Exercise 1: Basic Directory and File Operations
Create a directory named "my-folder"
```
mkdir my-folder
```

<img width="382" height="47" alt="image" src="https://github.com/user-attachments/assets/5a191256-15d9-4c97-ae67-24e030ec8822" />

## COMMAND AND OUTPUT

Remove the directory "my-folder" 

```
rmdir my-folder
```
<img width="395" height="61" alt="image" src="https://github.com/user-attachments/assets/706ba43b-edcd-4f26-818c-b3ca95083422" />

## COMMAND AND OUTPUT

Create the file Rose.txt
```
type nul > Rose.txt
```
<img width="436" height="46" alt="image" src="https://github.com/user-attachments/assets/9674b8d7-24b5-4065-99e7-ac66c3e2abde" />

## COMMAND AND OUTPUT

Create the file hello.txt using echo and redirection
```
echo Hello World > hello.txt
```
<img width="536" height="52" alt="image" src="https://github.com/user-attachments/assets/61148554-e730-424c-83e1-e409b0ae40cf" />

## COMMAND AND OUTPUT

Copy the file hello.txt into the file hello1.txt
```
copy hello.txt hello1.txt
```
<img width="502" height="66" alt="image" src="https://github.com/user-attachments/assets/7ce7c745-2964-473a-a0ee-7caa85b772fd" />

## COMMAND AND OUTPUT

Remove the file hello1.txt
```
del hello1.txt
```
<img width="369" height="49" alt="image" src="https://github.com/user-attachments/assets/38400bf2-80c2-46f6-8de0-29743bea5bb2" />

## COMMAND AND OUTPUT

List out the file hello1.txt in the current directory
```
dir hello1.txt
```
<img width="428" height="183" alt="image" src="https://github.com/user-attachments/assets/faae0d92-06d0-4d42-9a98-e12dd8be08db" />

## COMMAND AND OUTPUT

List out all the associated file extensions 
```
assoc
```
<img width="505" height="1056" alt="image" src="https://github.com/user-attachments/assets/7af0ef04-5778-45df-b9fe-43adb8d5e256" />

## COMMAND AND OUTPUT

Compare the file hello.txt and rose.
```
fc hello.txt Rose.txt
```
<img width="504" height="171" alt="image" src="https://github.com/user-attachments/assets/f8ca5729-13f4-46f6-882c-bcedfc3c2798" />


## COMMAND AND OUTPUT

## Exercise 2: Advanced Batch Scripting
Create a batch file named on the desktop. The batch file need to have a variable assigned with a desired name for ex. name="John" and display as "Hello, John".
```
@echo off
:: Set the variable
set "name=John"

:: Display the message using the variable
echo Hello, %name%

:: Pause to view the output
pause
```

## OUTPUT
<img width="406" height="78" alt="image" src="https://github.com/user-attachments/assets/0ce944db-dd0a-4a03-9f41-16a20ad52e66" />


Create a batch file  on the desktop that checks whether a user-input number is odd or not. The script should:
Prompt the user to enter a number.
Calculate the remainder when the number is divided by 2.
Display whether the number is odd or not.
Ask the user if they want to check another number.
Repeat the process if the user enters Y, and exit with a thank-you message if the user enters N.
Handle invalid inputs for the continuation prompt (Y/N) gracefully.

```
@echo off
:start
cls
echo --- Odd or Even Checker ---

:: Prompt user for input
set /p "num=Enter a number: "

:: Calculate remainder
set /a remainder=num %% 2

:: Check remainder
if %remainder%==0 (
    echo The number %num% is Even.
) else (
    echo The number %num% is Odd.
)

:ask_retry
echo.
:: Prompt to continue
set /p "choice=Do you want to check another number? (Y/N): "

:: Handle Yes (Case insensitive /I)
if /I "%choice%"=="Y" goto start

:: Handle No (Case insensitive /I)
if /I "%choice%"=="N" goto goodbye

:: Handle Invalid Input
echo Invalid input. Please enter Y or N.
goto ask_retry

:goodbye
echo.
echo Thank you for using the checker!
pause
exit
```

## OUTPUT

<img width="563" height="225" alt="image" src="https://github.com/user-attachments/assets/afe800a5-d854-4160-9d7b-36a2e8340210" />




Write a batch file that uses a FOR loop to iterate over a sequence of numbers (1 to 5) and displays each number with the label Number:. The output should pause at the end.
```
@echo off
echo Loop Sequence:
echo.

:: Loop from 1 to 5
:: The syntax (1,1,5) means (Start, Step, End)
for /L %%i in (1,1,5) do (
    echo Number: %%i
)

echo.
pause
```
## OUTPUT

<img width="439" height="244" alt="image" src="https://github.com/user-attachments/assets/51176d95-e1ff-48b2-97ba-0cfd9f57087f" />


Write a batch script to check whether a file named sample.txt exists in the current directory. If the file exists, display the message sample.txt exists. Otherwise, display sample.txt does not exist. Pause the script at the end to view the result.

Instructions:
Use the IF EXIST conditional statement.
Make sure the script works for files located in the same directory as the batch file.
Use pause to keep the command window open after displaying the message.
Expected Output (if the file exists):
```
@echo off

:: Check if the file exists in the current directory
if exist "sample.txt" (
    echo sample.txt exists
) else (
    echo sample.txt does not exist
)

:: Pause to view the result
pause
```
## OUTPUT
<img width="412" height="130" alt="image" src="https://github.com/user-attachments/assets/87739d58-6997-457d-8977-c394234da724" />


Write a batch script that displays a simple menu with three options:
Say Hello – Displays the message Hello, World!
Create a File – Creates a file named newfile.txt with the content This is a new file
Exit – Exits the script with a goodbye message
The script should repeatedly display the menu until the user chooses to exit. Use goto statements to handle menu navigation.
```
@echo off
:menu
cls
echo ==============================
echo        BATCH MENU
echo ==============================
echo 1. Say Hello
echo 2. Create a File (newfile.txt)
echo 3. Exit
echo ==============================

:: Get user choice
set /p "opt=Select an option (1-3): "

:: Navigation logic
if "%opt%"=="1" goto say_hello
if "%opt%"=="2" goto create_file
if "%opt%"=="3" goto exit_script

:: Handle invalid menu choice
echo Invalid option selected. Please try again.
pause
goto menu

:say_hello
cls
echo.
echo Hello, World!
echo.
pause
goto menu

:create_file
cls
echo Creating file...
:: Create the file with specific content
echo This is a new file > newfile.txt
echo.
echo 'newfile.txt' has been created successfully.
pause
goto menu

:exit_script
cls
echo.
echo Goodbye! Thanks for using the script.
pause
exit
```

## OUTPUT
<img width="433" height="367" alt="image" src="https://github.com/user-attachments/assets/921bbfeb-5f80-4d47-b2b4-e5cdc89ea676" />



# RESULT:
The commands/batch files are executed successfully.

