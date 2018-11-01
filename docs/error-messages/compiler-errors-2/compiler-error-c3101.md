---
title: Erreur du compilateur C3101
ms.date: 11/04/2016
f1_keywords:
- C3101
helpviewer_keywords:
- C3101
ms.assetid: 4f673766-d4f7-4632-94a5-d36a83f7f4b5
ms.openlocfilehash: 8db1ba622a0c83a7f2a6421d79ff5853cbc4d9a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555556"
---
# <a name="compiler-error-c3101"></a>Erreur du compilateur C3101

expression non conforme pour l’attribut nommé argument 'field'

Lors de l’initialisation d’un argument d’attribut nommé, la valeur doit être une constante de compilation.

Pour plus d’informations sur les attributs, consultez [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3101.

```
// C3101.cpp
// compile with: /clr /c
ref class AAttribute : System::Attribute {
public:
   int Field;
};

extern int i;

[assembly:A(Field = i)];   // C3101
[assembly:A(Field = 0)];   // OK
```