# fuff
FFUF is a powerful and fast tool for discovering hidden parts of a website by automating the process of testing many different inputs against a web server and analyzing the responses.Here’s a simple explanation of how it works and what it does:


Purpose:

FFUF helps in discovering hidden elements of a website that are not easily accessible or visible. This is particularly useful for security testing and bug hunting.

Fuzzing:

It automates the process of sending numerous requests to a web server with different inputs (like potential directory names or file names) to see how the server responds. This helps in uncovering directories, files, or parameters that are not linked directly on the site but still accessible.

Speed:

One of the key features of FFUF is its speed. It’s designed to be fast and efficient, making it capable of handling large wordlists and high volumes of requests quickly.

Usage:

To use FFUF, you typically provide a URL and a wordlist. The wordlist contains potential directory or file names. FFUF then replaces a placeholder in the URL with each entry from the wordlist and checks the server's response.

Command Example:

ffuf -u http://example.com/FUZZ -w wordlist.txt

-u http://example.com/FUZZ: The target URL where FUZZ is the placeholder.

-w wordlist.txt: The wordlist file containing different names to test.

Results: FFUF provides feedback on which inputs lead to valid responses from the server. These responses might indicate the presence of hidden files or directories.

Customization:

FFUF offers various options to customize the fuzzing process, such as specifying HTTP methods, headers, cookies, and filtering responses based on status codes, response size, or words.

How to install fuff in kali linux:

Command:sudo apt-get install ffuf

![ffuf1](https://github.com/HarikaReddy20/fuff/assets/160827002/7ead45ab-b36c-427b-a824-e4158303c2ab)

Use the command:ffuf -h.We can find the help page we can explore the tool with this command.

![ffuf2](https://github.com/HarikaReddy20/fuff/assets/160827002/8191661a-a84e-4a54-8f8d-8ead0a32da97)

fuff offers many options for fuzzing.

To specify the position to be fuzzed, use the word "FUZZ" in the ffuf command.

Directory and File Discovery You can find directories on a website with the following command. It uses the -w flag to provide a wordlist and the -u flag to specify the URL with "FUZZ" as the placeholder for fuzzing.

ffuf -w wordlist.txt -u http://website.com/FUZZ

For file discovery, you can use the same command. To include specific file extensions from the wordlist, use the -e flag.

ffuf -w wordlist.txt -u http://website.com/FUZZ -e .aspx,.html,.php,.txt

![image](https://github.com/HarikaReddy20/fuff/assets/160827002/c4d10ad3-b9ee-43ae-b5bb-086b068534e0)

image ffuf offers options to filter responses by specific status codes, line counts, response sizes, word counts, and regex patterns.

Filtering Options -mc: Status code -ml: Number of lines in the response -mr: Regex pattern -ms: Response size -mw: Number of words in the response Examples

To get responses with status codes 200 and 302, use: Command : ffuf -w wordlist.txt -u http://website.com/FUZZ -e .aspx,.html -mc 200,302 Recursion

URL parameters ending with FUZZ support recursion. The -recursion flag activates this, allowing ffuf to fuzz URLs and then fuzz further within the directories it discovers. -recursion-depth: Specifies the depth of recursion -maxtime: Sets a maximum time in seconds for the fuzzing process -maxtime-job: Used with -recursion to set a maximum time for each new job created per directory found

Example for a maximum fuzzing time of 60 seconds:

Command : ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u https://geeksforgeeks.org/FUZZ -maxtime 60

![ffuf3](https://github.com/HarikaReddy20/fuff/assets/160827002/6402bfb4-7a3f-41f0-8476-9a28a0970a0b)


Example:

Command: ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u https://geeksforgeeks.org/FUZZ

In this example, We are fuzzing the directories of geeksforgeeks.org target domain.

![ffuf4](https://github.com/HarikaReddy20/fuff/assets/160827002/93e9cd19-92af-4d86-a0a5-ebb9d9c4dd50)
