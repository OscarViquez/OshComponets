https://www.codingnepalweb.com/2020/09/how-to-configure-xampp-to-send-mail-from-localhost-in-php.html

How to configure XAMPP to send Mail from Localhost in PHP ?
CodingNepalSeptember 07, 202032 Comments
Facebook
Twitter

Hello readers, Today in this blog you'll learn how to send Mail from Localhost XAMPP using PHP. Simply, XAMPP is an abbreviation for cross-platform, Apache, MySQL, PHP, and Perl. XAMPP lets you work on a local server and test local copies of websites using PHP code and MySQL databases.

How to configure XAMPP to send Mail from Localhost in PHP

As a part of the experiment, developers need to send emails, and as we all know that sending mail in XAMPP through the localhost can be much more painful if we don’t know how to configure XAMPP to send mail through the localhost using Gmail.

To send mail from localhost XAMPP using Gmail, configure XAMPP after installing it. To configure the XAMPP server to send mail from the localhost, we have to make some changes in two files one is php.ini and another one is sendmail.ini.

First, go to the XAMPP installation directory and open the XAMPP folder and follow the below steps same:
1. Go to the (C:\xampp\php) and open the php.ini file then find the [mail function] with scrolling down or simply press ctrl+f to search directly.

Find the following lines and pass these values:

PHP.INI File:
[mail function]
For Win32 only.
http://php.net/smtp
SMTP=smtp.gmail.com
http://php.net/smtp-port
smtp_port=587
sendmail_from = your_email_address_here
sendmail_path = "\"C:\xampp\sendmail\sendmail.exe\" -t"



That's all for this file, save the file by pressing ctrl+s and close.

2. Now, go the (C:\xampp\sendmail) and open the sendmail.ini  then find [sendmail] with scrolling down or press ctrl+f to search directly.

Find the following lines and pass these values:

SENDMAIL.INI FILE: 
smtp_server=smtp.gmail.com
smtp_port=587
error_logfile=error.log
debug_logfile=debug.log
auth_username=your_email_address_here
auth_password=your_password_here
force_sender=your_email_address_here (it's optional)



That's all for this file, save the file by pressing ctrl+s and close.

Now, you're done with the required changes in these files. To send mail using Gmail paste the following codes in your PHP file.

PHP FILE: 
<?php
$receiver = "receiver email address here";
$subject = "Email Test via PHP using Localhost";
$body = "Hi, there...This is a test email send from Localhost.";
$sender = "From:sender email address here";

if(mail($receiver, $subject, $body, $sender)){
    echo "Email sent successfully to $receiver";
}else{
    echo "Sorry, failed while sending mail!";
}

 Copy

Important note: If your mail isn't sent and you got a warning or error. Please configure your google account security as "Less secure apps". To configure it:
- Go to your Google account then click on the Security tab and scroll down, there you can see the Less secure app access panel, Simply turn on that. This panel only shows if you haven't enabled 2-Step Verification.

If you're getting an error as a password is wrong then simply go to the sendmail.ini file and put the correct password of your that Gmail account which you've provided in sendmail_from.
