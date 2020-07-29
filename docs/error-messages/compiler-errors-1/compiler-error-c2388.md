---
title: Erreur du compilateur C2388
ms.date: 11/04/2016
f1_keywords:
- C2388
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
ms.openlocfilehash: 50148f4fb5c3af33d8de8b005f75f491b0540271
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225499"
---
# <a name="compiler-error-c2388"></a>Erreur du compilateur C2388

'Symbol' : un symbole ne peut pas être déclaré avec __declspec (AppDomain) et \_ _declspec (processus)

Les `appdomain` `process` **`__declspec`** modificateurs et ne peuvent pas être utilisés sur le même symbole. Le stockage d’une variable existe par processus ou par domaine d’application.

Pour plus d’informations, consultez [appdomain](../../cpp/appdomain.md) et [process](../../cpp/process.md).

L’exemple suivant génère l’erreur C2388 :

```cpp
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```
