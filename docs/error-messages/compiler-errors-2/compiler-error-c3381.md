---
title: Erreur du compilateur C3381
ms.date: 11/04/2016
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: eadc9b45b4cd4f2d9b533f387dadd66be8acc963
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749566"
---
# <a name="compiler-error-c3381"></a>Erreur du compilateur C3381

'assembly' : les spécificateurs d’accès à l’assembly ne sont disponibles que dans le code compilé avec une option/clr

Les types natifs peuvent être visibles à l’extérieur de l’assembly, mais vous pouvez uniquement spécifier l’accès à l’assembly pour les types natifs dans une compilation **/CLR** .

Pour plus d’informations, consultez [type Visibility](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) et [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3381.

```cpp
// C3381.cpp
// compile with: /c
public class A {};   // C3381
```
