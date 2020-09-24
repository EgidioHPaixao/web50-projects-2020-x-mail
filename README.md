# web50-projects-2020-x-mail
CS50W projetct 3 - Design a front-end for an email client that makes API calls to send and receive emails.



### Troubleshoots

#### Console.log isn't working

Refresh the page using CTRL + F5

#### Uncaught (in promise) SyntaxError: Unexpected token < in JSON at position 0

When I was getting any e-mail (sent, inbox, archive), It wasn't working.
The reason was the strftime function in models.py. The format of the string uses codes like "%-d" and "%-I".
But this codes with "-" (hyphen or dash sign) doesn't work on Windows. Instead, I had to replace them for "#". So "%#d" and "%#I" works on Windows.

#### Page always refreshing after form submission

Solution: inf your javascript function, insert ``` return false ``` in the end

#### Page skipping without waiting to the event

In this project, the user click on the e-mail to view all the details. In the detailed view, the use can click on a "reply" button, to answer that e-mail. The error was: when clicking to view the details of the e-mail, the page was skipping the details page and going directly to the reply page.

Soluction (actually a mistake): it was missing ```() => ``` in the function below:
```document.getElementById('reply-email-button').addEventListener('click', () => compose_email(email) );```
Without ````() =>```, javascript won't wait the event to happen and it will execute it immediately.

#### Function being called every other time 

After I send an e-mail, the page loads the list of sent e-mails. In the first time, the list updates with the recent email created.
If I do the same (create and send an-email), the list doesn't show the new e-mail (even though it's created in the database). It will work only in the following request.

Solution: add ```localStorage.clear();``` before calling the method to get the e-mails. I believe the browser doesn't execute the request because the last request was still recent and, thus, it can reuse the same old response saved locally.