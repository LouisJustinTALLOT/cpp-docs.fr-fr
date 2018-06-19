---
title: '&lt;utility&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <utility>
dev_langs:
- C++
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84464f485d39f1146f55fb6b5b1970cf1c9321df
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858131"
---
# <a name="ltutilitygt"></a>&lt;utility&gt;

Définit des types, des fonctions et des opérateurs de la bibliothèque standard C++ qui aident à construire et à gérer des paires d’objets qui sont utiles quand deux objets doivent être traités comme s’ils n’en étaient qu’un seul.

## <a name="syntax"></a>Syntaxe

```cpp
#include <utility>

```

## <a name="remarks"></a>Notes

Les paires sont largement utilisées dans la bibliothèque standard C++. Elles sont nécessaires comme arguments et valeurs de retour pour diverses fonctions et comme types d’éléments pour des conteneurs tels que la [classe map](../standard-library/map-class.md) et la [classe multimap](../standard-library/multimap-class.md). L’en-tête \<utility> est inclus automatiquement par \<map> pour aider à gérer leurs éléments de type paire clé/valeur.

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|Classe qui encapsule le type d'un élément `pair`.|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|Classe qui encapsule le nombre d'éléments `pair`.|

### <a name="functions"></a>Fonctions

|Fonction|Description|
|-|-|
|[forward](../standard-library/utility-functions.md#forward)|Empêche que le type de référence (`lvalue` ou `rvalue`) de l'argument ne soit masqué par le transfert parfait.|
|[get](../standard-library/utility-functions.md#get)|Fonction qui obtient un élément d'un objet `pair`.|
|[make_pair](../standard-library/utility-functions.md#make_pair)|Fonction d'assistance de modèle qui sert à construire des objets de type `pair`, où les types de composants sont basés sur les types de données passés comme paramètres.|
|[move](../standard-library/utility-functions.md#move)|Retourne l'argument passé comme référence `rvalue`.|
|[swap](../standard-library/utility-functions.md#swap)|Échange les éléments de deux objets `pair`.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator!=](../standard-library/utility-operators.md#op_neq)|Teste si l'objet pair situé à gauche de l'opérateur n'est pas égal à l'objet pair situé à droite.|
|[operator==](../standard-library/utility-operators.md#op_eq_eq)|Teste si l'objet pair situé à gauche de l'opérateur est égal à l'objet pair situé à droite.|
|[operator<](../standard-library/utility-operators.md#op_lt)|Teste si l'objet pair situé à gauche de l'opérateur est inférieur à l'objet pair situé à droite.|
|[operator\<=](../standard-library/utility-operators.md#op_gt_eq)|Teste si l'objet pair situé à gauche de l'opérateur est inférieur ou égal à l'objet pair situé à droite.|
|[operator>](../standard-library/utility-operators.md#op_gt)|Teste si l'objet pair situé à gauche de l'opérateur est supérieur à l'objet pair situé à droite.|
|[operator>=](../standard-library/utility-operators.md#op_gt_eq)|Teste si l'objet pair situé à gauche de l'opérateur est supérieur ou égal à l'objet pair situé à droite.|

### <a name="structs"></a>Structs

|||
|-|-|
|[identity](../standard-library/identity-structure.md)||
|[pair](../standard-library/pair-structure.md)|Struct qui permet de traiter deux objets comme s'il s'agissait d'un objet unique.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
