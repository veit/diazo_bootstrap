<h1 class="kss-title kss-title-main">Diazo Bootstrap Styleguide </h1>

Welcome to the Diazo Bootstrap CSS Styleguide. Before reading this, you should
have a general understanding for specificity, the [LESS](http://www.lesscss.de/)
syntax, and [KSS](http://warpspire.com/kss/) documentation.

## Coding Style

* Use soft-tabs with a four space indent e.g. in `~/.vimrc`:

   ```
   " Changes all tabs in spaces
   set expandtab
   " Number of spaces for each Tab
   set shiftwidth=4
   set tabstop=4
   " Tabs are always 'tabstop' positions
   set softtabstop=4
   ```

* Put spaces after `:` in property declarations.
* Put spaces before `{` in rule declarations.
* Use hex color codes, e.g. `#000` unless using `rgba` e.g.:

   ```
   //
   // Jumbotrons base class
   .jumbotron {
       border-bottom: 1px solid #ddd;
       color: #fff;
       text-shadow: 0 1px 3px rgba(0,0,0,.4), 0 0 30px rgba(0,0,0,.075);
       background: linear-gradient(45deg, #020031 0%,#6d3353 100%);
   }
   ```

* Use `//` for comment blocks (instead of `/* */`) e.g.:

   ```
   // 
   // Scaffolding
   // --------------------------------------------------

    
   // Images
   // -------------------------

   // Rounded corners
   .img-rounded {
     .border-radius(6px);
   }
   ```

* Document styles with [KSS](https://github.com/kneath/kss).

## File Organization

   ```
   less/
   ├── accordion.less
   ├── alerts.less
   ├── bootstrap.less
   ├── breadcrumbs.less
   ├── button-groups.less
   ├── buttons.less
   ├── carousel.less
   ├── close.less
   ├── code.less
   ├── component-animations.less
   ├── dropdowns.less
   ├── font-awesome.less
   ├── forms.less
   ├── grid.less
   ├── hero-unit.less
   ├── labels-badges.less
   ├── layouts.less
   ├── media.less
   ├── mixins.less
   ├── modals.less
   ├── navbar.less
   ├── navs.less
   ├── pager.less
   ├── pagination.less
   ├── plone.less
   ├── popovers.less
   ├── progress-bars.less
   ├── reset.less
   ├── responsive-1200px-min.less
   ├── responsive-767px-max.less
   ├── responsive-768px-979px.less
   ├── responsive-navbar.less
   ├── responsive-utilities.less
   ├── responsive.less
   ├── scaffolding.less
   ├── sprites.less
   ├── styleguide.md
   ├── tables.less
   ├── thumbnails.less
   ├── tooltip.less
   ├── type.less
   ├── utilities.less
   ├── variables.less
   └── wells.less

   ```

## Units

font-size
sollte px verwendet werden da es deutlich mehr Kontrolle über die Erscheinung des Texts bietet.
line-height
kann ohne Maßangabe verwendet werden da die Zeilenhöhe direkt auf font-size basiert.

<dl>
    <dt><tt>font-size</tt></dt>
    <dd>sollte <tt>px</tt> verwendet werden da es deutlich mehr Kontrolle über die
Erscheinung des Texts bietet.</dd>
    <dt><tt>line-height</tt></dt>
    <dd>kann ohne Maßangabe verwendet werden da die Zeilenhöhe direkt auf
<tt>font-size</tt> basiert.</dd>
</dl>

## File Organization
The styleguide should be organized by numbered sections. These sections can go as deep as you like. Every element should have a numbered section to refer to. For example:

## Naming Conventions

<dl>
    <dt><tt>js-</tt>-Präfix</dt>
    <dd>sollten nie in CSS-Klassen verwendet werden sondern nur von Javascript-
        Dateien</dd>
    <dt><tt>is-</tt>-Pröfix</dt>
    <dd>soll für Elemente verwendet werden, die sowohl von CSS- als auch von
        Javascript-Dateien verwendet werden</dd>
</dl>

##  Specificity

(`class` vs. `id`)

Elements that occur exactly once inside a page should use IDs, otherwise, use
classes.

Good candidates for ids are `header`, `footer`, `modal-popup`.

Bad candidates for ids are `navigation`, `listing`, `view`.

## Organization

The styleguide is organized by numbered sections:

```
1.0 Core variables and mixins
    1.1 Variables
    1.2 Mixins
2.0 Grid system and page structure
    2.1 Scaffolding
    2.2 Grid system
    2.3 Layouts
3.0 Base
    3.1 Typography
    3.2 Code
    3.3 Forms
    3.4 Tables
4.0 Common
    4.1 Font Awesome
    4.2 Sprites
    4.3 Dropdown menus
    4.4 Wells
    4.5 Component animations
    4.6 Close icons
5.0 Buttons & Alerts
    5.1 Buttons
    5.2 Button groups
    5.3 Alerts
6.0 Nav
    6.1 Navs
    6.2 Navbars (Redux)
    6.3 Breadcrumbs
    6.4 Pagination (multiple pages)
    6.5 Pager pagination
7.0 Popovers
    7.1 Modals
    7.2 Tooltips
    7.3 Popovers
8.0 Misc
    8.1 Thumbnails
    8.2 Media objects
    8.3 Labels and badges
    8.4 Progress bars
    8.5 Accordion
    8.6 Carousel
    8.7 Hero unit
    8.8 Plone
```
