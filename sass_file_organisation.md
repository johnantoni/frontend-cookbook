#### sass file organisation

    stylesheets
      admin/    (admin sub-project)
        modules/
        partials/
        _base.scss

      account/  (account sub-project)
        modules/
        partials/
        _base.scss

      site      (site sub-project)
        modules/
        partials/
        _base.scss

      vendor    (css or sass from other projects
        _colorpicker-1.1.scss
        _jquery.ui.core.1.9.1.scss

        ...primary stylesheets for each project
      admin.scss
      account.scss
      site.scss

#### simpler

    stylesheets
      common/
        base.scss
        buttons.scss
        footer.scss

      platform/
        ie/
        tablet/
        ios/
        android/

      vendor/
        foundation.scss

      site/
        home.scss
        about.scss

      common.scss
      platform.scss
      vendor.scss
      site.scss

#### other components....

    base/
    modules/
    themes/
    states/
    media-queries/
    pseudo-elements/
    data-attributes/

