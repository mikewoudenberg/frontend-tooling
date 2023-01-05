# Frontend tooling

Ruben Oostinga<br >
Mike Woudenberg<br >

https://twitter.com/rubenoostinga
https://twitter.com/mikewoudenberg

![Logo Xebia](img/logo-xebia.png)

---

### Introduce yourself

- What is your name?
- What is your current front-end experience?
- What do you want to get out of this course?

---

### Programme

- History of module bundling / loading
- Bundling tools
- Monorepo tools
- Quality of life tools
- Test tools
- Documentation tools

Note:

- History also compares tools
- Lots of cool tools today
- try to see if you can use it on your projects
- QOL makes you more productive

---

### Concepts to understand

- JS bundles
- Minification
- JS dependencies
- Modules

Note:

- JS bundle:
  - Concatenation of JS files
  - Faster to load than separate files
- Minification:
  - Shortens all variables names
  - Removes whitespace
  - Other optimizes for minimal filesize
  - Goal: load fast in browser
- JS dependencies
  - You can put all javascript in a single file
  - Too big -> split it up
  - Split up files need to run in a specific order
  - Code depends on other code
  - Example:
    - Angular module declaration should run before you add controllers / directives to that angular module
- Modules:
  - JS file with private scope
  - By default vars declarations are global
  - Wrapping code in a function makes it a module
  - Immediately-Invoked Function Expression (IIFE)

vvv

### Immediately-Invoked Function Expression (IIFE)

```js[1,14|2-13]
var counter = (function () {
  var i = 0;
  return {
    get: function () {
      return i;
    },
    set: function (val) {
      i = val;
    },
    increment: function () {
      return ++i;
    },
  };
})();
```

Note:

- Has anyone used this?
- Example of a classic JS module
- There are others:
  - AMD
  - CommonJS: like NodeJS
  - ES6: JS standard modules
- Function is invoked immediately
- `var i` is locally scoped
- a public API is exposed:
  - `get`, `set`, `increment`

---

### What problem are we solving?

- Only solve problems you have
- Especially when you already have a working project
- There are too many cool new tools to use everything
- You want to bundle your javascript for performance
- There are dependencies between modules
- A giant list of files is hard to maintain

vvv

<pre>
  <code>
    <script src="/config-variables.js"></script>

    <!-- build:js /scripts/common.js -->
    <script src="/bower_components/jquery/dist/jquery.js"></script>
    <script src="/bower_components/jquery-ui/ui/core.js"></script>
    <script src="/bower_components/angular/angular.js"></script>
    <script src="/bower_components/angular-i18n/angular-locale_nl-be.js"></script>
    <script src="/bower_components/lodash/lodash.js"></script>
    <script src="/bower_components/underscore.string/dist/underscore.string.js"></script>
    <script src="/bower_components/angular-cookie/angular-cookie.js"></script>
    <script src="/bower_components/angular-route/angular-route.js"></script>
    <script src="/bower_components/angular-sanitize/angular-sanitize.js"></script>
    <script src="/bower_components/angular-touch/angular-touch.js"></script>
    <script src="/bower_components/angular-ui-bootstrap/src/pagination/pagination.js"></script>
    <script src="/bower_components/angular-ui-bootstrap/src/bindHtml/bindHtml.js"></script>
    <script src="/bower_components/angular-ui-bootstrap/src/position/position.js"></script>
    <script src="/bower_components/angular-ui-bootstrap/src/typeahead/typeahead.js"></script>
    <script src="/bower_components/angular-ui-bootstrap/src/modal/modal.js"></script>
    <script src="/bower_components/angular-ui-bootstrap/src/transition/transition.js"></script>
    <script src="/bower_components/angulartics/src/angulartics.js"></script>
    <script src="/bower_components/matchMedia/matchMedia.js"></script>

    <script src="/scripts/common/environment/environment-module.js"></script>
    <script src="/scripts/common/environment/environment-constants.js"></script>
    <script src="/scripts/common/environment/culture-filter.js"></script>
    <script src="/scripts/common/environment/currency-filter.js"></script>

    <script src="/scripts/common/analytics/analytics-module.js"></script>
    <script src="/scripts/common/analytics/tealium-script-service.js"></script>
    <script src="/scripts/common/analytics/divolte-script-service.js"></script>
    <script src="/scripts/common/analytics/async-script-service.js"></script>
    <script src="/scripts/common/analytics/cookie-service.js"></script>
    <script src="/scripts/common/analytics/iframe-service.js"></script>
    <script src="/scripts/common/analytics/angulartics-config-provider.js"></script>
    <script src="/scripts/common/analytics/tealium-analytics-provider.js"></script>
    <script src="/scripts/common/analytics/criteo-analytics-provider.js"></script>
    <script src="/scripts/common/analytics/google-analytics-provider.js"></script>
    <script src="/scripts/common/analytics/divolte-analytics-provider.js"></script>
    <script src="/scripts/common/analytics/facebook-analytics-provider.js"></script>
    <script src="/scripts/common/analytics/floodlight-analytics-provider.js"></script>
    <script src="/scripts/common/analytics/angulartics-debug.js"></script>
    <script src="/scripts/common/analytics/domain/product.js"></script>
    <script src="/scripts/common/analytics/domain/product-variant.js"></script>
    <script src="/scripts/common/analytics/domain/order.js"></script>
    <script src="/scripts/common/analytics/domain/order-line.js"></script>
    <script src="/scripts/common/analytics/analytics-constants.js"></script>

    <script src="/scripts/common/newsletter/newsletter-module.js"></script>
    <script src="/scripts/common/newsletter/newsletter-service.js"></script>
    <script src="/scripts/common/newsletter/newsletter-controller.js"></script>

    <script src="/scripts/common/search-bar/search-bar-module.js"></script>
    <script src="/scripts/common/search-bar/search-bar-typeahead-directive.js"></script>
    <script src="/scripts/common/search-bar/search-bar-typeahead-service.js"></script>

    <script src="/scripts/common/search-page/search-page-module.js"></script>
    <script src="/scripts/common/search-page/search-service.js"></script>
    <script src="/scripts/common/search-page/search-page-url-service.js"></script>
    <script src="/scripts/common/search-page/search-page-location-service.js"></script>
    <script src="/scripts/common/search-page/search-page-pagination-directive.js"></script>
    <script src="/scripts/common/search-page/category-filter-controller.js"></script>
    <script src="/scripts/common/search-page/facet-controller.js"></script>
    <script src="/scripts/common/search-page/filter-feedback-directive.js"></script>
    <script src="/scripts/common/search-page/price-filter-directive.js"></script>
    <script src="/scripts/common/search-page/product-list-directive.js"></script>
    <script src="/scripts/common/search-page/sorting-dropdown-directive.js"></script>
    <script src="/scripts/common/search-page/natural-sorting-service.js"></script>
    <script src="/scripts/common/search-page/price-directive.js"></script>
    <script src="/scripts/common/search-page/search-page-pagination-link-directive.js"></script>

    <script src="/scripts/common/common-module.js"></script>
    <script src="/scripts/common/amplience-area-directive.js"></script>
    <script src="/scripts/common/accordion-directive.js"></script>
    <script src="/scripts/common/api-http-request-interceptor.js"></script>
    <script src="/scripts/common/back-button-directive.js"></script>
    <script src="/scripts/common/basket-service.js"></script>
    <script src="/scripts/common/collapsible-directive.js"></script>
    <script src="/scripts/common/content-repository-service.js"></script>
    <script src="/scripts/common/cookie-controller.js"></script>
    <script src="/scripts/common/nl-user-controller.js"></script>
    <script src="/scripts/common/nl-user-modal-controller.js"></script>
    <script src="/scripts/common/current-year-directive.js"></script>
    <script src="/scripts/common/date-filter.js"></script>
    <script src="/scripts/common/form-autofill-directive.js"></script>
    <script src="/scripts/common/form-field-validation-directive.js"></script>
    <script src="/scripts/common/form-submit.js"></script>
    <script src="/scripts/common/global-error-service.js"></script>
    <script src="/scripts/common/header-directive.js"></script>
    <script src="/scripts/common/input-validation-directive.js"></script>
    <script src="/scripts/common/ip-location-service.js"></script>
    <script src="/scripts/common/mini-basket-directive.js"></script>
    <script src="/scripts/common/mobile-menu-directive.js"></script>
    <script src="/scripts/common/nav-set-active-directive.js"></script>
    <script src="/scripts/common/object-dimension-service.js"></script>
    <script src="/scripts/common/options-disabled-directive.js"></script>
    <script src="/scripts/common/product-filter.js"></script>
    <script src="/scripts/common/responsive-image-directive.js"></script>
    <script src="/scripts/common/scrollto-directive.js"></script>
    <script src="/scripts/common/select-update-wrapper-directive.js"></script>
    <script src="/scripts/common/trusted-url-filter.js"></script>
    <script src="/scripts/common/validation-service.js"></script>
    <script src="/scripts/common/product-image-directive.js"></script>
    <script src="/scripts/common/scroll-to-top-directive.js"></script>
    <script src="/scripts/common/category-toggle-view-directive.js"></script>

  </code>
</pre>

Note:

- Familiar with code like this?

---

### First generation improvements

- Task runners
  - Grunt
  - Gulp
- Module loaders / bundlers
  - RequireJS
  - browserify
  - jspm

Note:

- Give a history of where these tools come from
- Compare their features

---

### Second generation
