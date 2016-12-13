<article class="post-content">
In one of my previous articles, 
[Using Heading Elements to Create a Document Outline][1], I explained the
importance of having valid outlines in an HTML page.

> The outline for an HTML document shows the structure of the content on the
> page. This is useful for user agents, who can use the outline to create, for 
> example, a table of contents for the document. This can then be used by screen 
> readers to help people better navigate the page.
>  

Last week, HTML 5.1 was officially released. There were a 
[number of interesting changes made][2], two of which relate to how we create a
valid document outline.

*   **Removed**: The use of nested `<section>` elements each with an 
    `<h1>` to create an outline
*   **Changed**: `<header>` and `<footer>` elements can be nested,
    if each level is within a sectioning element
   

## Creating Document Outlines with Nested `<section>` Elements {#
creatingdocumentoutlineswithnestedsectionelements
}

In HTML 5.0, a new way of creating a document outline was introduced. It
involved using only the`<h1>` heading rank, and instead nesting 
`<section>` elements to define nested sections within the document. 

Take, for example, this markup - 

    <section>  
    <h1>Heading Level One</h1>
    
        <section>
            <h1>Heading Level Two</h1>
        </section>
    
        <section>
            <h1>Heading Level Two</h1>
    
            <section>
                <h1>Heading Level Three</h1>
            </section>
        </section>
    
    <section>  
    

Deprecated method

Using that markup, it should have created the following document outline - 

    1. Heading Level One  
        1. Heading Level Two
        2. Heading Level Two
            1. Heading Level Three
    

In my [previous article][1], I mentioned that this method was not currently
recognised by user agents and should not be used yet. In HTML 5.1,**this method
has been removed from the specification completely**. 

Now, the advised method for creating a document outline is to still make use of
nested`<section>` elements, but in combination with the appropriate
heading rank for each section. For example, to create the document outline above,
we should use the following markup
- 

    <section>  
    <h1>Heading Level One</h1>
    
        <section>
            <h2>Heading Level Two</h2>
        </section>
    
        <section>
            <h2>Heading Level Two</h2>
    
            <section>
                <h3>Heading Level Three</h3>
            </section>
        </section>
    
    <section>  
    

In HTML 5.0, `<header>` elements couldn’t be nested within 
`<header>` elements, and `<footer>` elements couldn’t be nested
within`<footer>` elements.

In HTML 5.1, this has been changed. Now, we can have nested `<header>`
and`<footer>` elements, but only if they are within a new sectioning
context, which is created by nesting them within a sectioning element. These are
one of the following
-

*   `<article>`
*   `<section>`
*   `<aside>`
*   `<nav>`

This way, the `<header>` or `<footer>` element is always related to
a unique sectioning element, such as`<section>`, and not just the 
`<header>` or `<footer>` element itself. For example, an 
`<article>` element can have a `<header>`, which has various 
`<sections>`, detailing different information about the article. 

    <article>  
      <header>
        <h1>Creating a Document Outline in HTML 5.1</h1>
        <section>
          <header>
            <h2>The Author</h2>
          </header>
          <p>Ire Aderinokun</p>
          <address>Lorem ipsum dolor sit amet</address>
        </section>
        <section>
          <header>
            <h2>The Publication</h2>
          </header>
          <p>bitsofcode</p>
          <address>Lorem ipsum dolor sit amet</address>
        </section>
      </header>
      <h2>Introduction</h2>
      <p>Lorem ipsum dolor sit amet</p>
    </article>  
    

This markup will produce the following outline - 

    1. Creating a Document Outline in HTML 5.1  
        1. The Author
        1. The Publication
        1. Introduction
    </article>

 [1]: https://bitsofco.de/using-heading-elements-to-create-a-document-outline/
 [2]: https://www.w3.org/TR/2016/REC-html51-20161101/changes.html#changes