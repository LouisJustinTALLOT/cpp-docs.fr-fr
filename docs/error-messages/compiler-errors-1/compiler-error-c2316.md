---
description: 'En savoir plus sur : erreur du compilateur C2316'
title: Erreur du compilateur C2316
ms.date: 07/08/2019
f1_keywords:
- C2316
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
ms.openlocfilehash: 0e2f528b3f13964a971b88fca110980947bd7d11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282195"
---
# <a name="compiler-error-c2316"></a>Erreur du compilateur C2316

> '*class_type*' : ne peut pas être intercepté en tant que destructeur et/ou le constructeur de copie est inaccessible ou supprimé

Une exception a été interceptée par valeur ou par référence, mais le constructeur de copie, l’opérateur d’assignation, ou les deux, sont inaccessibles.

## <a name="remarks"></a>Notes

Les modifications de conformité dans Visual Studio 2015 ont fait que cette erreur s’applique aux instructions catch erronées des exceptions MFC dérivées de `CException` . Comme `CException` a un constructeur de copie privé hérité, la classe et ses dérivés ne peuvent pas être copiés et ne peuvent pas être passés par valeur, ce qui signifie également qu’ils ne peuvent pas être interceptés par valeur. Les instructions catch qui ont intercepté des exceptions MFC par valeur ont précédemment entraîné des exceptions non interceptées au moment de l’exécution. À présent, le compilateur identifie correctement cette situation et signale une erreur C2316. Pour résoudre ce problème, nous vous recommandons d’utiliser les macros MFC TRY/CATCH plutôt que d’écrire vos propres gestionnaires d’exceptions. Si ce n’est pas approprié pour votre code, interceptez les exceptions MFC par référence à la place.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2316 et montre un moyen de le corriger :

```cpp
// C2316.cpp
// compile with: /EHsc
#include <stdio.h>

struct B
{
public:
    B() {}
    // Delete the following line to resolve.
private:
    // copy constructor
    B(const B&) {}
};

void f(const B&)
{
}

int main()
{
    try
    {
        B aB;
        f(aB);
    }
    catch (B b)    // C2316
    {
        printf_s("Caught an exception!\n");
    }
}
```
