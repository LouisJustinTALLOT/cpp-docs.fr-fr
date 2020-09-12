---
title: Vue d’ensemble de la classe de collection ATL
ms.date: 11/19/2018
helpviewer_keywords:
- DestructElements function
- collection classes, choosing
- ConstructElements function
- SerializeElements function
- traits classes
- collection classes, about collection classes
- CTraits classes
- collection classes
ms.assetid: 4d619d46-5b4e-41dd-b9fd-e86b1fbc00b5
ms.openlocfilehash: 039af388a3713540c6ba7d39e8b639cf83d291ff
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040858"
---
# <a name="atl-collection-classes"></a>Classes de collection ATL

ATL fournit de nombreuses classes pour le stockage et l’accès aux données. La classe que vous décidez d’utiliser dépend de plusieurs facteurs, notamment :

- Quantité de données à stocker

- Efficacité et performances lors de l’accès aux données

- La possibilité d’accéder aux données par index ou par clé

- Mode de tri des données

- Préférences personnelles

## <a name="small-collection-classes"></a>Classes de collection de petite taille

ATL fournit les classes de tableau suivantes pour traiter un petit nombre d’objets. Toutefois, ces classes sont limitées et conçues pour une utilisation en interne par ATL. Il n’est pas recommandé de les utiliser dans vos programmes.

|Classe|Type de stockage de données|
|-----------|--------------------------|
|[CSimpleArray](../atl/reference/csimplearray-class.md)|Implémente une classe de tableau pour traiter un petit nombre d’objets.|
|[CSimpleMap](../atl/reference/csimplemap-class.md)|Implémente une classe de mappage pour traiter un petit nombre d’objets.|

## <a name="general-purpose-collection-classes"></a>Classes de collection usage général

Les classes suivantes implémentent des tableaux, des listes et des mappages, et sont fournies en tant que classes de collection à usage général :

|Classe|Type de stockage de données|
|-----------|--------------------------|
|[CAtlArray](../atl/reference/catlarray-class.md)|Implémente un tableau.|
|[CAtlList](../atl/reference/catllist-class.md)|Implémente une liste.|
|[CAtlMap](../atl/reference/catlmap-class.md)|Implémente une structure de mappage, dans laquelle les données peuvent être référencées par la clé ou la valeur.|
|[CRBMap](../atl/reference/crbmap-class.md)|Implémente une structure de mappage à l’aide de l’algorithme rouge-noir.|
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|Implémente une structure de multimappage rouge-noir.|

Ces classes interceptent de nombreuses erreurs de programmation quand elles sont utilisées dans les versions Debug, mais pour des raisons de performances, ces vérifications ne sont pas effectuées dans les versions commerciales.

## <a name="specialized-collection-classes"></a>Classes de collection spécialisées

Des classes de collection plus spécialisées sont également fournies pour la gestion des pointeurs de mémoire et des pointeurs d’interface :

|Classe|Objectif|
|-----------|-------------|
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|Fournit des méthodes utiles lors de la construction d’un tableau de pointeurs intelligents.|
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|Fournit des méthodes utiles lors de la construction d’une liste de pointeurs intelligents.|
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|Stocke `IUnknown` des pointeurs et est conçu pour être utilisé comme paramètre de la classe de modèle [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) .|
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|Fournit des méthodes utiles lors de la construction d’une liste de pointeurs de tas.|
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|Fournit des méthodes utiles lors de la construction d’un tableau de pointeurs d’interface COM.|
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|Fournit des méthodes utiles lors de la construction d’une liste de pointeurs d’interface COM.|

## <a name="choosing-a-collection-class"></a>Choix d’une classe de collection

Chacune des classes de collection disponibles offre des caractéristiques de performances différentes, comme indiqué dans le tableau ci-dessous.

- Les colonnes 2 et 3 décrivent les caractéristiques d’accès et de classement de chaque classe. Dans le tableau, le terme « ordonné » signifie que l’ordre dans lequel les éléments sont insérés et supprimés détermine leur ordre dans la collection. Il ne signifie pas que les éléments sont triés en fonction de leur contenu. Le terme « indexé » signifie que les éléments de la collection peuvent être récupérés par un index entier, comme les éléments d’un tableau standard.

- Les colonnes 4 et 5 décrivent les performances de chaque classe. Dans les applications qui nécessitent de nombreuses insertions dans la collection, la vitesse d’insertion peut être particulièrement importante. Pour d’autres applications, la vitesse de recherche peut être plus importante.

- La colonne 6 indique si chaque forme autorise des éléments en double.

- Les performances d’une opération de classe de collection donnée sont exprimées en termes de relation entre le temps nécessaire à l’exécution de l’opération et le nombre d’éléments dans la collection. Une opération qui prend un laps de temps qui augmente de façon linéaire à mesure que le nombre d’éléments augmente est décrite comme un algorithme O (n). En revanche, une opération qui prend un certain temps qui augmente le nombre d’éléments augmente, et moins, est décrite comme un algorithme O (log n). Par conséquent, en termes de performances, les algorithmes O (log n) surpassent les algorithmes O (n) de plus en plus, à mesure que le nombre d’éléments augmente.

### <a name="collection-shape-features"></a>Fonctionnalités des formes de collection

|Forme|Ordered (Validée)|Indexée|Insérer un<br /><br /> element|Rechercher<br /><br /> élément spécifié|Dupliquer<br /><br /> elements|
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|
|List|Oui|Non|Rapide (temps constant)|O lent (n)|Oui|
|Array|Oui|Par int (temps constant)|Lent O (n), sauf en cas d’insertion à la fin, auquel cas une heure constante|O lent (n)|Oui|
|Carte|Non|Par clé (temps constant)|Rapide (temps constant)|Rapide (temps constant)|Non (clés) Oui (valeurs)|
|Carte rouge-noire|Oui (par clé)|Par clé O (log n)|O rapide (log n)|O rapide (log n)|Non|
|Multimap rouge-noir|Oui (par clé)|Par clé O (log n) (valeurs multiples par clé)|O rapide (log n)|O rapide (log n)|Oui (valeurs multiples par clé)|

## <a name="using-ctraits-objects"></a>Utilisation d’objets CTraits

Comme les classes de collection ATL peuvent être utilisées pour stocker un large éventail de types de données définis par l’utilisateur, il peut être utile de pouvoir substituer des fonctions importantes telles que les comparaisons. Cela est possible à l’aide des classes CTraits.

Les classes CTraits sont similaires, mais plus flexibles que, les fonctions d’assistance de classe de collection MFC ; Pour plus d’informations, consultez [assistances de classe de collection](../mfc/reference/collection-class-helpers.md) .

Lors de la construction de votre classe de collection, vous avez la possibilité de spécifier une classe CTraits. Cette classe contiendra le code qui effectuera des opérations telles que les comparaisons quand elles sont appelées par d’autres méthodes qui composent la classe de collection. Par exemple, si votre objet de liste contient vos propres structures définies par l’utilisateur, vous souhaiterez peut-être redéfinir le test d’égalité pour comparer uniquement certaines variables membres. De cette façon, la méthode Find de l’objet List fonctionnera de manière plus utile.

## <a name="example"></a>Exemple

### <a name="code"></a>Code

[!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]

## <a name="comments"></a>Commentaires

Pour obtenir la liste des classes CTraits, consultez [classes de collection](../atl/collection-classes.md).

Le diagramme suivant montre la hiérarchie de classes pour les classes CTraits.

![Hiérarchie des traits des classes de collection](../atl/media/vctraitscollectionclasseshierarchy.gif "Hiérarchie des traits des classes de collection")

## <a name="collection-classes-samples"></a>Exemples de classes de collection

Les exemples suivants illustrent les classes de collection :

- [Exemple MMXSwarm](../overview/visual-cpp-samples.md)

- [DynamicConsumer, exemple](../overview/visual-cpp-samples.md)

- [Exemple UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

- [Exemple de texte défilant](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)<br/>
[Classes de collection](../atl/collection-classes.md)
