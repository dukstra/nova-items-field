# Dukstra Nova Items Field

An editable Nova field for string arrays, with add/remove, validation and drag-to-reorder support. This Laravel Nova 5 update is based on the MIT-licensed `dillingham/nova-items-field` and the Nova 5-compatible work in `blendbyte/nova-items-field`.

## Requirements

- PHP 8.3+
- Laravel 13
- Laravel Nova 5

## Installation

```bash
composer require dukstra/nova-items-field
```

## Use

```php
use Dukstra\NovaItemsField\Items;

Items::make('Direct Emails', 'direct_emails')
    ->rules(['direct_emails.*' => 'email|min:10'])
    ->listFirst()
    ->placeholder('Email')
    ->draggable();
```

Cast the model attribute as an array so Nova reads the saved JSON as a PHP array:

```php
protected $casts = [
    'direct_emails' => 'array',
];
```

The field submits and stores the same JSON array of strings as the original package. An empty field saves `null`; a populated field saves the submitted values in their display order.

## Options

- `max($count)` limits the number of values.
- `draggable()` enables drag-to-reorder.
- `listFirst()` moves the add control below the list.
- `placeholder($text)` sets the input placeholder.
- `inputType($type)` sets the input type.
- `fullWidth()` expands the field.
- `maxHeight($pixels)` limits the list height.
- `hideCreateButton()` hides the add button.
- `createButtonValue($text)` and `deleteButtonValue($text)` customize button labels.
- `indexAsList()` shows values as a list on the index page.
- `detailsAsTotal()` shows the item count on the detail page.

The Nova 5 compatible frontend bundle is included in `dist/`.
