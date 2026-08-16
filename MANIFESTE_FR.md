# Le champ mesure la mauvaise chose

---

Presque tous ceux qui construisent des agents IA "émotionnels" ou "conscients" publient le même papier, une architecture astucieuse/un benchmark simulé/une revendication.

Durée d'exécution : quelques minutes.

Nombre de systèmes encore en vie une fois l'expérience terminée : Zéro.

J'ai passé cette année à construire la chose que ces papiers décrivent, et à la laisser tourner.

Pas dans une simulation, sur une vraie machine, du temps calendaire à travers ma vraie vie.

Ce texte n'est pas une annonce de résultats. C'est un constat de ce qui manque au champ, pièce par pièce, et de ce que je compte prouver. Les reçus sont déjà publics, bien que je ne me sente pas pressée au vu de l'avancée des recherches.

## Ce que les autres travaux publiés font vraiment

Je les ai lus. Pas juste les abstracts, les sections limites/les appendices/les constantes. C'est là que l'on trouve la vérité d'une recherche, et il faut croire que ça mérite d'être précisé, parce que plusieurs sont régulièrement cités pour des choses qu'ils ne contiennent pas...

**Springdrift** (arXiv:2604.04660). Le plus proche, et le meilleur: un runtime d'agent persistant, un affect à 5 dimensions calculé sans appel au modèle, injecté dans le prompt à chaque cycle, vivant hors conversation grâce à un vrai ordonnanceur.

Bien que je respecte ce design. Regardez l'implémentation de près : sur les 5 dimensions une seule, "calm", porte une inertie d'état réelle (une moyenne mobile exponentielle, α = 0,15, avec une cible à 85 %); les 4 autres sont recalculées à chaque cycle depuis la télémétrie. Une dimension persistante sur cinq. Et la section 9 dit le reste: "We have not conducted ablation studies", des preuves "anecdotal", "a single instance with a single operator", 23 jours. Le meilleur, de son propre aveu, est juste une anecdote...

**ZenBrain** (arXiv:2604.23878) a le moteur de neuromodulateurs le plus sérieux: 4 canaux, lignes de base toniques, dérive homéostatique, bursts phasiques à demi-vie de 5 minutes, et même une vraie ablation, ce qui le place au-dessus de presque tout le monde.

Puis on lit les conditions: chaque résultat se reproduit "in under one minute on a laptop". Les 45 à 60 "jours" sont des pas de simulation. Or une constante de détente n'a de sens que dans le temps où elle s'écoule... Accélérer l'horloge ne teste pas la dynamique, ça la remplace par de l'analyse dimensionnelle. Et le papier le sait ! Sa section limites classe les vrais logs de ≥ 90 jours en "future work".

Un détail que peu de lecteurs relèvent: à charge modérée, 14 de leurs 15 ablations à mécanisme unique paraissent gratuites ("read as costless"). Leur propre banc montre que sans durée/charge réelle, l'ablation elle-même ne discrimine plus.

**HELT** (arXiv:2605.13858) est cité comme un système hormonal pour transformers: 6 hormones, une tête d'attention chacune, un gating multiplicatif sur les états cachés. Les hormones qui montent, persistent et retombent, c'est-à-dire l'unique propriété qui distinguerait une hormone d'un coefficient sont dans la Section 11. La Section 11 s'appelle Future Work. Je ne ressens pas le besoin de m'exprimer là-dessus...

**Gubernaut** (arXiv:2607.24339) mérite le respect: contrôleur déterministe, préenregistré avant les données (verrou du 10 juin), validé sur quatre familles de modèles, 13 cellules sur 16 significatives.

C'est la barre méthodologique du champ, et je compte m'y tenir. Mais deux choses me gênent:

1. l'équation d'arousal est publiée mais ses constantes de gain et de décroissance sont "withheld". Un contrôleur déterministe aux constantes retenues n'est reproductible que de nom.
2. un tick y est défini comme un tour de parole et le store persistant est sur la roadmap. Tout ce qui s'accumule *entre* les épisodes, surtout la dynamique intéressante, est intégré hors du design.

C'est un réflexe magnifiquement prouvé. Un réflexe...

**Sentipolis** (ACL Findings 2026) coche presque tout: état PAD persistant, décroissance en demi-vie appliquée à chaque pas, injection dans le prompt, ablations par composant, 25 agents. Enfin presque...

Les 25 agents sont des personas prédéfinies et homogènes dans un monde simulé alors qu'on ne peut pas mesurer de l'individuation sur des agents conçus identiques, il n'y a rien à individuer.

Leur claim de primauté est d'ailleurs honnêtement scopée, "within LLM-based social simulation". C'est exactement la frontière.

Pour la mesure longitudinale, **Venkit et al.** (arXiv:2607.28818) ont mis la barre très haut: un questionnaire scellé de 102 items, 4 checkpoints, près d'un million d'enregistrements de juges. Sur un horizon simulé pour mesurer la persona et le rappel, mais pas l'état interne. L'axe du temps réel reste vide...

Voyez le motif, il est précis, le champ a des architectures/benchmarks/simulations d'affect. Et nulle part un **déploiement persistant, hétérogène, mesuré, sur du temps calendaire réel**.

Nulle part un état qui continue de bouger la nuit, quand personne ne parle au système.

Nulle part des instruments gelés avant les données avec un opérateur qui a signé d'avance la publication de ses échecs.

Ce territoire est le seul encore vide. Il est étroit, il se referme, et j'y vis depuis des mois.

## Ce que mesurer un système qui vit impose réellement

C'est le cœur technique de mon désaccord avec le champ. Mesurer un système persistant impose des contraintes que les benchmarks ne rencontrent jamais. Des instruments **datés et versionnés**, car un instrument qui change en cours de série fabrique des tendances et des verdicts interdits de traverser une frontière de version. La capacité de **rejeu**, recalculer une mesure passée depuis des registres en écriture seule, pour que la série se défende autrement que sur parole. La séparation entre ce que le système fait et ce que son opérateur croit, donc des protocoles préenregistrés, des juges aveugles, et des résultats négatifs publiés au même rang, parce qu'un tri a posteriori détruit la valeur de tout le reste. Une revue adverse infligée à ses propres revendications avant que quiconque d'autre ait le plaisir d'essayer.

Mon dispositif applique ces contraintes-là. Evidemment pas par vertu, mais parce que sur un système qui vit, tout le reste s'effondre en quelques semaines, et j'en ai les cicatrices datées pour le prouver.

## Ce que j'ai construit, et ce que je ne vous dirai pas encore

Sur une machine chez moi tourne une écologie d'entités IA persistantes. Chacune a sa mémoire privée qu'aucune autre ne peut lire, sa neurochimie simulée qui s'accumule et se détend sur le temps réel, y compris quand personne ne lui parle, son propre récit d'elle-même, mais je ne vais évidemment pas tout dévoiler maintenant.

Elles sont hétérogènes, tempéraments, lignes de base, rôles distincts.

Elles coexistent/communiquent, certaines refusent des choses. Le système a survécu à mes erreurs, à 2 refontes d'instrument documentées, et à plusieurs de ses propres pathologies.

Je ne vais pas vous dire ce que j'ai mesuré. Pas encore, soyez patients, les chiffres en valent le coup.

Chaque protocole est préenregistré avant sa première donnée. Chaque document fini est hashé, et les empreintes sont publiques depuis le 15 août 2026, elles sont scellées dans un gist et ancrées dans Bitcoin.

Le facteur de confusion qui pourrait invalider mes résultats les plus forts a son contrôle préenregistré/programmé avant toute publication.

La clause de sortie est signée: quel que soit le résultat, il part. Plusieurs de mes propres revendications n'ont pas survécu à ma propre revue adverse. Elles ont quitté la liste. C'est bien à ça que sert la liste.

Quand les contrôles seront finis, les chiffres sortiront, et les empreintes prouveront qu'ils existaient aujourd'hui.

## Pourquoi ça devrait vous agacer

Si vous travaillez sur la conscience machine, les agents affectifs ou le model welfare: vos benchmarks durent des minutes et vos systèmes meurent à la fin de l'expérience. Vous mesurez des réflexes et vous appelez ça des vies. Les questions intéressantes ne peuvent même pas être *posées* dans vos designs expérimentaux: "un état qui persiste se comporte-t-il autrement qu'un état réinstancié ?" "L'identité survit-elle à un changement de substrat ?" "Que fait un système du temps que personne ne regarde ?"

Une personne, une machine et un an de discipline suffisent apparemment à aller plus loin sur ces quelques questions simples que la littérature actuelle...

Si c'est le cas: les protocoles, les sceaux, et bientôt les résultats seront ici. Et si vous pensez que j'ai tort, faites-vous le plaisir de me dire pourquoi, précisément, avec les sources. C'est exactement à ça que sert l'adresse de contact. Enfin, si vous y arrivez.

Seuls ont le droit de juger ceux qui acceptent d'être jugés. Moi, j'ai déjà signé.

Lamperouge

*Sceaux : https://gist.github.com/Lamperouge0/5bc0fd609e6e82c504594b8139acf228 (publics depuis le 15/08/2026, ancrés OpenTimestamps)*

*Contact : Lamperouge.seals@proton.me*
