---
title: Erreur du compilateur C3399
ms.date: 11/04/2016
f1_keywords:
- C3399
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
ms.openlocfilehash: e400c181f987a83588f8aedc63ecdedb82be310f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568676"
---
# <a name="compiler-error-c3399"></a>Erreur du compilateur C3399

'type' : impossible de fournir des arguments lors de la création d’une instance d’un paramètre générique

Quand vous spécifiez la contrainte `gcnew()` , vous indiquez que le type de contrainte aura un constructeur sans paramètre. Il est donc incorrect d’essayer d’instancier ce type et de passer un paramètre.

Consultez [contraintes sur les paramètres de Type générique (C++ / c++ / CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md) pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3399.

```
// C3399.cpp
// compile with: /clr /c
generic <class T>
where T : gcnew()
void f() {
   T t = gcnew T(1);   // C3399
   T t2 = gcnew T();   // OK
}
```