---
title: Avertissement du compilateur (niveau 3) C4839
ms.date: 09/13/2018
f1_keywords:
- C4839
helpviewer_keywords:
- C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
ms.openlocfilehash: 2c238dc16359583bf55f7590d2ce7c0363d66df7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198573"
---
# <a name="compiler-warning-level-3-c4839"></a>Avertissement du compilateur (niveau 3) C4839

> utilisation non standard de la classe'*type*'en tant qu’argument d’une fonction variadiques

Les classes ou les structs passés à une fonction variadiques, comme `printf`, doivent être copiés de manière triviale. Quand de tels objets sont passés, le compilateur effectue simplement une copie au niveau du bit et n’appelle pas le constructeur ou le destructeur.

Cet avertissement est disponible à partir de Visual Studio 2017.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4839 :

```cpp
// C4839.cpp
// compile by using: cl /EHsc /W3 C4839.cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function
}
```

Pour corriger cette erreur, vous pouvez appeler une fonction membre qui retourne un type copiable de manière triviale,

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

Pour les chaînes générées et gérées à l’aide de `CStringW`, le `operator LPCWSTR()` fourni doit être utilisé pour effectuer un cast d’un objet `CStringW` vers le pointeur C attendu par la chaîne de format.

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```
