# Accessibility

Ofter shorten to a11y or i18n

## What is Accessibility

This means that the content should be available for every one.
And that the functionality can be operated by everyone.

## Some statistics on disability for the US:

* Around 2% of the population has some kind of vision disability (i.e. are blind or have significant difficulty seeing even with glasses)
* Around 50% of the population has some kind of clinically significant refractive error (a visual impairment which may be corrected with glasses if mild enough)
* Around 8% of males and 0.5% of females have some form of color vision deficiency
* Around 2% of adults have a hearing disability
* Over 4% have a cognitive disability (difficulty remembering, concentrating, or making decisions)

## guidelines

[WCAG 2.0](https://webaim.org/standards/wcag/checklist)

[Web content Accessibility guidelines 2.0(wcag)](https://www.w3.org/TR/WCAG20/)

### Focus

tabindex can be added to each html element if the tabindex = -1 you can use the `.focus()` to attract it's attention.

Usefull for offscreen content this way when it opens the screen readers focus points to the offscreen element.

##### example

`document.querySelector('#modal').focus()`

`tabindex="0"`
_ in the natural tab order
_ can be programmatically focused

`<div id="dropdown" tabindex="0">Settings</div>`

`tabindex="0"`
_ in the natural tab order
_ can be programmatically focused \* Anti-pattern!

##### manage focus

set header tabindex to -1 and only when that page has loaded the content add focus dynamically to the header element.

#### skip link

html markup example

`<a href="#maincontent" class="skip-link">Skip to main content</a>

<nav>
    ...
</nav>
<main id="maincontent" tabindex="-1">
    ...
</main>
`

css markup example

`.skip-link {
position: absolute;
top: -40px;
left: 0;
background: #bf1722;
color: #fff;
padding: 8px;
z-index: 100;
}

.skip-link:focus {
top: 0;
}
`

#### Roving focus

`<li tabindex="-1" checked>...</li>

 <li tabindex="0">...</li> call focus and use setAttribute to move checked
 <li tabindex="-1">...</li>
 <li tabindex="-1">...</li>
 <li tabindex="-1">...</li> go back to first element
`
