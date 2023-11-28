# _Robot => writing functionality tests with robot_

![](https://lh7-us.googleusercontent.com/IzuejNALWHEtxCzdPZ14YBvO8kun5co7oDdxipCrk9-pygqojjGhxZvWMi-cBshbE6JZ9BnvfQnW_Ov0hU_k58AyxP87bvm52hK-yfy5V_Z29008gyIJOub449-VYDdxPv7mfIksg8AJj0xepZH9PjA)

# Table of Contents

- [Introduction](#Introduction)

- [What is Robot Framework?](#What-is-Robot-Framework)

- [Different Types of testing supported by Robot Framework](#Different-Types-of-testing-supported-by-Robot-Framework)

- [Basic Concepts of Robot Framework](#Basic-Concepts-of-Robot-Framework)

- [Set Up](#Set-Up)

- [Writing your first Test case in Robot framework](#Writing-your-first-Test-case-in-Robot-framework)

- [Writing your second Test case in Robot framework](#Writing-your-Second-Test-case-in-Robot-framework)




## Introduction

Robot Framework is an open-source test automation framework that uses keyword-driven testing and allows easy-to-use tabular syntax to create test cases. It supports different testing approaches such as acceptance, integration, and unit testing. It uses a keyword-driven testing approach where testers can easily create test cases in tabular syntax. This guide will provide a comprehensive understanding of the Robot Framework, its basic concepts, syntax, and how it can be used for automated testing. You can follow this guide as a robot framework tutorial.


## What is Robot Framework?

Robot Framework is a generic open source automation framework. It can be used for test automation and robotic process automation (RPA).

Robot Framework is supported by Robot Framework Foundation. Many industry-leading companies use the tool in their software development.

Robot Framework is open and extensible. Robot Framework can be integrated with virtually any other tool to create powerful and flexible automation solutions. Robot Framework is free to use without licensing costs.

Robot Framework has an easy syntax, utilizing human-readable keywords. Its capabilities can be extended by libraries implemented with Python, Java or many other programming languages. Robot Framework has a rich ecosystem around it, consisting of libraries and tools that are developed as separate projects.


## Different Types of testing supported by Robot Framework

Robot Framework is used when there is a need for test automation in a software development process. It is particularly useful in projects that require continuous integration and delivery, as it supports different types of testing and can be easily integrated with other tools such as Jenkins and Git.

Robot Test Framework is a versatile test automation framework that can be used in a variety of scenarios. Some common use cases for the Robot Framework include:

- **Acceptance Testing**: Robot Automation Framework is often used for acceptance testing, which involves testing whether a software system meets the specified requirements. This type of testing can be done at various stages of the software development lifecycle, from early prototypes to final releases.

- **Regression Testing**: Regression testing is used to ensure that software changes or updates do not introduce new bugs or issues. Robot Framework is a popular choice for regression testing because of its modular architecture and ability to easily reuse test cases.

- **Functional Testing** Python Robot Framework can be used for functional testing, which involves testing the functionality of a software system. This can include testing individual functions or components, as well as testing the system as a whole.

- **Integration Testing**: Integration testing involves testing how different components of a software system work together. The Robot Framework can be used to automate this type of testing, allowing testers to easily test the interactions between different components.

- **Continuous Integration/Continuous Delivery (CI/CD):** It can be integrated with CI/CD pipelines to automate testing as part of the software development process. This allows teams to catch issues early in the development cycle and ensure that new changes do not introduce new bugs or issues.
  
- **API Testing:** Robot Framework has built-in libraries for testing APIs, making it a popular choice for testing RESTful and SOAP web services.


##

##

##

## Basic Concepts of Robot Framework

Robot Framework is a popular test automation framework that uses a keyword-driven approach to create test cases. The framework is built in Python and can be used for both web-based and desktop-based applications. Here are some basic concepts of Robot Framework:

- **Keywords**: Keywords are the building blocks of Robot Framework test cases. They represent a single action or step that the test case will take. Keywords can be either user-defined or built-in. User-defined keywords are custom functions created by the tester, while built-in keywords are pre-defined functions that are included in the Robot Framework library.

<!---->

          *** Keywords ***
          My Keyword
          Log This is my first keyword

- **Test Cases**: Test cases are a collection of keywords that represent a specific test scenario. Test cases can be organized into test suites, which are collections of related test cases.

<!---->

          *** Test Cases ***
    My Test Case

- **Variables**: Variables are used to store data that can be used throughout the test case. Variables can be assigned a value using the keyword “**Set Variable**“, and their value can be retrieved using the keyword “**Get Variable Value**“.

<!---->

    *** Variables ***
    ${MY_VARIABLE} Hello World

- **Test Data**: Test data is the input that is used in a test case. Test data can be stored in a separate file, such as a CSV or Excel file, and then accessed using the “**Data-Driven Testing**” approach in Robot Framework. In the below example, the “Get File” keyword is used to read the test data from the “login\_data.csv” file and store it in a variable called “${data}”. The “FOR” loop is then used to iterate over each row of the test data and set the “${username}” and “${password}” variables to the values from the CSV file. Finally, the “Login” keyword is used to perform the login functionality with the specified username and password.

<!---->

    *** Keywords ***
    Login With Credentials From CSV
    [Arguments] ${filename}
    ${data}= Get File ${filename}
    : FOR ${row} IN @{data}
    ${username}= Set Variable ${row['username']}
    ${password}= Set Variable ${row['password']}
    Login ${username} ${password}

- **Assertions**: Assertions are used to validate the expected output of a test case. Robot Framework provides a wide range of built-in assertions, such as “**Should Be True**“, “**Should Be False**“, “**Should Be Equal**“, and “**Should Not Be Equal**“.

<!---->

    *** Keywords ***
    Login With Credentials From CSV
    [Arguments] ${filename}
    ${data}= Get File ${filename}
    FOR ${row} IN @{data}
    ${username}= Set Variable ${row['username']}
    ${password}= Set Variable ${row['password']}
    Login ${username} ${password}
    Should Be Equal verify HomePage #assertion for Homepage
    END

- **Libraries**: Libraries are a collection of reusable code that can be used in Robot Framework. Libraries can be either built-in or user-defined. Built-in libraries are included in the Robot Framework library, while user-defined libraries can be created by the tester. Adding a library to Robot Framework is a straightforward process. To add a library, you need to download the library and save it to a directory on your computer. You can then add the directory path to the Robot Framework settings using the Library keyword.

<!---->

    *** Settings ***
    Library SeleniumLibrary

- **Tags:** Tags are used to categorize test cases and make it easier to run specific tests. Tags are defined using the keyword “**Tags**” followed by the tag name.

<!---->

    *** Test Cases ***
    My Test Case
    Tags Smoke Test

- **Test Execution**: Test execution is the process of running the test cases. Robot Framework provides multiple ways to execute tests, such as running individual test cases, running test suites, or running all test cases in a directory.
- **Exception catching:** Exception catching is used to handle errors and exceptions that may occur during the test execution. Robot Framework provides a built-in keyword named “**Run Keyword And Expect Error**” that can be used to catch exceptions. This keyword executes a given keyword and expects it to fail with a specific error message. If the keyword does not fail or fails with a different error message, the test case will fail.\
  Suppose you have a login functionality that raises an exception if the username or password is incorrect. You can use the “**Run Keyword And Expect Error**” keyword to catch the exception and handle it in a custom way. Here’s an example of how to use this keyword to catch an exception in a login test case:


<!---->

    *** Test Cases ***
    Login Test
    [Documentation] Test the login functionality
    : TRY
    Login john.doe password
    Log Login successful
    : EXCEPT AssertionError
    Log Login failed: username or password is incorrect

- **Reports and Logs**: Robot Framework provides detailed reports and logs that can be used to analyze the test results. The reports include information such as the test case status, execution time, and error messages.


## Set Up

&#x20; **Command:-**

 ## Install Python
```
   sudo apt install python3
```

**Output:-**

Reading package lists... Done

Building dependency tree   

Reading state information... Done

python3 is already the newest version (3.8.2-0ubuntu2).

python3 set to manually installed.

The following packages were automatically installed and are no longer required:

  gir1.2-goa-1.0 linux-headers-5.15.0-46-generic

  linux-hwe-5.15-headers-5.15.0-46 linux-image-5.15.0-46-generic

  linux-modules-5.15.0-46-generic linux-modules-extra-5.15.0-46-generic

Use 'sudo apt autoremove' to remove them.

0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

 **Verify Installation**     
 ```
python3 --version
```
**Output:-**

Python 3.8.10

 ## 2.**Install Pip**
```
    sudo apt install python3-pip
```

**Output:-**

Reading package lists... Done

Building dependency tree   

Reading state information... Done

The following packages were automatically installed and are no longer required:

  gir1.2-goa-1.0 linux-headers-5.15.0-46-generic

  linux-hwe-5.15-headers-5.15.0-46 linux-image-5.15.0-46-generic

  linux-modules-5.15.0-46-generic linux-modules-extra-5.15.0-46-generic

Use 'sudo apt autoremove' to remove them.

The following additional packages will be installed:

  binutils binutils-common binutils-x86-64-linux-gnu build-essential dpkg-dev

  fakeroot g++ g++-9 gcc gcc-9 libalgorithm-diff-perl

  libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan5 libbinutils

  libc-dev-bin libc6-dev libcrypt-dev libctf-nobfd0 libctf0 libexpat1-dev

  libfakeroot libgcc-9-dev libitm1 liblsan0 libpython3-dev libpython3.8-dev

  libquadmath0 libstdc++-9-dev libtsan0 libubsan1 linux-libc-dev make

  manpages-dev python-pip-whl python3-dev python3-distutils python3-setuptools

  python3-wheel python3.8-dev zlib1g-dev

Suggested packages:

  binutils-doc debian-keyring g++-multilib g++-9-multilib gcc-9-doc

  gcc-multilib autoconf automake libtool flex bison gcc-doc gcc-9-multilib

  gcc-9-locales glibc-doc libstdc++-9-doc make-doc python-setuptools-doc

The following NEW packages will be installed:

  binutils binutils-common binutils-x86-64-linux-gnu build-essential dpkg-dev

  fakeroot g++ g++-9 gcc gcc-9 libalgorithm-diff-perl

  libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan5 libbinutils

  libc-dev-bin libc6-dev libcrypt-dev libctf-nobfd0 libctf0 libexpat1-dev

  libfakeroot libgcc-9-dev libitm1 liblsan0 libpython3-dev libpython3.8-dev

  libquadmath0 libstdc++-9-dev libtsan0 libubsan1 linux-libc-dev make

  manpages-dev python-pip-whl python3-dev python3-distutils python3-pip

  python3-setuptools python3-wheel python3.8-dev zlib1g-dev

0 upgraded, 42 newly installed, 0 to remove and 8 not upgraded.

Need to get 44.1 MB of archives.

After this operation, 199 MB of additional disk space will be used.

Do you want to continue? \[Y/n] y

Get:1 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 binutils-common amd64 2.34-6ubuntu1.6 \[207 kB]

Get:2 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 libbinutils amd64 2.34-6ubuntu1.6 \[473 kB]

Get:3 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 libctf-nobfd0 amd64 2.34-6ubuntu1.6 \[47.4 kB]

Get:4 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 libctf0 amd64 2.34-6ubuntu1.6 \[46.6 kB]

Get:5 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 binutils-x86-64-linux-gnu amd64 2.34-6ubuntu1.6 \[1,613 kB]

Get:6 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 binutils amd64 2.34-6ubuntu1.6 \[3,376 B]

Get:7 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 libc-dev-bin amd64 2.31-0ubuntu9.12 \[71.6 kB]

Get:8 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-libc-dev amd64 5.4.0-167.184 \[1,117 kB]

Get:9 http\://in.archive.ubuntu.com/ubuntu focal/main amd64 libcrypt-dev amd64 1:4.4.10-10ubuntu4 \[104 kB]

Get:10 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 libc6-dev amd64 2.31-0ubuntu9.12 \[2,519 kB]

Get:11 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 libitm1 amd64 10.5.0-1ubuntu1\~20.04 \[26.2 kB]

Get:12 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 libasan5 amd64 9.4.0-1ubuntu1\~20.04.2 \[2,752 kB]

Get:13 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 liblsan0 amd64 10.5.0-1ubuntu1\~20.04 \[835 kB]

Get:14 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 libtsan0 amd64 10.5.0-1ubuntu1\~20.04 \[2,016 kB]

Get:15 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 libubsan1 amd64 10.5.0-1ubuntu1\~20.04 \[785 kB]

Get:16 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 libquadmath0 amd64 10.5.0-1ubuntu1\~20.04 \[146 kB]

Get:17 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 libgcc-9-dev amd64 9.4.0-1ubuntu1\~20.04.2 \[2,359 kB]

Get:18 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 gcc-9 amd64 9.4.0-1ubuntu1\~20.04.2 \[8,276 kB]

Get:19 http\://in.archive.ubuntu.com/ubuntu focal/main amd64 gcc amd64 4:9.3.0-1ubuntu2 \[5,208 B]

Get:20 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 libstdc++-9-dev amd64 9.4.0-1ubuntu1\~20.04.2 \[1,722 kB]

Get:21 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 g++-9 amd64 9.4.0-1ubuntu1\~20.04.2 \[8,421 kB]

Get:22 http\://in.archive.ubuntu.com/ubuntu focal/main amd64 g++ amd64 4:9.3.0-1ubuntu2 \[1,604 B]

Get:23 http\://in.archive.ubuntu.com/ubuntu focal/main amd64 make amd64 4.2.1-1.2 \[162 kB]

Get:24 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 dpkg-dev all 1.19.7ubuntu3.2 \[679 kB]

Get:25 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 build-essential amd64 12.8ubuntu1.1 \[4,664 B]

Get:26 http\://in.archive.ubuntu.com/ubuntu focal/main amd64 libfakeroot amd64 1.24-1 \[25.7 kB]

Get:27 http\://in.archive.ubuntu.com/ubuntu focal/main amd64 fakeroot amd64 1.24-1 \[62.6 kB]

Get:28 http\://in.archive.ubuntu.com/ubuntu focal/main amd64 libalgorithm-diff-perl all 1.19.03-2 \[46.6 kB]

Get:29 http\://in.archive.ubuntu.com/ubuntu focal/main amd64 libalgorithm-diff-xs-perl amd64 0.04-6 \[11.3 kB]

Get:30 http\://in.archive.ubuntu.com/ubuntu focal/main amd64 libalgorithm-merge-perl all 0.08-3 \[12.0 kB]

Get:31 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 libexpat1-dev amd64 2.2.9-1ubuntu0.6 \[116 kB]

Get:32 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 libpython3.8-dev amd64 3.8.10-0ubuntu1\~20.04.8 \[3,950 kB]

Get:33 http\://in.archive.ubuntu.com/ubuntu focal/main amd64 libpython3-dev amd64 3.8.2-0ubuntu2 \[7,236 B]

Get:34 http\://in.archive.ubuntu.com/ubuntu focal/main amd64 manpages-dev all 5.05-1 \[2,266 kB]

Get:35 http\://in.archive.ubuntu.com/ubuntu focal-updates/universe amd64 python-pip-whl all 20.0.2-5ubuntu1.10 \[1,805 kB]

Get:36 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 zlib1g-dev amd64 1:1.2.11.dfsg-2ubuntu1.5 \[155 kB]

Get:37 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 python3.8-dev amd64 3.8.10-0ubuntu1\~20.04.8 \[514 kB]

Get:38 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 python3-distutils all 3.8.10-0ubuntu1\~20.04 \[141 kB]

Get:39 http\://in.archive.ubuntu.com/ubuntu focal/main amd64 python3-dev amd64 3.8.2-0ubuntu2 \[1,212 B]

Get:40 http\://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 python3-setuptools all 45.2.0-1ubuntu0.1 \[330 kB]

Get:41 http\://in.archive.ubuntu.com/ubuntu focal-updates/universe amd64 python3-wheel all 0.34.2-1ubuntu0.1 \[23.9 kB]

Get:42 http\://in.archive.ubuntu.com/ubuntu focal-updates/universe amd64 python3-pip all 20.0.2-5ubuntu1.10 \[231 kB]

Fetched 44.1 MB in 18s (2,455 kB/s)                                        

Extracting templates from packages: 100%

Selecting previously unselected package binutils-common:amd64.

(Reading database ... 227341 files and directories currently installed.)

Preparing to unpack .../00-binutils-common\_2.34-6ubuntu1.6\_amd64.deb ...

Unpacking binutils-common:amd64 (2.34-6ubuntu1.6) ...

Selecting previously unselected package libbinutils:amd64.

Preparing to unpack .../01-libbinutils\_2.34-6ubuntu1.6\_amd64.deb ...

Unpacking libbinutils:amd64 (2.34-6ubuntu1.6) ...

Selecting previously unselected package libctf-nobfd0:amd64.

Preparing to unpack .../02-libctf-nobfd0\_2.34-6ubuntu1.6\_amd64.deb ...

Unpacking libctf-nobfd0:amd64 (2.34-6ubuntu1.6) ...

Selecting previously unselected package libctf0:amd64.

Preparing to unpack .../03-libctf0\_2.34-6ubuntu1.6\_amd64.deb ...

Unpacking libctf0:amd64 (2.34-6ubuntu1.6) ...

Selecting previously unselected package binutils-x86-64-linux-gnu.

Preparing to unpack .../04-binutils-x86-64-linux-gnu\_2.34-6ubuntu1.6\_amd64.deb .

..

Unpacking binutils-x86-64-linux-gnu (2.34-6ubuntu1.6) ...

Selecting previously unselected package binutils.

Preparing to unpack .../05-binutils\_2.34-6ubuntu1.6\_amd64.deb ...

Unpacking binutils (2.34-6ubuntu1.6) ...

Selecting previously unselected package libc-dev-bin.

Preparing to unpack .../06-libc-dev-bin\_2.31-0ubuntu9.12\_amd64.deb ...

Unpacking libc-dev-bin (2.31-0ubuntu9.12) ...

Selecting previously unselected package linux-libc-dev:amd64.

Preparing to unpack .../07-linux-libc-dev\_5.4.0-167.184\_amd64.deb ...

Unpacking linux-libc-dev:amd64 (5.4.0-167.184) ...

Selecting previously unselected package libcrypt-dev:amd64.

Preparing to unpack .../08-libcrypt-dev\_1%3a4.4.10-10ubuntu4\_amd64.deb ...

Unpacking libcrypt-dev:amd64 (1:4.4.10-10ubuntu4) ...

Selecting previously unselected package libc6-dev:amd64.

Preparing to unpack .../09-libc6-dev\_2.31-0ubuntu9.12\_amd64.deb ...

Unpacking libc6-dev:amd64 (2.31-0ubuntu9.12) ...

Selecting previously unselected package libitm1:amd64.

Preparing to unpack .../10-libitm1\_10.5.0-1ubuntu1\~20.04\_amd64.deb ...

Unpacking libitm1:amd64 (10.5.0-1ubuntu1\~20.04) ...

Selecting previously unselected package libasan5:amd64.

Preparing to unpack .../11-libasan5\_9.4.0-1ubuntu1\~20.04.2\_amd64.deb ...

Unpacking libasan5:amd64 (9.4.0-1ubuntu1\~20.04.2) ...

Selecting previously unselected package liblsan0:amd64.

Preparing to unpack .../12-liblsan0\_10.5.0-1ubuntu1\~20.04\_amd64.deb ...

Unpacking liblsan0:amd64 (10.5.0-1ubuntu1\~20.04) ...

Selecting previously unselected package libtsan0:amd64.

Preparing to unpack .../13-libtsan0\_10.5.0-1ubuntu1\~20.04\_amd64.deb ...

Unpacking libtsan0:amd64 (10.5.0-1ubuntu1\~20.04) ...

Selecting previously unselected package libubsan1:amd64.

Preparing to unpack .../14-libubsan1\_10.5.0-1ubuntu1\~20.04\_amd64.deb ...

Unpacking libubsan1:amd64 (10.5.0-1ubuntu1\~20.04) ...

Selecting previously unselected package libquadmath0:amd64.

Preparing to unpack .../15-libquadmath0\_10.5.0-1ubuntu1\~20.04\_amd64.deb ...

Unpacking libquadmath0:amd64 (10.5.0-1ubuntu1\~20.04) ...

Selecting previously unselected package libgcc-9-dev:amd64.

Preparing to unpack .../16-libgcc-9-dev\_9.4.0-1ubuntu1\~20.04.2\_amd64.deb ...

Unpacking libgcc-9-dev:amd64 (9.4.0-1ubuntu1\~20.04.2) ...

Selecting previously unselected package gcc-9.

Preparing to unpack .../17-gcc-9\_9.4.0-1ubuntu1\~20.04.2\_amd64.deb ...

Unpacking gcc-9 (9.4.0-1ubuntu1\~20.04.2) ...

Selecting previously unselected package gcc.

Preparing to unpack .../18-gcc\_4%3a9.3.0-1ubuntu2\_amd64.deb ...

Unpacking gcc (4:9.3.0-1ubuntu2) ...

Selecting previously unselected package libstdc++-9-dev:amd64.

Preparing to unpack .../19-libstdc++-9-dev\_9.4.0-1ubuntu1\~20.04.2\_amd64.deb ...

Unpacking libstdc++-9-dev:amd64 (9.4.0-1ubuntu1\~20.04.2) ...

Selecting previously unselected package g++-9.

Preparing to unpack .../20-g++-9\_9.4.0-1ubuntu1\~20.04.2\_amd64.deb ...

Unpacking g++-9 (9.4.0-1ubuntu1\~20.04.2) ...

Selecting previously unselected package g++.

Preparing to unpack .../21-g++\_4%3a9.3.0-1ubuntu2\_amd64.deb ...

Unpacking g++ (4:9.3.0-1ubuntu2) ...

Selecting previously unselected package make.

Preparing to unpack .../22-make\_4.2.1-1.2\_amd64.deb ...

Unpacking make (4.2.1-1.2) ...

Selecting previously unselected package dpkg-dev.

Preparing to unpack .../23-dpkg-dev\_1.19.7ubuntu3.2\_all.deb ...

Unpacking dpkg-dev (1.19.7ubuntu3.2) ...

Selecting previously unselected package build-essential.

Preparing to unpack .../24-build-essential\_12.8ubuntu1.1\_amd64.deb ...

Unpacking build-essential (12.8ubuntu1.1) ...

Selecting previously unselected package libfakeroot:amd64.

Preparing to unpack .../25-libfakeroot\_1.24-1\_amd64.deb ...

Unpacking libfakeroot:amd64 (1.24-1) ...

Selecting previously unselected package fakeroot.

Preparing to unpack .../26-fakeroot\_1.24-1\_amd64.deb ...

Unpacking fakeroot (1.24-1) ...

Selecting previously unselected package libalgorithm-diff-perl.

Preparing to unpack .../27-libalgorithm-diff-perl\_1.19.03-2\_all.deb ...

Unpacking libalgorithm-diff-perl (1.19.03-2) ...

Selecting previously unselected package libalgorithm-diff-xs-perl.

Preparing to unpack .../28-libalgorithm-diff-xs-perl\_0.04-6\_amd64.deb ...

Unpacking libalgorithm-diff-xs-perl (0.04-6) ...

Selecting previously unselected package libalgorithm-merge-perl.

Preparing to unpack .../29-libalgorithm-merge-perl\_0.08-3\_all.deb ...

Unpacking libalgorithm-merge-perl (0.08-3) ...

Selecting previously unselected package libexpat1-dev:amd64.

Preparing to unpack .../30-libexpat1-dev\_2.2.9-1ubuntu0.6\_amd64.deb ...

Unpacking libexpat1-dev:amd64 (2.2.9-1ubuntu0.6) ...

Selecting previously unselected package libpython3.8-dev:amd64.

Preparing to unpack .../31-libpython3.8-dev\_3.8.10-0ubuntu1\~20.04.8\_amd64.deb ..

.

Unpacking libpython3.8-dev:amd64 (3.8.10-0ubuntu1\~20.04.8) ...

Selecting previously unselected package libpython3-dev:amd64.

Preparing to unpack .../32-libpython3-dev\_3.8.2-0ubuntu2\_amd64.deb ...

Unpacking libpython3-dev:amd64 (3.8.2-0ubuntu2) ...

Selecting previously unselected package manpages-dev.

Preparing to unpack .../33-manpages-dev\_5.05-1\_all.deb ...

Unpacking manpages-dev (5.05-1) ...

Selecting previously unselected package python-pip-whl.

Preparing to unpack .../34-python-pip-whl\_20.0.2-5ubuntu1.10\_all.deb ...

Unpacking python-pip-whl (20.0.2-5ubuntu1.10) ...

Selecting previously unselected package zlib1g-dev:amd64.

Preparing to unpack .../35-zlib1g-dev\_1%3a1.2.11.dfsg-2ubuntu1.5\_amd64.deb ...

Unpacking zlib1g-dev:amd64 (1:1.2.11.dfsg-2ubuntu1.5) ...

Selecting previously unselected package python3.8-dev.

Preparing to unpack .../36-python3.8-dev\_3.8.10-0ubuntu1\~20.04.8\_amd64.deb ...

Unpacking python3.8-dev (3.8.10-0ubuntu1\~20.04.8) ...

Selecting previously unselected package python3-distutils.

Preparing to unpack .../37-python3-distutils\_3.8.10-0ubuntu1\~20.04\_all.deb ...

Unpacking python3-distutils (3.8.10-0ubuntu1\~20.04) ...

Selecting previously unselected package python3-dev.

Preparing to unpack .../38-python3-dev\_3.8.2-0ubuntu2\_amd64.deb ...

Unpacking python3-dev (3.8.2-0ubuntu2) ...

Selecting previously unselected package python3-setuptools.

Preparing to unpack .../39-python3-setuptools\_45.2.0-1ubuntu0.1\_all.deb ...

Unpacking python3-setuptools (45.2.0-1ubuntu0.1) ...

Selecting previously unselected package python3-wheel.

Preparing to unpack .../40-python3-wheel\_0.34.2-1ubuntu0.1\_all.deb ...

Unpacking python3-wheel (0.34.2-1ubuntu0.1) ...

Selecting previously unselected package python3-pip.

Preparing to unpack .../41-python3-pip\_20.0.2-5ubuntu1.10\_all.deb ...

Unpacking python3-pip (20.0.2-5ubuntu1.10) ...

Setting up python3-distutils (3.8.10-0ubuntu1\~20.04) ...

Setting up manpages-dev (5.05-1) ...

Setting up python3-setuptools (45.2.0-1ubuntu0.1) ...

Setting up libalgorithm-diff-perl (1.19.03-2) ...

Setting up binutils-common:amd64 (2.34-6ubuntu1.6) ...

Setting up linux-libc-dev:amd64 (5.4.0-167.184) ...

Setting up libctf-nobfd0:amd64 (2.34-6ubuntu1.6) ...

Setting up python3-wheel (0.34.2-1ubuntu0.1) ...

Setting up libfakeroot:amd64 (1.24-1) ...

Setting up fakeroot (1.24-1) ...

update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (

fakeroot) in auto mode

Setting up libasan5:amd64 (9.4.0-1ubuntu1\~20.04.2) ...

Setting up make (4.2.1-1.2) ...

Setting up libquadmath0:amd64 (10.5.0-1ubuntu1\~20.04) ...

Setting up libubsan1:amd64 (10.5.0-1ubuntu1\~20.04) ...

Setting up libcrypt-dev:amd64 (1:4.4.10-10ubuntu4) ...

Setting up python-pip-whl (20.0.2-5ubuntu1.10) ...

Setting up libbinutils:amd64 (2.34-6ubuntu1.6) ...

Setting up libc-dev-bin (2.31-0ubuntu9.12) ...

Setting up libalgorithm-diff-xs-perl (0.04-6) ...

Setting up liblsan0:amd64 (10.5.0-1ubuntu1\~20.04) ...

Setting up libitm1:amd64 (10.5.0-1ubuntu1\~20.04) ...

Setting up libalgorithm-merge-perl (0.08-3) ...

Setting up libtsan0:amd64 (10.5.0-1ubuntu1\~20.04) ...

Setting up libctf0:amd64 (2.34-6ubuntu1.6) ...

Setting up libgcc-9-dev:amd64 (9.4.0-1ubuntu1\~20.04.2) ...

Setting up python3-pip (20.0.2-5ubuntu1.10) ...

Setting up libc6-dev:amd64 (2.31-0ubuntu9.12) ...

Setting up binutils-x86-64-linux-gnu (2.34-6ubuntu1.6) ...

Setting up libstdc++-9-dev:amd64 (9.4.0-1ubuntu1\~20.04.2) ...

Setting up binutils (2.34-6ubuntu1.6) ...

Setting up dpkg-dev (1.19.7ubuntu3.2) ...

Setting up libexpat1-dev:amd64 (2.2.9-1ubuntu0.6) ...

Setting up libpython3.8-dev:amd64 (3.8.10-0ubuntu1\~20.04.8) ...

Setting up zlib1g-dev:amd64 (1:1.2.11.dfsg-2ubuntu1.5) ...

Setting up gcc-9 (9.4.0-1ubuntu1\~20.04.2) ...

Setting up libpython3-dev:amd64 (3.8.2-0ubuntu2) ...

Setting up gcc (4:9.3.0-1ubuntu2) ...

Setting up g++-9 (9.4.0-1ubuntu1\~20.04.2) ...

Setting up python3.8-dev (3.8.10-0ubuntu1\~20.04.8) ...

Setting up g++ (4:9.3.0-1ubuntu2) ...

update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mo

de

Setting up build-essential (12.8ubuntu1.1) ...

Setting up python3-dev (3.8.2-0ubuntu2) ...

Processing triggers for man-db (2.9.1-1) ...

Processing triggers for libc-bin (2.31-0ubuntu9.12) …

**Verify Installation**    
```
pip3 --version
```
**Output:-**

pip 20.0.2 from /usr/lib/python3/dist-packages/pip (python 3.8)

 ## 3.**Install Selenium**
 ```
   pip3 install selenium
```

**Output:-**

Collecting selenium

  Downloading selenium-4.15.2-py3-none-any.whl (10.2 MB)

  |████████████████████████████████| 10.2 MB 511 kB/s

Collecting trio-websocket\~=0.9

  Downloading trio\_websocket-0.11.1-py3-none-any.whl (17 kB)

Collecting trio\~=0.17

  Downloading trio-0.23.1-py3-none-any.whl (448 kB)

  |████████████████████████████████| 448 kB 570 kB/s

Collecting urllib3\[socks]<3,>=1.26

  Downloading urllib3-2.1.0-py3-none-any.whl (104 kB)

  |████████████████████████████████| 104 kB 821 kB/s

Collecting certifi>=2021.10.8

  Downloading certifi-2023.11.17-py3-none-any.whl (162 kB)

  |████████████████████████████████| 162 kB 863 kB/s

Collecting exceptiongroup; python\_version < "3.11"

  Downloading exceptiongroup-1.2.0-py3-none-any.whl (16 kB)

Collecting wsproto>=0.14

  Downloading wsproto-1.2.0-py3-none-any.whl (24 kB)

Requirement already satisfied: idna in /usr/lib/python3/dist-packages (from trio\~=0.17->selenium) (2.8)

Collecting sniffio>=1.3.0

  Downloading sniffio-1.3.0-py3-none-any.whl (10 kB)

Collecting attrs>=20.1.0

  Downloading attrs-23.1.0-py3-none-any.whl (61 kB)

  |████████████████████████████████| 61 kB 897 kB/s

Collecting sortedcontainers

  Downloading sortedcontainers-2.4.0-py2.py3-none-any.whl (29 kB)

Collecting outcome

  Downloading outcome-1.3.0.post0-py2.py3-none-any.whl (10 kB)

Collecting pysocks!=1.5.7,<2.0,>=1.5.6; extra == "socks"

  Downloading PySocks-1.7.1-py3-none-any.whl (16 kB)

Collecting h11<1,>=0.9.0

  Downloading h11-0.14.0-py3-none-any.whl (58 kB)

  |████████████████████████████████| 58 kB 558 kB/s

Installing collected packages: exceptiongroup, h11, wsproto, sniffio, attrs, sortedcontainers, outcome, trio, trio-websocket, pysocks, urllib3, certifi, selenium

Successfully installed attrs-23.1.0 certifi-2023.11.17 exceptiongroup-1.2.0 h11-0.14.0 outcome-1.3.0.post0 pysocks-1.7.1 selenium-4.15.2 sniffio-1.3.0 sortedcontainers-2.4.0 trio-0.23.1 trio-websocket-0.11.1 urllib3-2.1.0 wsproto-1.2.0

**Verify Installation**    -
```
pip3 show selenium
```
**Output:-**

Name: selenium

Version: 4.15.2

Summary: None

Home-page: https\://www\.selenium.dev

Author: None

Author-email: None

License: Apache 2.0

Location: /home/aakash/.local/lib/python3.8/site-packages

Requires: trio-websocket, urllib3, certifi, trio

Required-by:

## 4.**Install Pycharm**
   ```
    sudo snap install pycharm-community --classic
```
**Output:-**

pycharm-community 2023.2.5 from jetbrains\*\* installed


##   

 ## 5. **Install Robot Framework**
```
   pip3 install robotframework
   ```

**Output:-**

Collecting robotframework

  Downloading robotframework-6.1.1-py3-none-any.whl (699 kB)

  |████████████████████████████████| 699 kB 1.2 MB/s

Installing collected packages: robotframework

  WARNING: The scripts libdoc, rebot and robot are installed in '/home/aakash/.local/bin' which is not on PATH.

  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.

Successfully installed robotframework-6.1.1

## 6.**Install Robot Framework Selenium**
```
 pip3 install robotframework-seleniumlibrary
```
**Output:-**

Collecting robotframework-seleniumlibrary

  Downloading robotframework\_seleniumlibrary-6.2.0-py2.py3-none-any.whl (95 kB)

  |████████████████████████████████| 95 kB 840 kB/s

Requirement already satisfied: selenium>=4.3.0 in ./.local/lib/python3.8/site-packages (from robotframework-seleniumlibrary) (4.15.2)

Collecting robotframework-pythonlibcore>=3.0.0

  Downloading robotframework\_pythonlibcore-4.3.0-py2.py3-none-any.whl (10 kB)

Requirement already satisfied: robotframework>=4.1.3 in ./.local/lib/python3.8/site-packages (from robotframework-seleniumlibrary) (6.1.1)

Requirement already satisfied: trio\~=0.17 in ./.local/lib/python3.8/site-packages (from selenium>=4.3.0->robotframework-seleniumlibrary) (0.23.1)

Requirement already satisfied: certifi>=2021.10.8 in ./.local/lib/python3.8/site-packages (from selenium>=4.3.0->robotframework-seleniumlibrary) (2023.11.17)

Requirement already satisfied: trio-websocket\~=0.9 in ./.local/lib/python3.8/site-packages (from selenium>=4.3.0->robotframework-seleniumlibrary) (0.11.1)

Requirement already satisfied: urllib3\[socks]<3,>=1.26 in ./.local/lib/python3.8/site-packages (from selenium>=4.3.0->robotframework-seleniumlibrary) (2.1.0)

Requirement already satisfied: sniffio>=1.3.0 in ./.local/lib/python3.8/site-packages (from trio\~=0.17->selenium>=4.3.0->robotframework-seleniumlibrary) (1.3.0)

Requirement already satisfied: attrs>=20.1.0 in ./.local/lib/python3.8/site-packages (from trio\~=0.17->selenium>=4.3.0->robotframework-seleniumlibrary) (23.1.0)

Requirement already satisfied: outcome in ./.local/lib/python3.8/site-packages (from trio\~=0.17->selenium>=4.3.0->robotframework-seleniumlibrary) (1.3.0.post0)

Requirement already satisfied: idna in /usr/lib/python3/dist-packages (from trio\~=0.17->selenium>=4.3.0->robotframework-seleniumlibrary) (2.8)

Requirement already satisfied: sortedcontainers in ./.local/lib/python3.8/site-packages (from trio\~=0.17->selenium>=4.3.0->robotframework-seleniumlibrary) (2.4.0)

Requirement already satisfied: exceptiongroup>=1.0.0rc9; python\_version < "3.11" in ./.local/lib/python3.8/site-packages (from trio\~=0.17->selenium>=4.3.0->robotframework-seleniumlibrary) (1.2.0)

Requirement already satisfied: wsproto>=0.14 in ./.local/lib/python3.8/site-packages (from trio-websocket\~=0.9->selenium>=4.3.0->robotframework-seleniumlibrary) (1.2.0)

Requirement already satisfied: pysocks!=1.5.7,<2.0,>=1.5.6; extra == "socks" in ./.local/lib/python3.8/site-packages (from urllib3\[socks]<3,>=1.26->selenium>=4.3.0->robotframework-seleniumlibrary) (1.7.1)

Requirement already satisfied: h11<1,>=0.9.0 in ./.local/lib/python3.8/site-packages (from wsproto>=0.14->trio-websocket\~=0.9->selenium>=4.3.0->robotframework-seleniumlibrary) (0.14.0)

Installing collected packages: robotframework-pythonlibcore, robotframework-seleniumlibrary

Successfully installed robotframework-pythonlibcore-4.3.0 robotframework-seleniumlibrary-6.2.0

## 7. **Install Robot Framework-Datadriver -**
```
  pip3 install robotframework-datadriver
```
**Output:-**

Collecting robotframework-datadriver

  Downloading robotframework\_datadriver-1.9.0-py3-none-any.whl (52 kB)

  |████████████████████████████████| 52 kB 491 kB/s

Requirement already satisfied: robotframework>=4.0.2 in ./.local/lib/python3.8/site-packages (from robotframework-datadriver) (6.1.1)

Collecting Pygments

  Downloading pygments-2.17.2-py3-none-any.whl (1.2 MB)

  |████████████████████████████████| 1.2 MB 677 kB/s

Collecting docutils

  Downloading docutils-0.20.1-py3-none-any.whl (572 kB)

  |████████████████████████████████| 572 kB 792 kB/s

Installing collected packages: Pygments, docutils, robotframework-datadriver

  WARNING: The script pygmentize is installed in '/home/aakash/.local/bin' which is not on PATH.

  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.

  WARNING: The script docutils is installed in '/home/aakash/.local/bin' which is not on PATH.

  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.

Successfully installed Pygments-2.17.2 docutils-0.20.1 robotframework-datadriver-1.9.0

 ## 8.**Install Required Packages in Pycharm:-**

<!---->

1. Selenium
2. Robotframework
3. robotframework-seleniumlibrary

![](https://lh7-us.googleusercontent.com/Lq87ud1fOVMw8f-7MPYXvnrmPh3qlULYG8JUIgRHbGpjkX9nZgb9p3qD8IGiD65NuuFn4FM7h6kyWrj1zezm6Vu9cYq2Nw7MZT4WiOT83j3rI0dGFIgigxYzphRncUzMFHbO02G93Sq4HYwXGlhBlKA)


## Writing your first Test case in Robot framework

Create a file under ‘Tests’ folder with .robot extension. The **.robot** files are considered as Test Suites by Robot Framework.

![](https://lh7-us.googleusercontent.com/a07SabbjP-S9omueA9Z5d5-PK1tikNMqgTE7o7wgrNMq7YtortPG5q--s2bZ77nbkgRJu5bHWuC8Qmthfwf9vffQaPKG6CmiEv_JtAr-kz_oA7Q_KjCtzLjUz0uFTIXwDB7qXQRn0kYy54C-h9L44Fk)

 **Now we will write our tests.**

    *** Settings ***
    Library    SeleniumLibrary

<!---->

    *** Variables ***
    ${browser}      chrome
    ${url}         https://demo.nopcommerce.com

<!---->

    *** Test Cases ***
    TestingInputbox
       Open Browser    ${url}    ${browser}
       Maximize Browser Window
       Title Should Be    nopCommerce demo store
       Click Link    xpath://a[@class='ico-login']
       ${emailLocator}    Set Variable    id:Email
       ${PasswordLocator}    Set Variable    id:Password

<!---->

       Wait Until Element Is Visible    ${emailLocator}
       Wait Until Element Is Visible     ${PasswordLocator}
       Element Should Be Enabled    ${emailLocator}
        Element Should Be Enabled     ${PasswordLocator}

<!---->

       Input Text    ${emailLocator}    amanvats402@gmail.com
         Input Text    ${PasswordLocator}    Aman@123
       Sleep    5
       Clear Element Text    ${emailLocator}
       Clear Element Text    ${PasswordLocator}
       Sleep    3
    #    Click Element    xpath://input[@class='button-1 login-button']
       Close Browser

**Output:-**

(venv) aakash\@aakash-Aspire-A715-75G:\~/PycharmProjects/pythonProject$ robot Testcases/TC.robot

\==============================================================================

TC                                                                        

\==============================================================================

TestingInputbox                                                   | PASS |

\------------------------------------------------------------------------------

TC                                                                | PASS |

1 test, 1 passed, 0 failed

\==============================================================================

Output:  /home/aakash/PycharmProjects/pythonProject/output.xml

Log: /home/aakash/PycharmProjects/pythonProject/log.html

Report:  /home/aakash/PycharmProjects/pythonProject/report.html

## Writing your Second Test case in Robot framework

**Robot File:-**

    *** Settings ***
    Library    SeleniumLibrary
    Resource    ../Resources/LogIn_Resources.robot
    Suite Setup    Open My Browser
    Suite Teardown    Close Browsers
    Test Template      Invalid User

<!---->

    *** Test Cases ***        username        Password
    Right username empty Password        Aman-Sharma-au49        ${EMPTY}
    Right username Wrong Password        Aman-Sharma-au49        aman
    Wrong username empty Password        Aman-Sharma       ${EMPTY} 
    Wrong username Wrong Password        Aman-Sharma        vats
    Empty username empty password        ${EMPTY}        ${EMPTY}
    #Right username Right password        Aman-Sharma-au49        Aman@639
       Sleep    3

<!---->

    *** Keywords ***
    Invalid User
       [Arguments]    ${username}    ${Password}
       Input Username       ${username}
       Input pwd       ${Password}
       Click Login Button
       Error Massege Should be visible

     

**Resources Files:-**

    *** Settings ***
    Library    SeleniumLibrary

<!---->

    *** Variables ***
    ${logURL}        https://github.com/login
    ${Browser}        Chrome

<!---->

    *** Keywords ***
    Open My Browser
       Open Browser        ${logURL}        ${Browser}
       Maximize Browser Window

<!---->

    Close Browsers
       Close All Browsers

<!---->

    Open Login Page
       Go To    ${LOGIN URL}

<!---->

    Input Username
       [Arguments]    ${username}
       Input Text    name:login        ${username}

<!---->

    Input pwd
       [Arguments]    ${Password}
       Input Text    name:password       ${Password}

<!---->

    Click Login Button
       Click Element    xpath://*[@id="login"]/div[4]/form/div/input[13]

<!---->

    Click logOut Button
       Click Link    logOut

<!---->

    Error Massege Should be visible
       Page Should Contain    Incorrect username or password

<!---->

    Dashbord Page Should be visible
       Page Should Contain    Dashbord

**Output:-**

 ****aman\@aman-Mi-NoteBook-Horizon-Edition-14:\~/PycharmProjects/pythonProject1$ robot Testcases/DataDriven.robot

\==============================================================================

DataDriven                                                                    

\==============================================================================

Right username empty Password                                         | PASS |

\------------------------------------------------------------------------------

Right username Wrong Password                                         | PASS |

\------------------------------------------------------------------------------

Wrong username empty Password                                         | PASS |

\------------------------------------------------------------------------------

Wrong username Wrong Password                                         | PASS |

\------------------------------------------------------------------------------

Empty username empty password                                         | PASS |

\------------------------------------------------------------------------------

DataDriven                                                            | PASS |

5 tests, 5 passed, 0 failed

\==============================================================================

Output:  /home/aman/PycharmProjects/pythonProject1/output.xml

Log:     /home/aman/PycharmProjects/pythonProject1/log.html

Report:  /home/aman/PycharmProjects/pythonProject1/report.html
