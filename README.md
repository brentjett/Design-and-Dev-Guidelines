# Design & Development Guidelines for WordPress Websites

This is a workspace for developing rules and guidelines for our team when designing websites and developing them on WordPress.

## Design
- Mockups
- Client deliverables

## Theme Development

### Theme Support
- Automatic Feed Links - In almost all cases, automatic feed links should be set to true. This is the default behavior and can be left unset.


- Theme Organization
- Styling
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
- Plugins

## Deliverables
For a 3rd party developer, I think there are two primary deliverables that we want back from them.

- Final theme in git repo - a git repository that we provide to them with the finished theme in it.
    - README.md - explainer file. Should tell what's going on in the theme.
    - CHANGELOG.md - Versions file.
- Fully configured development instance of WordPress
