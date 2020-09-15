Consumers of FIXM information may not need, and/or may not be able to
process and interpret extension data supplementing a core FIXM dataset.

Using XSLTs is one approach for removing unwanted Extension data (known
or unknown) from a FIXM XML dataset, as appropriate. An example of an
XSLT that removes all Extension content is provided below:

```xml
<?xml version="1.0" encoding="UTF-8"?> 
<xsl:stylesheet version="2.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"> 
   <xsl:output method="xml" version="1.0" encoding="UTF-8" indent="yes"/> 
   <xsl:template match="@\*\|node()"> 
      <xsl:copy> 
         <xsl:apply-templates select="@\*\|node()"/> 
      </xsl:copy> 
   </xsl:template> 
   <xsl:template match="\*:extension"/> 
</xsl:stylesheet>
```