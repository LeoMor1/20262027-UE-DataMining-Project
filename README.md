# Data Mining Project — 2026/2027

## Équipe du projet

- **Membre 1 :** Doaa SAMADI
- **Membre 2 :** Nina ALLAM
- **Membre 3 :** Imene IKHLEF
- **Membre 4 :** Yassine HACHGUER
- **Membre 5 :** Jérémie COULIBALY
- **Membre 6 :** Léo MORIN


---

## 1. Présentation du projet

Ce projet de Data Mining consiste à explorer plusieurs ensembles de données qui, pris séparément, semblent décrire des activités sans lien direct : le suivi de la faune, les autorisations administratives, les mouvements logistiques et les dossiers médicaux.

Notre objectif est de dépasser cette lecture séparée. En analysant chaque domaine, puis en rapprochant les indices qui peuvent être reliés, nous cherchons à comprendre ce qui se cache derrière ces activités et à reconstruire un **secret global cohérent avec les données**.

L'enquête s'organise autour de quatre domaines :

- **Ecology** : évolution des populations de chauves-souris, conditions environnementales, équipements de surveillance et rapports de terrain.
- **Public Records** : demandes d'accès aux sites, organisations, dirigeants, procédures administratives et documents historiques ou d'investigation.
- **Logistics** : expéditions, transporteurs, entrepôts, réceptions, inventaires et approvisionnements des établissements médicaux.
- **Health** : profils physiologiques, observations cliniques, signaux cardiaques et procédures médicales particulières.

Le fil conducteur qui se dessine progressivement est celui d'un possible **circuit biologique confidentiel**, reliant des activités de terrain, une chaîne logistique spécialisée et un programme clinique soumis à des autorisations restreintes. Le projet ne cherche pas à présenter cette interprétation comme une vérité définitivement établie : il distingue les observations issues des notebooks des hypothèses proposées pour expliquer leur convergence.

Les résultats soulèvent également une piste intéressante autour de la longévité biologique. Certaines recherches scientifiques étudient les mécanismes qui pourraient expliquer la longévité exceptionnelle de certaines espèces, notamment les chauves-souris. On peut alors se demander si les échantillons biologiques identifiés dans notre enquête pourraient être liés à des recherches de ce type, éventuellement en rapport avec les procédures médicales observées par la suite

---

## 2. Organisation du projet

```text
20262027-UE-DataMining-Project/
│
├── data/
│   ├── ecology/
│   ├── health/
│   ├── logistics/
│   ├── public_records/
│   └── data_dictionary.csv
│
├── Ecology_part.ipynb
├── Health_part.ipynb
├── Partie_logistique_avec_visualisations.ipynb
├── Public_Records_part.ipynb
├── Base_notebook_to_complete.ipynb
├── requirements.txt
└── README.md
```

Chaque notebook correspond à une partie de l'enquête. Les fichiers sources sont conservés dans le dossier `data/` et organisés par domaine.

| Notebook | Domaine | Rôle dans l'enquête |
|---|---|---|
| `Ecology_part.ipynb` | Ecology | Repérer les diminutions inhabituelles de chauves-souris et examiner les rapports associés. |
| `Public_Records_part.ipynb` | Public Records | Comprendre qui accède aux sites, quelles organisations interviennent et ce que révèlent les archives. |
| `Partie_logistique_avec_visualisations.ipynb` | Logistics | Reconstituer les circuits d'expédition et rapprocher les livraisons des événements de terrain et des procédures médicales. |
| `Health_part.ipynb` | Health | Identifier des profils cliniques atypiques et étudier les patients concernés par MRP-42. |


---

## 3. Démarche suivie

Les quatre parties utilisent des méthodes adaptées à leurs données, mais suivent une même logique : explorer, repérer les éléments inhabituels, vérifier leur contexte, puis rechercher des correspondances avec les autres domaines.

Les analyses mobilisent notamment :

- des statistiques descriptives et des visualisations ;
- des méthodes de détection d'anomalies, dont le Z-score, l'IQR et Isolation Forest ;
- des méthodes de regroupement et de réduction de dimension, comme le clustering hiérarchique, K-means, PCA et DBSCAN ;
- des analyses de graphes et de relations entre entités ;
- le Process Mining pour étudier les parcours administratifs ;
- le Text Mining, notamment TF-IDF, similarité cosinus, NMF, entités nommées et cooccurrences ;
- des analyses temporelles et des tests statistiques pour évaluer certaines associations.

Les résultats ne sont pas interprétés isolément. Une anomalie devient une piste à examiner ; elle ne constitue pas, à elle seule, une preuve d'une activité particulière.

---

# 4. Résultats des quatre domaines

## 4.1. Ecology — Une baisse qui ne semble pas naturelle

La première partie étudie les populations de chauves-souris observées sur différents sites. L'enjeu est de repérer les diminutions inhabituelles, puis de vérifier si elles peuvent être expliquées par des conditions météorologiques défavorables, une perturbation de l'habitat ou un problème de matériel.

Après avoir testé plusieurs approches, l'analyse retient une méthode fondée sur le Z-score des variations mensuelles. Les périodes détectées sont ensuite comparées aux données environnementales et aux informations de fonctionnement des équipements. Cette étape permet d'écarter plusieurs anomalies qui peuvent s'expliquer par des facteurs techniques ou naturels.

L'analyse des rapports de terrain réduit ensuite l'investigation à quelques observations particulièrement intéressantes. Le rapport associé au site **KNT-KES** se distingue nettement des autres : il décrit une baisse du nombre de chauves-souris alors que les instruments et les conditions météorologiques ne présentent pas d'anomalie évidente. Il mentionne également des traces non identifiées, qui pourraient correspondre à une intrusion ou à une activité de braconnage.

**Ce que cette partie apporte au secret :** elle fait émerger une possible activité humaine sur un site où la baisse de la population animale ne semble pas avoir d'explication naturelle ou technique immédiate. KNT-KES devient ainsi un lieu important à rapprocher des demandes d'accès étudiées dans Public Records.

## 4.2. Public Records - Analyse des accès et des archives

La partie Public Records examine les demandes d'accès aux sites, les étapes de leur traitement, les organisations impliquées, les relations entre dirigeants et les documents institutionnels ou d'investigation.

Une organisation ressort progressivement : **Horizon Field Research Cooperative**. Ses demandes d'accès présentent plus fréquemment des examens de sécurité que celles des autres organisations. Certaines suivent également des parcours administratifs particuliers, avec un refus initial, une nouvelle soumission et une autorisation ultérieure.

L'étude temporelle permet de revenir sur le site KNT-KES. Trois interventions de Horizon y sont enregistrées en mars 2018, 2021 et 2024. Elles ont des caractéristiques très similaires : elles se déroulent de nuit, commencent à 18 h et se terminent à 3 h. L'une des demandes mentionne du matériel portable de surveillance et de stockage frigorifique. Ces éléments donnent un contexte administratif aux observations relevées dans Ecology, sans prouver ce qui s'est réellement déroulé sur le terrain.

Le Text Mining apporte une autre pièce importante. Parmi les documents étudiés, le document **PUB-510079**, intitulé *Message Concerning Collected Eonycteris*, contient un témoignage attribué à Mara Venn. Celui-ci évoque la collecte de chauves-souris *Eonycteris spelaea*, des unités biologiques scellées, des ajustements d'inventaire et des fiches de préparation faisant référence à une possible consommation. Le document constitue une piste majeure, mais reste un témoignage qui ne confirme pas à lui seul la réalité de toutes les opérations décrites.

Les archives font également apparaître des liens documentaires entre plusieurs noms historiques, notamment Jonah Bell, Julien Marot, Jacob Vale et Adrian Vosmere. Deux chaînes chronologiques de dirigeants sont étudiées. Les documents montrent des cooccurrences, des adresses et des références communes, mais ne démontrent pas que ces personnes seraient des identités successives d'un même individu.

Enfin, certains documents décrivent des stratégies environnementales opposées : d'un côté, des acteurs défendent la transparence et la réduction de l'extraction industrielle ; de l'autre, certains privilégient la continuité de programmes spécifiques et un contrôle plus strict de la divulgation des informations.

**Ce que cette partie apporte au secret :** elle relie le site KNT-KES à des accès répétés de Horizon, fait émerger un témoignage concernant la collecte d'*Eonycteris spelaea* et révèle un environnement administratif et documentaire marqué par la confidentialité. Les archives historiques enrichissent le contexte, mais les hypothèses d'identité restent ouvertes.

## 4.3. Logistics — Le circuit entre le terrain et les établissements médicaux

La partie Logistics suit les partenaires, les expéditions, les réceptions, les stocks et les mouvements de marchandises. Elle permet de passer des autorisations administratives à des mouvements matériels observables dans les données. L’analyse combine règles d’association (Apriori), détection d’anomalies (IQR, z-score modifié, Isolation Forest, LOF, DBSCAN, visualisés par ACP), clustering (K-Means validé par CAH), analyse de réseau et tests statistiques.

### 1. Premier circuit : Horizon, Northstar et Meridian

Un premier circuit apparaît autour de **Horizon Field Research Cooperative**, **Northstar Cold Chain Services** et **Meridian BioLogistics**.

Apriori isole 18 expéditions d’échantillons biologiques conservés entre 2 et 8 °C (lift de 22,5), dont 11 sont enregistrées comme des boucles, contre 11 sur 432 pour les autres expéditions (Fisher, p ≈ 6·10⁻¹²).

Le K-Means regroupe ces trois acteurs dans un cluster à part.

Les 18 accès aux sites demandés par Horizon sont tous suivis d’une expédition environnementale dans les 48 heures (délai médian de 15 h), contre 0 sur 36 pour les autres organisations, ce qui renforce l’hypothèse d’un lien opérationnel entre le terrain et le circuit logistique.

### 2. Anomalies dans les inventaires biologiques

Les inventaires font ressortir des écarts de matériel biologique : 26 écarts aberrants sur 502 (IQR et z-score), dont 13 confirmés par Isolation Forest, LOF et DBSCAN à la fois.

Ils se concentrent sur les sites de Meridian (FCL-1019, FCL-1020, FCL-1027).

Les mois avec expédition présentent un écart moyen de −7,2 unités contre +0,1 sans expédition (p = 0,0001), et les ajustements n’expliquent qu’environ 20 % de ces baisses : ce sont des sorties non documentées.

### 3. Second circuit : Meridian et les établissements Asterion

Un second circuit conduit de **Meridian BioLogistics** vers les établissements **Asterion**.

Les 26 livraisons cliniques sont toutes suivies, sur le même site, d’une procédure **MRP-42 — Targeted Metabolic Resilience Administration** (délai médian de 6,5 jours).

Sur 49 procédures MRP-42, 28 suivent une livraison, contre environ 4 attendues au hasard. Les six autres procédures ne présentent pas ce comportement.

### 4. Les documents internes : CHAMELEO et Unwabu

Les documents internes font apparaître les désignations **CHAMELEO** et **Unwabu** : un dispositif séparant les informations ordinaires sur les expéditions d’annexes sécurisées contenant les itinéraires détaillés.


Le message de la lanceuse d’alerte **Mara Venn** affirme que des chauves-souris *Eonycteris spelaea* ont été collectées puis retirées des inventaires habituels, ce qui relie les stocks biologiques manquants aux chauves-souris et à des expériences sur la longévité et la résilience métabolique (MRP-42).

### 5. Ce que cette partie apporte au secret

Elle fait apparaître deux flux qui convergent autour de Meridian :

- **Un flux environnemental** associé à Horizon et Northstar, déclenché par les accès aux sites.
- **Un flux clinique** destiné aux établissements Asterion, systématiquement suivi de la procédure MRP-42.

Elle met aussi en évidence des anomalies de stock biologique, confirmées par plusieurs méthodes, qui seraient liées aux chauves-souris.

## 4.4. Health — Deux phénomènes médicaux distincts

La partie Health analyse les dossiers de patients, les observations cliniques, les consultations et les enregistrements cardiaques. Elle fait émerger deux groupes qu'il est important de ne pas confondre.

Le premier est un groupe de **dix patients présentant un profil physiologique atypique**, appelé CORE dans le notebook. Il est identifié à partir de plusieurs caractéristiques combinées : une discordance entre le pouls apical et périphérique, un signal thoracique secondaire, un balancement particulier malgré un équilibre préservé, des observations oculaires atypiques et certaines incohérences d'identification.

Ce groupe est retrouvé par plusieurs approches complémentaires, notamment une règle fondée sur cinq critères, PCA, K-means et Isolation Forest. Pour six de ces patients, les enregistrements cardiaques montrent deux rythmes réguliers distincts. Pour les quatre autres, les observations cliniques sont présentes, mais les enregistrements ne permettent pas de confirmer cette signature.

Le second phénomène concerne les patients ayant reçu **MRP-42 avec l'autorisation `restricted_specialist`**. Le notebook identifie huit patients, tous associés à des fonctions de direction ou à de hautes responsabilités. Leur âge biologique estimé est en moyenne inférieur d'environ onze ans à leur âge chronologique. Leur parcours de soins est également particulier et distinct de celui des autres patients.

Le notebook teste par ailleurs une piste d'identification reliant un patient à **Dr. Elias Voss**, dirigeant de Meridian BioLogistics. La correspondance proposée dans une note clinique ne se vérifie pas pour le patient initialement cité. Un autre patient présente des attributs administratifs plus proches, mais cela ne constitue pas une preuve d'identité. Le notebook recommande explicitement de conserver ces possibilités comme des hypothèses et de ne pas attribuer publiquement une identité.

**Ce que cette partie apporte au secret :** elle révèle un programme médical restreint associé à des responsables dont l'âge biologique estimé est particulièrement bas, ainsi qu'un autre groupe de patients présentant des caractéristiques physiologiques rares. Les données ne démontrent pas que ces deux groupes sont liés, ni que les procédures MRP-42 expliquent le profil du groupe CORE.

---

# 5. Le secret global — Reconstitution du scénario

## 5.1. De l'observation de terrain à la chaîne biologique

Au départ, l'enquête porte sur des baisses inhabituelles de populations de chauves-souris. Le site KNT-KES attire l'attention : un rapport y décrit une diminution qui ne semble pas expliquée par la météo ou par le fonctionnement des équipements, ainsi que des traces non identifiées.

Public Records permet ensuite de découvrir que Horizon Field Research Cooperative intervient régulièrement sur ce site. Les demandes d'accès sont encadrées par des procédures particulières et les interventions observées se répètent selon un calendrier et des horaires similaires. L'une des demandes mentionne du matériel de stockage frigorifique.

Un témoignage retrouvé dans les archives, le document PUB-510079, donne alors une nouvelle signification possible à ces observations. Il évoque la collecte de chauves-souris *Eonycteris spelaea*, leur conditionnement dans des unités scellées et des documents d'inventaire associés.

La partie Logistics apporte un élément matériel supplémentaire : les données montrent un circuit d'expéditions biologiques reliant Horizon à Meridian BioLogistics par l'intermédiaire de Northstar Cold Chain Services. Ces expéditions sont fortement rapprochées dans le temps des accès aux sites. Les inventaires présentent par ailleurs des écarts qui rendent certains mouvements difficiles à suivre.

Pris ensemble, ces éléments dessinent la possibilité d'une activité organisée de collecte et de transport de matériel biologique, dont la nature exacte et la destination ne sont pas entièrement documentées.

## 5.2. De Meridian aux procédures MRP-42

L'enquête ne s'arrête pas au circuit environnemental. Meridian BioLogistics apparaît également dans les livraisons destinées aux établissements Asterion.

Le rapprochement entre les dates de livraison et les événements médicaux révèle une association spécifique avec MRP-42, une procédure réalisée sous autorisation restreinte. Cette association est beaucoup plus marquée que pour les autres procédures cliniques étudiées.

Health apporte alors un élément particulièrement troublant : huit patients ayant reçu MRP-42 sous autorisation `restricted_specialist` occupent des fonctions de direction ou de haute responsabilité. Leur âge biologique estimé est en moyenne inférieur d'environ onze ans à leur âge chronologique.

Cette découverte ouvre une hypothèse : MRP-42 pourrait être associé à un programme de résilience métabolique ou de maintien physiologique destiné à un cercle restreint de responsables. Les données établissent une association entre les livraisons cliniques et les procédures MRP-42, ainsi qu'un profil d'âge biologique inhabituel chez les huit patients concernés. Elles ne révèlent toutefois ni la composition du produit, ni son mécanisme, ni un lien direct avec les échantillons issus du circuit environnemental.

## 5.3. L'hypothèse centrale

**Le secret global le plus cohérent avec les résultats des quatre notebooks serait l'existence possible d'un programme biologique confidentiel, organisé autour de deux circuits complémentaires :**

1. **Un circuit de terrain et de collecte**, dans lequel Horizon Field Research Cooperative accède à des sites environnementaux, puis des échantillons biologiques sont transportés par Northstar Cold Chain Services vers Meridian BioLogistics.
2. **Un circuit clinique**, dans lequel Meridian approvisionne des établissements Asterion avant des procédures MRP-42 réalisées sous autorisation restreinte auprès de patients occupant des fonctions importantes.

Les écarts d'inventaire, les documents sécurisés et le témoignage sur les chauves-souris pourraient indiquer que certaines activités biologiques ne sont pas entièrement visibles dans les registres ordinaires. Le profil des bénéficiaires de MRP-42 donne à ce programme une finalité potentiellement liée à la résilience métabolique ou au vieillissement.

Une piste complémentaire pourrait concerner les mécanismes biologiques associés à la longévité. Certaines recherches scientifiques, notamment menées sur des modèles animaux comme la souris, étudient des protéines et des mécanismes susceptibles d'influencer le vieillissement. Les chauves-souris présentent également des caractéristiques biologiques intéressantes pour la recherche sur la longévité. On peut donc envisager que les collectes biologiques identifiées dans notre enquête puissent être liées à l'étude de tels mécanismes. Si cette piste était confirmée, elle pourrait apporter un éclairage sur la finalité éventuelle de MRP-42 et sur les profils biologiques observés chez certains patients. Toutefois, aucun élément de nos données ne permet actuellement d'établir ce lien.


---

## 6. Ce que les données permettent — et ne permettent pas — de conclure

Pour préserver la rigueur de l'enquête, il est important de distinguer les observations des interprétations.

### Éléments directement observés dans les notebooks

- Des baisses inhabituelles de populations de chauves-souris, dont une observation préoccupante à KNT-KES.
- Des interventions répétées de Horizon Field Research Cooperative sur ce site.
- Des expéditions biologiques reliant Horizon, Northstar Cold Chain Services et Meridian BioLogistics.
- Une proximité temporelle marquée entre les accès de Horizon et les expéditions environnementales.
- Des anomalies de stocks et des problèmes de traçabilité.
- Des livraisons cliniques suivies de procédures MRP-42 dans les établissements concernés.
- Huit patients `restricted_specialist` présentant un écart important entre âge biologique estimé et âge chronologique.
- Un groupe CORE de dix patients présentant un profil physiologique atypique, dont six avec une signature cardiaque à deux rythmes confirmée.

### Hypothèses qui restent à vérifier

- Les échantillons transportés proviendraient effectivement de chauves-souris *Eonycteris spelaea*.
- Les activités de collecte seraient directement liées aux procédures MRP-42.
- Les écarts de stocks correspondraient à une dissimulation volontaire.
- Le programme MRP-42 aurait pour objectif de prolonger la longévité ou de modifier durablement le vieillissement.
- Certaines identités historiques correspondraient à une même personne.
- Le groupe CORE et les bénéficiaires de MRP-42 seraient liés.
- Les collectes biologiques pourraient viser l'étude de mécanismes de longévité chez les chauves-souris, avec une éventuelle application à la recherche sur le vieillissement humain.


---

## 7. Conclusion

En croisant les quatre domaines, notre enquête fait émerger un scénario qui dépasse largement les observations initiales. Une activité de terrain autour de sites fréquentés par les chauves-souris semble liée à des expéditions biologiques spécialisées. Ces flux passent par des acteurs logistiques identifiés, notamment Northstar Cold Chain Services et Meridian BioLogistics. Cette dernière organisation apparaît également dans un second circuit, celui des livraisons vers des établissements Asterion où sont réalisées des procédures MRP-42.

Les données médicales rendent le scénario encore plus intrigant : certains bénéficiaires de MRP-42 sont des responsables de haut niveau dont l'âge biologique estimé est nettement inférieur à leur âge réel. En parallèle, un groupe distinct de patients présente des caractéristiques physiologiques rares. Les documents historiques et les archives suggèrent enfin que les activités étudiées s'inscrivent dans un environnement où la confidentialité, la gouvernance et les stratégies environnementales jouent un rôle important.

**Notre hypothèse finale est donc celle d'un programme biologique confidentiel reliant potentiellement collecte environnementale, logistique spécialisée et interventions cliniques réservées à certains responsables.**

Une piste intéressante serait que ce programme cherche à étudier les caractéristiques biologiques des chauves-souris afin d'explorer leur éventuelle utilisation dans des recherches visant le ralentissement du vieillissement et le rajeunissement des êtres humains.

Le croisement des quatre domaines donne du sens à cette hypothèse : Ecology révèle les anomalies concernant les chauves-souris, Public Records met en évidence les accès aux sites et les témoignages de collecte, Logistics retrace les mouvements de matériel biologique vers Meridian, et Health identifie huit bénéficiaires de MRP-42, tous occupant des postes à responsabilité, dont l'âge biologique estimé est en moyenne inférieur d'environ onze ans à leur âge chronologique.

Cette interprétation reste une hypothèse : les données ne confirment ni l'utilisation des échantillons de chauves-souris dans MRP-42, ni l'existence d'un véritable procédé de rajeunissement humain.

---

## 8. Utilisation de l'intelligence artificielle

L'intelligence artificielle générative a été utilisée comme **outil d'accompagnement** pendant le projet. Elle a notamment servi à mieux comprendre le fonctionnement et la logique de certains algorithmes, à obtenir des explications étape par étape sur des notions de Data Mining, à faciliter l'interprétation de certains résultats et à améliorer la formulation ainsi que la correction orthographique des textes. Elle a donc joué un rôle d'aide à la compréhension et à la rédaction, sans se substituer au travail d'analyse, aux choix méthodologiques, à l'exécution des notebooks ni à la vérification des résultats par les membres du groupe.

---

## 9. Exécution

Les notebooks doivent être ouverts depuis le répertoire racine du projet afin que les chemins relatifs vers les fichiers du dossier `data/` fonctionnent correctement.

1. Décompresser le projet.
2. Ouvrir un terminal dans le dossier `20262027-UE-DataMining-Project`.
3. Installer ou activer un environnement Python contenant les bibliothèques nécessaires.
4. Lancer JupyterLab ou Jupyter Notebook.
5. Ouvrir les notebooks et exécuter les cellules depuis le répertoire racine.

```bash
jupyter lab
```

Les notebooks utilisent notamment des bibliothèques de traitement de données, de visualisation, de statistiques et de Machine Learning telles que `pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy`, `scikit-learn` et les outils Jupyter.

**Remarque :** le fichier `requirements.txt` fourni est un export d'environnement Conda spécifique à Windows. Selon le système d'exploitation et la version de Python utilisés, certaines dépendances peuvent nécessiter une installation ou une adaptation.

## 10. Références scientifiques

Afin d'apporter un contexte scientifique à notre hypothèse autour de la longévité biologique, nous nous sommes appuyés sur plusieurs travaux de recherche portant sur les mécanismes du vieillissement chez les mammifères, notamment les souris et les chauves-souris.

1. **Sinha, M. et al. (2014).** *Restoring systemic GDF11 levels reverses age-related dysfunction in mouse skeletal muscle.* Science, 344(6184), 649–652.  
   [https://pubmed.ncbi.nlm.nih.gov/24797481/](https://pubmed.ncbi.nlm.nih.gov/24797481/)  
   Cette étude examine le rôle de la protéine GDF11 dans le fonctionnement et la régénération musculaire chez des souris âgées.

2. **Huang, Z. et al. (2019).** *Longitudinal comparative transcriptomics reveals unique mechanisms underlying extended healthspan in bats.* Nature Ecology & Evolution, 3, 1110–1120.  
   [https://doi.org/10.1038/s41559-019-0913-3](https://doi.org/10.1038/s41559-019-0913-3)  
   Cette recherche étudie les signatures moléculaires associées au vieillissement en bonne santé chez les chauves-souris, à partir d'une analyse longitudinale de l'expression des gènes.

3. **Kacprzyk, J. et al. (2021).** *Evolution of mammalian longevity: age-related increase in autophagy in bats compared to other mammals.* Aging, 13(6), 7998–8025.  
   [https://pubmed.ncbi.nlm.nih.gov/33744862/](https://pubmed.ncbi.nlm.nih.gov/33744862/)  
   Cette étude met en évidence une augmentation particulière de l'expression de mécanismes liés à l'autophagie avec l'âge chez les chauves-souris, un processus impliqué dans le maintien de l'équilibre cellulaire.

4. **Vazquez, J. M. et al. (2026).** *Insights into longevity and virus-driven adaptation from Myotis bat genomes.* Nature, 658, 153–162.  
   [https://doi.org/10.1038/s41586-026-10932-7](https://doi.org/10.1038/s41586-026-10932-7)  
   Cette publication récente analyse les adaptations génétiques de plusieurs espèces de chauves-souris du genre *Myotis*, en étudiant notamment les mécanismes associés à la longévité, à la résistance au cancer et aux interactions avec les virus.
