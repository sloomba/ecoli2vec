## ecoli2vec
### Embedding E.coli host to a vector space | sloomba

./dat_ecoli2vec contains 100-dimensional vector space embeddings of key genes (including transcription factors) and promoters of E.coli. The embeddings have been derived by using "strong" RegulonDB ontologies (see ./dat_regulondb) that describe:

1. regulatory relationships
* <tf> "regulates" <gene>; <gene> "regulated_by" <tf>
* <tf> "positively_regulates" <gene>; <gene> "positively_regulated_by" <tf>
* <tf> "negatively_regulates" <gene>; <gene> "negatively_regulated_by" <tf>
2. causal binding & promotor relationships
* <tf> "binds_to" <promoter>; <promoter> "bound_by" <tf>
* <promoter> "promotor_of" <gene>; <gene> "promoted_by" <promoter>
3. sequence descriptions
* <tf_seq> "seq_of" <tf>
* <promoter_seq> "seq_of" <gene>
* <gene_seq> "seq_of" <gene>

Accordingly, we derive 3 types of embeddings:
1. ecoli2vec_grn_100.tsv: embed only regulatory relationships
2. ecoli2vec_seqgrn_100.tsv: embed regulatory relationships + sequence information of TFs and genes
3. ecoli2vec_causalgrn_100.tsv: embed regulatory and causal relationships + sequence information of TFs, promoters and genes

Note: For each pair of entities observing <entity_src> <relationship> <entity_tgt>, the relationships have been symmetrisized to include <entity_tgt> <relationship_reverse> <entity_src>. Additionally, each entity has 2 vector representations: the input and the output representation corresponding to when it acts as a source and when it acts as a target in a relationship, respectively. (This decoupling makes learning representations more tractable, see the original word2vec paper by Mikolov et. al (2013) for more.) The input representation is noted as such, while the output representation is noted with a "__label__" prefix.
