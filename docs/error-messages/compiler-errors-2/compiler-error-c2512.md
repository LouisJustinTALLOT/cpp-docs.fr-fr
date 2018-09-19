---
title: Erreur du compilateur C2512 | Microsoft Docs
ms.custom: ''
ms.date: 02/09/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2512
dev_langs:
- C++
helpviewer_keywords:
- C2512
ms.assetid: 15206da9-1164-451a-b869-280e00711aad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba1fbba98237879927fd82d6535c0c2688c1c304
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036916"
---
# <a name="compiler-error-c2512"></a>Erreur du compilateur C2512

> «*identificateur*' : aucun constructeur par défaut approprié disponible

Un *constructeur par défaut*, un constructeur qui ne requiert aucun argument, n’est pas disponible pour la classe spécifiée, de structure ou union. Le compilateur fournit un constructeur par défaut uniquement si aucun constructeur défini par l’utilisateur n’est fournis.

Si vous fournissez un constructeur qui accepte un paramètre non void et que vous souhaitez autoriser votre classe d’être créés sans paramètres (comme par exemple, les éléments d’un tableau), vous devez également fournir un constructeur par défaut. Le constructeur par défaut peut être un constructeur avec des valeurs par défaut pour tous les paramètres.

## <a name="example"></a>Exemple

Une cause courante de l’erreur C2512 est lorsque vous définissez un constructeur de classe ou un struct qui accepte des arguments, et vous tentez de déclarer une instance de votre classe ou struct sans arguments. Par exemple, `struct B` ci-dessous déclare un constructeur qui nécessite un `char *` argument, mais pas celui qui n’accepte aucun argument. Dans `main`, une instance de B est déclarée, mais aucun argument n’est fourni. Le compilateur génère l’erreur C2512, car il ne trouve pas un constructeur par défaut pour B.

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

Vous pouvez résoudre ce problème en définissant un constructeur par défaut pour votre struct ou d’une classe, tel que `B() {}`, ou un constructeur dans lequel tous les arguments ont des valeurs par défaut, comme `B (char * = nullptr) {}`.
