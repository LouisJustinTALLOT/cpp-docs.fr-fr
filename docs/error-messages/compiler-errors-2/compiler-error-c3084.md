---
title: Erreur du compilateur C3084
ms.date: 11/04/2016
f1_keywords:
- C3084
helpviewer_keywords:
- C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
ms.openlocfilehash: 01e229fe0ae5bf9e04c577bb653ff1ed7fdb33bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243282"
---
# <a name="compiler-error-c3084"></a>Erreur du compilateur C3084

'function' : un finaliseur/destructeur ne peut pas avoir la valeur 'keyword'

Un finaliseur ou un destructeur n’a pas été correctement déclaré.

Par exemple, un destructeur ne doit pas être marqué comme sealed.  Le destructeur sera inaccessible aux types dérivés.  Pour plus d’informations, consultez [substitutions explicites](../../extensions/explicit-overrides-cpp-component-extensions.md) et [destructeurs et finaliseurs dans Comment : Définir et consommer des classes et structs (C++ / c++ / CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3084.

```
// C3084.cpp
// compile with: /clr /c
ref struct R {
protected:
   !R() sealed;   // C3084
   !R() abstract;   // C3084
   !R();
};
```