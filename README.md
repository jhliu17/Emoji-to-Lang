# Emoji to Lang

**Translate Emoji to Human Language**

Emoji-to-Lang translates emoji code in a sentence to its language representations. The default converting languages contain ``'en'``, ``'es'``, and ``'pt'``. Support multilingual language translation based on Emoji annotation files in [CLDR](https://github.com/unicode-org/cldr/tree/release-38/common/annotations).


## Usage

The built-in supported languages are English (``language='en'``), Spanish (``'es'``), and Portuguese (``'pt'``).

```python
>> print(emoji.demojize('Python is 👍'))
Python is :thumbs_up:
>> print(emoji.demojize('Python es 👍', language='es'))
Python es :pulgar_hacia_arriba:
>>> print(emoji.demojize("Python é 👍", language='pt'))
Python é :polegar_para_cima:️
```

If you want to translate Emoji code into other languages, an annotation file is necessary. Take the ``Indonesian`` as
an example, download the ``id.xml`` in [CLDR](https://github.com/unicode-org/cldr/tree/release-38/common/annotations) and
import it.

```python
>> emoji.import_from_annotation('annotaion_xml/id.xml', language='id')
100%|████████████████████████████████████████| 3392/3392 [00:00<00:00, 50062.74it/s]
Language `id` annotation file imported successfully.
>> print(emoji.demojize('Python adalah 👍', language='id'))
Python adalah :jempol_ke_atas:
```

Emoji-to-Lang only translates the emoji into different language representations without changing the remaining parts.

```python
>> print(emoji.demojize('那是真的🐂🍺', language='id'))
那是真的:lembu::mug_bir:
```

You can define the template format by setting `delimiters` and `sticky_character`.

```python
>> print(demojize('Language is 😊', delimiters=('[', ']'), language='id', sticky_character=' '))
Language is [wajah tersenyum dengan mata bahagia]
```

## Installation

```bash
$ git clone https://github.com/jhliu17/emoji-to-lang.git
$ cd emoji-to-lang
$ python setup.py install
```

## Acknowledgment

This project is developed based on the [emoji](https://github.com/carpedm20/emoji).
