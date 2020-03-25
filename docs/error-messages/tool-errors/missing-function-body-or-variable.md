---
title: Corps de fonction ou variable manquant
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 6d2ef22b90009d320485fb6fe3f7e308ae05c442
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173619"
---
# <a name="missing-function-body-or-variable"></a>Corps de fonction ou variable manquant

Avec juste un prototype de fonction, le compilateur peut continuer sans erreur, mais l’éditeur de liens ne peut pas résoudre un appel à une adresse, car aucun code de fonction ou espace de variable n’est réservé. Vous ne verrez pas cette erreur tant que vous n’avez pas créé un appel à la fonction que l’éditeur de liens doit résoudre.

## <a name="example"></a>Exemple

L’appel de fonction dans main entraînera l’erreur LNK2019, car le prototype permet au compilateur de croire que la fonction existe.  L’éditeur de liens détecte qu’il ne l’a pas.

```cpp
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example"></a>Exemple

Dans C++, assurez-vous que vous incluez l’implémentation d’une fonction spécifique pour une classe et pas simplement un prototype dans la définition de classe. Si vous définissez la classe en dehors du fichier d’en-tête, veillez à inclure le nom de la classe avant la fonction (`Classname::memberfunction`).

```cpp
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
