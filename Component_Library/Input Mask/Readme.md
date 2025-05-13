Description

This Power Apps component is a simple text input that applies formatting to a phone number after each keystroke.  The text input only allows numbers to be entered.

Here's how it works:

The app developer defines the phone number format as "(###) ###-####"
A user opens the app and types a phone number as 2049876543
The text input shows (204) 987-6543
 

Give a Thumbs Up if you like the component to make it easier for others to find

Follow me on Twitter for Power Apps tips & articles https://twitter.com/mattbdevaney 

Send me a message if you find any bugs and I will fix them as quickly as possible


Phone Number Input Mask Properties

The Phone Number input mask shares the same properties as a Text Input along with 4 new properties.

InputMask (input property) - A text string that defines the phone number formatting to be applied

InputMaskMultipleFormats (input property) - A table that defines multiple phone number for countries with more than one phone number format.  To use this property the InputMask field must be blank.

PhoneNumber (output property) - A unformatted text string with all digits in the phone number

 

Text (output property) - A text string with the formatting phone number.


Example - Single Phone Number Format


To format a phone number for a country in the table below use the following values InputMask property.

 

Country	Example	InputMask
Canada	204-998-8344	"###-###-####"
US	(204) 998-8344	"(###) ###-####"
United Kingdom    	+44 1234 567890    	"+## #### ######"    
Japan	(03)-4567-1234	"(##)-####-####"
India	+91 0123 456789	"+## ####-######"


Example - Multiple Phone Number Formats

 

Here's how UK phone number formatting works:

Numbers beginning 01 are 01### ######
Numbers beginning 02 are 02# #### ####
Numbers beginning 03 are 03## ### ####
Numbers beginning 07 are 07### ######
Numbers beginning 08 are 08## ### ####

All other phone numbers are ##### ######

 

Use this code in the InputMaskMultipleFormats property to define phone number formatting.  The InputMask property must be blank in order for multiple formats to appear.


Table(
 {
 Prefix: "01",
 Format: "##### ######"
 },
 {
 Prefix: "02",
 Format: "### #### ####"
 },
 {
 Prefix: "03",
 Format: "#### ### ####"
 },
 {
 Prefix: "07",
 Format: "##### ######"
 },
 {
 Prefix: "08",
 Format: "#### ### ####"
 },
 {
 Prefix: "",
 Format: "##### ######"
 }
)
 

Limitations

 

Power Apps components cannot be used in Galleries and Edit Forms.  To use this component you must create your own form and submit data using the PATCH function.  If you want to have this functionality inside of an Edit Form check out this article I wrote which shows how to build this components functionality from scratch.

Link: https://www.matthewdevaney.com/power-apps-phone-number-formatting-in-a-form-input-mask/
