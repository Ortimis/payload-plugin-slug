# Payload Plugin Slug

A convenient drop-in field for [Payload CMS](https://payloadcms.com) to quickly add a slug field to a collection with sensible defaults.



## Background

Payload CMS does not provide a default slug field, and implementing one for quick projects requires building a custom component. This repo is here to help.

The implementation is mainly based on PaylodCMS' own [Website Template](https://github.com/payloadcms/payload/blob/v3.0.0-beta.122/templates/website/src/fields/slug/SlugComponent.tsx).


## How to use

1. Add this to your collection config.
2. Done!

This is not a plugin in payload's stricter terms. Do not add this to your payload.config() in the Plugin array.

```ts
import { slugField } from 'payload-plugin-slug'

export default buildConfig({

  collections: [
    {
      slug: 'users',
      auth: true,
      fields: [],
    },
    {
      slug: 'pages',
      admin: {
        useAsTitle: 'title',
      },
      fields: [
        {
          name: 'title',
          type: 'text',
        },
        {
          name: 'content',
          type: 'richText',
        },

        ...slugField(), // add the field like so.
      ],
    },
  ],
  
})
```

## Change defaults

You can change the field by which standard slugs are generated from, as well as change config defaults.

```ts
...slugField("field-to-use-", {
  TextField: {
    required: false,
  },
  CheckboxField: {
    //...
  }
})
```


If you want to extend the field, you can simply copy & paste it to your own field library.