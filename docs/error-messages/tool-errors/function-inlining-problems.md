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
ms.openlocfilehash: fec3884dff0dda7140f18fa53e493c12996edcf0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031522"
---
# <a name="function-inlining-problems"></a>Problèmes de fonctions inline

Si vous utilisez des fonctions inline, vous devez :

- Avoir les fonctions inline implémentées dans le fichier d’en-tête inclus.

- Avez incorporation (inlining) dans le fichier d’en-tête.

```
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

```
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

Si vous utilisez le `#pragma inline_depth` veillez directive du compilateur vous définition disposez une valeur de 2 ou supérieur. Une valeur égale à zéro s’éteint incorporation (inlining). Vérifiez également que vous utilisez le **/Ob1** ou **/Ob2** options du compilateur.

Panachage d’options de compilation en ligne et non en ligne sur les différents modules peut parfois entraîner des problèmes. Si une bibliothèque C++ est créée avec la fonctionnalité inline activée ([/Ob1](../../build/reference/ob-inline-function-expansion.md) ou [/Ob2](../../build/reference/ob-inline-function-expansion.md)), mais le fichier d’en-tête correspondant décrivant les fonctions a désactivé cette fonctionnalité (sans option), vous obtiendrez l’erreur LNK2001. Les fonctions n’obtiennent pas inline dans le code à partir du fichier d’en-tête, mais dans la mesure où ils ne sont pas dans le fichier de bibliothèque aucune adresse n’est pour résoudre la référence.

De même, un projet qui utilise la fonction inline mais définit les fonctions dans un fichier .cpp au plutôt que dans l’en-tête de fichier recevront également l’erreur LNK2019. Le fichier d’en-tête est inclus partout semble approprié, mais les fonctions sont uniquement inline lorsque le fichier .cpp passe par le compilateur ; Par conséquent, l’éditeur de liens considère les fonctions comme externes non résolus lorsqu’il est utilisé dans d’autres modules.

```
// LNK2019_FIP.h
struct testclass {
   void PublicStatMemFunc1(void);
};
```

Et puis

```
// LNK2019_FIP.cpp
// compile with: /c
#include "LNK2019_FIP.h"
inline void testclass::PublicStatMemFunc1(void) {}
```

Et puis

```
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