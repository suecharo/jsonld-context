# jsonld-context

Test for https://www.w3.org/TR/json-ld/#scoped-contexts.

From [`./example.json`](./example.json):

```json
{
  "@graph": [
    {
      "@id": "https://example.com/path/to/base_file",
      "@type": "File",
      "@context": "https://raw.githubusercontent.com/suecharo/jsonld-context/main/base.jsonld",
      "name": "base file"
    },
    {
      "@id": "https://example.com/path/to/ext_file",
      "@type": "File",
      "@context": "https://raw.githubusercontent.com/suecharo/jsonld-context/main/ext.jsonld",
      "name": "ext file",
      "description": "ext file description"
    },
    {
      "@id": "https://example.com/dataset",
      "@type": "Dataset",
      "@context": "https://raw.githubusercontent.com/suecharo/jsonld-context/main/base.jsonld",
      "name": "dataset",
      "hasPart": [
        {
          "@id": "https://example.com/path/to/base_file"
        },
        {
          "@id": "https://example.com/path/to/ext_file"
        }
      ]
    }
  ]
}
```

To:

```json
[
  {
    "@id": "https://example.com/path/to/base_file",
    "@type": [
      "https://raw.githubusercontent.com/suecharo/jsonld-context/main/base.yml#File"
    ],
    "https://raw.githubusercontent.com/suecharo/jsonld-context/main/base.yml#File#name": [
      {
        "@value": "base file"
      }
    ]
  },
  {
    "@id": "https://example.com/path/to/ext_file",
    "@type": [
      "https://raw.githubusercontent.com/suecharo/jsonld-context/main/ext.yml#File"
    ],
    "https://raw.githubusercontent.com/suecharo/jsonld-context/main/ext.yml#File#description": [
      {
        "@value": "ext file description"
      }
    ],
    "https://raw.githubusercontent.com/suecharo/jsonld-context/main/ext.yml#File#name": [
      {
        "@value": "ext file"
      }
    ]
  },
  {
    "@id": "https://example.com/dataset",
    "@type": [
      "https://raw.githubusercontent.com/suecharo/jsonld-context/main/base.yml#Dataset"
    ],
    "https://raw.githubusercontent.com/suecharo/jsonld-context/main/base.yml#Dataset#hasPart": [
      {
        "@id": "https://example.com/path/to/base_file"
      },
      {
        "@id": "https://example.com/path/to/ext_file"
      }
    ],
    "https://raw.githubusercontent.com/suecharo/jsonld-context/main/base.yml#Dataset#name": [
      {
        "@value": "dataset"
      }
    ]
  }
]
```
