---
title: '&lt;bitset&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <bitset>
dev_langs:
- C++
helpviewer_keywords:
- <bitset> header
- bitset header
ms.assetid: af30a9b9-489e-46e3-9d29-5f3ea07ae6dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9294edb0a6b258fff9041c01dc4354e918a8c380
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841632"
---
# <a name="ltbitsetgt"></a>&lt;bitset&gt;

Définit la classe de modèle bitset et deux fonctions de modèle de prise en charge pour la représentation et la manipulation de séquences de bits de taille fixe.

## <a name="syntax"></a>Syntaxe

```

#include <bitset>

```

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator&](../standard-library/bitset-operators.md#op_amp)|Exécute une opération AND au niveau du bit entre deux bitsets.|
|[operator<\<](../standard-library/bitset-operators.md#op_lt_lt)|Insère une représentation textuelle de la séquence de bits dans le flux de sortie standard.|
|[operator>>](../standard-library/bitset-operators.md#op_gt_gt)|Insère une représentation textuelle de la séquence de bits dans le flux d'entrée standard.|
|[operator^](../standard-library/bitset-operators.md#op_xor)|Exécute une opération EXCLUSIVE-OR au niveau du bit entre deux bitsets.|
|[operator&#124;](../standard-library/bitset-operators.md#op_or)|Exécute une opération OR au niveau du bit entre deux bitsets.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[bitset, classe](../standard-library/bitset-class.md)|La classe de modèle décrit un type d'objet qui stocke une séquence composée d'un nombre fixe de bits qui offrent un moyen compact de conserver des indicateurs pour un ensemble d'éléments ou de conditions.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
