---
title: Erreur du compilateur C3381 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3381
dev_langs:
- C++
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bd6c1d641f7476d3c372939b948931a306e0f80
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080712"
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