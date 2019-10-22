---
title: '&lt;liste&gt;'
ms.date: 11/04/2016
f1_keywords:
- <list>
- std::<list>
helpviewer_keywords:
- list header
ms.assetid: 2345823b-5612-44d8-95d3-aa96ed076d17
ms.openlocfilehash: c81990f14c6f9dc2400362015b838df5aed86429
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689431"
---
# <a name="ltlistgt"></a>&lt;liste&gt;

Définit la liste de modèles de classe de conteneur et plusieurs modèles de prise en charge.

## <a name="syntax"></a>Syntaxe

```cpp
#include <list>
```

> [!NOTE]
> La bibliothèque de > \<list utilise également l’instruction `#include <initializer_list>`.

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
|[list, classe](../standard-library/list-class.md)|Modèle de classe de conteneurs de séquences qui maintiennent leurs éléments dans une disposition linéaire et permettent des insertions et des suppressions efficaces à n’importe quel emplacement de la séquence.|

## <a name="see-also"></a>Voir aussi

[Référence de fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
