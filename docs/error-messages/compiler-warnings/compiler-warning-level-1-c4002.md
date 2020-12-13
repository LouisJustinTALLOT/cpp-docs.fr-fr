---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4002'
title: Avertissement du compilateur (niveau 1) C4002
ms.date: 11/04/2016
f1_keywords:
- C4002
helpviewer_keywords:
- C4002
ms.assetid: 6bda1dfe-e2e4-4771-9794-5a404c466dd5
ms.openlocfilehash: 5a0150c10e6a80604b97528dcedfc15b2cf4d0e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336010"
---
# <a name="compiler-warning-level-1-c4002"></a>Avertissement du compilateur (niveau 1) C4002

trop de paramètres réels pour la macro 'identifier'

Le nombre de paramètres réels dans la macro dépasse le nombre de paramètres formels dans la définition de macro. Le préprocesseur collecte les paramètres supplémentaires mais les ignore pendant l’expansion macro.

L’avertissement C4002 peut se produire en cas d’utilisation incorrecte de [Variadic Macros](../../preprocessor/variadic-macros.md).

L’exemple suivant génère l’avertissement C4002 :

```cpp
// C4002.cpp
// compile with: /W1
#define test(a) (a)

int main() {
   int a = 1;
   int b = 2;
   a = test(a,b);   // C4002
   // try..
   a = test(a);
}
```

Cette erreur peut également être générée en raison de la mise en conformité du compilateur pour Visual Studio .NET 2003 : les virgules superflues dans la macro ne sont plus acceptées.

Le compilateur n’accepte plus les virgules superflues dans une macro. Pour que le code soit valide dans les versions Visual Studio .NET 2003 et Visual Studio .NET de Visual C++, supprimez les virgules superflues.

```cpp
// C4002b.cpp
// compile with: /W1
#define F(x,y)
int main()
{
   F(2,,,,,,3,,,,,,)   // C4002
   // Try the following line instead:
   // F(2,3)
}
```
