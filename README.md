# Design & Development Guidelines for WordPress Websites

This is a workspace for developing rules and guidelines for our team when designing websites and developing them on WordPress.

## Design
- Mockups
- Client deliverables

## Theme Development

### Theme Support
- Automatic Feed Links - In almost all cases, automatic feed links should be set to true. This is the default behavior and can be left unset.
- HTML5 Support
- Post Formats
- Post Thumbnails
- Custom Background
- Custom Header - There is almost never a reason to support custom header images.


### Theme Organization
- Styling vs. Layout
- Templates
    - Do NOT print *title tag*. Use theme support.
    - Required Hooks
        - wp_head()
        - wp_footer()
        - body_class()
        - post_class()
    - Required Custom Hooks
        - do_action('neh_after_open_body') directly after *body* tag. This is a dependancy for our plugins that insert GTM containers into page. [TK theme](https://github.com/Themekraft/_tk) uses the 'before' action here. No harm if you want to include both.
- Assets - Do we need a specific folder naming convention for assets?
- Admin Pages & Customizer
- Plugins

### Hooks vs. Functions
In order to maintain a "never broken" environment, themes should always favor the use of actions and filters instead of calling functions specified outside of WordPress core directly.
```php
// get_field() is specified in the ACF plugin. If the function is used without the plugin being active, this will trigger a PHP error.
$data = get_field('my_data');

// Instead, using a filter creates a passive way to handle this and allows for default values. If no theme or plugin registers a filter to this hook, the $default variable will simply pass through unaltered.
$data = apply_filters('neh_get_my_data', $default);
```

## Deliverables
For a 3rd party developer, I think there are two primary deliverables that we want back from them.

- Final theme in git repo - a git repository that we provide to them with the finished theme in it.
    - README.md - explainer file. Should tell what's going on in the theme.
    - CHANGELOG.md - Versions file.
- Fully configured development instance of WordPress
