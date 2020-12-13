---
description: 'En savoir plus sur : erreur du compilateur C3069'
title: Erreur du compilateur C3069
ms.date: 11/04/2016
f1_keywords:
- C3069
helpviewer_keywords:
- C3069
ms.assetid: ca94291b-2bb4-4e3f-9acf-534234b83513
ms.openlocfilehash: cc56ded4f14e137b9f5bf28681fb319a650f363a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341137"
---
# <a name="compiler-error-c3069"></a>Erreur du compilateur C3069

'operator' : non autorisé pour un type d’énumération

Un opérateur n’est pas pris en charge dans les énumérations CLR.  Pour plus d’informations, consultez [Comment : définir et consommer des énumérations en C++/CLI](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3069 :

```cpp
// C3069.cpp
// compile with: /clr
enum struct E { e1 };
enum F { f1 };

int main() {
   E e = E::e1;
   bool tf;
   tf = !e;   // C3069

   // supported for native enums
   F f = f1;
   tf = !f;
}
```
