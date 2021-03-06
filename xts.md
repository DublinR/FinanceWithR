%%- https://cran.r-project.org/web/packages/xts/vignettes/xts.pdf

## The structure of xts
To understand a bit more of what an xts object can do, it may be beneficial to
know what an xts object is. This section is intended to provide a quick overview
of the basics of the class, as well as what features make it unique.

#### 2.1 It’s a zoo in here
At the core of an xts object is a zoo object from the package of the same
name. Simplified, this class contains an array of values comprising your data
(often in matrix form) and an index attribute to provide information about the
data’s ordering. Most of the details surrounding zoo objects apply equally to
xts. As it would be redundent to simply retell the excellent introductory zoo
vignette, the reader is advised to read, absorb, and re-read that documentation
to best understand the power of this class. 

The authors of the xts package
recognize that zoo’s strength comes from its simplicity of use, as well as its
overall flexibility. What motivated the xts extension was a desire to have even
more flexibility, while imposing reasonable constraints to make this class into a
true time-based one.

#### 2.2 xts modifications
Objects of class xts differ from objects of class zoo in three key ways: the use
of formal time-based classes for indexing, internal xts properties, and perhaps
most uniquely — user-added attributes.

#### True time-based indexes
To allow for functions that make use of xts objects as a general time-series
object - it was necessary to impose a simple rule on the class. The index of each
xts object must be of a known and supported time or date class. At present
this includes any one of the following - Date, POSIXct, chron, yearmon, yearqtr,
or timeDate. 
The relative merits of each are left to the judgement of the user,
though the first three are expected to be sufficient for most applications.
Internal attributes: .CLASS, .ROWNAMES, etc.

In order for one major feature of the xts class to be possible - the conversion and
re-conversion of classes to and from xts - certain elements must be preserved
within the converted object. These are for internal use, and as such require
little further explanation in an introductory document. Interested readers are
invited to examine the source as well as read the developer documentation.

#### xtsAttributes
This is what makes the xts class an extensible time-series class. Arbitrary attributes
may be assigned and removed from the object without causing issues
with the data’s display or otherwise. Additionally this is where other class specific
attributes (e.g. FinCenter from timeSeries) are stored during conversion
to an xts object so they may be restored with reclass.
