All of these functions expect valid UTF-8 data. Therefore the first step in your application is to filter incoming data to insure it's valid.

    $utf8_text = to_utf8($_POST['text']);

From there on you can be sure that $utf8_text is valid UTF-8 and can be stored in your database or parsed by your application. 

If using a database make sure to set the the proper connection encoding (MySQL example):

    mysql_query('SET NAMES utf8');

Make sure to HTML encode *everything you show to the user*. This prevents XSS and CSFR attempts:

    print htmlspecialchars($utf8_text, ENT_QUOTES, 'utf-8');

Also make sure to send the proper UTF-8 header if you are displaying HTML:

    //Sending UTF-8 HTML data
    header('Content-Type: text/html; charset=utf-8');

Have fun!
[David Pennington](http://xeoncross.com)