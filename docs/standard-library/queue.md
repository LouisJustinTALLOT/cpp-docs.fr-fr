---
title: '&lt;queue&gt;'
ms.date: 11/04/2016
f1_keywords:
- <queue>
helpviewer_keywords:
- queue header
ms.assetid: 24fcf350-eb0e-48cf-9fef-978be1aeda1f
ms.openlocfilehash: d7a13b98ba8cff78839b2afb98371ffba5ced461
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458337"
---
# <a name="ltqueuegt"></a>&lt;queue&gt;

Définit les classes de modèle priority_queue et queue et plusieurs modèles de prise en charge.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<queue>

**Espace de noms :** std

> [!NOTE]
> La \<bibliothèque de > de file d' `#include <initializer_list>` attente utilise également l’instruction.

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[!=, opérateur](../standard-library/queue-operators.md#op_neq)|Teste si l'objet de file d'attente situé à gauche de l'opérateur n'est pas égal à l'objet de file d'attente situé à droite.|
|[operator<](../standard-library/queue-operators.md#op_lt)|Teste si l'objet de file d'attente situé à gauche de l'opérateur est inférieur à l'objet de file d'attente situé à droite.|
|[operator\<=](../standard-library/queue-operators.md#op_gt_eq)|Teste si l'objet de file d'attente situé à gauche de l'opérateur est inférieur ou égal à l'objet de file d'attente situé à droite.|
|[operator==](../standard-library/queue-operators.md#op_eq_eq)|Teste si l'objet de file d'attente situé à gauche de l'opérateur est égal à l'objet de file d'attente situé à droite.|
|[operator>](../standard-library/queue-operators.md#op_gt)|Teste si l'objet de file d'attente situé à gauche de l'opérateur est supérieur à l'objet de file d'attente situé à droite.|
|[operator>=](../standard-library/queue-operators.md#op_gt_eq)|Teste si l'objet de file d'attente situé à gauche de l'opérateur est supérieur ou égal à l'objet de file d'attente situé à droite.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[swap]()||

### <a name="classes"></a>Classes

|||
|-|-|
|[queue, classe](../standard-library/queue-class.md)|Classe d'adaptateur de conteneur de modèle qui fournit une restriction de fonctionnalité limitant l'accès aux premier et dernier éléments d'un certain type de conteneur sous-jacent.|
|[priority_queue, classe](../standard-library/priority-queue-class.md)|Classe d'adaptateur de conteneur de modèle qui fournit une restriction de fonctionnalité limitant l'accès à l'élément supérieur d'un certain type de conteneur sous-jacent, qui est toujours le plus grand.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
