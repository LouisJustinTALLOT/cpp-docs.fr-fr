---
description: En savoir plus sur les constantes globales en C++
title: Constantes globales en C++
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: 8e960e7e10942fc231fcdeafef6e8d755694c460
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261656"
---
# <a name="global-constants-in-c"></a>Constantes globales en C++

Les constantes globales C++ ont une liaison statique. Cela est différent de C. Si vous essayez d’utiliser une constante globale en C++ dans plusieurs fichiers, vous recevez une erreur externe non résolue. Le compilateur optimise les constantes globales, ne laissant aucun espace réservé pour la variable.

Une façon de résoudre cette erreur consiste à inclure les initialisations const dans un fichier d’en-tête et à inclure cet en-tête dans vos fichiers CPP lorsque cela est nécessaire, comme s’il s’agissait d’un prototype de fonction. Une autre possibilité consiste à rendre la variable non constante et à utiliser une référence constante lors de son évaluation.

L’exemple suivant génère l’C2019 :

```cpp
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

Puis,

```cpp
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>Voir aussi

[Erreur des outils Éditeur de liens LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
