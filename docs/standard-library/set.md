---
title: '&lt;set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <set>
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
ms.openlocfilehash: 4ac5c0bbf94c4d17389efb424d2e12b84717c4a9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846223"
---
# <a name="ltsetgt"></a>&lt;set&gt;

Définit l’ensemble de modèles de classe de conteneur et le multiensemble et leurs modèles de prise en charge.

## <a name="requirements"></a>Configuration requise

**En-tête :**\<set>

**Espace de noms :** std

> [!NOTE]
> La \<set> bibliothèque utilise également l' `#include <initializer_list>` instruction.

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|Version set|Version multiset|Description|
|-|-|-|
|[opérateur ! = (Set)](../standard-library/set-operators.md#op_neq)|[Operator ! = (multiensemble)](../standard-library/set-operators.md#op_neq)|Teste si l'objet set ou multiset situé à gauche de l'opérateur n'est pas égal à l'objet set ou multiset situé à droite.|
|[< d’opérateur (Set)](../standard-library/set-operators.md#op_lt)|[< d’opérateur (multijeu)](../standard-library/set-operators.md#op_lt_multiset)|Teste si l'objet set ou multiset situé à gauche de l'opérateur est inférieur à l'objet set ou multiset situé à droite.|
|[<opérateur = (Set)](../standard-library/set-operators.md#op_lt_eq)|[operator\<= (multiset)](../standard-library/set-operators.md#op_lt_eq_multiset)|Teste si l'objet set ou multiset situé à gauche de l'opérateur est inférieur ou égal à l'objet set ou multiset situé à droite.|
|[opérateur = = (Set)](../standard-library/set-operators.md#op_eq_eq)|[opérateur = = (multiensemble)](../standard-library/set-operators.md#op_eq_eq_multiset)|Teste si l'objet set ou multiset situé à gauche de l'opérateur est égal à l'objet set ou multiset situé à droite.|
|[> d’opérateur (Set)](../standard-library/set-operators.md#op_gt)|[> d’opérateur (multijeu)](../standard-library/set-operators.md#op_gt_multiset)|Teste si l'objet set ou multiset situé à gauche de l'opérateur est supérieur à l'objet set ou multiset situé à droite.|
|[>opérateur = (Set)](../standard-library/set-operators.md#op_gt_eq)|[>opérateur = (multiensemble)](../standard-library/set-operators.md#op_gt_eq_multiset)|Teste si l'objet set ou multiset situé à gauche de l'opérateur est supérieur ou égal à l'objet set ou multiset situé à droite.|

### <a name="specialized-template-functions"></a>Fonctions avec modèle spécialisé

|Version set|Version multiset|Description|
|-|-|-|
|[swap](../standard-library/set-functions.md#swap)|[swap (multiset)](../standard-library/set-functions.md#swap_multiset)|Échange les éléments de deux classes set ou multiset.|

### <a name="classes"></a>Classes

|Nom|Description|
|-|-|
|[Set, classe](../standard-library/set-class.md)|Sert au stockage et à la récupération des données d’une collection dans laquelle les valeurs des éléments contenus sont uniques et servent de valeurs de clés en fonction desquelles les données sont automatiquement triées.|
|[multiensemble (classe)](../standard-library/multiset-class.md)|Sert au stockage et à la récupération des données d’une collection dans laquelle les valeurs des éléments contenus n’ont pas besoin d’être uniques et servent de valeurs de clés en fonction desquelles les données sont automatiquement triées.|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
