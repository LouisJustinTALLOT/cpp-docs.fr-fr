---
description: 'En savoir plus sur : erreur du compilateur C3809'
title: Erreur du compilateur C3809
ms.date: 11/04/2016
f1_keywords:
- C3809
helpviewer_keywords:
- C3809
ms.assetid: 37eca584-c20c-464e-8e45-a987214b7ce4
ms.openlocfilehash: 62e7ff06e6ed5bf34861fdbae3f823e19ad5aad4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328208"
---
# <a name="compiler-error-c3809"></a>Erreur du compilateur C3809

'classe' : un type managé ou WinRT ne peut pas avoir de fonctions/classes/interfaces friend

Les types managés et les types Windows Runtime n'autorisent pas l'utilisation des friends. Pour corriger cette erreur, ne déclarez ne pas de friend à l'intérieur des types managés ou Windows Runtime.

L'exemple suivant génère l'erreur C3809 :

```cpp
// C3809a.cpp
// compile with: /clr
ref class A {};

ref class B
{
public:
   friend ref class A;   // C3809
};

int main()
{
}
```
