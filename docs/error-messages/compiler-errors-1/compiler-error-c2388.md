---
title: Erreur du compilateur C2388
ms.date: 11/04/2016
f1_keywords:
- C2388
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
ms.openlocfilehash: 62afcb1fafc19d3d61a86f2fbc10cb99e095afc5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459759"
---
# <a name="compiler-error-c2388"></a>Erreur du compilateur C2388

'symbole' : un symbole ne peut pas être déclaré avec les deux __declspec et \__declspec(process)

Le `appdomain` et `process` `__declspec` les modificateurs ne peuvent pas être utilisés sur le même symbole. Le stockage d’une variable existe par processus ou par domaine d’application.

Pour plus d’informations, consultez [appdomain](../../cpp/appdomain.md) et [process](../../cpp/process.md).

L’exemple suivant génère l’erreur C2388 :

```
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```