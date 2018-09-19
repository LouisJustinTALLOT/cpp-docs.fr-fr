---
title: Opérateurs de bits signés | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 184fd5a0e6c12cb58e9fed759459e7b8172896f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038293"
---
# <a name="signed-bitwise-operations"></a>Opérateurs de bits signés

**ANSI 3.3** Résultats des opérations au niveau du bit sur les entiers signés

Les opérations au niveau du bit sur les entiers signés fonctionnent de la même façon que les opérations au niveau du bit sur les entiers non signés. Par exemple, les valeurs `-16 & 99` peuvent être exprimées au format binaire sous la forme

```
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Le résultat de l'opération de bits AND est 96.

## <a name="see-also"></a>Voir aussi

[Entiers](../c-language/integers.md)