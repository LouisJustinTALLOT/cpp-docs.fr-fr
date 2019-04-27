---
title: Avertissement du compilateur (niveau 1) C4286
ms.date: 11/04/2016
f1_keywords:
- C4286
helpviewer_keywords:
- C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
ms.openlocfilehash: be02d330678eaab7f538ed092641f957bdcb01b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207067"
---
# <a name="compiler-warning-level-1-c4286"></a>Avertissement du compilateur (niveau 1) C4286

'type1' : intercepté par la classe de base ('type2') sur le numéro de ligne

Le type d’exception spécifié est géré par un gestionnaire précédent. Le type de la seconde interception est dérivé du type de la première. Exceptions pour une classe de base interceptent des exceptions pour une classe dérivée.

## <a name="example"></a>Exemple

```
//C4286.cpp
// compile with: /W1
#include <eh.h>
class C {};
class D : public  C {};
int main()
{
    try
    {
        throw "ooops!";
    }
    catch( C ) {}
    catch( D ) {}  // warning C4286, D is derived from C
}
```