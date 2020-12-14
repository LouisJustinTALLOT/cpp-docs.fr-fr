---
description: 'En savoir plus sur : erreur du compilateur C3399'
title: Erreur du compilateur C3399
ms.date: 11/04/2016
f1_keywords:
- C3399
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
ms.openlocfilehash: a950857e88c5cfcad50ac2efb064af4d7a5c0cf1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316425"
---
# <a name="compiler-error-c3399"></a>Erreur du compilateur C3399

'type' : impossible de fournir des arguments lors de la création d’une instance d’un paramètre générique

Quand vous spécifiez la contrainte `gcnew()` , vous indiquez que le type de contrainte aura un constructeur sans paramètre. Il est donc incorrect d’essayer d’instancier ce type et de passer un paramètre.

Pour plus d’informations, consultez [contraintes sur les paramètres de type générique (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) .

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
