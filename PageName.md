# Introduction #
This PHP class is designed to accept a v0.1 OpenURL and convert the output into
Downloadable RIS file for importing into Endnote and other citation
management software.  It will map most of the OpenURL fields specified
in the 0.1 specification, but does not support the OpenURL 1.0 standards.


# Details #

The script does contain a few areas of custom logic, namely it will try to automatically
determine the material type if the genre field is omitted.  If the item does
not have either an ISSN, ISBN, or a genre supplied, it will simply default
to book.  Also, it will try a few attempts to get a date from the OpenURL,
as well as the author name.

It currently does not support multiple author names, unless they are supplied
via a concatenated author field in the OpenURL.

The class is provided with a citation.php file that accepts the OpenURL,
and produces the file for download.  The use of the class is as follows:

$ris = new RIS(SANTIZED\_OPENURL\_GET\_ARRAY, ["Title of provider"]);
//instantiate the class with the OpenURL array and the provider title

echo($ris->output());  //Prints to screen, not typically used but useful for debugging
$ris->download();	   //Creates download file to browser

NOTE: The OpenURL should be passed to the class as a _GET array, but it should
be sanitized for security.  Some basic sanitization is provided, but you will
likely want to expand this to fit your institutional specifications._

For more information, please contact WSULS Developer Librarian Paul Gallagher @ paul.gallagher@wayne.edu