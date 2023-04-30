### 💡 **Compétences du projet**


| <div align="center">` Compétences acquises 💡 ` | ` Outils utilisées `
| :--- | :---: |
| Prétraiter des données stockées en les classifiant et en corrigeant les erreurs et les incohérences présentes. |![python](https://img.icons8.com/color/28/null/python--v1.png) |
| Manipulation des data frames |![python](https://img.icons8.com/color/28/null/python--v1.png) | 

<br>

# Synthèse des résultats de l'analyse.

- [Introduction](#introduction)
- [Cahier des charges](#cahier-des-charges)
- [Libreries utilisées et version](#libreries-utilisées-et-version)
- [Les pays avec des problemes de sous-nutrition](#les-pays-avec-des-problemes-de-sous-nutrition)
- [Nombre theroique des personnes qui peuvent être nourris](#nombre-theroique-des-personnes-qui-peuvent-être-nourris)
- [Conclusion](#conclusion)


## Introduction

![fao](https://github.com/ocon-ene/openclassrooms-Data-Analyst/blob/main/images/bottleneck.PNG)

Vous êtes une data analyst free lance et vous avez reussi a decrocher vôtre premier travail chez Bottleneck, un marchand de vin très prestigieux.

Laurent, le manager de cette mission, vous parle des problemes de l'entreprise : 

>Actuellement, pour gérer nos ressources, nos clients, etc., on utilise un ERP (Entreprise Resource Planning) qui n’est absolument pas relié à notre site de vente en ligne. Pour être tout à fait honnête, les outils en place sont vraiment artisanaux et dans ces conditions, la gestion des stocks est vraiment complexe et notre visibilité en termes d’analyse des ventes sur le Net est vraiment réduite, car très peu de personnes ont accès au back-office. En attendant une solution plus centralisée, un rapprochement entre les 2 bases, même manuel, pourrait être très utile…

## Cahier des charges

Premier mission:
-Rapprocher deux exports: un export de l’ERP contenant les références produit, leur prix de vente et leur état de stock, et un export d’une table de l’outil de CMS (Content Management System) contenant les informations des produits commercialisés en ligne (nom, description, nombre de ventes...)
-

Deuxieme mission:
-Une fois le rapprochement effectué, calculer le chiffre d’affaires par produit, ainsi que le total du chiffre d’affaires réalisé en ligne.
	
Troisieme mission:
-Analyser la variable "prix" afin de détecter d’éventuelles valeurs aberrantes, de les lister et d’en faire une représentation graphique pour plus de lisibilité.

## Librairies utilisées et version

```python
numpy version is 1.21.5
pandas version is 1.4.2
seaborn version is 0.11.2
```
## Les pays avec des problèmes de sous-nutrition

D'abord nous pouvons parler des pays qui ont le plus de personnes en sous nutrition en proportion à leur population.
Malheureusement Haiti est au top mondial du classement en 2017, suivi de la Corée du nord. 
Dans cette table on peut observer une tendance, les pays qui ont des problèmes politiques ou qu'ont eu des guerres, sont les pays qui ont les plus de problèmes à nourrir leur population.

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Zone</th>
      <th>Personnes en sous nutrition en milles</th>
      <th>Population en milles</th>
      <th>Pourcentage</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>78</th>
      <td>Haïti</td>
      <td>5300.0</td>
      <td>10982.37</td>
      <td>48.26</td>
    </tr>
    <tr>
      <th>157</th>
      <td>République populaire démocratique de Corée</td>
      <td>12000.0</td>
      <td>25429.82</td>
      <td>47.19</td>
    </tr>
    <tr>
      <th>108</th>
      <td>Madagascar</td>
      <td>10500.0</td>
      <td>25570.51</td>
      <td>41.06</td>
    </tr>
    <tr>
      <th>103</th>
      <td>Libéria</td>
      <td>1800.0</td>
      <td>4702.23</td>
      <td>38.28</td>
    </tr>
    <tr>
      <th>100</th>
      <td>Lesotho</td>
      <td>800.0</td>
      <td>2091.53</td>
      <td>38.25</td>
    </tr>
  </tbody>
</table>
</div>

## Nombre théorique des personnes qui peuvent être nourris

Ensuite nous allons analyser les nombre théorique des personnes qui pourraient être nourris avec la production actuelle de nourriture.

D'abord il faut savoir que les besoin énergétiques diffèrent entre les pays, il y a des pays avec une structure morphologique plus petite, ou qui ont des besoins caloriques plus important du fait de leur climat. On a donc importé depuis le site de la FAO, le fichier qui donne les besoin énergétiques par pays : 

```python
besoin_alimentaires_2017 = pd.read_csv("C:/Users/ocon_/Sync/1_Data_analyst/P4_ocon_jorge/Données/besoin_energetiques_2017.csv")
```
Quelle conclusion en tirer donc sur ce point ? Deux
1. La production actuelle permet de nourrir l'ensemble de la population mondial, et donc nous avons un problème d'inégalité dans l'accès à la nourriture entre pays et/ou des problèmes de distribution au sein d'un même pays
2. Une diète exclusivement végétarienne pour toute la planète serait difficile d'atteint avec les moyennes actuelles, mais elle serait possible si l'on destine une partie de la culture pour l'alimentation des animaux aux humaines.

	<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>?l?ment</th>
      <th>Zone</th>
      <th>Aliments pour animaux</th>
      <th>Disponibilité intérieure</th>
      <th>Nourriture</th>
      <th>Proportion aliments pour animaux %</th>
      <th>Proportion aliments pour nourriture humaine %</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>51</th>
      <td>Danemark</td>
      <td>7171</td>
      <td>8591</td>
      <td>697</td>
      <td>83.47</td>
      <td>8.11</td>
    </tr>
    <tr>
      <th>79</th>
      <td>Irlande</td>
      <td>3253</td>
      <td>4035</td>
      <td>592</td>
      <td>80.62</td>
      <td>14.67</td>
    </tr>
    <tr>
      <th>129</th>
      <td>Pays-Bas</td>
      <td>9909</td>
      <td>13604</td>
      <td>1626</td>
      <td>72.84</td>
      <td>11.95</td>
    </tr>
    <tr>
      <th>55</th>
      <td>Espagne</td>
      <td>22618</td>
      <td>31235</td>
      <td>5227</td>
      <td>72.41</td>
      <td>16.73</td>
    </tr>
    <tr>
      <th>44</th>
      <td>Chypre</td>
      <td>432</td>
      <td>626</td>
      <td>170</td>
      <td>69.01</td>
      <td>27.16</td>
    </tr>
  </tbody>
</table>
</div>
	
Pour finir, nous ne pouvons pas fermer les yeux face à l'absurde quantité de nourriture qui est jetée avec plus de 10%.

## Conclusion

Un pourcentage élevé de la nourriture est soit destinée à la consommation des animaux, soit jeté à la poubelle pendant que des pays pauvres sont en difficulté et n'arrivent pas à nourrir l'ensemble de sa population.

Pour accèder au code complet [click ici](https://github.com/ocon-ene/openclassrooms-Data-Analyst/blob/main/PM1-%C3%A9tude%20de%20sant%C3%A9%20publique/Ocon_Jorge_1_P4_042022.ipynb) 

