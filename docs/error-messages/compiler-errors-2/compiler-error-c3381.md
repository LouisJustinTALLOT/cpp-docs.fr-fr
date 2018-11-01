---
title: Erreur du compilateur C3381
ms.date: 11/04/2016
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: ae416d68831d1964c89d938dfcddd364e521195c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440272"
---
# <a name="compiler-error-c3381"></a>Erreur du compilateur C3381

'assembly' : les spécificateurs d’accès assembly sont uniquement disponibles dans le code compilé avec une option/CLR

Les types natifs peuvent être visibles en dehors de l’assembly, mais vous pouvez spécifier uniquement un accès d’assembly pour les types natifs dans un **/CLR** compilation.

Pour plus d’informations, consultez [tapez visibilité](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) et [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3381.

```
// C3381.cpp
// compile with: /c
public class A {};   // C3381
```