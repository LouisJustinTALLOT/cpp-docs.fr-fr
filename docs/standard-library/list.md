---
title: '&lt;liste&gt;'
ms.date: 11/04/2016
f1_keywords:
- <list>
- std::<list>
helpviewer_keywords:
- list header
ms.assetid: 2345823b-5612-44d8-95d3-aa96ed076d17
ms.openlocfilehash: 8eb497e6a4380affd0f13f41c7b55990c562b7d3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453656"
---
# <a name="ltlistgt"></a>&lt;liste&gt;

Définit la classe de modèle de conteneur list et plusieurs modèles de prise en charge.

## <a name="syntax"></a>Syntaxe

```cpp
#include <list>
```

> [!NOTE]
> La \<bibliothèque de listes > utilise également `#include <initializer_list>` l’instruction.

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[!=, opérateur](../standard-library/list-operators.md#op_neq)|Teste si l'objet de liste situé à gauche de l'opérateur n'est pas égal à l'objet de liste situé à droite.|
|[operator<](../standard-library/list-operators.md#op_lt)|Teste si l'objet de liste situé à gauche de l'opérateur est inférieur à l'objet de liste situé à droite.|
|[operator\<=](../standard-library/list-operators.md#op_gt_eq)|Teste si l'objet de liste situé à gauche de l'opérateur est inférieur ou égal à l'objet de liste situé à droite.|
|[operator==](../standard-library/list-operators.md#op_eq_eq)|Teste si l'objet de liste situé à gauche de l'opérateur est égal à l'objet de liste situé à droite.|
|[operator>](../standard-library/list-operators.md#op_gt)|Teste si l'objet de liste situé à gauche de l'opérateur est supérieur à l'objet de liste situé à droite.|
|[operator>=](../standard-library/list-operators.md#op_gt_eq)|Teste si l'objet de liste situé à gauche de l'opérateur est supérieur ou égal à l'objet de liste situé à droite.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[swap](../standard-library/list-functions.md#swap)|Échange les éléments de deux listes.|

### <a name="classes"></a>Classes

|||
|-|-|
|[list, classe](../standard-library/list-class.md)|Classe de modèle de conteneurs de séquences. Ces derniers conservent leurs éléments dans une disposition linéaire, et permettent des insertions et des suppressions efficaces à n'importe quel emplacement de la séquence.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
