---
title: Soustraction de pointeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- pointer subtraction
ms.assetid: 4d515690-088a-43f6-bb8c-57b849f7ccf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9756861fd1204a05179ac77dfa648822ed83e5a3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079533"
---
# <a name="pointer-subtraction"></a>Soustraction de pointeur

**ANSI 3.3.6, 4.1.1** Le type d'entier requis pour conserver la différence entre deux pointeurs vers des éléments du même tableau, **ptrdiff_t**

Le typedef `ptrdiff_t` est un `int` sur la plateforme x86 32 bits. Sur les plateformes 64 bits, le typedef `ptrdiff_t` est un `__int64`.

## <a name="see-also"></a>Voir aussi

[Tableaux et pointeurs](../c-language/arrays-and-pointers.md)
