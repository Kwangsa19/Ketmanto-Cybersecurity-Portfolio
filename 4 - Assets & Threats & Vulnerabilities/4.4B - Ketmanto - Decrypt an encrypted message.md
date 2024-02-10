# Decryption

## Scenario

In this scenario, all of the files in your home directory have been encrypted. You’ll need to use Linux commands to break the Caesar cipher and decrypt the files so that you can read the hidden messages they contain.

Here’s how you’ll do this task: First, you’ll explore the contents of the home directory and read the contents of a file. Next, you’ll find a hidden file and decrypt the Caesar cipher it contains. Finally, you’ll decrypt the encrypted data file to recover your data and reveal the hidden message.

OK, it's time to decrypt some messages in Linux!

> It starts with you logged in as user analyst, with your home directory, /home/analyst, as the current working directory.

## Solution 

1. Read the contents of a file
* Use the `ls` command to list the files in the directory:
`ls /home/analyst`.

![chrome_5p8h7bnpSZ](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/2bf4701d-3283-4214-afaf-5d49ff8496ea)


* List the contents of the README.txt file: 
`cat README.txt`.

![chrome_OMbPE4mYh5](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/00d86c7f-a394-42f8-9f62-45522d3a5e91)

The message in the README.txt file advises that the caesar subdirectory contains a hidden file.

2. Find a hidden file
In this task, you need to find a hidden file in your home directory and decrypt the Caesar cipher it contains.
* Use `cd` command to caesar subdirectory and use `ls -a` to list all files including hidden files: `cd caesar` and `ls -a`.
  
![chrome_vVzk6li9Ir](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/a263ea12-a496-414a-b5da-9a4e87c956af)

* Use the `cat` command to list the contents of the hidden file:
`cat .leftShift3`.

![chrome_2KE6gkd6Z3](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/35cddc8e-c1d6-4d09-886f-61a222559d9c)

The message appears to be scrambled due to being encrypted with a Caesar cipher. The cipher can be solved by shifting each alphabet character to the left or right by a fixed number of spaces. In this example, the shift is three letters to the left. Thus `"d"` stands for `"a"`, and `"e"`stands for `"b"`.

* Decrypt the Cipher using the command `cat` and `tr`:
`cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"`.

![chrome_yqTsKokU9s](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/2ae37e92-2b0d-460f-b1f0-7d31fb4921e5)

> The tr command translates text from one set of characters to another, using a mapping. The first parameter to the tr command represents the input set of characters, and the second represents the output set of characters. Hence, if you provide parameters “abcd” and “pqrs”, and the input string to the tr command is “ac”, the output string will be “pr".


4. Decrypt a file 
* Go back to initial working directory and run this command to decrypt a file:
`openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute`.

![chrome_vji0fyPapn](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/43b92274-8d80-44ba-b816-81dc13d25b4c)



This command reverses the encryption of the file with a secure symmetric cipher as indicated by AES-256-CBC. The `-pbkdf2` option is used to add extra security to the key, and `-a` indicates the desired encoding for the output. The `-d` indicates decrypting, while `-in` specifies the input file and `-out` specifies the output file. The `-k` specifies the password, which in this example is ettubrute.

* Use the `ls` command and `cat Q1.recovered`.

![chrome_r4HkolC4jH](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/23ce648c-b076-4124-9e56-4b6962fc71b5)




  
