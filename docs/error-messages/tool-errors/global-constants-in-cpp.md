---
title: Constantes globales en C++
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: 1ae29b8744e24b6471f0d5536f3f13cc5ae59499
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030191"
---
# <a name="global-constants-in-c"></a>Constantes globales en C++

Constantes globales en C++ ont une liaison statique. Cela est différent de C. Si vous essayez d’utiliser un global constante en C++ dans plusieurs fichiers, vous obtenez une erreur externe non résolue. Le compilateur optimise les constantes globales, en laissant aucun espace réservé pour la variable.

Pour résoudre cette erreur consiste à inclure les initialisations dans un fichier d’en-tête et inclure cet en-tête dans vos fichiers CPP lorsque cela est nécessaire, comme s’il s’agissait de prototype de fonction. Une autre possibilité consiste à rendre la variable non constante et utiliser une référence constante lors de l’évaluation il.

L’exemple suivant génère l’erreur C2019 :

```
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

Puis,

```
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>Voir aussi

[Erreur des outils Éditeur de liens LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)