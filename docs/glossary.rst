Glossary of terms used
======================

book:
    A UTF-8 encoded text file that has been imported into CLiC, invariably from the corpora repository.

region:
    A labelled portion of a book. Each region will have:

    * A name (or rclass), for example 'chapter.sentence'. For all possible names, see :github:`/schema/10-rclass.sql`.
    * A start and end character position within the full book text
    * (optionally) a number (or rvalue), for example it's position within a chapter.

    Regions are added by *region tagger* scripts, which are in :mod:`clic.region`.

token:
    A token is a labelled portion of a book that contains a single word.
    In the phrase ``'For _more_!' said Mr. Limbkins.``, ``For``, ``more``, ``said``, ``Mr``, ``Limbkins`` would be tokens.

    See :mod:`clic.tokenizer`.

type/ttype:
    A token has a type (thus ttype). This is a normalised form of the token.
    The tokens in the phrase ``'For _more_!' said Mr. Limbkins.`` would have types ``for``, ``more``, ``said``, ``mr``, ``limbkins``.

    See :mod:`clic.tokenizer`.

analysis tree (FlexiConc):
    An analysis tree is the research documentation that is generated while analysing concordances in FlexiConc. The tree can be saved and imported as a JSON file.

algorithm (FlexiConc):
    An algorithm is an operation that you apply to a concordance in FlexiConc mode.
    To sort your concordance in alphabetical order, you apply the algorithm ``Select by Token-Level String Attribute`` and configure the settings.

annotation (FlexiConc):
    Annotation is additional information that you can add to a concordance in FlexiConc mode.
    Running ``Annotate with spaCy POS tags`` adds part-of-speech tags to all tokens in your concordance line. You can then use the algorithm ``Select by Token-Level String Attribute`` to select concordance lines with an adjective to the left of the node.
