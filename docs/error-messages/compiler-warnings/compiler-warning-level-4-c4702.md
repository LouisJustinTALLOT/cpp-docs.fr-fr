---
title: Avertissement du compilateur (niveau 4) C4702
ms.date: 11/04/2016
f1_keywords:
- C4702
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
ms.openlocfilehash: 5e46bfef925f999ed7f04b5bbe7c88800209ed14
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990647"
---
# <a name="compiler-warning-level-4-c4702"></a>Avertissement du compilateur (niveau 4) C4702

code inaccessible

Cet avertissement est le résultat du travail de conformité du compilateur pour Visual Studio .NET 2003 : code inaccessible. Lorsque le compilateur (back end) détecte un code inaccessible, il génère C4702, un avertissement de niveau 4.

Pour le code qui est valide dans les versions Visual Studio .NET 2003 et Visual Studio .NET de Visual C++, supprimez le code inaccessible ou assurez-vous que tout le code source est accessible par un workflow d’exécution.

## <a name="example"></a>Exemple

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

## <a name="example"></a>Exemple

Lors de la compilation avec **/GX**, **/EHC**, **/EHsc**ou **/EHac** et à l’aide de fonctions c extern, le code peut devenir inaccessible car les fonctions c externes sont supposées ne pas lever, donc le bloc catch n’est pas accessible.  Si vous estimez que cet avertissement n’est pas valide, car une fonction peut lever une exception, compilez avec **/EHa** ou **/EHS**, en fonction de l’exception levée.

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
