---
title: Problèmes de fonctions inline
ms.date: 11/04/2016
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
ms.openlocfilehash: cb4653bd2f03683b9abad1eea0e9ffa88222090e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184240"
---
# <a name="function-inlining-problems"></a>Problèmes de fonctions inline

Si vous utilisez l’incorporation de fonction, vous devez :

- Les fonctions inline sont implémentées dans le fichier d’en-tête que vous incluez.

- Activez l’incorporation dans le fichier d’en-tête.

```cpp
// LNK2019_function_inline.cpp
// compile with: /c
// post-build command: lib LNK2019_function_inline.obj
#include <stdio.h>
struct _load_config_used {
   void Test();
   void Test2() { printf("in Test2\n"); }
};

void _load_config_used::Test() { printf("in Test\n"); }
```

Puis,

```cpp
// LNK2019_function_inline_2.cpp
// compile with: LNK2019_function_inline.lib
struct _load_config_used {
   void Test();
   void Test2();
};

int main() {
   _load_config_used x;
   x.Test();
   x.Test2();   // LNK2019
}
```

Si vous utilisez la directive de compilateur `#pragma inline_depth`, assurez-vous que la valeur est supérieure ou égale à 2. La valeur zéro désactive l’incorporation. Vérifiez également que vous utilisez les options du compilateur **/Ob1** ou **/OB2** .

La combinaison d’options de compilation inline et non inline sur des modules différents peut parfois provoquer des problèmes. Si une C++ bibliothèque est créée avec la fonction inline activée ([/Ob1](../../build/reference/ob-inline-function-expansion.md) ou [/OB2](../../build/reference/ob-inline-function-expansion.md)), mais que le fichier d’en-tête correspondant décrivant les fonctions a désactivé l’incorporation (aucune option), vous obtiendrez l’erreur LNK2001. Les fonctions ne sont pas inline dans le code du fichier d’en-tête, mais comme elles ne se trouvent pas dans le fichier de bibliothèque, il n’existe aucune adresse pour résoudre la référence.

De même, un projet qui utilise la fonction inline, mais définit les fonctions dans un fichier. cpp plutôt que dans le fichier d’en-tête obtiendra également l’erreur LNK2019. Le fichier d’en-tête est inclus partout jugé approprié, mais les fonctions ne sont Inline que lorsque le fichier. cpp passe par le compilateur. par conséquent, l’éditeur de liens voit les fonctions comme externes non résolus lorsqu’ils sont utilisés dans d’autres modules.

```cpp
// LNK2019_FIP.h
struct testclass {
   void PublicStatMemFunc1(void);
};
```

Et puis

```cpp
// LNK2019_FIP.cpp
// compile with: /c
#include "LNK2019_FIP.h"
inline void testclass::PublicStatMemFunc1(void) {}
```

Et puis

```cpp
// LNK2019_FIP_2.cpp
// compile with: LNK2019_FIP.cpp
// LNK2019 expected
#include "LNK2019_FIP.h"
int main() {
   testclass testclsObject;

   // module cannot see the implementation of PublicStatMemFunc1
   testclsObject.PublicStatMemFunc1();
}
```

## <a name="see-also"></a>Voir aussi

[Erreur des outils Éditeur de liens LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
