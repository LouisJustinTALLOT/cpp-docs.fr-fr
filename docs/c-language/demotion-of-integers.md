---
title: Rétrogradation des entiers | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49177e7df11c0c7c4d7fefb201035ce12c5242af
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087524"
---
# <a name="demotion-of-integers"></a>Rétrogradation des entiers

**ANSI 3.2.1.2** Le résultat de la conversion d’un entier en un entier signé plus court, ou le résultat de la conversion d’un entier non signé en entier signé de longueur égale si la valeur ne peut pas être représentée

Lorsqu’un entier **long** est casté en un **short** ou qu’un **short** est casté en un `char`, les octets moins significatifs sont conservés.

Par exemple, cette ligne

```
short x = (short)0x12345678L;
```

assigne la valeur 0x5678 à `x`, et cette ligne

```
char y = (char)0x1234;
```

assigne la valeur 0x34 à `y`.

Lorsque des variables signées sont converties en variables non signées et vice versa, les modèles binaires restent les mêmes. Par exemple, le cast de -2 (0xFE) en une valeur non signée produit 254 (également 0xFE).

## <a name="see-also"></a>Voir aussi

[Entiers](../c-language/integers.md)