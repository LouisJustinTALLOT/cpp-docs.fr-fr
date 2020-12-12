---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4067'
title: Avertissement du compilateur (niveau 1) C4067
ms.date: 11/04/2016
f1_keywords:
- C4067
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
ms.openlocfilehash: b11167ba5648e71be16197ecfb418d92cb5d879a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267662"
---
# <a name="compiler-warning-level-1-c4067"></a>Avertissement du compilateur (niveau 1) C4067

> jetons inattendus après la directive du préprocesseur-saut de ligne ATTENDU

## <a name="remarks"></a>Notes

Le compilateur a trouvé et ignoré des caractères supplémentaires après une directive de préprocesseur. Cela peut être dû à des caractères inattendus, bien qu’une cause fréquente soit un point-virgule parasite après la directive. Les commentaires ne provoquent pas cet avertissement. L’option de compilateur **/za** active cet avertissement pour davantage de directives de préprocesseur que le paramètre par défaut.

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

Pour résoudre cet avertissement, supprimez les caractères isolés ou déplacez-les dans un bloc de commentaires. Certains avertissements C4067 peuvent être désactivés en supprimant l’option **/za** du compilateur.

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
