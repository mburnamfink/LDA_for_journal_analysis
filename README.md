# LDA_for_journal_analysis

This project used natural language processing to evaluate science for novelty.

The genesis for this project was my previous work using Rao-Stirling diversity to assess the interdisciplinarity of scientific papers. While I think Rao-Stirling is a solid metric, it's based on citations, and in particular how journals are assigned to the 224 Web of Science journal categories, and the overall pattern of citations in 2010 via Loet Leydesdorff's [Science Overlay Toolkit](https://www.leydesdorff.net/overlaytoolkit/). While these measures are widely used, their validity has not been conclusive proved.

I believed I could use Natural Language Processing on article abstracts to derive a scientometric measure based on the actual language used by scientists to describe their own research, which would be more granular and accurate than a citation based measure. Using Latent Dirichlet Allocation via [gensim](https://radimrehurek.com/gensim/), I analyzed 71000 articles published in the 40 most important journals over the past decade. Each abstract was lemmatized, the corpus broken down into trigrams, and then allocated to a 40 topic LDA model.

These topics accurately predicted which journal an article was published in (0.96 accuracy). The Jensen-Shannon divergence between a given abstractract and its topic composition measures the degree to which an article differs from random jargon in its field, i.e. its scientific novelty. Novelty in practice varies between 0.55 and 0.69, and is negative correlated with citation velocity, an expected result from the tendency of science to organize around disciplinary 'thought collectives' (see Ludwig Fleck and Thomas Kuhn), and for high impact results to modify their fields.

Visualizations are available on Tableau.
https://public.tableau.com/profile/michael.burnam.fink#!/vizhome/MBF_Fletcher_Journal_Topic_Explorer/Dashboard2
https://public.tableau.com/profile/michael.burnam.fink#!/vizhome/MBF_Fletcher_Paper_Explorer/Dashboard1
