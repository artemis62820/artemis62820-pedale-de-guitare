## Conception aléatoire de pédalier de guitare

### Ce projet est archivé

Je suis allé aussi loin que je le souhaitais dans ce formulaire.

Les pédales analogiques n'ont jamais été très intéressantes d'un point de vue sonore,
mais elles étaient parfaites pour apprendre les bases. Cette dernière pédale de boost (pas
au format 1590LB, malgré son nom) avec une paire de condensateurs à longue queue
et quelques sources de courant, était à peu près tout ce qui m'intéressait
du côté analogique.

Au fil du temps, j'ai appris des choses sur les transistors (BJT, MOSFET et JFET),
sur les mélangeurs à diodes, les cellules de Gilbert, etc. Aucune des pédales ne produisait de sons agréables,
et je pense toujours que les pédales analogiques ne servent à rien, mais comme exercice d'apprentissage,
c'était génial.

J'ai ensuite mis plus de temps à m'intéresser à la pédale numérique car il y avait
tellement de choix et la première étape était plus importante - mais je n'ai jamais été
intéressé par le simple fait de connecter les pédaliers d'autres personnes.

Il faut bien l'avouer, c'est la chose sensée à faire : se procurer un Raspberry Pi, choisir parmi les nombreux modules audio disponibles, et laisser libre cours à sa créativité.

Mais une fois la ligne de départ franchie sur le tableau d'affichage numérique, je dois dire que j'ai vraiment beaucoup plus apprécié que je ne l'aurais cru.

## Les points positifs :

### RP2354A

Le RP2354A était un vrai plaisir à utiliser avec le moteur PIO et, de manière générale,
grâce à son excellent SDK et à sa conception de carte minimale bien documentée.
La programmation via USB était simple, et bien que j'aie configuré un TagConnect pour
l'option de débogage SWD « au cas où », je ne l'ai finalement pas utilisée. Je
le conserverais probablement pour une future carte, mais ce n'est qu'une supposition.

L'exemple de carte minimale était bien fait, et la documentation est bonne. En résumé,
une très bonne expérience. Le fait que la carte ait fonctionné du premier coup
et que je n'aie rencontré aucun problème majeur malgré mon manque d'expertise en électronique,
était vraiment très positif.

J'étais un peu nerveux à l'idée de faire du I2S manuellement, mais c'était très simple et
cela a fonctionné étonnamment bien du premier coup, même si je n'avais jamais
fait de I2S auparavant et que je me contentais de lire les fiches techniques de TI pour
le codec. Ce qui m'amène à…

### TAC5112

Toute la gamme TC5xxx de TI semble être une très belle collection. J'avais choisi le TAC5112 non pas parce que c'était le choix le plus judicieux, mais parce qu'il était disponible chez JLCPCB. Je n'ai même pas branché les entrées et sorties stéréo ; le TAC5111 aurait donc été plus adapté à ce projet, mais cela n'avait pas vraiment d'importance.

Je n'ai guère exploité tout le potentiel du TAC5112, mais l'installation est simple, les filtres biquad matériels étaient assez simples à monter, et je n'ai rien à redire.

Oui, je pensais faire une boucle de retour analogique, mais même sans
toucher aux paramètres de faible latence, le simple fait de renvoyer l'entrée ADC
au DAC avec la configuration i2s 52 kHz que j'ai utilisée présentait des latences de l'ordre de 700 µs.

En fait, la façon dont j'ai réalisé tous les effets d'exemple leur conférait la même
très faible latence, mais c'était parce que je n'ai jamais dépassé le modèle « un échantillon audio à la fois, avec une ligne à retard ».

## Le mauvais :

L'audio analogique est tout simplement surestimé. À part pour apprendre à connaître les composants, il n'y a aucune raison de s'y intéresser. Y compris les alimentations linéaires.

Et si je classe ça dans la catégorie « mauvais », c'est parce que j'ai fini par être très
agacé par les potentiomètres analogiques et le commutateur au pied sur la carte finale.
Ils provenaient de cette époque analogique et semblaient logiques comme solution de transition,
mais ils sont aussi mauvais. Quatre potentiomètres prennent beaucoup de
place et restaient trop limitants.

Donc, si je reviens un jour à ce projet, je n'utiliserai pas de potentiomètres et j'utiliserai
les broches ADC du microcontrôleur. Ce n'est pas par hasard que les pédales d'effet modernes utilisent un encodeur rotatif et un afficheur.

En fait, la seule raison qui pourrait me pousser à relancer ce projet serait de
remplacer les quatre potentiomètres par un ou deux encodeurs rotatifs et quelques
interrupteurs. Et _tout_ cela serait basé sur des capteurs à effet Hall ou
un dispositif similaire. Plus aucun composant analogique, à l'exception des entrées et sorties audio analogiques.

Je ne me rendais pas compte à quel point ces choses seraient agaçantes une fois qu'on aurait un microcontrôleur. Je le saurai la prochaine fois.

## Le laid

Ce circuit imprimé à six couches était vraiment une erreur. Je l'ai fait uniquement parce qu'il y avait un coupon JLCPCB pour les circuits imprimés à six couches. Comme je voulais des vias intégrés et une finition ENIG, je pense que ça m'a finalement coûté quelques euros.
Tout faire sur six couches m'a même fait économiser un peu d'argent. Une des couches de mon circuit imprimé était littéralement vide : je n'y ai même pas fait de plan de masse, car j'en avais déjà deux.

Ce circuit imprimé est vraiment absurde. Je ne ferais jamais une carte à deux couches comme
l'exemple minimal pour Raspberry Pi, car ça ne vaut tout simplement pas la peine,
mais cette carte à six couches était tout simplement stupide. Tout a fonctionné — du premier coup —
mais quand même… Mieux vaut ne pas la regarder.

### Arrière-plan

Il s'agit d'un projet de jouet personnel qui a connu plusieurs phases, mais
le thème commun a toujours été qu'il n'a absolument aucun sens en dehors de
la niche très spécifique de « Linus essaie d'apprendre des choses aléatoires sur
l'électronique ».

So keep that in mind: there is very little point to any of this to
anybody else.  Don't expect some great useful guitar pedal experience.

Je l'appelle mon passe-temps « LEGO pour adultes », car tout a commencé lorsque j'ai voulu prolonger mon activité traditionnelle d'après Noël (qui consistait à recevoir et à construire de _vrais_ kits LEGO, ce que je fais depuis ma plus tendre enfance) avec autre chose.

Pour Noël 2024, je me suis offert un nouveau fer à souder et j'ai commencé, un peu par hasard,
à fabriquer des kits de pédales d'effet pour guitare. Au cours des deux mois suivants, j'en ai assemblé
au moins deux douzaines, et j'ai dû littéralement chercher des personnes à qui les donner
car je n'en avais aucune utilité moi-même.

> [!NOTE]
> De tous les kits que j'ai montés, ceux que j'ai le plus appréciés étaient les Aion FX
> et si vous recherchez un kit de pédales d'effet analogiques traditionnelles,
> je les recommande sans hésiter.
>
>La documentation, le service client, les composants et les boîtiers étaient tous d'excellente qualité.
Voir ["Aion FX"](https://aionfx.com/)

Bref, après avoir construit un bon nombre de ces kits de pédales d'effet analogiques traditionnelles pour guitare,
j'ai décidé que je voulais vraiment comprendre comment elles fonctionnaient,
car je n'avais que très peu d'expérience avec les circuits analogiques.


Bien que j'aie fait un peu d'électronique pendant la majeure partie de ma vie,
presque tout a été lié aux ordinateurs, donc il s'agissait soit de logique numérique,
soit d'alimentations électriques.

De plus, je recherchais une expérience de soudure différente,
où l'on couperait moins les pattes des composants traversants. J'aime bien souder des composants CMS, mais ce n'est généralement pas ce que font les kits de pédales de guitare.

J'avais fait un peu de conception de circuits imprimés avec KiCad il y a quelques années, alors j'ai décidé de me pencher davantage sur les circuits analogiques. Et puis, c'est devenu une passion.

### Conception électrique

Il s'agit de la « quatrième génération » de mon parcours de conception de pédales de guitare, et
c'est un nouveau dépôt car l'objectif de l'expérience d'apprentissage a
évolué.

Ce qui avait commencé par concerner les circuits analogiques (et les alimentations :
c’était toujours un point crucial) m’a amené à réaliser que
je voulais vraiment concevoir un système à signaux mixtes : comprendre le fonctionnement des circuits
est une chose, recréer un design analogique des années 70 quand on
ne se soucie pas vraiment du son, c’est une autre paire de manches.

Par ailleurs, concernant le traitement du signal analogique, j'ai commencé par utiliser des amplificateurs opérationnels, mais
en cherchant à comprendre leur fonctionnement, je suis passé
à un modèle utilisant uniquement des composants discrets, et je poursuis cette tendance
(à l'exception de toute la partie numérique, bien sûr).

> [!NOTE]
> Pour moi, les « composants discrets » incluent bien des packages plus optimisés :
> Des composants comme des diodes doubles ou des transistors appariés, mais pas plus complexes.
> des circuits comme un amplificateur opérationnel (ou une minuterie 555 ou une bascule D ou d'autres circuits classiques)
> Circuit intégré logique)

De plus, comme je n'écoute généralement pas le résultat final, mais que je l'observe
avec un générateur de signaux et un oscilloscope, j'ai fini par détester
le bruit de l'alimentation électrique.

Ne sachant pas ce que je faisais, bon nombre de mes circuits étaient très
bruyants, et ont intégré du bruit de l'alimentation électrique dans la
chaîne de signal, et cela se voit clairement sur un oscilloscope même si
ce n'est pas toujours audible.

Même dans les conceptions d'amplificateurs opérationnels, où l'amplificateur opérationnel lui-même possède un PSRR très élevé et
ne mélange pas le bruit de l'alimentation électrique au signal, mes circuits de polarisation
n'étaient souvent pas optimaux, et l'amplificateur opérationnel voyait donc non seulement le signal
mais aussi le bruit de l'alimentation électrique entrant par la polarisation CC.

Et chaque fois que j'essayais une double alimentation (pour pouvoir simplement garder le
signal référencé à la masse), le bruit de la commutation finissait par être
toujours perceptible, et la complexité supplémentaire était ennuyeuse car de nombreux
effets n'avaient alors aucune réelle utilité pour la double alimentation.

Le filtrage est évidemment utile, mais ceci n'est qu'une explication un peu longue
pour expliquer pourquoi j'ai fini par vraiment apprécier le modèle JFET « polarisé à la masse »
pour le côté entrée du signal, et le suiveur de drain commun en particulier.

Cela fonctionne avec un seul JFET (le MMBF5103 a bien fonctionné pour moi), mais
ma conception préférée jusqu'à présent est un LS844 à deux JFET, le second JFET apparié étant utilisé comme puits de courant. Il possède une impédance d'entrée pratiquement infinie (et
peut être couplé en courant continu, bien que j'utilise un condensateur de couplage avec une résistance
à la masse) et fournit un bon signal de sortie à peu près au milieu de la tension d'alimentation unique de 9 V.

Voir [LS844 Application note](https://www.linearsystems.com/_files/ugd/7e8069_52b1022fbded45fab609459acb337629.pdf)

Pourquoi mentionner ceci en particulier ? Principalement parce que c'est un excellent exemple
de l'absurdité de mes conceptions. Ce LS844 est utilisé comme
suiveur de tension avec un décalage CC notable, et ce simple composant double JFET
SOT-23-6 est plus cher — et plus difficile à trouver — qu'un
simple amplificateur opérationnel.

Pour vous donner une idée : vous pouvez acheter des LM358 chez Mouser pour
environ 0,07 $ pièce en quantités raisonnables (une centaine, par exemple). Certes,
ce n'est pas le meilleur amplificateur opérationnel du marché et il vous faudrait un régulateur 5 V, alors
il serait peut-être plus judicieux, même en payant le double, d'opter pour un TL082 ou un TL072.
Ou encore, choisissez un modèle à entrée BJT, ce qui sera encore moins cher.

Le LS844 ? Plus difficile à trouver et *beaucoup* plus cher. S'il est en stock, vous le trouverez à 2,50 $ à partir de dix unités. Je l'utilise comme solution de fortune pour remplacer une entrée d'un de ces amplificateurs opérationnels bon marché.

En d'autres termes : pour des créations sensées, cherchez ailleurs. Ce n'est pas le bon endroit.

Mais cela fonctionne plutôt bien. Voir quelques notes sur les tests du chemin du signal :
[ici](Documentation/Passthrough/Notes.md)


### Conception physique

J'ai commencé par de petits modèles que j'ai choisis pour intégrer parfaitement dans un boîtier 1590A (le plus petit format standard pour pédales de guitare), car je le trouvais mignon. Les contraintes physiques liées à l'agencement étaient en fait intéressantes, et comme j'utilisais des composants CMS et des circuits simples, la taille des circuits n'a jamais posé de problème.

Cependant, ayant décidé d'abandonner les effets audio analogiques ringards des années 60 et 70, le boîtier du 1590A est devenu un véritable calvaire. Y installer une pédale Electrosmith Daisy Seed est possible, mais seulement si l'on se passe d'un véritable commutateur au pied et que l'on se limite à deux potentiomètres. Et oui, c'est ce que j'ai fait.

Est-ce que je souhaite utiliser le Daisy Seed pré-compilé ? Peut-être, peut-être pas.
Ce dépôt contient les prémices d'un projet de « et si je créais ma propre version d'un microcontrôleur et d'un codec ? », car c'est aussi une expérience d'apprentissage intéressante.
J'ai commencé ce projet car cela me permettrait d'optimiser l'intégration des composants dans un 1590A.

Mais ensuite, mes médicaments ont fait effet, et j'ai finalement abandonné le 1590A.
Il est mignon. Les défis mécaniques étaient intéressants. Mais ils sont passés de « intéressants » à « trop contraignants ».

Du coup, j'opte pour un boîtier beaucoup plus raisonnable. Ce sera donc un 1590B.
Ça simplifie grandement les choses et le résultat final est bien plus
harmonieux.

### Composants

J'ai fait fabriquer des circuits imprimés chez JLCPCB, PCBWAY et OSH Park.
Le résultat final est toujours bon ; choisissez celui avec lequel vous vous sentez le plus à l'aise.
J'ai constaté que, du moins pour moi, JLCPCB offre les délais de livraison les plus rapides,
mais je pense que cela dépend beaucoup de votre lieu de résidence.

Par le passé, j'ai également réalisé des assemblages de circuits imprimés, et PCBWAY a fait du bon travail. Pour ce projet, où la soudure manuelle fait partie intégrante de l'expérience, je n'ai pour l'instant réalisé que des cartes nues.

J'ai envisagé de faire du montage au cas où je
déciderais de travailler sur des composants plus complexes, mais c'est vraiment pour plus tard,
et si je m'occupais aussi du numérique ? Je n'en suis pas encore là.

Les connecteurs et les potentiomètres proviennent généralement de Tayda Electronics,
et la plupart des composants CMS courants sont issus de kits ou de Mouser.

Quelques composants typiques de Tayda :

- [Prise jack audio mono A-6976](https://www.taydaelectronics.com/6-35-mm-1-4-righ-angle-mono-female-connector-thread-lock-panel-mount.html)

- [Prise jack CC cylindrique 2,1 mm A-4118](https://www.taydaelectronics.com/dc-power-jack-2-1mm-barrel-type-pcb-mount.html)

- [Potentiomètre linéaire 10 kΩ 9 mm A-1847](https://www.taydaelectronics.com/10k-ohm-linear-taper-potentiometer-round-shaft-pcb-9mm.html)

- [Interrupteur au pied compact DPDT [A-1884](https://www.taydaelectronics.com/dpdt-compact-stomp-foot-pedal-switch-momentary-pcb.html)

- [Connecteur IDC coudé A-2943](https://www.taydaelectronics.com/10-pin-box-header-connector-2-54mm-right-angle.html)

Pour les condensateurs et résistances CMS divers, procurez-vous un kit.
Je recommande vivement les kits Guanruixin disponibles sur Amazon :
ils proposent des kits 0805 et 1206 pour les condensateurs et les résistances, et j'apprécie particulièrement
l'emballage et l'étiquetage. Idéal pour s'organiser, même pour un amateur.

L'étui de rangement à lui seul justifie leur achat :

 - [Guanruixin 0805 Capacitor Kit](https://www.amazon.com/Guanruixin-Capacitor-1pF-47uF-Capacitance-Compliant/dp/B0B3JV5PMT)
 - [Guanruixin 0805 Resistor Kit](https://www.amazon.com/Guanruixin-Resistor-Assortment-Tolerance-Compliant/dp/B0B3JVDMZ1)
 - .. any other sizes you want

Il existe d'autres kits, mais c'est pratique d'avoir un bon coffret compact
avec une sélection de résistances de différentes valeurs. Si vous êtes comme moi, vous finirez par manquer de résistances courantes, et dans ce cas, j'achète du ruban prédécoupé chez Mouser
et je remplis simplement les compartiments correspondants dans le coffret.

Ce qui nous amène à Mouser, DigiKey et autres : non seulement pour les recharges,
mais aussi pour tout ce qui est un peu plus spécialisé. Comme le LS844,
mais en fait la plupart des composants CMS qui ne sont pas entièrement standard.

Mes choix précis de composants CMS ont été assez aléatoires, et nombre d'entre eux
ont été influencés par l'encombrement plutôt que par leurs mérites techniques.
J'ai une préférence pour les boîtiers SOT-23-6 à deux transistors, et si vous
regardez mes choix de MOSFET, vous constaterez que le critère principal
était le boîtier et une tension V<sub>GSS</sub> suffisamment élevée.

En d'autres termes : je ne prétends pas que mes choix de composants soient forcément
logiques. Ils ont fonctionné pour moi, souvent parce que « l'autre composant
était tout simplement trop délicat à souder, alors je l'ai remplacé par celui-ci
qui me convient ».

> [!NOTE]
> Si vous savez réellement ce que vous faites, et que vous avez examiné le
> schématisé et dit : « Linus est clairement dépassé, et c'est tout. »
> Tout simplement stupide », que ce soit en ce qui concerne le choix des pièces ou simplement…
> circuit en général, merci de me le faire savoir.
> En particulier, n'ayez pas l'impression que ce serait impoli de me dire que je suis
> incompétent et faisant des bêtises. Je sais pertinemment que je ne le suis pas.
> Compétent et ouvert à toute critique. Parmi les meilleurs
> Les moments d'apprentissage ont été ceux où je n'ai pas compris quelque chose, et
> Quelqu'un a pris la parole pour me dire que je devrais faire Xyz.
>
> Je vais laisser le lien vers le
> ["Tremolo doubling as a metronome"](https://github.com/torvalds/1590A/issues/4)
> problème lié au projet de pédale 1590A, car il s'agissait d'un cas de
> Quelqu'un (@gralco) est venu me dire très poliment que je faisais
> Des choses stupides.
>
> Le fait de m'avoir poussé à faire des simulations dans KiCad a complètement changé la donne.
> Alors n'hésitez pas à me dire que mes circuits sont nuls. Parce que c'est littéralement…
> Pourquoi je fais ça !