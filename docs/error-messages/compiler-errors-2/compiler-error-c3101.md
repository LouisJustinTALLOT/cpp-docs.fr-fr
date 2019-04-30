---
title: Erreur du compilateur C3101
ms.date: 11/04/2016
f1_keywords:
- C3101
helpviewer_keywords:
- C3101
ms.assetid: 4f673766-d4f7-4632-94a5-d36a83f7f4b5
ms.openlocfilehash: d39afc548010df95bdf31b2c7708bc4fa0310bcd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404193"
---
# <a name="compiler-error-c3101"></a>Erreur du compilateur C3101

expression non conforme pour l’attribut nommé argument 'field'

Lors de l’initialisation d’un argument d’attribut nommé, la valeur doit être une constante de compilation.

Pour plus d’informations sur les attributs, consultez [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md).

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