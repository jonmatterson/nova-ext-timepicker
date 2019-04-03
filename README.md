# Nova Extension: Timepicker

This extension provides a helper for adding timepickers (using the [jQuery Timepicker plugin](https://timepicker.co/)) to input elements collecting time values. It is intended as a utility for extension writers, skin designers and sim manager comfortable with modifying Nova's view files, and it does not provide any changes to Nova on its own.

## Requirements

This extension requires:

- Nova 2.6+

## Installation

Copy the entire directory into `applications/extensions/timepicker`.

Add the following to `application/config/extensions.php`:

```
$config['extensions']['enabled'][] = 'timepicker';
```

## Usage

The simplest way to enable a timepicker is simply to add `data-timepicker` as an attribute on an element. This will initialize a jQuery.timepicker with no options.

To pass options, simply JSON-encode them (with escaped quotes) as the value of `data-timepicker` such as:

```
<input type="text" 
       name="chronological_mission_post_time" 
       value="0000" 
       id="chronological_mission_post_time" 
       data-timepicker="{&quot;timeFormat&quot;:&quot;HHmm&quot;,&quot;defaultTime&quot;:&quot;0000&quot;}">
```

These can also be written to be passed to the input helper such as:

```
array(
  'name' => 'chronological_mission_post_time',
  'id' => 'chronological_mission_post_time',
  'data-timepicker' => str_replace('"', '&quot;', json_encode([
    'timeFormat' => 'HHmm',
    'defaultTime' =>  $post ? $post->post_chronological_mission_post_time : '0000'
  ])),
  'value' => $post ? $post->post_chronological_mission_post_time : '0000'
);
```

## Issues

If you encounter a bug or have a feature request, please report it on GitHub in the issue tracker here: https://github.com/jonmatterson/nova-ext-timepicker/issues

## License

Copyright (c) 2018-2019 Jon Matterson.

This module is open-source software licensed under the **MIT License**. The full text of the license may be found in the `LICENSE` file.
