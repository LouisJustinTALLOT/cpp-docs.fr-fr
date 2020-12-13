---
description: 'En savoir plus sur : erreur du compilateur C3380'
title: Erreur du compilateur C3380
ms.date: 11/04/2016
f1_keywords:
- C3380
helpviewer_keywords:
- C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
ms.openlocfilehash: bb633d75d08fdbb902f086b3a4cd6a8a6db1fc69
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334984"
---
# <a name="compiler-error-c3380"></a>Erreur du compilateur C3380

'class' : spécificateur d’accès à l’assembly non valide - seuls 'public' ou 'private' sont autorisés

En cas d’application à une classe managée ou à une structure, les mots clés [public](../../cpp/public-cpp.md) et [private](../../cpp/private-cpp.md) indiquent si la classe doit être exposée dans les métadonnées de l’assembly. Seuls `public` ou `private` peuvent être appliqués à une classe contenue dans un programme compilé avec [/clr](../../build/reference/clr-common-language-runtime-compilation.md).

Les `ref` `value` Mots clés et, lorsqu’ils sont utilisés avec [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), indiquent qu’une classe est managée (consultez [classes et structs](../../extensions/classes-and-structs-cpp-component-extensions.md)).

L’exemple suivant génère l’erreur C3380 :

```cpp
// C3380_2.cpp
// compile with: /clr
protected ref class A {   // C3380
// try the following line instead
// ref class A {
public:
   static int i = 9;
};

int main() {
   A^ myA = gcnew A;
   System::Console::WriteLine(myA->i);
}
```
