---
title: '&lt;queue&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <queue>
dev_langs:
- C++
helpviewer_keywords:
- queue header
ms.assetid: 24fcf350-eb0e-48cf-9fef-978be1aeda1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ba139e2b50f1dd7c9887701a522a002173c21ee
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
---
# <a name="ltqueuegt"></a>&lt;queue&gt;

Définit les classes de modèle priority_queue et queue et plusieurs modèles de prise en charge.

## <a name="syntax"></a>Syntaxe

```cpp
#include <queue>

```

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator!=](../standard-library/queue-operators.md#op_neq)|Teste si l'objet de file d'attente situé à gauche de l'opérateur n'est pas égal à l'objet de file d'attente situé à droite.|
|[operator<](../standard-library/queue-operators.md#op_lt)|Teste si l'objet de file d'attente situé à gauche de l'opérateur est inférieur à l'objet de file d'attente situé à droite.|
|[operator\<=](../standard-library/queue-operators.md#op_gt_eq)|Teste si l'objet de file d'attente situé à gauche de l'opérateur est inférieur ou égal à l'objet de file d'attente situé à droite.|
|[operator==](../standard-library/queue-operators.md#op_eq_eq)|Teste si l'objet de file d'attente situé à gauche de l'opérateur est égal à l'objet de file d'attente situé à droite.|
|[operator>](../standard-library/queue-operators.md#op_gt)|Teste si l'objet de file d'attente situé à gauche de l'opérateur est supérieur à l'objet de file d'attente situé à droite.|
|[operator>=](../standard-library/queue-operators.md#op_gt_eq)|Teste si l'objet de file d'attente situé à gauche de l'opérateur est supérieur ou égal à l'objet de file d'attente situé à droite.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[queue, classe](../standard-library/queue-class.md)|Classe d'adaptateur de conteneur de modèle qui fournit une restriction de fonctionnalité limitant l'accès aux premier et dernier éléments d'un certain type de conteneur sous-jacent.|
|[priority_queue, classe](../standard-library/priority-queue-class.md)|Classe d'adaptateur de conteneur de modèle qui fournit une restriction de fonctionnalité limitant l'accès à l'élément supérieur d'un certain type de conteneur sous-jacent, qui est toujours le plus grand.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
