# Mister Sparkle

### An experiment in preserving engaging prose across languages

> Preserving meaning while maintaining voice

Documentation that people enjoy reading often has a distinct voice: rhythm, well-chosen idiom, concrete examples, and sometimes humor. The approach isn't suitable for all kinds of technical content. But when it supports the content, that voice is kind of a superpower. Engaged readers are much more likely to keep going even when the material is dry or challenging.

Those same engaging qualities can make documentation hard to translate and difficult for some readers to understand. Machine translation systems are better than they were, but they can still struggle with source-language-specific idiom, tone, and cultural context.

The Mister Sparkle experiment aims to retain reader engagement while improving translatability. Separate out the sparkle; retain meaning, terminology, constraints, warnings, and uncertainty; translate what's left; re-inject appropriate sparkle in the target language.


## The AI opportunity

In the 1980s, the aerospace industry adopted Simplified Technical English, a controlled form of English that defines specific vocabulary and sentence structures that make documentation more understandable and translatable. Similar approaches have since been widely adopted in global enterprises.

Writers consistently report that writing in these restricted dialects is soul-crushing, and demotivated writers are less likely to produce their best work. So any solution that relies exclusively on human discipline can have implications for documentation quality.

A chain of LLM-assisted transformations may make it possible to produce documentation that is both enjoyable to read and easier to translate. The first transformation removes language that is difficult to translate while retaining technical meaning, constraints, uncertainty, terminology, and the document’s task structure. The resulting intermediate English would not be strictly Simplified Technical English, but it might occupy similar territory. (Fortunately, LLMs don't have souls to crush.)

This intermediate English version may itself be useful as a plain-language or controlled-language reading option for readers who prefer direct, low-idiom prose. It's also the input to the next transformation: translation. Reducing idiom and other source-language-specific phrasing might make automated translation more reliable and easier to evaluate.

For example, translation produces a simplified Japanese document that can be published as-is for readers who prefer low-idiom content. AI can then revise that translation into natural, engaging Japanese for its intended audience, using Japanese rhetorical conventions rather than literally translated English idioms.

We can also "translate" the simplified English version back into idiomatic English, essentially performing a controlled rewriting or editorial normalization pass. That wasn't our original goal, but for some teams, it might actually be Mister Sparkle's primary use case.

LLMs can often detect abstract features in written language, but are they reliable enough for this task?

## Defining "sparkle"

How do we define "sparkle" better than "we know it when we see it?" Broadly, sparkle comprises aspects of writing that support reader engagement or create an appropriate emotional effect. Some are specific to the language in which the text is written or to the culture of its typical readers; others are more general rhetorical or explanatory choices. Examples of what we mean include:

- Reader-oriented pacing
- Concrete images and examples
- Idioms and figures of speech
- Curiosity and question–answer momentum
- Contrast, surprise, and productive tension
- Sentence rhythm and variation
- Metaphor and analogy
- Carefully rationed humor
- Acknowledgment of reader effort or uncertainty
- Understanding of stakes
- Transitions that make each sentence create a reason to read the next

Sparkle is not merely a synonym for humor. The purpose of sparkle isn't merely to enliven boring technical content with jokes. Target-language adaptation must respect genre, situation, audience, and emotional register. It can effectively provide:

- A reward for the reader after they have followed a difficult point
- A concrete image that makes an abstract distinction stick
- A small release of tension in dense or procedural material
- Evidence that a human being, not a malfunctioning policy generator, wrote the document
- A way to signal proportion: this is important, but we need not dress it in solemnity.

## The central questions

Can a properly prompted model identify the features that make a document engaging, determine what functions they serve, and decide which should be preserved, adapted, or omitted in another language?

Can we produce effective low-idiom intermediate documents? If so, how do we re-insert idiomatic expression in the target language in the right places? Can we rely on the LLM's instincts, or do we need to track where those characteristics were located in the original? How do we keep "sparkle" from being added in places where it doesn't belong? This matters especially outside technical documentation: an obituary may need warmth and a distinctive voice, but a joke is almost certainly the wrong kind of engagement. 

Other open questions include:

- How do we identify which documents already have sparkle that must be preserved?
- What must an intermediate representation preserve to support faithful translation and natural target-language rewriting?
- How do we effectively prompt generation of intermediate representations?
- How much guidance must we provide about the desired target-language voice after translation?
- Do Japanese prompts work better with Japanese documents than English prompts?
- Which models work best for each stage of the pipeline?
- Which model parameters, such as `temperature` and `top-p`, affect quality at each stage?
- How can we minimize token use in pre-translation and post-translation processing?
- For which document types, language pairs, and risk levels can human review be reduced or eliminated?

## Project status

Mister Sparkle is an informal research project and will remain one for the indefinite future. We will develop approaches, prompts, and reusable skills to achieve the necessary content transformations, along with a rubric for evaluating their effectiveness.

It may be that our undertaking is fundamentally infeasible at present, or that only some stages of the pipeline can be made effective. That's a useful finding in itself. We'll learn more about the current limits of machine translation and develop metrics for evaluating future language models on the task.

## How you can help

Please suggest approaches, prompts, and other ideas here by raising issues and creating pull requests. For example:

- Source documents, especially deliberately difficult test passages
- Transformation prompts and reusable skills
- Structured representations or annotation guidelines
- Target-language rewrites for languages you know
- Bilingual evaluation rubrics and translation-quality metrics
- Translation-error definitions and taxonomies
- Reproducibility practices, including model, version, and prompt records

I'm looking for bilingual volunteers to evaluate translation effectiveness. Please contact me at engyrus@gmail.com. Spammer no spamming!

## About me

I'm Jerry Kindall, an experienced technical communicator (formerly with AWS, Snowflake, and Microsoft) engaging with AI to improve the effectiveness of technical documents.

Another of my projects is [Charlie](../charlie-project/), a restricted English scheme intended for writing more reliable AI prompts and skills while preserving readability. We might use Charlie concepts in our Mister Sparkle prompting.

## The name

*Of course* it's a Simpsons reference: "In Marge We Trust," season 8, episode 22. The goal of our project is to use AI to retain the engaging qualities ("sparkle") of prose during translation. The name sprang immediately into my head and wouldn't leave.

I spell out "Mister" to help people find the project without wading through a sea of Simpsons fan pages.

## Suggested reading

There's no requirement to read anything in particular—non-specialists' thoughts are just as valuable here as those of seasoned AI practitioners or researchers—but you might find these useful.

* *Le Ton beau de Marot: In Praise of the Music of Language,* Douglas Hofstadter, Basic Books, 1997. ISBN 0-465-08645-4. Noted AI researcher explores translation issues by collecting dozens of translations of a light French lyric poem ("Ma Mignonne" by Clément Marot) into English. It includes several 1997-era machine translations, which are as dreadful as you'd expect. The book's title is a multi-layered pun.

If you only read one thing for this project, make it Hofstadter. *Marot* provides a conceptual anchor for thinking about which traits matter when text crosses language boundaries. Translating poetry is Mister Sparkle on hard mode, and the book is enjoyable and stimulating. And long, but you can skip around at will.

### Controlled text transformation

- “Deep Learning for Text Style Transfer: A Survey,” Di Jin et al. (2022). A broad survey of methods, datasets, and evaluation for changing attributes such as style, politeness, emotion, and humor while attempting to preserve content.

- “Controllable Text Generation for Large Language Models: A Survey” (2024). A survey of methods for constraining LLM output by content and attribute requirements, including linguistic style.

- “Automatic and Human-AI Interactive Text Generation,” ACL tutorial (2024). Covers text simplification, paraphrase generation, style transfer, human-AI collaboration, and evaluation. These are close relatives of Mister Sparkle’s proposed transformations.

### Translation and evaluation

- *Neural Machine Translation*, Philipp Koehn. A technical introduction to neural machine translation, including models, training, decoding, data, and evaluation.

- *Speech and Language Processing*, Daniel Jurafsky and James H. Martin, chapter on machine translation. Broad background on machine translation and evaluation, including automatic metrics and their limitations.

### Optional background

- “Attention Is All You Need,” Ashish Vaswani et al. (2017). The paper that introduced the Transformer architecture behind most contemporary LLMs. Useful background on the systems that the project will use, rather than on the project’s translation methodology.

