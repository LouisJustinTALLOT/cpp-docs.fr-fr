---
title: '&lt;stack&gt;'
ms.date: 11/04/2016
f1_keywords:
- <stack>
helpviewer_keywords:
- stack, stack header
- stack header
ms.assetid: 89d8999e-c773-46f2-86c1-4b3b5aedb1c1
ms.openlocfilehash: 8a31ccd553638b9b548db89a191da40bc513a05f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453774"
---
# <a name="ltstackgt"></a>&lt;stack&gt;

Définit la pile de classe de modèle et les deux modèles de prise en charge.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<stack>

**Espace de noms :** std

> [!NOTE]
> La \<bibliothèque de > de pile utilise `#include <initializer_list>` également l’instruction.

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[!=, opérateur](../standard-library/stack-operators.md#op_neq)|Teste si l'objet de pile situé à gauche de l'opérateur n'est pas égal à l'objet de pile situé à droite.|
|[operator<](../standard-library/stack-operators.md#op_lt)|Teste si l'objet de pile situé à gauche de l'opérateur est inférieur à l'objet de pile situé à droite.|
|[operator\<=](../standard-library/stack-operators.md#op_lt_eq)|Teste si l'objet de pile situé à gauche de l'opérateur est inférieur ou égal à l'objet de pile situé à droite.|
|[operator==](../standard-library/stack-operators.md#op_eq_eq)|Teste si l'objet de pile situé à gauche de l'opérateur est égal à l'objet de pile situé à droite.|
|[operator>](../standard-library/stack-operators.md#op_gt)|Teste si l'objet de pile situé à gauche de l'opérateur est supérieur à l'objet de pile situé à droite.|
|[operator>=](../standard-library/stack-operators.md#op_gt_eq)|Teste si l'objet de pile situé à gauche de l'opérateur est supérieur ou égal à l'objet de pile situé à droite.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[swap]()||

### <a name="classes"></a>Classes

|||
|-|-|
|[stack, classe](../standard-library/stack-class.md)|Classe d'adaptateur de conteneur modèle qui fournit une restriction des fonctionnalités limitant l'accès à l'élément ajouté le plus récemment pour un type de conteneur sous-jacent.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
