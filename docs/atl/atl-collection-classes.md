---
title: Classes de Collection ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4594b87f07cd4d89937ba640d9a04aeacf2ef866
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="atl-collection-classes"></a>Classes de collection ATL
ATL fournit de nombreuses classes de stockage et l’accès aux données. La classe que vous décidez d’utiliser dépend de plusieurs facteurs, notamment :  
  
-   La quantité de données à stocker  
  
-   Efficacité et les performances d’accès aux données  
  
-   La possibilité d’accéder aux données par index ou par clé  
  
-   Comment les données sont triées.  
  
-   Préférences personnelles  
  
## <a name="small-collection-classes"></a>Classes de Collection de petites  
 ATL fournit les classes de tableau suivantes pour traiter des petites quantités d’objets. Cependant, ces classes sont limitées et conçus pour être utilisé en interne par ATL. Il est déconseillé de les utiliser dans vos programmes.  
  
|Classe|Type de stockage de données|  
|-----------|--------------------------|  
|[CSimpleArray](../atl/reference/csimplearray-class.md)|Implémente une classe de tableau pour traiter des petites quantités d’objets.|  
|[CSimpleMap](../atl/reference/csimplemap-class.md)|Implémente une classe de mappage pour traiter des petites quantités d’objets.|  
  
## <a name="general-purpose-collection-classes"></a>Classes de Collection usage général  
 Les classes suivantes implémentent des tableaux, listes et mappages et sont fournies en tant que classes de collection usage général :  
  
|Classe|Type de stockage de données|  
|-----------|--------------------------|  
|[CAtlArray](../atl/reference/catlarray-class.md)|Implémente un tableau.|  
|[CAtlList](../atl/reference/catllist-class.md)|Implémente une liste.|  
|[CAtlMap](../atl/reference/catlmap-class.md)|Implémente une structure de mappage, par laquelle les données peuvent être référencées par la clé ou une valeur.|  
|[CRBMap](../atl/reference/crbmap-class.md)|Implémente une structure de mappage à l’aide de l’algorithme rouge-noire.|  
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|Implémente une structure de multimappage rouge-noire.|  
  
 Ces classes seront intercepter de nombreuses erreurs de programmation lorsqu’il est utilisé dans les versions debug, mais pour les besoins de performances, ces contrôles ne seront pas effectuées dans les versions commerciales.  
  
## <a name="specialized-collection-classes"></a>Classes de Collection spécialisées  
 Classes de collection plus spécialisées sont également fournis pour la gestion des pointeurs de mémoire et des pointeurs d’interface :  
  
|Classe|Objectif|  
|-----------|-------------|  
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|Fournit des méthodes utiles lors de la construction d’un tableau de pointeurs intelligents.|  
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|Fournit des méthodes utiles lors de la construction d’une liste de pointeurs intelligents.|  
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|Magasins `IUnknown` pointeurs et est conçu pour être utilisé en tant que paramètre à la [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) classe de modèle.|  
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|Fournit des méthodes utiles lors de la construction d’une liste de pointeurs de tas.|  
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|Fournit des méthodes utiles lors de la construction d’un tableau de pointeurs d’interface COM.|  
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|Fournit des méthodes utiles lors de la construction d’une liste de pointeurs d’interface COM.|  
  
## <a name="choosing-a-collection-class"></a>Choix d’une classe de Collection  
 Chacune des classes de collection disponible offre des caractéristiques de performances différentes, comme indiqué dans le tableau ci-dessous.  
  
-   Les colonnes 2 et 3 décrivent le classement de chaque classe caractéristiques et d’accès. Dans le tableau, le terme « ordonné » signifie que l’ordre dans lequel les éléments sont insérés et supprimés détermine leur ordre dans la collection. Il ne signifie pas que les éléments sont triés en fonction de leur contenu. Le terme « indexé » signifie que les éléments de la collection peuvent être récupérés par un index entier, comme les éléments d’un tableau standard.  
  
-   Les colonnes 4 et 5 décrivent les performances de chaque classe. Dans les applications qui nécessitent de nombreuses insertions dans la collection, la vitesse d’insertion peut être particulièrement importante. Pour d’autres applications, la vitesse de recherche peut être plus importante.  
  
-   La colonne 6 indique si chaque forme autorise des éléments en double.  
  
-   Les performances d’une opération de classe de collection donnée sont exprimée en termes de la relation entre le temps nécessaire pour terminer l’opération et le nombre d’éléments dans la collection. Une opération exigeant un laps de temps qui augmente proportionnellement au nombre d’éléments est décrite comme un algorithme o (n). En revanche, une opération exigeant un laps de temps qui augmente de moins en moins que le nombre d’éléments augmente est décrite comme un algorithme O (n journal). Par conséquent, en termes de performances, les algorithmes O (n journal) maintiennent des algorithmes plus en tant que le nombre d’éléments augmente.  
  
### <a name="collection-shape-features"></a>Fonctionnalités des formes de collection  
  
|Forme|Ordered|Indexées|Insérer un<br /><br /> d'élément|Rechercher<br /><br /> élément spécifié|Dupliquer<br /><br /> éléments|  
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|  
|Liste|Oui|Non|Rapide (temps constant)|Lente o (n)|Oui|  
|Tableau|Oui|Par int (temps constant)|Lente o (n), sauf si insertion à la fin, dans quel cas temps constant|Lente o (n)|Oui|  
|Carte|Non|Par clé (temps constant)|Rapide (temps constant)|Rapide (temps constant)|Non (clés) Oui (valeurs)|  
|Table rouge-noire|Oui (par clé)|Par clé O (n journal)|Rapide O (n journal)|Rapide O (n journal)|Non|  
|Rouge-noire Multimap|Oui (par clé)|Par clé O(log n) (plusieurs valeurs par clé)|Rapide O (n journal)|Rapide O (n journal)|Oui (plusieurs valeurs par clé)|  
  
## <a name="using-ctraits-objects"></a>Utilisation des objets CTraits  
 Comme les classes de collection ATL peuvent être utilisés pour stocker un large éventail de types de données définis par l’utilisateur, il peut être utile de pouvoir substituer des fonctions importantes telles que les comparaisons. Cela est possible en utilisant les classes CTraits.  
  
 CTraits (classes) sont semblables aux, mais il est plus flexible que les fonctions d’assistance du classe de collection MFC ; consultez [Assistants de classe de Collection](../mfc/reference/collection-class-helpers.md) pour plus d’informations.  
  
 Lors de la construction de votre classe de collection, vous avez la possibilité de spécifier une classe CTraits. Cette classe contiendra le code qui effectue des opérations telles que des comparaisons lorsqu’elle est appelée par les autres méthodes qui composent la classe de collection. Par exemple, si votre objet de liste contient vos propres structures définies par l’utilisateur, vous souhaiterez redéfinir le test d’égalité pour comparer uniquement certaines variables de membre. De cette façon, méthode de recherche de l’objet de liste fonctionne de manière plus utile.  
  
## <a name="example"></a>Exemple  
  
### <a name="code"></a>Code  
 [!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]  
  
## <a name="comments"></a>Commentaires  
 Pour obtenir la liste des classes CTraits, consultez [Classes de Collection](../atl/collection-classes.md).  
  
 Le diagramme suivant illustre la hiérarchie de classes pour les classes CTraits.  
  
 ![Hiérarchie des traits des classes de collection](../atl/media/vctraitscollectionclasseshierarchy.gif "vctraitscollectionclasseshierarchy")  
  
## <a name="collection-classes-samples"></a>Exemples de Classes de collection  
 Les exemples suivants illustrent les classes de collection :  
  
-   [MMXSwarm, exemple](../visual-cpp-samples.md)  
  
-   [DynamicConsumer, exemple](../visual-cpp-samples.md)  
  
-   [Exemple UpdatePV](../visual-cpp-samples.md)  
  
-   [Exemple de texte défilant](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../atl/active-template-library-atl-concepts.md)   
 [Classes de collections](../atl/collection-classes.md)

