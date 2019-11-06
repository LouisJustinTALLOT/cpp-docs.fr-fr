---
title: Avertissement du compilateur (niveau 1) C4286
ms.date: 11/04/2016
f1_keywords:
- C4286
helpviewer_keywords:
- C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
ms.openlocfilehash: ed2e6c10e35e53c6a67de9fecfce5da5ae429b93
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626669"
---
# <a name="compiler-warning-level-1-c4286"></a>Avertissement du compilateur (niveau 1) C4286

'type1 ' : intercepté par la classe de base ('type2 ') sur le numéro de ligne

Le type d’exception spécifié est géré par un gestionnaire précédent. Le type de la deuxième interception est dérivé du type de la première. Les exceptions pour une classe de base interceptent des exceptions pour une classe dérivée.

## <a name="example"></a>Exemple

```cpp
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