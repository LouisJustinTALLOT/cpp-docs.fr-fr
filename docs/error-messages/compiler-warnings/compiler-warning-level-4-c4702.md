---
title: Avertissement du compilateur (niveau 4) C4702
ms.date: 11/04/2016
f1_keywords:
- C4702
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
ms.openlocfilehash: 96ae3a0742db5e3a5006f031ce62beb281c38ccd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395246"
---
# <a name="compiler-warning-level-4-c4702"></a>Avertissement du compilateur (niveau 4) C4702

code inaccessible

Cet avertissement est le résultat du travail de mise en conformité du compilateur pour Visual Studio .NET 2003 : code inaccessible. Lorsque le compilateur (back-end) détecte un code inaccessible, il génère C4702, un avertissement de niveau 4.

Pour le code qui est valide dans les versions de Visual Studio .NET 2003 et de Visual Studio .NET de Visual C++, supprimez le code inaccessible ou assurez-vous que tout le code source est accessible par un flux d’exécution.

## <a name="example"></a>Exemple

L’exemple suivant génère C4702.

```
// C4702.cpp
// compile with: /W4
#include <stdio.h>

int main() {
   return 1;
   printf_s("I won't print.\n");   // C4702 unreachable
}
```

## <a name="example"></a>Exemple

Lors de la compilation avec **/GX**, **/EHc**, **/EHsc**, ou **/EHac** et à l’aide de fonctions C extern, code peut devenir inaccessible, car extern C les fonctions sont supposées ne pas lever, par conséquent, le bloc catch n’est pas accessible.  Si vous estimez que cet avertissement n’est pas valide, car une fonction peut lever une exception, compilez avec **/EHa** ou **/EHs**, en fonction de l’exception levée.

Pour plus d’informations, consultez [/EH (modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md) pour plus d’informations.

L’exemple suivant génère C4702.

```
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