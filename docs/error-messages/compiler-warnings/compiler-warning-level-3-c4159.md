---
title: Compilateur avertissement (niveau 3) C4159
ms.date: 11/04/2016
f1_keywords:
- C4159
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
ms.openlocfilehash: e898af8f109ed23bd1784df7b39c174bbed675f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552280"
---
# <a name="compiler-warning-level-3-c4159"></a>Compilateur avertissement (niveau 3) C4159

> #<a name="pragma-pragmapop--has-popped-previously-pushed-identifier-identifier"></a>pragma pragma(pop,...) : a exécuté un POP l’identificateur '*identificateur*'

## <a name="remarks"></a>Notes

Votre code source contient un **push** instruction avec un identificateur pour un pragma suivi d’un **pop** instruction sans identificateur. Par conséquent, *identificateur* est la fenêtre et les utilisations de *identificateur* peuvent provoquer un comportement inattendu.

## <a name="example"></a>Exemple

Pour éviter cet avertissement, donnez un identificateur dans le **pop** instruction. Exemple :

```cpp
// C4159.cpp
// compile with: /W3
#pragma pack(push, f)
#pragma pack(pop)   // C4159

// using the identifier resolves the warning
// #pragma pack(pop, f)

int main()
{
}
```