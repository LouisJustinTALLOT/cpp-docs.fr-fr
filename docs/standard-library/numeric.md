---
description: 'En savoir plus sur : &lt; numérique&gt;'
title: '&lt;numeric&gt;'
ms.date: 11/04/2016
f1_keywords:
- <numeric>
helpviewer_keywords:
- <numeric> header
ms.assetid: 6d6ccb94-48cc-479b-b4a9-bd9c78d4896a
ms.openlocfilehash: 5ff2a0ff2b765afbb60d117745976ad3919dd18f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338044"
---
# <a name="ltnumericgt"></a>&lt;numeric&gt;

Définit les fonctions de modèle de conteneur qui exécutent des algorithmes pour le traitement numérique.

## <a name="requirements"></a>Spécifications

**En-tête**: \<numeric>

**Espace de noms :** std

## <a name="remarks"></a>Notes

Les algorithmes numériques ressemblent aux algorithmes de la bibliothèque C++ standard dans [\<algorithm>](algorithm.md) et peuvent fonctionner sur diverses structures de données. Cela comprend les classes de conteneur de la bibliothèque standard C++ (par exemple, [vector](../standard-library/vector-class.md) et [list](../standard-library/list-class.md)), ainsi que les structures de données et les tableaux d’éléments définis par programmation qui répondent aux exigences d’un algorithme en particulier. Ces algorithmes atteignent ce niveau de généralité en parcourant les éléments d'un conteneur indirectement, via des itérateurs. Les algorithmes traitent les plages d'itérateurs qui sont généralement spécifiées par leur position de début ou de fin. Les plages référencées doivent être valides, c'est-à-dire que tous les pointeurs de ces plages doivent pouvoir être déréférencés et se trouver dans les séquences de chaque plage. La dernière position doit être accessible depuis la première au moyen d'une incrémentation.

Les algorithmes étendent les actions prises en charge par les opérations et les fonctions membres de chaque conteneur de la bibliothèque standard C++, et permettent l’interaction simultanée avec différents types d’objets conteneurs.

## <a name="members"></a>Membres

### <a name="functions"></a>Fonctions

|Nom|Description|
|-|-|
|[accumulate](../standard-library/numeric-functions.md#accumulate)|Calcule la somme de tous les éléments d'une plage spécifiée (y compris une valeur initiale) en calculant des sommes partielles successives, ou calcule le résultat de résultats partiels consécutifs qui sont obtenus en utilisant une opération binaire spécifiée au lieu de l'opération de somme.|
|[adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)|Détermine les différences successives entre chaque élément et son prédécesseur au sein d'une plage d'entrée et génère les résultats dans une plage de destination, ou calcule le résultat d'une procédure généralisée dans laquelle l'opération de différence est remplacée par une autre opération binaire spécifiée.|
|[exclusive_scan](../standard-library/numeric-functions.md#exclusive_scan)||
|[GCD](../standard-library/numeric-functions.md#gcd)||
|[inclusive_scan](../standard-library/numeric-functions.md#inclusive_scan)||
|[inner_product](../standard-library/numeric-functions.md#inner_product)|Calcule la somme du produit d'éléments de deux plages et l'ajoute à une valeur initiale spécifiée, ou calcule le résultat d'une procédure généralisée dans laquelle les opérations de somme et de produit sont remplacées par d'autres opérations binaires spécifiées.|
|[culbut](../standard-library/numeric-functions.md#iota)|Stocke une valeur de départ, en commençant par le premier élément et en remplissant avec des incréments successifs de la valeur (`value++`) de chaque élément de l'intervalle `[first, last)`.|
|[LCM](../standard-library/numeric-functions.md#lcm)||
|[partial_sum](../standard-library/numeric-functions.md#partial_sum)|Calcule une série de sommes dans une plage d’entrée à partir du premier élément jusqu’à l’élément numéro *i*, puis stocke le résultat de chaque somme dans l’élément numéro *i* d’une plage de destination, ou calcule le résultat d’une procédure généralisée où l’opération de somme est remplacée par une autre opération binaire spécifiée.|
|[abaisse](../standard-library/numeric-functions.md#reduce)||
|[transform_exclusive_scan](../standard-library/numeric-functions.md#transform_exclusive_scan)||
|[transform_inclusive_scan](../standard-library/numeric-functions.md#transform_inclusive_scan)||
|[transform_reduce](../standard-library/numeric-functions.md#transform_reduce)||

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
