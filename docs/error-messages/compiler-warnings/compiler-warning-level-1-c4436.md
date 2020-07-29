---
title: Avertissement du compilateur (niveau 1) C4436
ms.date: 11/04/2016
f1_keywords:
- C4436
helpviewer_keywords:
- C4436
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
ms.openlocfilehash: 6a15220cb02a48fb11936b69e5830412f1221108
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230673"
---
# <a name="compiler-warning-level-1-c4436"></a>Avertissement du compilateur (niveau 1) C4436

dynamic_cast de la base virtuelle « classe1 » à « Class2 » dans le constructeur ou le destructeur peut échouer avec une compilation d’objet partiellement construite avec/VD2 ou définir « Class2 » avec #pragma vtordisp (2) en vigueur

Le compilateur a rencontré une **`dynamic_cast`** opération avec les caractéristiques suivantes.

- Le cast provient d’un pointeur de classe de base vers un pointeur de classe dérivée.

- La classe dérivée hérite pratiquement de la classe de base.

- La classe dérivée n’a pas de `vtordisp` champ pour la base virtuelle.

- Le cast est trouvé dans un constructeur ou un destructeur de la classe dérivée, ou dans une classe qui hérite encore de la classe dérivée.

L’avertissement indique **`dynamic_cast`** que peut ne pas s’exécuter correctement, s’il fonctionne sur un objet partiellement construit.  Cela se produit si le constructeur/destructeur dérivé fonctionne sur un sous-objet d’un autre objet dérivé.  Si la classe dérivée nommée dans l’avertissement n’est jamais dérivée, l’avertissement peut être ignoré.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4436 et montre le problème de génération de code qui se produit à partir du `vtordisp` champ manquant.

```cpp
// C4436.cpp
// To see the warning and runtime assert, compile with: /W1
// To eliminate the warning and assert, compile with: /W1 /vd2
//       or compile with: /W1 /DFIX
#include <cassert>

struct A
{
public:
    virtual ~A() {}
};

#if defined(FIX)
#pragma vtordisp(push, 2)
#endif
struct B : virtual A
{
    B()
    {
        A* a = static_cast<A*>(this);
        B* b = dynamic_cast<B*>(a);     // C4436
        assert(this == b);              // assert unless compiled with /vd2
    }
};
#if defined(FIX)
#pragma vtordisp(pop)
#endif

struct C : B
{
    int i;
};

int main()
{
    C c;
}
```

## <a name="see-also"></a>Voir aussi

[Opérateur dynamic_cast](../../cpp/dynamic-cast-operator.md)<br/>
[vtordisp](../../preprocessor/vtordisp.md)<br/>
[Avertissement du compilateur (niveau 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)
