---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4702'
title: Avertissement du compilateur (niveau 4) C4702
ms.date: 11/04/2016
f1_keywords:
- C4702
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
ms.openlocfilehash: 9a171641a2c923083471d510e27fbdb3ebd08832
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133794"
---
# <a name="compiler-warning-level-4-c4702"></a>Avertissement du compilateur (niveau 4) C4702

code inaccessible

Cet avertissement est le résultat du travail de conformité du compilateur pour Visual Studio .NET 2003 : code inaccessible. Lorsque le compilateur (back end) détecte un code inaccessible, il génère C4702, un avertissement de niveau 4.

Pour le code qui est valide dans les versions Visual Studio .NET 2003 et Visual Studio .NET de Visual C++, supprimez le code inaccessible ou assurez-vous que tout le code source est accessible par un workflow d’exécution.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C4702.

```cpp
// C4702.cpp
// compile with: /W4
#include <stdio.h>

int main() {
   return 1;
   printf_s("I won't print.\n");   // C4702 unreachable
}
```

Lors de la compilation avec **/GX**, **/EHC**, **/EHsc** ou **/EHac** et à l’aide de fonctions c extern, le code peut devenir inaccessible car les fonctions c externes sont supposées ne pas lever, donc le bloc catch n’est pas accessible.  Si vous estimez que cet avertissement n’est pas valide, car une fonction peut lever une exception, compilez avec **/EHa** ou **/EHS**, en fonction de l’exception levée.

Pour plus d’informations, consultez [/Eh (modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md) .

L’exemple suivant génère l’C4702.

```cpp
// C4702b.cpp
// compile with: /W4 /EHsc
#include <iostream>

using namespace std;
extern "C" __declspec(dllexport) void Function2(){}

int main() {
   try {
      Function2();
   }
   catch (...) {
      cout << "Exp: Function2!" << endl;   // C4702
   }
}
```
