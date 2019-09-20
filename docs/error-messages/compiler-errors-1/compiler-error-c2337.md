---
title: Erreur du compilateur C2337
ms.date: 09/19/2019
f1_keywords:
- C2337
helpviewer_keywords:
- C2337
ms.assetid: eccc9178-a15e-42cd-bbd0-3cea7cf2d55b
ms.openlocfilehash: bf9b3e782804add13aeaef0e6672d2dd66d193be
ms.sourcegitcommit: f907b15f50a6b945d0b87c03af0050946157d701
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71158775"
---
# <a name="compiler-error-c2337"></a>Erreur du compilateur C2337

> '*attribute-name*' : attribut introuvable

Votre code utilise un attribut qui n’est pas pris en charge dans ce contexte. Ou bien, l’attribut n’est pas disponible dans cette version du compilateur. Pour résoudre ce problème, supprimez l’attribut non pris en charge.

L’exemple suivant génère l’erreur C2337 :

```cpp
// C2337.cpp
// compile with: /c
[emitidl];
[module(name="x")];
[grasshopper]   // C2337, not a supported attribute
class a{};
```
