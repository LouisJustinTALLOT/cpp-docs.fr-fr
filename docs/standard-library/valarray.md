---
title: '&lt;valarray&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <valarray>
dev_langs:
- C++
helpviewer_keywords:
- valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 65a25ded6194eccf3371b8f731fca423bd728085
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ltvalarraygt"></a>&lt;valarray&gt;

Définit la classe de modèle valarray et de nombreuses fonctions et classes de modèle de prise en charge.

## <a name="syntax"></a>Syntaxe

```cpp
#include <valarray>

```

## <a name="remarks"></a>Notes

Une latitude inhabituelle est accordée à ces fonctions et classes de modèle afin d'améliorer les performances. Plus spécifiquement, toute fonction qui retourne le type **valarray\<** T1**>** peut retourner un objet d’un autre type T2. Dans ce cas, toute fonction qui accepte un ou plusieurs arguments de type **valarray\<** T2**>** doit avoir des surcharges qui acceptent des combinaisons arbitraires de ces arguments, chacun remplacé par un argument de type T2.

### <a name="functions"></a>Fonctions

|Fonction|Description|
|-|-|
|[abs](../standard-library/valarray-functions.md#abs)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à la valeur absolue des éléments du valarray d'entrée.|
|[acos](../standard-library/valarray-functions.md#acos)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à l'arccosinus des éléments du valarray d'entrée.|
|[asin](../standard-library/valarray-functions.md#asin)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à l'arcsinus des éléments du valarray d'entrée.|
|[atan](../standard-library/valarray-functions.md#atan)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à la valeur principale de l'arctangente des éléments du valarray d'entrée.|
|[atan2](../standard-library/valarray-functions.md#atan2)|Retourne un valarray dont les éléments sont égaux à l'arctangente des composants cartésiens spécifiés par une combinaison de constantes et d'éléments de valarrays.|
|[cos](../standard-library/valarray-functions.md#cos)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux au cosinus des éléments du valarray d'entrée.|
|[cosh](../standard-library/valarray-functions.md#cosh)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux au cosinus hyperbolique des éléments du valarray d'entrée.|
|[exp](../standard-library/valarray-functions.md#exp)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à l'exponentiel naturel des éléments du valarray d'entrée.|
|[log](../standard-library/valarray-functions.md#log)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux au logarithme naturel des éléments du valarray d'entrée.|
|[log10](../standard-library/valarray-functions.md#log10)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux au logarithme commun ou en base 10 des éléments du valarray d'entrée.|
|[pow](../standard-library/valarray-functions.md#pow)|Opère sur les éléments des constantes et valarrays d'entrée, retournant un valarray dont les éléments sont égaux à une base spécifiée soit par les éléments d'un valarray d'entrée, soit par une constante élevée à une puissance spécifiée par les éléments d'un valarray d'entrée ou une constante.|
|[sin](../standard-library/valarray-functions.md#sin)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux au sinus des éléments du valarray d'entrée.|
|[sinh](../standard-library/valarray-functions.md#sinh)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux au sinus hyperbolique des éléments du valarray d'entrée.|
|[sqrt](../standard-library/valarray-functions.md#sqrt)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à la racine carrée des éléments du valarray d'entrée.|
|[swap](../standard-library/valarray-functions.md#swap)||
|[tan](../standard-library/valarray-functions.md#tan)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à la tangente des éléments du valarray d'entrée.|
|[tanh](../standard-library/valarray-functions.md#tanh)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à la tangente hyperbolique des éléments du valarray d'entrée.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator!=](../standard-library/valarray-operators.md#op_neq)|Teste si les éléments correspondants de deux valarrays de taille égale sont inégaux ou si tous les éléments d'un valarray sont inégaux à une valeur spécifiée du type d'élément du valarray.|
|[operator%](../standard-library/valarray-operators.md#op_mod)|Obtient le reste de la division des éléments correspondants de deux valarrays de taille égale ou de la division d'un valarray par une valeur spécifiée du type d'élément du valarray ou de la division d'une valeur spécifiée par un valarray.|
|[operator&](../standard-library/valarray-operators.md#op_amp)|Obtient le résultat de l’opération de bits **AND** entre les éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d’élément.|
|[operator&&](../standard-library/valarray-operators.md#op_amp_amp)|Obtient le résultat de l’opération logique **AND** entre les éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d’élément du valarray.|
|[operator>](../standard-library/valarray-operators.md#op_gt)|Teste si les éléments d'un valarray sont supérieurs aux éléments d'un valarray de taille égale ou si tous les éléments d'un valarray sont supérieurs ou inférieurs à une valeur spécifiée du type d'élément du valarray.|
|[operator>=](../standard-library/valarray-operators.md#op_gt_eq)|Teste si les éléments d'un valarray sont supérieurs ou égaux aux éléments d'un valarray de taille égale ou si tous les éléments d'un valarray sont supérieurs ou égaux à, ou inférieurs ou égaux à, une valeur spécifiée.|
|[operator>>](../standard-library/valarray-operators.md#op_gt_gt)|Décale vers la droite les bits de chaque élément d'un valarray d'un nombre spécifié de positions ou d'une quantité d'éléments spécifiée par un deuxième valarray.|
|[operator<](../standard-library/valarray-operators.md#op_lt)|Teste si les éléments d'un valarray sont inférieurs aux éléments d'un valarray de taille égale ou si tous les éléments d'un valarray sont supérieurs ou inférieurs à une valeur spécifiée.|
|[operator<=](../standard-library/valarray-operators.md#op_lt_eq)|Teste si les éléments d'un valarray sont inférieurs ou égaux aux éléments d'un valarray de taille égale ou si tous les éléments d'un valarray sont supérieurs ou égaux à, ou inférieurs ou égaux à, une valeur spécifiée.|
|[operator<<](../standard-library/valarray-operators.md#op_lt_lt)|Décale vers la gauche les bits de chaque élément d'un valarray d'un nombre spécifié de positions ou d'une quantité d'éléments spécifiée par un deuxième valarray.|
|[operator*](../standard-library/valarray-operators.md#op_star)|Obtient le produit entre des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément du valarray.|
|[operator+](../standard-library/valarray-operators.md#op_add)|Obtient la somme des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément du valarray.|
|[operator-](../standard-library/valarray-operators.md#operator-)|Obtient la différence entre des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément du valarray.|
|[operator/](../standard-library/valarray-operators.md#op_div)|Obtient le quotient entre des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément du valarray.|
|[operator==](../standard-library/valarray-operators.md#op_eq_eq)|Teste si les éléments correspondants de deux valarrays de taille égale sont égaux ou si tous les éléments d'un valarray sont égaux à une valeur spécifiée du type d'élément du valarray.|
|[operator^](../standard-library/valarray-operators.md#op_xor)|Obtient le résultat de l'opération `OR` exclusif binaire entre des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément.|
|[operator&#124;](../standard-library/valarray-operators.md#op_or)|Obtient le résultat de l'opération `OR` binaire entre des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément.|
|[operator&#124;&#124;](../standard-library/valarray-operators.md#op_lor)|Obtient le résultat de l'opération `OR` logique entre des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément du valarray.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[gslice, classe](../standard-library/gslice-class.md)|Classe utilitaire de valarray qui sert à définir des secteurs multidimensionnels d'un valarray.|
|[gslice_array, classe](../standard-library/gslice-array-class.md)|Classe de modèle interne auxiliaire qui prend en charge les objets de secteurs généraux en fournissant des opérations entre des tableaux de sous-ensembles définis par le secteur général d'un valarray.|
|[indirect_array, classe](../standard-library/indirect-array-class.md)|Classe de modèle interne auxiliaire qui prend en charge les objets qui sont des sous-ensembles de valarrays en fournissant des opérations entre des tableaux de sous-ensembles définis en spécifiant un sous-ensemble d'index d'un valarray parent.|
|[mask_array, classe](../standard-library/mask-array-class.md)|Classe de modèle interne auxiliaire qui prend en charge les objets qui sont des sous-ensembles de valarrays parents, spécifiés avec une expression booléenne, en fournissant des opérations entre les tableaux de sous-ensembles.|
|[slice, classe](../standard-library/slice-class.md)|Classe utilitaire de valarray qui sert à définir des sous-ensembles vectoriels unidimensionnels d'un valarray parent.|
|[slice_array, classe](../standard-library/slice-array-class.md)|Classe de modèle interne auxiliaire qui prend en charge les objets de secteurs en fournissant des opérations entre des tableaux de sous-ensembles définis par le secteur d'un valarray.|
|[valarray, classe](../standard-library/valarray-class.md)|La classe de modèle décrit un objet qui contrôle une séquence d’éléments de type **Type** stockés sous forme de tableau, et qui est conçu pour effectuer des opérations mathématiques à grande vitesse et optimisé pour les performances de calcul.|

### <a name="specializations"></a>Spécialisations

|||
|-|-|
|[valarray\<bool>, classe](../standard-library/valarray-bool-class.md)|Version spécialisée de la classe de modèle valarray\<**Type**> pour les éléments de type `bool`.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
