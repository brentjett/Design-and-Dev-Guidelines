# Design & Development Guidelines for WordPress Websites

This is a workspace for developing rules and guidelines for our team when designing websites and developing them on WordPress.

## Design
- Mockups
- Client deliverables

## Theme Development
When developing themes for client sites, there are some general philosophies to follow.
- **Be Like WordPress:** In almost all cases, impliment features the way you would expect WordPress itself to impliment them. Don't roll your own solutions if a stable solution already exists. Don't add a lot of extra pages to the admin. When you do add settings, make sure they appear like the built-in settings pages do.
- **Discoverability:** If at all possible, make features easy to discover and understand without needing documentation. This goes for both UI features in WordPress and for the code in a theme. A developer with minimal understanding of the platform should be able to look at the theme code in six months and discover what is happening.
- **Documentation:** Regardless of how intuitive you think you've made your code, you must document it. **Choose code documentation standard**

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

## Deliverables for 3rd Party Developers
For a 3rd party developer, there are two primary deliverables that are expected.

- Theme Git Repo - A git repository will be provided for work on the client site's theme. All changes throughout the development of the site should be committed and pushed to the theme's repository. If branching is needed, a final stable build of the theme should be merged back into the master branch before being deployed to the staging or production environment.
    - README.md - explainer file. Should tell what's going on in the theme.
    - CHANGELOG.md - Versions file.
- Fully configured development instance of WordPress
