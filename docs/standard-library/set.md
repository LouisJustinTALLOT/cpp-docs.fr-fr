---
title: '&lt;set&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <set>
dev_langs:
- C++
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aacfbda591755af86857da6c7d0b7891d2e72ebb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
---
# <a name="ltsetgt"></a>&lt;set&gt;

Définit les classes de modèle de conteneur set et multiset et leurs modèles de prise en charge.

## <a name="syntax"></a>Syntaxe

```cpp
#include <set>

```

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|Version set|Version multiset|Description|
|-----------------|----------------------|-----------------|
|[operator!= (set)](../standard-library/set-operators.md#op_neq)|[operator!= (multiset)](../standard-library/set-operators.md#op_neq)|Teste si l'objet set ou multiset situé à gauche de l'opérateur n'est pas égal à l'objet set ou multiset situé à droite.|
|[operator< (set)](../standard-library/set-operators.md#op_lt)|[operator< (multiset)](../standard-library/set-operators.md#op_lt_multiset)|Teste si l'objet set ou multiset situé à gauche de l'opérateur est inférieur à l'objet set ou multiset situé à droite.|
|[operator<= (set)](../standard-library/set-operators.md#op_lt_eq)|[operator\<= (multiset)](../standard-library/set-operators.md#op_lt_eq_multiset)|Teste si l'objet set ou multiset situé à gauche de l'opérateur est inférieur ou égal à l'objet set ou multiset situé à droite.|
|[operator== (set)](../standard-library/set-operators.md#op_eq_eq)|[operator== (multiset)](../standard-library/set-operators.md#op_eq_eq_multiset)|Teste si l'objet set ou multiset situé à gauche de l'opérateur est égal à l'objet set ou multiset situé à droite.|
|[operator> (set)](../standard-library/set-operators.md#op_gt)|[operator> (multiset)](../standard-library/set-operators.md#op_gt_multiset)|Teste si l'objet set ou multiset situé à gauche de l'opérateur est supérieur à l'objet set ou multiset situé à droite.|
|[operator>= (set)](../standard-library/set-operators.md#op_gt_eq)|[operator>= (multiset)](../standard-library/set-operators.md#op_gt_eq_multiset)|Teste si l'objet set ou multiset situé à gauche de l'opérateur est supérieur ou égal à l'objet set ou multiset situé à droite.|

### <a name="specialized-template-functions"></a>Fonctions avec modèle spécialisé

|Version set|Version multiset|Description|
|-----------------|----------------------|-----------------|
|[swap](../standard-library/set-functions.md#swap)|[swap (multiset)](../standard-library/set-functions.md#swap_multiset)|Échange les éléments de deux classes set ou multiset.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[set, classe](../standard-library/set-class.md)|Sert au stockage et à la récupération des données d’une collection dans laquelle les valeurs des éléments contenus sont uniques et servent de valeurs de clés en fonction desquelles les données sont automatiquement triées.|
|[multiset, classe](../standard-library/multiset-class.md)|Sert au stockage et à la récupération des données d’une collection dans laquelle les valeurs des éléments contenus n’ont pas besoin d’être uniques et servent de valeurs de clés en fonction desquelles les données sont automatiquement triées.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
