---
description: 'En savoir plus sur : corps de fonction ou variable manquant'
title: Corps de fonction ou variable manquant
ms.date: 11/04/2016
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
ms.openlocfilehash: 6a4349c380fc0f573adc8e372f9e4d2fc3f83873
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155161"
---
# <a name="missing-function-body-or-variable"></a>Corps de fonction ou variable manquant

Avec juste un prototype de fonction, le compilateur peut continuer sans erreur, mais l’éditeur de liens ne peut pas résoudre un appel à une adresse, car aucun code de fonction ou espace de variable n’est réservé. Vous ne verrez pas cette erreur tant que vous n’avez pas créé un appel à la fonction que l’éditeur de liens doit résoudre.

## <a name="example-call-to-an-undefined-function"></a>Exemple : appel à une fonction non définie

L’appel de fonction dans main entraînera l’erreur LNK2019, car le prototype permet au compilateur de croire que la fonction existe.  L’éditeur de liens détecte qu’il ne l’a pas.

```cpp
// LNK2019_MFBV.cpp
// LNK2019 expected
void DoSomething(void);
int main() {
   DoSomething();
}
```

## <a name="example-call-to-an-implemented-function"></a>Exemple : appel à une fonction implémentée

En C++, veillez à inclure l’implémentation d’une fonction spécifique pour une classe et pas simplement un prototype dans la définition de classe. Si vous définissez la classe en dehors du fichier d’en-tête, veillez à inclure le nom de la classe avant la fonction ( `Classname::memberfunction` ).

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
