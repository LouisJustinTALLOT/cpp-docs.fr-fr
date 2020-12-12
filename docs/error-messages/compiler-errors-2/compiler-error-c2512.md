---
description: 'En savoir plus sur : erreur du compilateur C2512'
title: Erreur du compilateur C2512
ms.date: 02/09/2018
f1_keywords:
- C2512
helpviewer_keywords:
- C2512
ms.assetid: 15206da9-1164-451a-b869-280e00711aad
ms.openlocfilehash: 40574ab7fc54ba678729429401ed14fefefe9ebd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212907"
---
# <a name="compiler-error-c2512"></a>Erreur du compilateur C2512

> '*identificateur*' : aucun constructeur par défaut approprié disponible

Un *constructeur par défaut*, un constructeur qui ne requiert aucun argument, n’est pas disponible pour la classe, la structure ou l’Union spécifiée. Le compilateur fournit un constructeur par défaut uniquement si aucun constructeur défini par l’utilisateur n’est fourni.

Si vous fournissez un constructeur qui accepte un paramètre non void et que vous souhaitez autoriser la création de votre classe sans paramètres (par exemple, en tant qu’éléments d’un tableau), vous devez également fournir un constructeur par défaut. Le constructeur par défaut peut être un constructeur avec des valeurs par défaut pour tous les paramètres.

## <a name="example"></a>Exemple

Une cause courante de l’erreur C2512 est lorsque vous définissez un constructeur de classe ou de struct qui accepte des arguments, puis que vous tentez de déclarer une instance de votre classe ou structure sans aucun argument. Par exemple, `struct B` ci-dessous déclare un constructeur qui requiert un `char *` argument, mais pas un constructeur qui ne prend pas d’arguments. Dans `main` , une instance de B est déclarée, mais aucun argument n’est fourni. Le compilateur génère C2512, car il ne trouve pas de constructeur par défaut pour B.

```cpp
// C2512.cpp
// Compile with: cl /W4 c2512.cpp
// C2512 expected
struct B {
   B (char *) {}
   // Uncomment the following line to fix.
   // B() {}
};

int main() {
   B b;   // C2512 - This requires a default constructor
}
```

Vous pouvez résoudre ce problème en définissant un constructeur par défaut pour votre struct ou classe, tel que `B() {}` , ou un constructeur où tous les arguments ont des valeurs par défaut, tels que `B (char * = nullptr) {}` .
