# Codeschnipsel

## XML
### Inline
**Eingabeformat**
```
<Users>
`	<User id="123" userName="jdoe" firstName="John" lastName="Doe" emailAddress="john.doe@example.com"/>
</Users>
```

**Code**
```
use strict;
use warnings;
use XML::LibXML;

my $filename = $ARGV[0];

my $parser = XML::LibXML->new();
my $doc    = $parser->parse_file($filename);
my $xc = XML::LibXML::XPathContext->new( $doc->documentElement()  );

foreach my $sections ($xc->findnodes('/Users/User'))
{
  my($id) = $sections->getAttribute('id');
  my($firstName) = $sections->getAttribute('firstName');
  my($lastName) = $sections->getAttribute('lastName');
  my($emailAddress) = $sections->getAttribute('emailAddress');

  print $username.";".$firstName.";".$lastName.";".$emailAddress."\n";
}
```
