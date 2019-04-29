---
title: Compilateur Warning (level 1) C4067
ms.date: 11/04/2016
f1_keywords:
- C4067
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
ms.openlocfilehash: 012866e328433ec9511782c26a39265481ff4940
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386510"
---
# <a name="compiler-warning-level-1-c4067"></a>Compilateur Warning (level 1) C4067

> jetons inattendus après la directive du préprocesseur - prévu un saut de ligne

## <a name="remarks"></a>Notes

Le compilateur trouvé et ignoré des caractères supplémentaires après une directive de préprocesseur. Cela peut être dû de tous les caractères inattendus, même si une cause courante est un point-virgule isolée après la directive. Commentaires ne provoquent pas cet avertissement. Le **/Za** option du compilateur active cet avertissement pour les directives de préprocesseur plus que le paramètre par défaut.

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