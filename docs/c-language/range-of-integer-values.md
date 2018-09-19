---
title: Plage de valeurs entières | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 0e9c6161-8f3f-4bfb-9fcc-a6c8dc97d702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d940824e6bb1dc728cb999c1e820cb7adcedf8ce
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092646"
---
# <a name="range-of-integer-values"></a>Plage des valeurs entières

**ANSI 3.1.2.5** Représentations et jeux de valeurs des différents types d’entiers

Les entiers contiennent 32 bits (quatre octets). Les entiers signés sont représentés sous la forme d'un complément à deux. Le bit le plus significatif indique le signe : 1 pour les nombres négatifs, 0 pour les nombres positifs et zéro. Les valeurs sont répertoriées ci-dessous :

|Type|Minimum et maximum|
|----------|-------------------------|
|**unsigned short**|de 0 à 65535|
|`signed short`|de -32768 à 32767|
|`unsigned long`|de 0 à 4294967295|
|**signed long**|de -2147483648 à 2147483647|

## <a name="see-also"></a>Voir aussi

[Entiers](../c-language/integers.md)