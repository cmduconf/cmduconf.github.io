# CMD+U Conference static website

## Dependencies

This website is created using [Jekyll](https://jekyllrb.com/).

Installing dependencies:

* Install Jekyll: `gem install jekyll`
* Install gems: `bundle`
* Install npm depdendencies: `npm install`


## Running the website

In order to build the website, run `jekyll build`. If you want to develop the website and to build it when a file is changed, use `jekyll build --watch`.

The built website can be found in the `_site` directory. If you need a local server to check how the website looks / behaves you can use `http-server` (install using `npm install http-server`, `cd` in the `_site` directory and run `http-server`).

## HTML / Styling structure

The website is using [BEM](https://css-tricks.com/bem-101/) for structuring the sections and keeping the styling under control. It also has utility classes for common components (e.g. `u-title` for titles).

When writing the styles, you don't need to worry about vendor prefixes (e.g. `display: -webkit-flex`). The project has Autoprefixer which adds all the necessary vendor prefixes on compile.

### Sass structure

Sass files are inside the `_sass` directory. All partials are imported in the main file, in `css/main.scss`.

It's using [normalize.css](https://necolas.github.io/normalize.css/) to reset the CSS. The reseter can be found inside the `_normalize.scss` file (it was hardcoded there because of the way of Jekyll is building the asset pipeline + the way Sass is importing `.css` files).

`_base.scss` has all the styling related to the general website structure, not the individual components.

`_variables.scss` - pretty much what it says on the tin. It stores all the Sass variables that are used throughout the project. It also contains helper functions to extract the values easier from the Sass maps.

`_utilities.scss` contains all utility classes that can be applied onto existing components / elements. Structure of utility classes: `u-[class-name]`

All other files are corresponding to the website components (e.g. `_footer.scss` is corresponding to everything related to the footer). Please try not to mix them.


### Responsive

For managing the responsive bits, the project is using the [rs-breakpoints](http://razvandh.github.io/rs-breakpoints/) mixin (shameless plug).

If you want to apply a certain style only on small screens: `@include breakpoint(to mobile-small)`. If you want to apply something only on really large screens, apply `@include breakpoint(from desktop-large)`.

Options: any combination of `[mobile / tablet / desktop]-[small / medium / large]`. Smaller than a certain screen size is `to [...]`, greather than is `from [...]`, between two screen sizes is `from [...] to [...]`.


