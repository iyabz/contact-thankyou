<?php
 
if($_POST) {
    $visitor_name = "";
    $visitor_email = "";
    $email_title = "";
    $visitor_message = "";
     
    if(isset($_POST['visitor_name'])) {
        $visitor_name = filter_var($_POST['visitor_name'], FILTER_SANITIZE_STRING);
    }
     
    if(isset($_POST['email'])) {
        $email = str_replace(array("\r", "\n", "%0a", "%0d"), '', $_POST['visitor_email']);
        $email = filter_var($email, FILTER_VALIDATE_EMAIL);
    }
     
    if(isset($_POST['title'])) {
        $title = filter_var($_POST['title'], FILTER_SANITIZE_STRING);
    }
     
   
     
    if(isset($_POST['message'])) {
        $message = htmlspecialchars($_POST['message']);
    }
     
   
 
     
    $headers  = 'MIME-Version: 1.0' . "\r\n"
    .'Content-type: text/html; charset=utf-8' . "\r\n"
    .'From: ' . $email . "\r\n";
     
    if(mail($recipient, $title, $message, $headers)) {
        echo "<p>Thank you for reaching out, $visitor_name. I'll get back to you shortly.</p>
?>

