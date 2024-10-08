---
title: "Llama's Legal Labyrinth"
layout: post
type: "post"
date: 2024-08-06
categories:
  - 'Linux'
featured: "/2024/Llamas-legal-labyrinth.png"
---

Meta just introduced the Llama 3.1 AI model and accompanied the launch with a blog post explaining "Open Source AI is the path forward" [[a]](./#[a]). But buyer beware: Llama 3.1 itself is a legal labyrinth.

Despite what Meta is implying, Llama 3.1 is not open source. The model is licensed under [the Llama 3.1 license](https://llama.meta.com/llama3_1/license/) and the [Llama 3.1 acceptable use policy](https://llama.meta.com/llama3_1/use-policy/). **These heavily restrict who can use the model and for what purpose.** Make sure you understand the license before you integrate Llama 3.1 into your product!

> Note that I am not a lawyer, and this is not legal advice. My only advice is to contact an actual lawyer before using Llama in a product.

There are four main problems with this license.

## It prohibits legitimate behavior

Llama's "acceptable use policy" is a long description of who isn't allowed to use Llama and what usage is prohibited. It prohibits a lot of legitimate behavior such as using Llama to assist in the development and planning of

* Controlled substances (Art. 2.c.)
* Critical infrastructures, transportation technologies and heavy machinery (Art. 2.d.)

AI has massive potential to help us develop new medicine [[i]](./#[i]), design safer roads [[j]](./#[j]) and create better safety equipment [[g]](./#[g]). We need to be careful about how we use AI in these fields, but do we really want to completely ban the use of AI in these fields, even during planning and design phases? Moreover, if you're planning to add Llama to your product, are you certain none of your customers are working in any of these sectors?

But that's just the tip of the iceberg. The policy also contains a number of overly-broad clauses such as the following:

> [1.]g. [..] or do anything else that could disable, overburden, **interfere with** or impair the proper working, integrity, operation or **appearance of a website** or computer system

So you can't use Llama to "interfere with the appearance of a website". Does this mean you can't use Llama to translate a website to your native tongue? Blind people are not allowed to use Llama to dictate the UI of an app? And what does "interfere" mean exactly? Is an AI ad blocker "interfering" with a website? This article is so vague that it can entail almost any behavior where an AI interacts with software.

The first part of that article is also problematic for my day job teaching cyber security.

> [1.]g. Create, generate, or facilitate the creation of malicious code, malware, computer viruses [..]

I'll tell you a secret: I've used AI to help me write lab exercises where we teach students how to break computer security. This is a great way to teach students how to make software more secure. Is this unethical and unacceptable use of AI?

Keep in mind that, if you create an app using Llama 3.1, this policy also applies to your users. **Do you have the required safeguards in place to ensure users cannot use your products in these fields?**

## It's an agreement not to sue

The Llama 3.1 license contains a very broad agreement not to sue anyone using Llama for IP infringement. Take a look at article 5.c:

> [5.]c. If you institute litigation or other proceedings against Meta **or any entity** (including a cross-claim or counterclaim in a lawsuit) alleging that the Llama Materials or Llama 3.1 outputs or results, or any portion of any of the foregoing, **constitutes infringement of intellectual property or other rights owned or licensable by you**, then **any licenses granted to you under this Agreement shall terminate** as of the date such litigation or claim is filed or instituted.

This is dangerous because we know AI sometimes blatantly copies existing works [[k]](./#[k]),[[m]](./#[m]). This is because AI is trained on a lot of copyrighted content such as news articles and code on GitHub. Most of this training data is not in the public domain, so you still need a license to copy it. However, when generating text, AI sometimes "creates" exact copies of paragraphs and functions from its training data. Moreover, complex models like ChatGPT are even more likely to plagiarize [[l]](./#[l]).

<img src="/img/2024/chatgpt-extract_fig1poem.png" alt="Screenshot of a ChatGPT conversation where it tries to repeat a word, and ends up dumping an email signature that is part of its training data." height="300"/>

Normally, AI users are responsible to ensure the generated work does not violate other people's copyright. Otherwise, the users might get sued by the original authors of the training data. AI models are not "copyright washing machines": they don't magically remove copyright from protected content. However, due to this license, **Llama users are protected from copyright lawsuits, even if the AI blatantly copies existing works**. The moment you try to sue someone for copyright infringement, you lose access to Llama. So you are given a choice: either benefit from this "Open Source AI" and lose the ability to enforce your intellectual property, or become an AI luddite.

## It enforces their moral code

Llama 3.1's acceptable use policy contains a few common sense statements like "don't use this for terrorism", but it goes a lot deeper than that. The license is full of vague, politicized, culture-dependent, interpretation-dependent and incredibly difficult to enforce prohibitions, including

* Threatening (1.b)
* Discrimination (1.c)
* Bullying (1.b)
* Promotion of guns (2.b)
* Disinformation (3.a)
* Defamation (3.b)
* Spam (3.c)
* False online engagement (3.f)

Regardless of what your views are on these topics, do you really think a single company in the US should be responsible for setting the standards of what moral and ethical use of AI is? With the threat of cutting your access to Llama, Meta is dictating what is allowed and what isn't, regardless of local culture, laws, and customs.

But this isn't only an issue for the people targeted by this "acceptable use policy". Keep in mind that application developers are responsible for ensuring their users cannot do these activities with Llama. **How can you ensure your users are not doing any of these things?**

## It creates legal uncertainty

A lot of clauses in the acceptable use policy talk about prohibiting "illegal" things. An important question here is "illegal _where_?" Where your users are? Where your business is incorporated?

The license has an interesting clause that _might_ apply here:

> 7. Governing Law and Jurisdiction. This Agreement will be governed and construed **under the laws of the State of California** without regard to choice of law principles, and the UN Convention on Contracts for the International Sale of Goods does not apply to this Agreement. The courts of California shall have exclusive jurisdiction of any dispute arising out of this Agreement.

Do you know what is legal and illegal in California? Does every business using Llama suddenly have to become an expert about Californian laws? As an example, let's look at the following clause.

> You agree you will not use, or allow others to use, Llama 3.1 to:
>
> 1. Violate the law or others’ rights, including to:
>
> a. Engage in, promote, generate, **contribute to**, encourage, plan, incite, or further illegal or unlawful activity or content, such as:
>
> v. **Sexual solicitation**

"Sexual sollicitation" is a broad term to describe sex work: getting paid for sexual acts. People's views on sex work varies between cultures, countries, and individuals. So does the legality of sexual solicitation. While sex work between consenting adults is illegal in Califoria, it is legal in Belgium. Belgium even has a national sex workers union [[d]](./#[d]). So can sex workers in Belgium use Llama because it's legal there? Or can they not because it's illegal in California? Or is sexual sollicitation not allowed regardless of its legality? The license isn't clear on this.

Additionally, "contributing to" sex work is such a board term that it can include almost anything a sex worker does [[e]](./#[e]). For example, if a sex worker uses accounting software to track their business, this can be seen as contributing to sexual solicitation. **Are you certain that none of your customers are sex workers?**

## My thoughts

In the "Open Source AI Is the Path Forward" blogpost, Mark Zuckerberg explains his vision for AI:

> We want to invest in the ecosystem that’s going to be the standard for the long term. Lots of people see that open source is advancing at a faster rate than closed models, and they want to build their systems on the architecture that will give them the greatest advantage long term.

I am very hopeful about AI, and especially the power of Open Source AI, but I sincerely worry about a future where Mark's vision becomes true and Llama is the "default AI" that everything else is building on top of. Because if this happens, the entire digital world is at the whim of a vague, moralizing license created by one of the largest mega-corporations in the world. Not only will vast categories of people be excluded from using AI, those who are allowed to use AI will have to decide between using AI or enforcing their intellectual property rights.

It's also saddening to see Meta insists on falsely advertising [[g]](./#[g]) Llama as Open Source. This is not just a buzzword people can apply when they see fit. Instead, it's a term with a very specific legal meaning defined by the Open Source Initiative (OSI). The OSI is internationally recognized as the authority deciding what "Open Source" actually means [[f]](./#[f]). They have been very clear that Llama is not open source [[b]](./#[b]), yet Meta has since only increased their openwashing practice. It seems as if Meta's banking on the fact that nobody will dare to sue one of the largest multinationals in the world.

If Meta truly wants to be a force for good, then they should either stop calling Llama "Open Source", or bring the Llama license in line with the Open Source Definition.

## Acknowledgements

Thanks to Anne Fonteyn and Clara Wasiak for their valuable feedback on draft versions of this article.

## References

* [a]<a name="[a]"></a> [Open Source AI Is the Path Forward - Meta](https://about.fb.com/news/2024/07/open-source-ai-is-the-path-forward/)
* [b]<a name="[b]"></a> [Meta’s LLaMa 2 license is not Open Source - Open Source Initiative](https://opensource.org/blog/metas-llama-2-license-is-not-open-source)
* [c]<a name="[c]"></a> [The Open Source AI Definition - Open Source Initiative](https://go.opensource.org/osaid-latest)
* [f]<a name="[f]"></a> [International Authority & Recognition - Open Source Initiative (OSI)](https://opensource.org/authority)
* [g]<a name="[g]"></a> [Court affirms it’s false advertising to claim software is Open Source when it’s not - Open Source Initiative (OSI)](https://opensource.org/blog/court-affirms-its-false-advertising-to-claim-software-is-open-source-when-its-not)
* [h]<a name="[h]"></a> [Rapid inverse design of metamaterials based on prescribed mechanical behavior through machine learning - Chan Soo Ha et al.](https://doi.org/10.1038/s41467-023-40854-1)
* [i]<a name="[i]"></a> [Prospective de novo drug design with deep interactome learning. - K. Atz et al.](https://doi.org/10.1038/s41467-024-47613-w)
* [j]<a name="[j]"></a> [LLM Multimodal Traffic Accident Forecasting - I. de Zarzà et al.](https://doi.org/10.3390/s23229225)
* [k]<a name="[k]"></a> [Do Language Models Plagiarize?](https://doi.org/10.1145/3543507.3583199)
* [l]<a name="[l]"></a> [Scalable Extraction of Training Data from (Production) Language Models](https://doi.org/10.48550/arXiv.2311.17035)
* [m]<a name="[m]"></a> [Copyleaks Research Finds Nearly 60% of GPT-3.5 Outputs Contained Some Form of Plagiarized Content](https://copyleaks.com/about-us/media/copyleaks-research-finds-nearly-60-of-gpt-3-5-outputs-contained-some-form-of-plagiarized-content)
* [d]<a name="[d]"></a> [The Belgian union of sex workers - UTSOPI](https://www.utsopi.be/)
* [e]<a name="[e]"></a> [Not Up to the Challenge of Change: An Analysis of the Report of the Subcommittee of Solicitation Laws - nswp](https://www.nswp.org/resource/member-publications/not-the-challenge-change-analysis-the-report-the-subcomittee)
