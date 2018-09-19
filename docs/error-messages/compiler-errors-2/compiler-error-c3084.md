---
title: Erreur du compilateur C3084 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3084
dev_langs:
- C++
helpviewer_keywords:
- C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 44bab3f43efa186c83134a6b40e7cb3fcbcbd51d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027230"
---
# <a name="compiler-error-c3084"></a>Erreur du compilateur C3084

'function' : un finaliseur/destructeur ne peut pas avoir la valeur 'keyword'

Un finaliseur ou un destructeur n’a pas été correctement déclaré.

Par exemple, un destructeur ne doit pas être marqué comme sealed.  Le destructeur sera inaccessible aux types dérivés.  Pour plus d’informations, consultez [substitutions explicites](../../windows/explicit-overrides-cpp-component-extensions.md) et [destructeurs et finaliseurs dans Comment : définir et consommer des classes et structs (C++ / c++ / CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

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