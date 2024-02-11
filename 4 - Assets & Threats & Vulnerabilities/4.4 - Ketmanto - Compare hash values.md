# Compare Hash Values

## Description
As a security analyst, one of the security controls we can implement is hashing. It produces a code that cannot be decrypted. It works by uniquely identifying the contents of a file, later
known as a unique identifier (hash value or digest). For example, a malicious program may mimic an original program. If one code line is different from the original program, it produces a different hash value. Security teams can then identify the malicious program and work to mitigate the risk.

## Generate Hashes
First, `ls` command shows the files within the directory. We have two files and we would like to show the contents of them (`cat`). We could see from the picture below that the contents of both files appear to be identical.

![image](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/090063e2-c409-4f9f-b2a4-0e51742e0d38)

We can find if the files are really different or not by using the `sha256` command. From the picture below we can see both files have different hash values.

![image](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/e9e5aa82-14dd-41be-b9a9-a99032e96ce2)

## Compare Hashes Files
Let’s generate the hash of the `file1.txt` and `file2.txt` to a new file for `file1hash` and `file2hash` respectively.  

![image](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/43dac5fb-02a2-4a88-8649-860da04dcfc5)

Inspect the contents of them by using `cat` commands. Last but not least, compare both files by using `cmp` command.

![image](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/c1180c2b-6fc3-4af2-91c9-3396d0b3e328)

![image](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/4b18b138-0931-48bf-b3f4-9dac480ec2da)

## Summary
Though the contents of both files appear to be identical, only hash values of each file that can determine if they are the same or not.
