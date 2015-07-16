# [PROPOSED] StyleGuide API
The styleguide API offers a method of registering static pages that will be rendered using the theme's templates for the purpose of testing the theme's styling and explaining the available content elements.

The StyleGuide API registers a virtual page at /styleguide and additional child pages can be registered as well.

One possible organization of styleguide pages:
```
- Style Guide (/styleguide)
    - Basic Element Formatting
    - Content Elements / Shortcodes
    - Bootstrap Styling
    - Hook Reference
```

Registering a new page allows you to modify the wp_query object and the array of posts that the page will display. These two objects determine what template will be used from the template heirarchy. This allows us to simulate different content environments.

## API
- register page
- unregister page
