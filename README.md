# Shopify Library
At the beginning of 2021, I had a little over a week working on a client’s [Shopify](https://www.shopify.co.uk/) project. In the course of the project a few files were created that may be of use to others, and provide a backup for myself.

## Contents
- Colour Swatches Snippet: based upon Joe Dempsey's [Shopify Add Color Swatches To Collection Pages](https://gist.github.com/joe-dempsey/6ef2e9e047e8e95fde0342b7667b8289).
- Grid by Collection and Type: View single “Type” of products from within a collection on grid view.

## Colour Swatches Snippet
Based on Joe Dempsey’s work; the colour swatches snippet uses CSS styling to create colour-swatch boxes, which in the current code can bbe up to a multiple of four colours (this is done through css linear-gradient backgrounds). 

The limitations are that the colours currently must match to [CSS Color Names](https://www.w3.org/TR/2018/REC-css-color-3-20180619/). At first this was not considered an issue, but it does cause problems; for example Khaki is often used in fashion to denote a musty-green, whereas in the CSS Color Specification, and in definition, khaki is a sand colour. Unfortunately the project timescale did not allow for map/replace colour names functionality so that a product could be described as ‘Wine’ coloured and be mapped ‘darkred’ in the extended CSS keywords.

A warning would also be good if the colour name used was not accepted/errored. For ‘multi-coloured’ products a custom png was used as opposed to CSS drawn swatch. This may not be the optimum solution.

### Installation
Upload the snippet file, `product-color-listing.liquid`, to your themes snippet folder, and then where you wish the colour-swatches to be placed, include the snippet code in the appropriate template.
```
{% include 'product-color-listing', product: product %}
```
The styling of the Color Swatch boxes is controlled via CSS, so inclusion of a few lines is necessary in your `theme.css.liquid` file (in the assets subfolder).
```
ol.col-swatches {
    width: 100%;
    text-align: center;
}
    ol.col-swatches li {
        list-style-type: none;
        display: inline-block;
        width: 1em;
        height: 1em;
        border: 1px solid var(--color-border-form);
        box-sizing: content-box;
    }
    ol.col-swatches abbr {
        display: none;
        speak: normal;
    }
```
### How to use
Within your product creation/details, ensure that the colour name matches a CSS Color Keyword. These may be separated by slashes for multiple-colour products. e.g.
```
Dark Red\Black
```
The script removes any spaces when determining the color-keyword, and ensures that all characters are converted to lowercase—hence ‘darkred’ and ‘black’.
## Grid by Collection and Type
### Installation
Upload the snippet file `collection-type-only-filter.liquid` to your themes’ snippet folder on Shopify. The filter can then be added to your pages by adding include code;
```
{% include 'collection-type-only-filter', collection %}
```
As the action and process of submission are tied to Event Listeners, javascript is needed to ‘activate’ the control. This is done by uploading the `library.min.js` to your themes asset folder and including the javascript in the head of your pages.
