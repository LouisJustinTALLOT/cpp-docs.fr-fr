---
title: Compilateur avertissement (niveau 1) C4229 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4229
dev_langs:
- C++
helpviewer_keywords:
- C4229
ms.assetid: aadfc83b-1e5f-4229-bd0a-9c10a5d13182
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e485f4e49859a12b17eac5dd378853bb3795bd7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064040"
---
# <a name="compiler-warning-level-1-c4229"></a>Avertissement du compilateur (niveau 1) C4229

anachronisme utilisé : modificateurs de données sont ignorés.

À l’aide d’un modificateur Microsoft tel que `__cdecl` sur des données déclaration est une pratique obsolète.

## <a name="example"></a>Exemple

```
// C4229.cpp
// compile with: /W1 /LD
int __cdecl counter;   // C4229 cdecl ignored
```