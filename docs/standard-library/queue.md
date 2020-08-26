---
title: '&lt;queue&gt;'
ms.date: 11/04/2016
f1_keywords:
- <queue>
helpviewer_keywords:
- queue header
ms.assetid: 24fcf350-eb0e-48cf-9fef-978be1aeda1f
ms.openlocfilehash: a41d34b45264472a5c8c88ca0619e78444dd8aec
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832592"
---
# <a name="ltqueuegt"></a>&lt;queue&gt;

Définit les modèles de classe priority_queue et file d’attente, ainsi que plusieurs modèles de prise en charge.

## <a name="requirements"></a>Configuration requise

**En-tête :**\<queue>

**Espace de noms :** std

> [!NOTE]
> La \<queue> bibliothèque utilise également l' `#include <initializer_list>` instruction.

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur ! =](../standard-library/queue-operators.md#op_neq)|Teste si l'objet de file d'attente situé à gauche de l'opérateur n'est pas égal à l'objet de file d'attente situé à droite.|
|[<d’opérateur ](../standard-library/queue-operators.md#op_lt)|Teste si l'objet de file d'attente situé à gauche de l'opérateur est inférieur à l'objet de file d'attente situé à droite.|
|[and\<=](../standard-library/queue-operators.md#op_gt_eq)|Teste si l'objet de file d'attente situé à gauche de l'opérateur est inférieur ou égal à l'objet de file d'attente situé à droite.|
|[opérateur = =](../standard-library/queue-operators.md#op_eq_eq)|Teste si l'objet de file d'attente situé à gauche de l'opérateur est égal à l'objet de file d'attente situé à droite.|
|[>d’opérateur ](../standard-library/queue-operators.md#op_gt)|Teste si l'objet de file d'attente situé à gauche de l'opérateur est supérieur à l'objet de file d'attente situé à droite.|
|[>opérateur =](../standard-library/queue-operators.md#op_gt_eq)|Teste si l'objet de file d'attente situé à gauche de l'opérateur est supérieur ou égal à l'objet de file d'attente situé à droite.|

### <a name="classes"></a>Classes

|Nom|Description|
|-|-|
|[queue, classe](../standard-library/queue-class.md)|Classe d'adaptateur de conteneur de modèle qui fournit une restriction de fonctionnalité limitant l'accès aux premier et dernier éléments d'un certain type de conteneur sous-jacent.|
|[Classe priority_queue](../standard-library/priority-queue-class.md)|Classe d'adaptateur de conteneur de modèle qui fournit une restriction de fonctionnalité limitant l'accès à l'élément supérieur d'un certain type de conteneur sous-jacent, qui est toujours le plus grand.|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
