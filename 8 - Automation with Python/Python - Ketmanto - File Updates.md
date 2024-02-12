# Python - Update a File 

## Description
You are a security professional working at a health care company. As part of your job, you're required to regularly update a file that identifies the employees who can access restricted content. The contents of the file are based on who is working with personal patient records. Employees are restricted access based on their IP address. There is an allow list for IP addresses permitted to sign into the restricted subnetwork. There's also a remove list that identifies which employees you must remove from this allow list.

Your task is to create an algorithm that uses Python code to check whether the allow list contains any IP addresses identified on the remove list. If so, you should remove those IP addresses from the file containing the allow list. The following IPs to be removed are: 
* `192.168.97.225`
* `192.168.158.170`
* `192.168.201.40`
* `192.168.58.57`

> My Python code is in Jupyter Notebook. Please navigate to `Python - Ketmanto - Automation.ipynb`. 

## Import and Read the File Contents

```
# import the file 
import_file = "allow_list.txt"

# Open the file
with open(import_file, "r") as file: 
    ip_addresses = file.read()

# display the ip_addresses
print(ip_addresses)
```

For the first part of the algorithm, I imported the `allow_list.txt` by using `import` module. Then, I used `with open` statement to open the file. The `open()` function has two parameters: `import_file` and `r`. The first identifies the file to import, the second indicattes what I would like to do with the file (read the file). Finally, I assigned the string output of this method to the variable `ip_addresses` and `print` it. For your information, there are 17 IP addresses in `allow_list.txt`. 

The Result: 

![VSCodium_kuQb9u8xFI](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/b6774bba-d759-403a-aebf-857ccff3bceb)

## Convert the String into a List
```
# String into a list
import_file = "allow_list.txt"

# `with` statement to read the contents
with open(import_file, "r") as file: 
    ip_addresses = file.read()

# convert from a string to a list
ip_addresses = ip_addresses.split()

# Display the `ip_addresses`
print(ip_addresses)

```
To remove individual IP addresses from the `allow list`, I had to convert the string format into a list format. To do that, I used `split()` to convert `ip_addresses` string into a list. 

The Result:
```
 ['ip_address', '192.168.25.60', '192.168.205.12', '192.168.97.225', '192.168.6.9', '192.168.52.90', '192.168.158.170', '192.168.90.124', '192.168.186.176', '192.168.133.188', '192.168.203.198', '192.168.201.40', '192.168.218.219', '192.168.52.37', '192.168.156.224', '192.168.60.153', '192.168.58.57', '192.168.69.116']
```

## Remove IP Addresses That Are on the Remove List
```
# import the file 
import_file = "allow_list.txt"

# Assign `remove_list` to a list of IP addresses that are no longer allowed to access restricted information. 

remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

# `with`statement to read the contents
with open(import_file, "r") as file: 
    ip_addresses = file.read()

# convert from a string to a list
ip_addresses = ip_addresses.split()

# Build iterative statement
# Name loop variable `element`
# Loop through `ip_addresses`

for element in ip_addresses:
  
  # Build conditional statement
  # If current element is in `remove_list`,

    if element in remove_list:

        # then current element should be removed from `ip_addresses`

        ip_addresses.remove(element)

# Display `ip_addresses` 

print(ip_addresses)
```

I iterated through the remove list by incorporating a `for` loop: `for element in remove_list:`. If the element is in the remove list, then the current element should be removed from `ip_addresses`. The keyword `in` indicates to iterate to iterate through the sequence and assign each value to the loop variable element. Then, I applied `.remove()` to `ip_addresses` and successfully removed 4 IP addresses. Furthermore, there are 13 current IP addresses. 

The result: 
```
['ip_address', '192.168.25.60', '192.168.205.12', '192.168.6.9', '192.168.52.90', '192.168.90.124', '192.168.186.176', '192.168.133.188', '192.168.203.198', '192.168.218.219', '192.168.52.37', '192.168.156.224', '192.168.60.153', '192.168.69.116']
```

## Update the File With the Revised List of IP Addresses
```
import_file = "allow_list.txt"

remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

with open(import_file, "r") as file:

  ip_addresses = file.read()

ip_addresses = ip_addresses.split()

for element in ip_addresses:
   
    if element in remove_list:

        ip_addresses.remove(element)

# Convert `ip_addresses` back to a string so that it can be written into the text file     

ip_addresses = " ".join(ip_addresses)

# Build `with` statement to rewrite the original file

with open(import_file, "w") as file:

  # Rewrite the file, replacing its contents with `ip_addresses`

  file.write(ip_addresses)

# Build `with` statement to read in the updated file

with open(import_file, "r") as file:

    # Read in the updated file and store the contents in `text`

    text = file.read()

# Display the contents of `text`

print(text)
```

As a final step in this task, I had to update the `allow list` with the revised list of IP addresses. To do so, the list format has to be converted into a string. The `.join()` method combines all items in an iterable into a string. Here, I created a string from the list `ip_addresses` so that I could write an argument `.write()` method to write a new revised IP addresses in the `allow_list.txt`. The `"\n".join(ip_addresses)` places each element on a new line. 

The argument `w` with the `open()` and `with` statement, indicates the file that I want to open and write over its content. Once the code above is executed, the document will be updated in `allow_list.txt`. 

> The file `allow_list.txt` that I attached in this directory is the initial file. You might wanna run the code and observe its content to be revised. Otherwise, please head to `allow_list_revised.txt` to observe the differences. 

The result in the new `allow_list.txt` (13 IP addresses): 
![VSCodium_2IJHBymnA6](https://github.com/Kwangsa19/Ketmanto-Cybersecurity-Portfolio/assets/135963482/652efbd6-6698-4e44-92cb-06e8e37b4e2d)

## Summary
First, I opened the file and identified `remove_list` variable from `allow_list.txt`. Second, I converted the string into a list. Third, I removed some IP addresses from the list. Fourth, I converted the list into a string format and revise the `allow_list.txt`. 
