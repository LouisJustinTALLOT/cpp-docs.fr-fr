---
title: Erreur du compilateur C2506 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2506
dev_langs:
- C++
helpviewer_keywords:
- C2506
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4967c410dfdce781a4191c9ac848883228ba4d3a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093413"
---
# <a name="compiler-error-c2506"></a>Erreur du compilateur C2506

'membre' : '__declspec (modifier)' ne peut pas être appliqué à ce symbole

Vous ne pouvez pas déclarer par processus ou par appdomain pour les membres statiques d’une classe managée.

Pour plus d'informations, voir [appdomain](../../cpp/appdomain.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère C2506.

```
// C2506.cpp
// compile with: /clr /c
ref struct R {
   __declspec(process) static int n;   // C2506
   int o;   // OK
};
```