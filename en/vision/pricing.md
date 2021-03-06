---
editable: false
---
# Pricing for [!KEYREF vision-name]

## What goes into the cost of using [!KEYREF vision-short-name] {#rules}

The [!KEYREF vision-short-name] service provides [a set of features for image analysis](concepts/index.md#features).

Each successful analysis performed using any feature is charged as a single _unit_:

* If your request contains multiple images, each analyzed image is charged separately.
* If you send two requests to recognize text on the same image, you will be charged for two units. This makes sense when a text  [is written in languages from different language models](operations/ocr/text-detection.md#multiple-languages) (for example, it includes Arabic and Hebrew).
* Only successful analysis attempts are chargeable. You will not be charged if the server returned an error or the request configuration was incorrect.

[Face detection](concepts/face-detection/index.md) and [image classification](concepts/classification/index.md) are free of charge during the [Preview stage](../overview/concepts/launch-stages).

## Pricing {#prices}

| Feature | For 1000 units<br>/month, without VAT | For 1000 units<br>/month, with VAT |
| ----- | ----- | ----- |
| [Text recognition](concepts/ocr/index.md) | 100 ₽ | 120 ₽ |

