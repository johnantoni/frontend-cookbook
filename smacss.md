### architecture

* base
  single element selectors
  attribute selectors
  pseudo-class
  child
  siblings
  "whereever this element is on the page, it should look like this"

* layout
  divide the page into sections
  layouts hold one or more modules together

* module
  reusable, modular parts of our design
  ..callouts
  ..sidebars
  ..product lists
  ..etc.

* state
  describe how our modules or layouts will look when in a particular
  state.
  hidden? expanded?
  active? inactive?
  how module looks on homepage, list page, search page

* theme
  how modules or layouts might look.
  most sites don't need a layer of theming.
  whitelabeling

### naming

  is-hidden
  is-collapsed
  l-small / layout-small

  modules:
  .callout {}

  module with state:
  .callout.is-collapsed {}

  inline layout:
  .l-inline {}

  .l-flipped #sidebar {}
  .l-fixed #sidebar {}

### base rules

  body, form {
    margin: 0;
    padding: 0;
    background: white;
  }

  a {}
  a:hover {}

  ...no need for !important

### css reset

  either pick one or build your own and reuse it from project to
  project.

### layout rules

  header, article, footer {
    width: 960px;
    margin: auto;
  }

  article {
    border: 1px solid #ccc;
  }

  divided into major/minor

### semantics

  div.fld
    span.fld-name
      ...
    span.fld-items
      ...

### state

  .is-tab-closed
  .is-active
  .is-hidden

  button.is-active
  toolbar.is-active
  toolbar.is-hidden
  header.is-hidden.menu
  input.btn.is-inactive

  --- sub-module naming convention
  .btn
  .btn-pressed
  .btn-disabled

  --- state naming convention
  .btn
  .is-pressed
  .is-disabled

  --- state naming via attribute selectors (data- prefix)
  .btn[data-state=default]
  .btn[data-state=pressed]
  .btn[data-state=disabled]

  ...simpler compared to adding/removing classes

  state styles can apply to layout and/or module styles
  state styles indicate a javascript dependency

### theming

  prefix theme-....

  theme.css

### font sizes

  try to stick to 3-6 different font sizes

  there may not be a need to define font classes (like font-large)

  if you have more than 6 font sizes your users will likely not notice

### state-ful modular media queries

  /* default state for nav items */
  .nav > li {
    float: left;
  }

  /* alternate state for nav items on small screens */
  @media screen and (max-width: 400px) {
    .nav > li { float: none; }
  }

  ... elsewhere for layout ...
  /* default layout */
  .content {
    float: left;
    width: 75%; }
  .sidebar {
    float: right;
    width: 25%; }

  /* alternate state for layout on small screens */
  @media screen and (max-width: 400px) {
    .content, .sidebar {
      float: none;
      width: auto;
    }
  }

### minimizing depth

  duplication of rules:

  #sidebar div, #footer dic
  #sidebar div h3, #footer div h3
  #sidebar div ul, #footer div ul

  ...to:

  .pod
  .pod > h3
  .pod > ul

  the pod is still a container that relies on a particular html
  structure but it is of a much shallower depth than we had before.

  the trade off is that we have to repeat the pod class on numerous
  elements of the page.

### selector performance

* the style of an element is evaluated on element creation.

each node is evaluated and rendered to the viewport as it is received.

* css is evaluated from right to left.

### in-efficient rules (google)

* Rules with descendant selectors. E.g. #content h3
• Rules with child or adjacent selectors. E.g. #content > h3
• Rules with overly qualified selectors. E.g. div#content > h3
• Rules that apply ￼ to non-link elements. E.g. div#content:hover

note: the evaluation of any more than a single element to determine
styling is inefficient.

...taken with a pinch of salt but be careful to not overly qualify your
selectors.

### constrain yourself, don't choke yourself

three simple guidelines

* use child selectors
* avoid tag selectors for common elements
* use child names as the right-most selector

### deep nesting with sass

from:

    #sidebar {
      width: 300px; }
      #sidebar .box {
        border-radius: 10px;
        background-color: #EEE; }
        #sidebar .box h2 {
          font-size: 14px;
          font-weight: bold; }
        #sidebar .box ul {
          margin: 0;
          padding: 0; }
          #sidebar .box ul a {
            display: block; }

to this with smacss:

    #sidebar {
      width: 300px;
    }
    .box {
      border-radius: 10px;
      background-color: #EEE;
    }
    .box-header {
      font-size: 14px;
      font-weight: bold;
    }
    .box-body { margin: 0; padding: 0; a{
        display: block;
      }
    }


