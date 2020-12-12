---
description: 'En savoir plus sur : &lt; valarray&gt;'
title: '&lt;valarray&gt;'
ms.date: 11/04/2016
f1_keywords:
- <valarray>
helpviewer_keywords:
- valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
ms.openlocfilehash: 7cc902a60a68f9cb667530dac76812d4a8e082be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168772"
---
# <a name="ltvalarraygt"></a>&lt;valarray&gt;

Définit le modèle de classe valarray et de nombreux modèles de classe et fonctions de prise en charge.

## <a name="requirements"></a>Spécifications

**En-tête :**\<valarray>

**Espace de noms :** std

> [!NOTE]
> La \<valarray> bibliothèque utilise l’instruction « #include <initializer_list> ».

## <a name="remarks"></a>Notes

Ces modèles de classe et fonctions sont autorisés une latitude inhabituelle dans l’intérêt d’une amélioration des performances. Plus précisément, toute fonction `valarray<T1>` qui retourne un type peut retourner un objet d’un autre type T2. Dans ce cas, toute fonction qui accepte un ou plusieurs arguments de type `valarray<T2>` doit avoir des surcharges qui acceptent des combinaisons arbitraires de ces arguments, chacune remplacée par un argument de type T2.

## <a name="members"></a>Membres

### <a name="functions"></a>Fonctions

|Nom|Description|
|-|-|
|[absolue](../standard-library/valarray-functions.md#abs)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à la valeur absolue des éléments du valarray d'entrée.|
|[ACOS](../standard-library/valarray-functions.md#acos)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à l'arccosinus des éléments du valarray d'entrée.|
|[ASIN](../standard-library/valarray-functions.md#asin)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à l'arcsinus des éléments du valarray d'entrée.|
|[atan](../standard-library/valarray-functions.md#atan)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à la valeur principale de l'arctangente des éléments du valarray d'entrée.|
|[atan2](../standard-library/valarray-functions.md#atan2)|Retourne un valarray dont les éléments sont égaux à l'arctangente des composants cartésiens spécifiés par une combinaison de constantes et d'éléments de valarrays.|
|[commencer](../standard-library/valarray-functions.md#begin)||
|[COS](../standard-library/valarray-functions.md#cos)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux au cosinus des éléments du valarray d'entrée.|
|[cosh](../standard-library/valarray-functions.md#cosh)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux au cosinus hyperbolique des éléments du valarray d'entrée.|
|[end](../standard-library/valarray-functions.md#end)||
|[exp](../standard-library/valarray-functions.md#exp)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à l'exponentiel naturel des éléments du valarray d'entrée.|
|[Sign](../standard-library/valarray-functions.md#log)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux au logarithme naturel des éléments du valarray d'entrée.|
|[log10](../standard-library/valarray-functions.md#log10)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux au logarithme commun ou en base 10 des éléments du valarray d'entrée.|
|[Poe](../standard-library/valarray-functions.md#pow)|Opère sur les éléments des constantes et valarrays d'entrée, retournant un valarray dont les éléments sont égaux à une base spécifiée soit par les éléments d'un valarray d'entrée, soit par une constante élevée à une puissance spécifiée par les éléments d'un valarray d'entrée ou une constante.|
|[Sin](../standard-library/valarray-functions.md#sin)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux au sinus des éléments du valarray d'entrée.|
|[Sinh](../standard-library/valarray-functions.md#sinh)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux au sinus hyperbolique des éléments du valarray d'entrée.|
|[racine](../standard-library/valarray-functions.md#sqrt)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à la racine carrée des éléments du valarray d'entrée.|
|[swap](../standard-library/valarray-functions.md#swap)||
|[Tan](../standard-library/valarray-functions.md#tan)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à la tangente des éléments du valarray d'entrée.|
|[Tanh](../standard-library/valarray-functions.md#tanh)|Opère sur les éléments d'un valarray d'entrée, en retournant un valarray dont les éléments sont égaux à la tangente hyperbolique des éléments du valarray d'entrée.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur ! =](../standard-library/valarray-operators.md#op_neq)|Teste si les éléments correspondants de deux valarrays de taille égale sont inégaux ou si tous les éléments d'un valarray sont inégaux à une valeur spécifiée du type d'élément du valarray.|
|[and](../standard-library/valarray-operators.md#op_mod)|Obtient le reste de la division des éléments correspondants de deux valarrays de taille égale ou de la division d'un valarray par une valeur spécifiée du type d'élément du valarray ou de la division d'une valeur spécifiée par un valarray.|
|[&d’opérateur ](../standard-library/valarray-operators.md#op_amp)|Obtient le résultat de l'opération `AND` binaire entre des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément.|
|[&&d’opérateur ](../standard-library/valarray-operators.md#op_amp_amp)|Obtient le résultat de l'opération `AND` logique entre des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément du valarray.|
|[>d’opérateur ](../standard-library/valarray-operators.md#op_gt)|Teste si les éléments d'un valarray sont supérieurs aux éléments d'un valarray de taille égale ou si tous les éléments d'un valarray sont supérieurs ou inférieurs à une valeur spécifiée du type d'élément du valarray.|
|[>opérateur =](../standard-library/valarray-operators.md#op_gt_eq)|Teste si les éléments d'un valarray sont supérieurs ou égaux aux éléments d'un valarray de taille égale ou si tous les éléments d'un valarray sont supérieurs ou égaux à, ou inférieurs ou égaux à, une valeur spécifiée.|
|[>>d’opérateur ](../standard-library/valarray-operators.md#op_gt_gt)|Décale vers la droite les bits de chaque élément d'un valarray d'un nombre spécifié de positions ou d'une quantité d'éléments spécifiée par un deuxième valarray.|
|[<d’opérateur ](../standard-library/valarray-operators.md#op_lt)|Teste si les éléments d'un valarray sont inférieurs aux éléments d'un valarray de taille égale ou si tous les éléments d'un valarray sont supérieurs ou inférieurs à une valeur spécifiée.|
|[<opérateur =](../standard-library/valarray-operators.md#op_lt_eq)|Teste si les éléments d'un valarray sont inférieurs ou égaux aux éléments d'un valarray de taille égale ou si tous les éléments d'un valarray sont supérieurs ou égaux à, ou inférieurs ou égaux à, une valeur spécifiée.|
|[<<d’opérateur ](../standard-library/valarray-operators.md#op_lt_lt)|Décale vers la gauche les bits de chaque élément d'un valarray d'un nombre spécifié de positions ou d'une quantité d'éléments spécifiée par un deuxième valarray.|
|[and](../standard-library/valarray-operators.md#op_star)|Obtient le produit entre des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément du valarray.|
|[opérateur +](../standard-library/valarray-operators.md#op_add)|Obtient la somme des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément du valarray.|
|[and](../standard-library/valarray-operators.md#operator-)|Obtient la différence entre des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément du valarray.|
|[and](../standard-library/valarray-operators.md#op_div)|Obtient le quotient entre des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément du valarray.|
|[opérateur = =](../standard-library/valarray-operators.md#op_eq_eq)|Teste si les éléments correspondants de deux valarrays de taille égale sont égaux ou si tous les éléments d'un valarray sont égaux à une valeur spécifiée du type d'élément du valarray.|
|[opérateur ^](../standard-library/valarray-operators.md#op_xor)|Obtient le résultat de l'opération `OR` exclusif binaire entre des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément.|
|[&#124;d’opérateur ](../standard-library/valarray-operators.md#op_or)|Obtient le résultat de l'opération `OR` binaire entre des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément.|
|[&#124;&#124;d’opérateur ](../standard-library/valarray-operators.md#op_lor)|Obtient le résultat de l'opération `OR` logique entre des éléments correspondants de deux valarrays de taille égale ou entre un valarray et une valeur spécifiée du type d'élément du valarray.|

### <a name="classes"></a>Classes

|Nom|Description|
|-|-|
|[GSlice, classe](../standard-library/gslice-class.md)|Classe utilitaire de valarray qui sert à définir des secteurs multidimensionnels d'un valarray.|
|[Classe gslice_array](../standard-library/gslice-array-class.md)|Modèle de classe auxiliaire interne qui prend en charge les objets de tranche généraux en fournissant des opérations entre les tableaux de sous-ensembles définis par le secteur général d’un valarray.|
|[Classe indirect_array](../standard-library/indirect-array-class.md)|Modèle de classe auxiliaire interne qui prend en charge les objets qui sont des sous-ensembles de valarrays en fournissant des opérations entre les tableaux de sous-ensembles définis en spécifiant un sous-ensemble d’index d’un valarray parent.|
|[Classe mask_array](../standard-library/mask-array-class.md)|Modèle de classe auxiliaire interne qui prend en charge les objets qui sont des sous-ensembles de valarrays parents, spécifiés avec une expression booléenne, en fournissant des opérations entre les tableaux de sous-ensembles.|
|[Slice, classe](../standard-library/slice-class.md)|Classe utilitaire de valarray qui sert à définir des sous-ensembles vectoriels unidimensionnels d'un valarray parent.|
|[Classe slice_array](../standard-library/slice-array-class.md)|Modèle de classe auxiliaire interne qui prend en charge les objets Slice en fournissant des opérations entre les tableaux de sous-ensembles définis par le secteur d’un valarray.|
|[valarray, classe](../standard-library/valarray-class.md)|Le modèle de classe décrit un objet qui contrôle une séquence d’éléments de type `Type` qui sont stockés sous forme de tableau et conçus pour effectuer des opérations mathématiques à grande vitesse, optimisées pour les performances de calcul.|

### <a name="specializations"></a>Spécialisations

|Nom|Description|
|-|-|
|[valarray, \<bool> classe](../standard-library/valarray-bool-class.md)|Une version spécialisée du modèle de classe valarray \<**Type**> aux éléments de type **`bool`** .|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
