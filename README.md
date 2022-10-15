# OBJECTIVES

1. Describe how you would make a line of text in a homepage section editable from theme customization and how you would access this in liquid.
2. How would you add the collection featured image as a banner on the collection liquid template?
3. Using liquid code and HTML, create a simple pagination container, "< 1 2 ... 5 >".
4. Using liquid code, access the product named "Blue T-Shirt". Store the id, title, handle, price, url, and image in variables.
5. Using liquid code, create a key:value array using the list below. Loop through the array. Upon key type, store the value in a variable to be used later:
   - fruit:apple
   - vegetable:carrot
   - cloth:t-shirt
   - denim:jeans

# ANSWERS TO THE OBJECTIVES

1.  Describe how you would make a line of text in a homepage section editable from theme customization and how you would access this in liquid.
    - I made a section called homepage-editable-text.liquid, There is two main parts to this file.
      - `<h1>{{ section.settings.section_text }}</h1>`
      - `“settings” : [ { "type": "text", "id": "section_text", "label": "test section text" } ]`
      - the section.settings is getting the access to the ID in the settings object.
2.  How would you add the collection featured image as a banner on the collection liquid template?
    - I made a new collection.dyode.json file and a new section/dyode-featured-banner.liquid file and assigned that new collection template to a collection, inside that new collection template the featured image can be accessed with `{{ collection.image | image_url }}`, you can also access the first image of the first product in that collection if a featured image isn’t provided.
3.  Using liquid code and HTML, create a simple pagination container, "< 1 2 ... 5 >".
    - I was confused on what you wanted out of this, so I just paginated the collection by 1 product to show the pagination buttons.
      - `{% paginate collection.products by 1 %} {% for product in collection.products %} {{product.title}} {{product.featured_image}} etc...... {% endfor %} {% endpaginate %}`
4.  Using liquid code, access the product named "Blue T-Shirt". Store the id, title, handle, price, url, and image in variables.
    - ` {% assign product = all_products.blue-t-shirt %}`
    - this gets access to that specific product assuming the handle is blue-t-shirt
    - on that link these are printed out at the bottom of that collection page
    - `{% assign product_id = product.id %} {% assign product_title = product.title %} {% assign product_handle = product.handle %} {% assign product_price = product.compare_at_price_max %} {% assign product_url = product.url %}{% assign product_image = product.featured_image %}`
