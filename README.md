# poim-shared-datamodels
This repository contains common data models that are used within POI Management. It contains datamodels in protobuf but it can be used for further datamodels in the future

## Concept


![Concept](doc/concept.png)

## Howto use 

You can reference a specifc datmodel in your go code by importing this repo as a go module:


```go
import (
	"github.com/vwdfive/poim-shared-datamodels/proto"
)
```

and run:

`go get github.com/vwdfive/poim-shared-datamodels`

### VS Code adaption
This repo is only visible inside the organization. To make it accessible via `go get` you need configure the access to the repo in the vscode settings (https://docs.github.com/en/codespaces/managing-your-codespaces/managing-repository-access-for-your-codespaces): 
* open the `devcontainer.json`
* add this snippet: 

```
{
  "customizations": {
    "codespaces": {
      "repositories": {
        "vwdfive/poim-shared-datamodels": {
          "permissions": {
            "contents": "read-all"
          }
        }
      }
    }
  }
}
```

## Howto Extend / Adapt the datamodels

### Don'ts !!!

Please consider the best practices for protobuf: https://protobuf.dev/programming-guides/dos-donts/

Most important:

* To keep backward compability don't remove fields from messages. If you really want to remove a field, then reserve the number to prevent the re-use for a new attribute (also valid for enums. See: https://protobuf.dev/programming-guides/dos-donts/#do-reserve-numbers-for-deleted-enum-values)
* Never change the default value of a field (https://protobuf.dev/programming-guides/dos-donts/#dont-change-the-default-value-of-a-field).


### Do's
* Follow the Style Guides: https://protobuf.dev/programming-guides/dos-donts/#do-follow-the-style-guide-for-generated-code
* Consider API Best Practices (https://protobuf.dev/programming-guides/api/)


### Review Process

The data models shared in this repo a used in multiple project. To avoid breaking changes, representatives of all project teams must be included into the review process and give their approvals.


## Projects 

* POI Monetization Ad Service (Contact: @GerrJan)
* POI DOPI Service (@fabi-berlin)
