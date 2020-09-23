<div align="center">

## PHP GTK Entry Form


</div>

### Description

Initial code for PHPGTK using GtkLabel, GtkText, GtkRadiobutton,GtkButton,GtkEntry.
 
### More Info
 
Input form using GtkLabel, GtkText,GtkRadiobutton,GtkButton,GtkEntry

Basic Entry => Name , Address , Phone , Sex

No Assumptions ..

Captures the data entered on prompt.

Will upgrade soon so it enters into database and displayed on GtkWindow widget.

No side effects :-)

You will learn more PhpGtk


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Mandar Kelkar](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/mandar-kelkar.md)
**Level**          |Advanced
**User Rating**    |4.7 (42 globes from 9 users)
**Compatibility**  |PHP 3\.0, PHP 4\.0
**Category**       |[GUIs](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/guis__8-30.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/mandar-kelkar-php-gtk-entry-form__8-604/archive/master.zip)

### API Declarations

No Copyright


### Source Code

```
<?php
/*
Simple Entry Form Using PHP GTK
Author Mandar Kelkar
Email kelkar_mandar@yahoo.com
*/
if (!class_exists('gtk')){
	strtoupper(substr(PHP_OS,0,3) == 'WIN')?dl('php_gtk.dll'):dl('php_gtk.so');
	}
//Get the initial window with specific settings
$window = &new GtkWindow();
$window->set_position(GTK_WIN_POS_CENTER);
$window->set_title("Entry Form");
$window->set_border_width(5);
//$window->set_default_size((gdk::screen_width()/4),(gdk::screen_height()-80));
$window->set_default_size(500,300);
$window->connect_object("destroy", array("gtk","main_quit"));
$window->set_policy(false, false, false);
$window->realize();
//Get GTK TABLE and add it to the window
$table = &new GtkTable(4,2);
$table->set_row_spacings(5);
$table->set_col_spacings(5);
$window->add($table);
$name = &new GtkLabel("Your Name");
/*$tp = $name->get_colormap();
$tp->alloc(235,2,2);
$name->set_colormap($tp);
$name->set_usize(20,100);*/
$name->set_justify(GTK_JUSTIFY_FILL);
$table->attach($name,0,1,0,1);
$nametext = &new GtkEntry();
$nametext->set_editable(true);
//$nametext->set_usize(20,100);
$table->attach($nametext,2,3,0,1);
$address = &new GtkLabel("Your Address");
$address->set_justify(GTK_JUSTIFY_FILL);
//$address->set_usize(20,100);
$table->attach($address,0,1,1,2);
$addresstext = &new GtkText();
$addresstext->set_editable(true);
//$addresstext->set_usize(20,100);
$table->attach($addresstext,2,3,1,2);
$phone = &new GtkLabel("Phone No");
$phone->set_justify(GTK_JUSTIFY_FILL);
$table->attach($phone,0,1,2,3);
$phoneno = &new GtkEntry();
$phoneno->set_editable(true);
$table->attach($phoneno,2,3,2,3);
$sexlabel = &new GtkLabel("Sex");
$sexlabel->set_justify(GTK_JUSTIFY_FILL);
$table->attach($sexlabel,0,1,3,4);
$male = &new GtkRadioButton(null,'Male');
$female = &new GtkRadioButton($male,"Female");
$male->set_active(true);
$male->connect('pressed','sexfunc','male');
$female->connect('pressed','sexfunc','female');
$table->attach($male,2,3,3,4);
$table->attach($female,2,3,4,5);
$submit = &new GtkButton("Submit");
$submit->connect('clicked','Showdetails');
$table->attach($submit,2,3,6,7);
function sexfunc($widget,$sexvar){
global $varsex;
$varsex = $sexvar;
}
function Showdetails(){
global $window,$addresstext,$phoneno,$nametext,$varsex;
$enteredname = $nametext->get_text();
$enteredphone = $phoneno->get_text();
$len = $addresstext->get_length();
$newaddresstext = $addresstext->get_chars(0,$len);
print "\n Hi are the details from form => \n
		 Name = $enteredname \n
		 address = $newaddresstext \n
		 phone = $enteredphone \n
		 sex = $varsex\n \n";
Gtk::main_quit();
}
$window->show_all();
gtk::main();
?>
```

