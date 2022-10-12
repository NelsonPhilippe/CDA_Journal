#  Vélocité dans la méthode SCRUM 
*Qu’est-ce que la vélocité ?*

La vélocité est un indicateur utilisé sur des projets gérés à l’aide d’une méthode agile, comme Scrum par exemple. La vélocité agile permet de déterminer l’effort qu’est capable de fournir une équipe de développement pour la réalisation des tâches programmées dans un sprint. Elle est exprimée en nombre de points.

Le product owner place dans le product backlog un certain nombre de fonctionnalités à réaliser, ou items généralement formalisées sous la forme de user stories[^User Stories : En Agile, un projet est décomposé en unités plus petites. La plus petite unité de travail est connue sous le nom de "user story" et constitue un objectif final. Il s'agit d'une description écrite de la fonctionnalité du point de vue de l'utilisateur final]. L’équipe de développement attribue à chaque product backlog item (ou PBI) un certain nombre de points. Ces points représentent à la fois la complexité et la durée de la réalisation du PBI estimées de façon empirique. Il ne s’agit pas d’une échelle linéaire. La suite de Fibonacci est souvent utilisée.

Aussi, les valeurs pouvant être attribuées sont:

- 1 pour une tâche extrêmement simple, comme la correction d’un libellé par exemple,
- 2, 3, 5 pour une tâche légèrement plus complexe, comme la création d’un formulaire de saisie simple,
- 8, 13, 21, 34, 55, 89, 144 si l’on ne dispose pas de suffisamment d’informations pour estimer correctement cette tâche.
![](https://d6vdma9166ldh.cloudfront.net/media/images/1629964462787-What-Is-Velocity-In-Agile-1.png)
*Qui se charge de l’estimation des PBIs ?*
-
Le Product Owner a pour mission de donner à chaque product backlog les fonctionnalités ou items à réaliser durant le sprint. Lors de la session de planification, l’équipe doit prendre en compte sa capacité qui permettra de déterminer la vélocité moyenne.

Seule l’équipe de développement est en mesure de se charger de l’estimation des PBI. Elle se chargera de distribuer les points, estimés de manière empirique, à chaque PBI. Une fois définie, la vélocité servira à valider ou à réviser la planification du développement.

Notons que la vélocité durant les prochaines itérations sera plus ou moins égale à la précédente vélocité. À titre d’exemple, si les stories A et B (estimée chacune à 2 points) sont finies à 100 % et que la sortie C (3points) n’est achevée qu’à 80 %, la vélocité de l’itération sera de 4 points.
![](https://d6vdma9166ldh.cloudfront.net/media/images/1629964540476-What-Is-Velocity-In-Agile-2.png)

La vélocité peut également être calculée en considérant les story points. Les story points constituent les storys d'utilisateur et sont une unité de mesure qui représente la quantité d'effort nécessaire pour accomplir une tâche. En général, chaque organisation a sa propre méthode pour attribuer des valeurs aux story points.
La vélocité d'un sprint particulier est calculée en multipliant le nombre de story d'utilisateur achevées dans le sprint par le story point attribué à chaque histoire d'utilisateur. Par exemple : Si vous avez complété 4 user stories et que vous avez attribué 3 story points à chaque story, la vélocité totale du sprint sera de 4*3=12.
On peut faire la moyenne des vitesses de sprint individuelles pour obtenir la vitesse de sprint moyenne.

# *Comment utiliser la vélocité moyenne dans le développement agile ?*

Agile est synonyme de développement itératif, de solutions rapides et de mise sur le marché rapide des produits. Pour ce faire, les équipes Agile doivent savoir quelle quantité de travail elles peuvent effectuer dans un sprint et combien de temps il leur faudra pour terminer le projet ou le livrer au client. Velocity les aide à prendre cette décision et à travailler efficacement.

La vélocité moyenne est calculée une fois que le projet a progressé à travers trois ou quatre sprints. La vélocité moyenne est calculée en faisant la moyenne des story points accumulés dans chaque sprint. Sur la base de cette vélocité moyenne calculée, les équipes peuvent se baser sur la quantité de travail qui reste à faire.
Si nous considérons l'exemple ci-dessus de la vitesse moyenne d'un sprint, nous pouvons supposer que l'équipe peut accomplir le travail à raison de 12 story points par sprint. Donc, s'il vous reste 120 story points à compléter dans votre projet, vous pouvez supposer que vous aurez besoin de 10 sprints supplémentaires pour terminer le projet.
Bien qu'elle soit précise, elle est sujette à des fluctuations en fonction de l'évolution des besoins, de la taille de l'équipe et de la complexité du projet.

# Tableau de vélocité agile
La méthode Agile présente plusieurs outils pour représenter visuellement les points de données. Ceux-ci constituent un indicateur facile de l'avancement du projet et, s'ils sont basés sur le cloud, ils peuvent être consultés par toutes les personnes impliquées dans le projet.
Les diagrammes de vélocité Agile sont essentiellement des graphiques, avec les story points affichés sur l'axe Y ou vertical et les sprints terminés affichés sur l'axe X ou vertical.axe horizontal. Ils constituent un excellent moyen de rendre la vélocité de votre projet accessible à tous. Les graphiques basés sur le cloud peuvent être consultés par les équipes ainsi que par les parties prenantes.
![](https://business.adobe.com/blog/basics/media_147434281d4e66df53273bdc3bca726ff88839022.png?width=1200&format=pjpg&optimize=medium)
Un diagramme de vélocité est un excellent moyen de suivre l'état d'avancement du projet, de voir si le projet progresse de manière régulière et prévisible et d'identifier des modèles dans la vélocité du sprint de l'équipe. S'il y a beaucoup de creux et d'élévations irréguliers dans vos graphiques, alors vous pouvez supposer que votre projet est imprévisible car la vélocité n'est pas constante.


# Quel sont les avantages de la mesure de la vélocité ?
- Essentiel pour la planification des versions : La vélocité est indispensable à la planification des versions, car elle aide le product owner à déterminer combien de sprints seront nécessaires pour créer un produit ayant les fonctionnalités souhaitées. En obtenant une estimation du nombre de sprints nécessaires, le product owner peut estimez la date de sortie.
- Feedback pour l'équipe : La vélocité est un excellent outil pour mesurer les progrès de l'équipe. En suivant la vélocité dans le temps, les équipes peuvent mesurer si les changements qu'elles font pendant le sprint améliorent ou diminuent leur productivité. Alors que la vélocité peut fluctuer dans les nouvelles équipes, les équipes expérimentées ont une vélocité constante et peuvent mesurer leurs progrès grâce aux graphiques de vélocité.
- Prévision : La vélocité aide l'équipe à identifier le nombre de récits d'utilisateurs qu'elle peut réaliser dans un sprint. La prévision est un outil important qui aide les équipes à décider des délais et des budgets pour le projet.
La prévision se fait généralement en prenant la moyenne de la vélocité des trois derniers sprints.
#  Quels sont les inconvénients ?

>Mesurer les progrès sur la base de la vélocité :
Si la vélocité est un excellent outil pour mesurer la progression de l'équipe, il ne faut pas oublier qu'il s'agit d'une mesure empirique, ce qui signifie qu'elle peut être utilisée pour l'estimation, mais pas comme norme finale pour mesurer la progression de l'équipe. La vélocité est souvent basée sur les story points, qui sont subjectifs pour l'équipe. Les équipes peuvent avoir leurs propres valeurs de points de story pour les storys d'utilisateur et donc définir leur propre vélocité et portée du travail. La vélocité est donc une variable changeante qui ne doit pas être utilisée comme critère de mesure de la progression de l'équipe.

- Problèmes de démarrage :
La vélocité est mieux estimée par les équipes Scrum matures et bien rodées. Les équipes nouvelles ou en transition et les équipes qui se lancent dans de nouveaux projets auront besoin d'un certain temps pour devenir une machine bien huilée et obtenir une vélocité précise.

- Des tâches importantes :
Scrum/Agile fonctionne sur le principe de la décomposition de grands projets en petits morceaux et d'un produit livrable à la fin de chaque morceau. Un projet Scrum est généralement décomposé en épopées, sprints, user stories et tâches. Si les épopées ne sont pas suffisamment décomposées, cela aura un impact direct sur la vélocité, et les équipes peuvent voir une forte baisse de vélocité d'un sprint à l'autre. Cela rend la vélocité moins prévisible.

- Le temps d'inactivité n'est pas comptabilisé :
Un sprint ne se limite pas à la livraison ou à la production. Il y a beaucoup de choses qui se passent entre les deux, comme l'échange de courriels, les réunions de stand up, etc. Si ces éléments ne sont pas pris en compte dans la durée du sprint, la vélocité risque de faiblir.

# Conclusion 

La vélocité est une mesure importante utilisée par les Scrum Masters et les Product Owners pour suivre les progrès de leur équipe et assurer la réussite du projet. La réponse rapide, la livraison rapide, le cadre incrémentiel et itératif d'Agile garantissent des versions rapides, des produits de qualité et la satisfaction du client.
La vélocité aide à déterminer les délais du projet et permet aux propriétaires de produits de donner des estimations précises sans tomber dans le piège du sur engagement.


# Le Planning Poker
## C’est quoi le Planning Poker ?
   <u>    __**La méthode Agile du planning poker consiste en une estimation de la difficulté des taches fondée sur le consensus.**__</u>

>## *Qu'est-ce que le poker de planification ?*

Le planning poker, également connu sous le nom de "scrum poker" et de "pointing poker", est une technique ludique que les équipes de développement utilisent pour deviner l'effort des tâches de gestion de projet. Ces estimations sont basées sur l'apport et le consensus de l'ensemble du groupe, ce qui les rend plus engageantes et plus précises que d'autres méthodes. Pour aider à évaluer le nombre de story points pour les tâches pertinentes, les équipes utilisent des cartes de poker de planification, qui sont similaires aux cartes de poker.

![](https://www.visual-paradigm.com/servlet/editor-content/scrum/what-is-agile-planning-poker/sites/7/2018/12/fibonacci-sequence-and-planning-poker.png)

>La suite de Fibonacci est utilisée pour les évaluations. Comme nous cherchons un dimensionnement de l'effort, le message est clair : plus le scénario est gros, moins l'évaluation est précise. Le paquet de cartes utilisé pour le planning poker doit donc comporter les valeurs suivantes : 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144. Certains simplifient les grandes valeurs en les transformant en 20, 40, 100... puisqu'il s'agit d'être globalement bon plutôt que précisément erroné. On y ajoute généralement les valeurs 0 et 1/2.

# Comment se déroule un Poker Planning .
![](https://scrum-master.org/wp-content/uploads/elementor/thumbs/image-p9heaj9d5azmmgya3b4bub2zth9ug2yxj4gxgi8f1s.jpeg)
Au début d'une session de planification du poker, le product owner ou le client examine une user story agile et la lit à haute voix. Une user story est une explication générale et informelle d'une fonctionnalité logicielle qui décrit comment elle offrira de la valeur à l'utilisateur final (c'est-à-dire le client).
1. Distribuez les cartes aux participants
Distribuez à chacun un jeu de cartes identique. Chacun porte un numéro que l'équipe a convenu d'utiliser comme estimation. Chaque joueur doit disposer d'un jeu composé de nombres différents. Cohn recommande une séquence de 0, 1, 2, 3, 5, 8, 13, 20, 40 et 100.
D'autres séquences courantes comprennent le doublement du nombre suivant (par exemple, 1, 2, 4, 8, etc.). Ces valeurs peuvent représenter un certain nombre de choses : le nombre de story points, de jours idéaux, ou d'autres unités que l'équipe utilise pour l'estimation.
Les jeux de cartes sont intentionnellement maintenus à un niveau minimal avec des sauts de chiffres considérables. Cela permet de s'assurer que pour chaque histoire, tout le monde peut atteindre un nombre consensuel. Sinon, s'il y avait une carte pour chaque chiffre de 1 à 50, le processus serait terriblement lent.
2. Lisez la story à voix haute
Le modérateur (soit le product owner, soit le responsable du produit) raconte la story au groupe. Si les participants ont des questions, le modérateur y répond.
3. Discutez de la story
Une fois que le groupe a fini d'écouter la story, chacun partage son point de vue sur celle-ci. Certains de ces points de discussion incluront probablement :

	**Comment devons-nous gérer le travail ?**

	**Combien de personnes sont censées s'impliquer ?**

	**Quelles compétences seront nécessaires pour
travailler sur la story ?**

	**Comment s'attaquer aux obstacles qui retardent les progrès ?**
<u>Le groupe essaiera également d'en savoir plus sur la story et de poser des questions pour mieux la comprendre.</u>
4. Sélectionner et partager
Après la discussion, chaque personne choisira en privé une carte du jeu. Habituellement, elle est utilisée pour montrer une estimation des points de la story (mais peut aussi être utilisée pour représenter le nombre de jours idéaux). Une fois que tout le monde a choisi une carte, ils les montrent en même temps.
Si un joueur montre une carte supérieure, cela signifie que la story sera terminée.
avec plus de difficultés et prennent plus de temps à réaliser. N'oubliez pas qu'il est courant que les estimations varient considérablement.
5. Obtenir un consensus
Lorsque les membres de l'équipe montrent la même carte, ce nombre se transforme en un consensus. Maintenant, le groupe peut aller de l'avant et travailler sur la prochaine histoire.
Toutefois, si les cartes continuent à varier, d'autres discussions sur la story suivront. Les participants dont les estimations sont supérieures ou inférieures à celles des autres communiqueront leur point de vue. Puis, ils tenteront de convaincre leurs coéquipiers de comprendre leurs chiffres divergents.
Une fois cette nouvelle délibération terminée, tout le monde passera en revue son jeu et le montrera à nouveau. Si un participant est toujours d'accord avec son dernier choix, il répétera la carte ou en choisira éventuellement une nouvelle.
En général, les estimations commencent à converger après le deuxième tour. Si ce n'est pas le cas, le processus se répète jusqu'à ce que l'équipe se mette d'accord sur un chiffre unique.

# **Les avantages**
- Selon une étude, les estimations issues du planning poker sont statistiquement plus élevées que les estimations individuelles. Il a également été noté que pour les mêmes tâches, les estimations du poker de planification étaient plus précises que les estimations individuelles.
- Les autres avantages sont les suivants :
	- Estimer les tâches les unes par rapport aux autres. Il est souvent difficile d'évaluer le temps nécessaire à la réalisation d'un projet,surtout lorsqu'il s'agit de la première fois. Le poker de planification permet aux équipes de se familiariser avec leur évaluation. Après avoir joué le jeu pendant un certain temps, vous finissez par construire une série de tâches qui servent de référence future pour la comparaison.
	- Donner une voix égale à tous les membres de l'équipe. Il peut encourager les nouveaux employés à prendre la parole en jouant une carte et en expliquant leur logique. Par exemple, imaginez que vous faites une application de réservation de nourriture. Vous et votre collègue pourriez donner une estimation plus petite, comme 10 ou 15. En revanche, un nouvel employé pourrait donner une estimation de 100. Peut-être a-t-il eu l'expérience de la création d'une application similaire dans son dernier emploi et sait-il qu'une telle application prend beaucoup de temps, surtout par rapport aux autres.
	- Identifier les lacunes dans les exigences et la mise en œuvre. Lorsque les participants divulguent leurs estimations, ils doivent les étayer en expliquant pourquoi elles sont élevées ou faibles. Cela peut susciter des questions sur les exigences et la mise en œuvre - une boucle de rétroaction qui permet de détecter les lacunes.

# Qui inclure dans les réunions de planification du poker ?
![](https://3.bp.blogspot.com/-unMY49BQD8M/W6koCL_u9yI/AAAAAAAAYMM/DmDyp-hYyZgdaj_8LP-1z4Pck5ct9Uo5ACLcBGAs/s1600/shutterstock_496292356.jpg)
Les bonnes personnes doivent se joindre à la réunion, sinon il devient difficile de récolter les avantages décrits ci-dessus. Ces rôles cruciaux sont les suivants :
- Membres de l'équipe Scrum : les membres de l'équipe Scrum fournissent les éléments du backlog de produit - une liste de produits à livrer (par exemple, les nouvelles fonctionnalités). Ils apportent également leur contribution aux discussions sur les story points.
- Scrum master : un scrum leader est l'animateur des réunions agiles. Il doit participer à toutes les réunions standard.
- Product Owner : le PO ou le gestionnaire décrira toutes les storys des utilisateurs à l'équipe et répondra à leurs questions.
## Quand organiser une session de poker de planification ?
En général, les équipes organisent une session après avoir créé le backlog initial. Bien que les sessions puissent parfois prendre plus d'une journée, elles permettent d'élaborer des estimations initiales utiles pour le dimensionnement ou la délimitation du projet.
Les éléments sont ajoutés au backlog du produit de manière incrémentielle tout au long de la durée de vie du projet. C'est pourquoi il est généralement plus pratique pour les équipes de mener des sessions une fois par itération. Dans la plupart des cas, cela se produit à quelques jours après la fin de l'itération. De même, il se produit aussi juste après un standup quotidien (un type de réunion agile) parce que toute l'équipe est présente.
