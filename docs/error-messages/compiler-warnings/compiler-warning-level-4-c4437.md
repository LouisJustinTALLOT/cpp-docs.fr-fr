---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4437'
title: Avertissement du compilateur (niveau 4) C4437
ms.date: 11/04/2016
f1_keywords:
- C4437
helpviewer_keywords:
- C4437
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
ms.openlocfilehash: 6ea94a972c08dfa6752c5c165a9c547419b03334
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251425"
---
# <a name="compiler-warning-level-4-c4437"></a>Avertissement du compilateur (niveau 4) C4437

l’dynamic_cast de la base virtuelle « classe1 » à « Class2 » peut échouer dans certains contextes compilent avec/VD2 ou définissez « Class2 » avec #pragma vtordisp (2) en vigueur

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

Le compilateur a rencontré une **`dynamic_cast`** opération avec les caractéristiques suivantes.

- Le cast provient d’un pointeur de classe de base vers un pointeur de classe dérivée.

- La classe dérivée hérite pratiquement de la classe de base.

- La classe dérivée n’a pas de `vtordisp` champ pour la base virtuelle.

- Le cast est introuvable dans un constructeur ou un destructeur de la classe dérivée, ou dans une classe qui hérite encore de la classe dérivée (sinon, l’avertissement du compilateur C4436 sera émis).

L’avertissement indique que **`dynamic_cast`** peut ne pas fonctionner correctement s’il fonctionne sur un objet partiellement construit.  Cette situation se produit lorsque la fonction englobante est appelée à partir d’un constructeur ou d’un destructeur d’une classe qui hérite de la classe dérivée nommée dans l’avertissement.  Si la classe dérivée nommée dans l’avertissement n’est jamais dérivée davantage ou si la fonction englobante n’est pas appelée pendant la construction ou la destruction de l’objet, l’avertissement peut être ignoré.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4437 et montre le problème de génération de code qui se produit à partir du `vtordisp` champ manquant.

```cpp
// C4437.cpp
// To see the warning and runtime assert, compile with: /W4
// To eliminate the warning and assert, compile with: /W4 /vd2
//       or compile with: /W4 /DFIX
#pragma warning(default : 4437)
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
        func();
    }

    void func()
    {
        A* a = static_cast<A*>(this);
        B* b = dynamic_cast<B*>(a);     // C4437
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
[Avertissement du compilateur (niveau 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)
