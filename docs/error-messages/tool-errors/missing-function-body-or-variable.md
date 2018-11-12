---
title: Corps de fonction ou variable manquant
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 88470272192520e9aa0582fd06ff36a0542803ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647120"
---
# <a name="missing-function-body-or-variable"></a>Corps de fonction ou variable manquant

Avec seulement un prototype de fonction, le compilateur peut poursuivre sans erreur, mais l’éditeur de liens ne peut pas résoudre un appel à une adresse, car il n’existe pas de code de fonction ou variable espace réservé. Vous ne verrez pas cette erreur jusqu'à ce que vous créiez un appel à la fonction de l’éditeur de liens doit être résolue.

## <a name="example"></a>Exemple

L’appel de fonction dans main provoquera l’erreur LNK2019, car le prototype permet au compilateur de considérer que la fonction existe.  L’éditeur de liens recherche que ce n’est pas.

```
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>Exemple

En C++, assurez-vous que vous incluez l’implémentation d’une fonction spécifique pour une classe et pas seulement un prototype dans la définition de classe. Si vous définissez la classe en dehors du fichier d’en-tête, veillez à inclure le nom de classe avant la fonction (`Classname::memberfunction`).

```
// LNK2019_MFBV_2.cpp
// LNK2019 expected
struct A {
   static void Test();
};

// Should be void A::Test() {}
void Test() {}

int main() {
   A AObject;
   AObject.Test();
}
```

## <a name="see-also"></a>Voir aussi

[Erreur des outils Éditeur de liens LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)