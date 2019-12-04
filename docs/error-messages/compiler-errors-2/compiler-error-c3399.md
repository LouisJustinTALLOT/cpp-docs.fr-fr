---
title: Erreur du compilateur C3399
ms.date: 11/04/2016
f1_keywords:
- C3399
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
ms.openlocfilehash: d20b5e816930969278536fe3771df4ad38c3c86b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737515"
---
# <a name="compiler-error-c3399"></a>Erreur du compilateur C3399

'type' : impossible de fournir des arguments lors de la création d’une instance d’un paramètre générique

Quand vous spécifiez la contrainte `gcnew()` , vous indiquez que le type de contrainte aura un constructeur sans paramètre. Il est donc incorrect d’essayer d’instancier ce type et de passer un paramètre.

Pour plus d’informations, consultez [contraintesC++sur les paramètres de type générique (/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3399.

```cpp
// C3399.cpp
// compile with: /clr /c
generic <class T>
where T : gcnew()
void f() {
   T t = gcnew T(1);   // C3399
   T t2 = gcnew T();   // OK
}
```
