---
title: Erreur du compilateur C3809 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3809
dev_langs:
- C++
helpviewer_keywords:
- C3809
ms.assetid: 37eca584-c20c-464e-8e45-a987214b7ce4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b99cda2ab1790ce63ecbd0f6c5a3dc4d916d34c9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104216"
---
# <a name="compiler-error-c3809"></a>Erreur du compilateur C3809

'classe' : un type managé ou WinRT ne peut pas avoir de fonctions/classes/interfaces friend

Les types managés et les types Windows Runtime n'autorisent pas l'utilisation des friends. Pour corriger cette erreur, ne déclarez ne pas de friend à l'intérieur des types managés ou Windows Runtime.

L'exemple suivant génère l'erreur C3809 :

```
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