# [PROPOSED] Content Filters API
This is a proposed interface for common content transforms that should be available in our foundation theme.

## Phone Numbers
Phone numbers should be transformable between formatted and integer states. Also it should be easy to request tel: anchor tags. All phone numbers should be either linked or wrapped in a span tag with the appropriate classes applied for discovery/switching operations later.
```html
<!-- tel: links should have the phonelink class applied -->
<a href="tel:4445556666" class="phonelink">Click here to call</a>

<!-- text nodes containing phone numbers should wrap the number in a span tag and that span should have a class of phonenumber applied -->
<span class="phonenumber">(555) 444-3333</span>

<!-- if a link has the phone number in both the href and the label, both classes are applied -->
<a href="tel:5554443333" class="phonelink phonenumber">(555) 444-3333</a>
```

Phone number formatting and elements can be generated using filters. Filters should be used over direct function calls to prevent function_exists errors. See [Hooks vs. Functions](https://github.com/brentjett/Design-and-Dev-Guidelines#hooks-vs-functions)

### Phone Number Filters
**neh/format_phone** - Get formatted phone number text based on the system's declared preferred format style

**neh/strip_phone** - Get integer from formatted phone number

**neh/phone_tag** - Get element of appropriate type and with appropriate classes based on an array of arguments.

```php
// Get formatted number from raw integer - (444) 555-6666
$raw_number = 4445556666;
$formatted_number = apply_filters('neh/format_phone', $raw_number);

// Get raw integer from formatted number - 4445556666
$raw_number = apply_filters('neh/strip_phone', $formatted_number);

// Get appropriate element with correct classes based on arguments
$args = [
    'phone_number' => 5554443333,
    'is_anchor' => true,
    'label' => 'Click Here to Call' // leave blank to use formatted phone number as label,
    'classes' => ['hide-on-mobile'],
    'id' => 'desktop-main-phone'
];
$tag = apply_filters('neh/phone_tag', $args);
print $tag;
// <a href="tel:5554443333" id="desktop-main-phone" class="phonelink hide-on-mobile">Click Here to Call</a>
```
