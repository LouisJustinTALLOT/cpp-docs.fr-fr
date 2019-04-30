---
title: Avertissement du compilateur (niveau 1) C4436
ms.date: 11/04/2016
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
ms.openlocfilehash: 487fb8c804ac34ba52661774c2552199c764f6b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408184"
---
# <a name="compiler-warning-level-1-c4436"></a>Avertissement du compilateur (niveau 1) C4436

dynamic_cast de la base virtuelle 'classe1' en 'classe2' dans le constructeur ou un destructeur peut échouer avec l’objet partiellement construit compilation avec/vd2 ou définir 'classe2' avec #pragma vtordisp (2) système en vigueur

Le compilateur a rencontré un `dynamic_cast` opération avec les caractéristiques suivantes.

- Le cast est d’un pointeur de classe de base à un pointeur de la classe dérivée.

- La classe dérivée hérite pratiquement de la classe de base.

- La classe dérivée n’a pas un `vtordisp` champ pour la base virtuelle.

- Le cast se trouvent dans un constructeur ou un destructeur de la classe dérivée, ou une classe, ce qui hérite de la classe dérivée.

L’avertissement indique le `dynamic_cast` peuvent ne pas fonctionner correctement, si elle s’exécute sur un objet partiellement construit.  Cela se produit si le constructeur/destructeur dérivé fonctionne sur un sous-objet de certains objets dérivée ultérieure.  Si la classe dérivée nommée dans l’avertissement n’est jamais plus dérivé, l’avertissement peut être ignoré.

## <a name="example"></a>Exemple

L’exemple suivant génère C4436 et illustre le problème de génération de code qui produit de champ manquant `vtordisp` champ.

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

[dynamic_cast, opérateur](../../cpp/dynamic-cast-operator.md)<br/>
[vtordisp](../../preprocessor/vtordisp.md)<br/>
[Avertissement du compilateur (niveau 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)