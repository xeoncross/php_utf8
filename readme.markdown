## PHP UTF-8

A simple collection of functions to provide a standardized framework for working with multibyte strings (like UTF-8) in a variety of server environments. Requires either the [mbstring](http://php.net/mbstring) or [iconv](http://php.net/iconv) extensions to work!

## Function List

The following functions are included in this file to support most application needs when dealing with UTF-8 data.

 * mb_str_split()
 * mb_substr_replace()
 * mb_strrev()
 * is_ascii()
 * seems_utf8()
 * remove_accents()
 * sanitize()
 * sanitize_url()
 * sanitize_filename()
 * encode()

If the [mbstring PHP extension](http://php.net/mbstring) is not loaded then the following functions are also created:

 * mb_strlen()
 * mb_substr()
 * mb_strpos()
 * mb_strrpos()
 * mb_strtolower()
 * mb_strtoupper()

## Using UTF-8 in your application

All of these functions expect valid UTF-8 data. Therefore the first step in your application is to filter incoming data to insure it's valid.

    $utf8_text = encode($_POST['text']);

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