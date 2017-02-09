This repository contains the source files for the documentation website of [Sense/Stage](https://sensestage.eu).


# Format

See [_minibee/testpage.md]() for an example of the frontmatter of a page

## Overview pages

If you want to create an overview of a subcategory of pages:

* use `type: overview`
* use `layout: subcategory_overview`

Then a list of all pages within that subcategory will automatically be filled in.

Also, the page will be a hyperlink of the subcategory name in the index overview; this also means that each subcategory should only have one overview page.

The subcategory_overview layout could still be used if you want a list of the other pages in the same subcategory.


If you want a block of text at the top of each page in a subcategory, then you have to create a page in `_minibee_overviews` with a filename of `<category>_<subcategory>.md` and the `name:<category>_<subcategory>` defined in the frontmatter.
