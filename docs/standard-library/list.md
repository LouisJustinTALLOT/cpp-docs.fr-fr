---
title: '&lt;liste&gt;'
ms.date: 11/04/2016
f1_keywords:
- <list>
- std::<list>
helpviewer_keywords:
- list header
ms.assetid: 2345823b-5612-44d8-95d3-aa96ed076d17
ms.openlocfilehash: f2c04bb73bfa379ea87ba4c950bf805931c16ba1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245564"
---
# <a name="ltlistgt"></a>&lt;liste&gt;

Définit la classe de modèle de conteneur list et plusieurs modèles de prise en charge.

## <a name="syntax"></a>Syntaxe

```cpp
#include <list>
```

> [!NOTE]
> Le \<liste > bibliothèque utilise également la `#include <initializer_list>` instruction.

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

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
