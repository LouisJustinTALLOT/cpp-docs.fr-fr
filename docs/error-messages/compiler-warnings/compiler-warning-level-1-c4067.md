---
title: Du compilateur (niveau 1) d’avertissement C4067 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4067
dev_langs:
- C++
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ee6b48327e8754f9388e0df8f43009a5be70c97
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255451"
---
# <a name="compiler-warning-level-1-c4067"></a>Du compilateur (niveau 1) d’avertissement C4067

> jetons inattendus après la directive du préprocesseur - de saut de ligne attendu

## <a name="remarks"></a>Notes

Le compilateur trouvés et ignorés des caractères supplémentaires après une directive de préprocesseur. Cela peut résulter des caractères inattendus, si une cause courante est un point-virgule perdu après la directive. Commentaires ne provoquent pas cet avertissement. Le **/Za** option du compilateur active cet avertissement pour les directives de préprocesseur plus que le paramètre par défaut.

## <a name="example"></a>Exemple

```cpp
// C4067a.cpp
// compile with: cl /EHsc /DX /W1 /Za C4067a.cpp
#include <iostream>
#include <string> s     // C4067
#if defined(X);         // C4067
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif;                 // C4067 only under /Za
int main()
{
    std::cout << s << std::endl;
}
```

Pour résoudre cet avertissement, supprimez les caractères parasites, ou les déplacer dans un bloc de commentaire. Certains avertissements C4067 peuvent être désactivés en supprimant le **/Za** option du compilateur.

```cpp
// C4067b.cpp
// compile with: cl /EHsc /DX /W1 C4067b.cpp
#include <iostream>
#include <string>
#if defined(X)
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif
int main()
{
    std::cout << s << std::endl;
}
```