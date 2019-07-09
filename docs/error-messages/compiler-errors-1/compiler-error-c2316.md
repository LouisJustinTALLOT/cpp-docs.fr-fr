---
title: Erreur du compilateur C2316
ms.date: 07/08/2019
f1_keywords:
- C2316
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
ms.openlocfilehash: 5a3d9052775a5e1cbedfd58ccaaf0ff039a8475d
ms.sourcegitcommit: 07b34ca1c1fecced9fadc95de15dc5fee4f31e5a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693443"
---
# <a name="compiler-error-c2316"></a>Erreur du compilateur C2316

> «*class_type*' : ne peut pas être intercepté en tant que destructeur et/ou le constructeur de copie est inaccessible ou supprimé

Une exception a été interceptée par valeur ou par référence, mais le constructeur de copie, l’opérateur d’assignation, ou les deux n’étaient pas accessibles.

## <a name="remarks"></a>Notes

La conformité dans Visual Studio 2015 apportées cette erreur s’appliquent aux instructions catch incorrecte des exceptions MFC dérivées de `CException`. Étant donné que `CException` a un constructeur de copie privé héritée, la classe et ses dérivés ne sont pas être copiés et ne peuvent pas être passés par valeur, ce qui signifie également qu’ils ne peuvent pas être interceptées par valeur. Intercepter les instructions interceptée exceptions MFC par valeur précédemment a conduit à des exceptions non interceptées lors de l’exécution. Maintenant le compilateur identifie cette situation correctement et signale l’erreur C2316. Pour résoudre ce problème, nous vous recommandons d’utiliser les macros MFC TRY/CATCH plutôt que d’écrire vos propres gestionnaires d’exceptions. Si tel n’est pas approprié pour votre code, intercepter les exceptions MFC par référence.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2316 et illustre une méthode permettant de résoudre le problème :

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
