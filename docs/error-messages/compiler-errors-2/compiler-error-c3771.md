---
title: Erreur du compilateur C3771
ms.date: 11/04/2016
f1_keywords:
- C3771
helpviewer_keywords:
- C3771
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
ms.openlocfilehash: 6b15d867bbaf66f511cbda200d692f5db4371ab3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026692"
---
# <a name="compiler-error-c3771"></a>Erreur du compilateur C3771

"identifier" : déclaration friend introuvable dans la portée espace de noms la plus proche

La déclaration de modèle de classe pour le modèle spécifié *identifier* est introuvable dans l’espace de noms actuel.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Assurez-vous que la déclaration de modèle de classe pour l’identificateur de modèle est définie dans l’espace de noms actuel ou que l’identificateur de modèle est un nom complet.

## <a name="example"></a>Exemple

L’exemple de code suivant déclare un modèle de classe et une fonction dans l’espace de noms `NA`, mais tente de déclarer un modèle de fonction friend dans l’espace de noms `NB`.

```cpp
// C3771.cpp
// compile with: /c

namespace NA {
template<class T> class A {
    void aFunction(T t) {};
    };
}
// using namespace NA;
namespace NB {
    class X {
        template<class T> friend void A<T>::aFunction(T); // C3771
// try the following line instead
//      template<class T> friend void NA::A<T>::aFunction(T);
// or try "using namespace NA;" instead.
    };
}
```

## <a name="see-also"></a>Voir aussi

[Modèles](../../cpp/templates-cpp.md)