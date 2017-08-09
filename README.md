Reusable Custom WordPress Meta Boxes
====================================

### No longer supported - please fork to continue development on your own.

Contributors: [tammyhart](http://github.com/tammyhart)

Original Tutorial Series: (http://wp.tutsplus.com/author/tammy/)


Latest Update
-------------

09/08/2017 --> Modificación para añadir o no tabs (pestañas), para agrupar mejor los metaboxes. Creación de un nuevo campo (field) de tipo "title", el cual añade un titulo y descripción corta (util para usar al principio del contenido de cada pestaña/tab ).

Image and file upload buttons now use the new 3.5 media uploader!


Description
-----------

This project was originally a tutorial for WPTuts+, but as I continued to use the code in my own 
projects, I kept improving it and making the resusable part even better. Rather than update the 
tutorial, I decided to make it an open source project here where developers can keep up with 
improvements as well as contribute their own.

This project creates a class which makes it easy to create a custom meta box for any 
post type using a master switch case for the meta box and fields HTML and an array containing 
the data for the fields you want to use.


### Fields Included

* Text Input (types: text,tel, email, url, number)
* Textarea
* WYSIWYG Editor
* Single checkbox
* Select and [Chosen](http://harvesthq.github.com/chosen/) select with support for "multiple"
* Radio group
* Checkbox group
* Taxonomy Select box and Checkboxes
* Post select with support for "multiple" and [Chosen](http://harvesthq.github.com/chosen/)
* Post Checkboxes
* jQuery UI Date input
* jQuery UI Slider
* Farbtastic color chooser
* Post Drag and Drop Sort
* Image upload/select
* File upload/select
* Sortable Repeatable area with ability to use any of the above mentioned fields (with caution and reason)
* Title añade un titulo y descripción corta (util para usar al principio del contenido de cada pestaña/tab)

### Notes

Not all fields are covered in the included example, but they are in the [Wiki](https://github.com/tammyhart/Reusable-Custom-WordPress-Meta-Boxes/wiki)


Usage sin pestañas
------------------

These files are written from the perspecitve of being used in a theme. 

1. Add the metaboxes directory in your theme or plugin.
2. Include metaboxes/meta_box.php in your functions.php.
3. Use the class to create and add meta boxes to any post type (see Examples section below or the [Wiki](https://github.com/tammyhart/Reusable-Custom-WordPress-Meta-Boxes/wiki)
)
4. Llamar el metodo: "create_save_metabox".


Examples
--------

### Create an array that contains the field data (full examples of each filed type found in inc/sample.php)

	$prefix = 'sample_';
	
	$fields = array(
		array( // Text Input
			'label'	=> 'Text Input', // <label>
			'desc'	=> 'A description for the field.', // description
			'id'	=> $prefix.'text', // field id and name
			'type'	=> 'text' // type of field
		),
		array( // Textarea
			'label'	=> 'Textarea', // <label>
			'desc'	=> 'A description for the field.', // description
			'id'	=> $prefix.'textarea', // field id and name
			'type'	=> 'textarea' // type of field
		)
	);

### Instantiate the class with all required variables

	/**
	 * Instantiate the class with all variables to create a meta box
	 * var $id string meta box id
	 * var $title string title
	 * var $fields array fields
	 * var $page string|array post type to add meta box to
	 * var $js bool including javascript or not
	 */
	$sample_box = new custom_add_meta_box( 'sample_box', 'Sample Box', $fields, 'post', true );

	$sample_box->create_save_metabox();

Usage con pestañas
------------------

These files are written from the perspecitve of being used in a theme. 

1. Add the metaboxes directory in your theme or plugin.
2. Include metaboxes/meta_box.php in your functions.php.
3. Use the class to create and add meta boxes to any post type (see Examples section below or the [Wiki](https://github.com/tammyhart/Reusable-Custom-WordPress-Meta-Boxes/wiki)
)
4. Pasar el array con los label de las pestañas al metodo: "set_tabsnav($tabs_nav)"
5. Llamar el metodo: "create_save_metabox".

Examples
--------

### Create an array that contains the field data (full examples of each filed type found in inc/sample.php)

	$prefix = 'sample_';
	
	$tab_1 = array(
		array( // Text Input
			'label'	=> 'Text Input', // <label>
			'desc'	=> 'A description for the field.', // description
			'id'	=> $prefix.'text', // field id and name
			'type'	=> 'text' // type of field
		),
		array( // Textarea
			'label'	=> 'Textarea', // <label>
			'desc'	=> 'A description for the field.', // description
			'id'	=> $prefix.'textarea', // field id and name
			'type'	=> 'textarea' // type of field
		)
	);

	$tab_2 = array(
		array( //Title
			'label' => 'Title', // <label>
			'desc' => 'A description for the area.', // description
			'type' => 'title' // type of field
		),
		array( // Textarea
			'label' => 'Titulo destacado', // <label>
			'desc' => 'A description for the field.', // description
			'id' => 'main_title',
			'type' => 'textarea' // type of field
		)
	);

	$tabs_nav = array(
		'Pestaña 1', // <label>
		'Pestaña 2'// <label>
	);

	$tabs = array($tab_1, $tab_2);

### Instantiate the class with all required variables

	/**
	 * Instantiate the class with all variables to create a meta box
	 * var $id string meta box id
	 * var $title string title
	 * var $fields array fields
	 * var $page string|array post type to add meta box to
	 * var $js bool including javascript or not
	 */
	$sample_box = new custom_add_meta_box( 'sample_box', 'Sample Box', $tabs, 'post', true );

	$sample_box->set_tabsnav($tabs_nav);
	$sample_box->create_save_metabox();


Changelog
---------

### 0.5 (August 9, 2017)
* Añadido campo de tipo "title"
* Añadida posibilidad de usar tabs (pestañas)
* Cambio en la forma de uso
* Cambio en la documentación

### 0.4 (January 8, 2013)
* Cleaned up docs
* Cleaned up js
* Cleaned up the field output and nested repeatables
* Fixed several bugs 

### 0.3 (November 10, 2012)
* Added file field
* Added function to simplify the add file and add image thickbox
* added more fields to the Repeatable
* Added "chosen" and "multiple" options to select fields

### 0.2 (September 11, 2012)
* Functions combined into a class
* Major code cleanup and some docing added

### 0.1 (March 31, 2012)
* First release
