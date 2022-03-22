# Defining Content Presets | Stackbit Documentation - V2 Beta

[https://docs.stackbit.com/conceptual-guides/content-presets/](https://docs.stackbit.com/conceptual-guides/content-presets/)

Presets are sets of initial field values for new content objects created in the UI.

When you add a new page or section in the Stackbit UI, what you're actually doing is telling the UI to create a new content object whose properties are based on a specific model. Thus, presets are always defined for a specific model.

For each model there can be any number of presets in your project, depending on the needs of content editors.

When adding a new page in our UI, you're choosing the model to use from the list of models [marked as pages](https://docs.stackbit.com/reference/stackbit-yaml/mapping-content-models/) in the project configuration. If there are presets available for that model, the UI will let the user choose one as the basis for the new page.

Presets are particularly helpful with models that are generic in nature, such as the **PageLayout** model. Via presets, content creators can choose a look for the page that's focused on a specific use case: a contact page, an about page, a careers page - rather than start from scratch.

Here's a snippet from a preset file for **PageLayout,** edited for brevity. It contains two presets: one for a contact page, the other for an about page.

```
{
  "model": "PageLayout",
  "presets": [
    {
      "label": "Contact",
      "thumbnail": "images/page-contact.png",
      "data": {
        "title": "Contact us",
        "sections": [
          {
            "type": "HeroSection",
            "title": "Contact us",
            "text": "Fill out the form below...",
            "feature": {
              "type": "FormBlock",
              "action": "/.netlify/functions/submission_created",
              "fields": [
                {
                  "type": "TextFormControl",
                  "label": "Name"
                },
                {
                  "type": "EmailFormControl",
                  "label": "Email"
                }
              ]
            },
            "styles": {
              "self": {
                "alignItems": "center",
                "justifyContent": "center",
                "flexDirection": "row"
              },
              "title": {
                "fontWeight": 700
              },
              ...
            }
          }
        ]
      }
    },
    {
      "label": "About",
      "thumbnail": "images/page-about.png",
      "data": {
        "title": "About us",
        "sections": [
          {
            "type": "HeroSection",
            "title": "About Us",
            "subtitle": "Who We Are",
            "text": "Elaborate a bit about us...",
            "feature": {
              "type": "ImageBlock",
              "url": "/images/about.jpg"
            },
            "styles": ...
          },
          {
            "type": "CtaSection",
            "title": "Careers",
            "text": "Learn about open careers...",
            "actions": [
              {
                "type": "Button",
                "label": "Learn more",
                "url": "/"
              }
            ],
            "styles": ...
          }
        ]
      }
    }
  ]
}

```

To learn about the file format in more detail, where you should store preset files and how to organize them, see the [reference article](https://docs.stackbit.com/reference/content-presets).

The reference also comes with "this one cool trick..." on how to easily create this data!

Presets are also useful for components within pages. In particular, [section-type components](https://docs.stackbit.com/conceptual-guides/components/atomic-design) have a lot to benefit from presets, as they're complex components that can be molded to fit many purposes.

Our themes come built-in with a selection of presets for each section component. Here's a screenshot of the options presented in the UI when adding a new section. To the left is the list of models, and to the right - the thumbnails for each preset.

[Add a section with presets](https://docs.stackbit.com/static/d06101793172a723f91fa17d28c89ae2/9f9a4/add-section-presets.png)

![Defining%20C%208693f/add-section-presets.png](Defining%20C%208693f/add-section-presets.png)

Model files can also define [default values for fields](https://docs.stackbit.com/reference/defining-models/field-properties/#default) when a new instance of that model is created. There are generic defaults not bound to any theme, and each field can only have one default.

On the contrary, presets are typically more specific: they are geared for a concrete use case in mind, and there can be a number of them. Hence, if a content preset includes a value for a field that has a default value in the model, the preset wins.

For more information, see the [reference](https://docs.stackbit.com/reference/content-presets).