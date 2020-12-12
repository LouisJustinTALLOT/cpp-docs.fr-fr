---
description: 'En savoir plus sur : erreur du compilateur C3101'
title: Erreur du compilateur C3101
ms.date: 11/04/2016
f1_keywords:
- C3101
helpviewer_keywords:
- C3101
ms.assetid: 4f673766-d4f7-4632-94a5-d36a83f7f4b5
ms.openlocfilehash: e0c52eadd2af4b090b34f851d561535f360a7e59
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116169"
---
# <a name="compiler-error-c3101"></a>Erreur du compilateur C3101

expression non conforme pour l’argument d’attribut nommé’champ'

Lors de l’initialisation d’un argument d’attribut nommé, la valeur doit être une constante au moment de la compilation.

Pour plus d’informations sur les attributs, consultez [attributs définis par l’utilisateur](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3101.

```cpp
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
