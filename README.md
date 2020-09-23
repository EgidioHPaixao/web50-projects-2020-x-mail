# web50-projects-2020-x-mail
CS50W projetct 3 - Design a front-end for an email client that makes API calls to send and receive emails.



### Troubleshoots

#### Console.log isn't working

Refresh the page using CTRL + F5

#### Uncaught (in promise) SyntaxError: Unexpected token < in JSON at position 0

When I was getting any e-mail (sent, inbox, archive), It wasn't working.
The reason was the strftime function in models.py. The format of the string uses codes like "%-d" and "%-I".
But this codes with "-" (hyphen or dash sign) doesn't work on Windows. Instead, I had to replace them for "#". So "%#d" and "%#I" works on Windows.