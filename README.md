# Design & Development Guidelines for WordPress Websites

This is a workspace for developing rules and guidelines for our team when designing websites and developing them on WordPress.

## Design
- Mockups
- Client deliverables

## Development
- Theme Organization
- Styling
- Templates
    - Do NOT print <title> tag. Use theme support.
    - Required Hooks
        - wp_head()
        - wp_footer()
        - body_class()
        - post_class()
    - Required Custom Hooks
        - do_action('neh_after_open_body') directly after <body> tag. This is a dependancy for our plugins that insert GTM containers into page. [TK theme](https://github.com/Themekraft/_tk) uses the 'before' action here. No harm if you want to include both.
- Assets - Do we need a specific folder naming convention for assets?
- Plugins
