---
title: Erreur du compilateur C3224 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3224
dev_langs:
- C++
helpviewer_keywords:
- C3224
ms.assetid: 129be22f-8f3e-4fc6-9ccd-d27d8ef91251
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7eb7c5d9bc912eafb2c7772114448a0567d90cad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105035"
---
# <a name="compiler-error-c3224"></a>Erreur du compilateur C3224

'type' : aucune classe générique surchargée n’accepte 'nombre' arguments de type générique

Le compilateur n’a pas trouvé de surcharge appropriée.

L’exemple suivant génère l’erreur C3224 :

```
// C3224.cs
// compile with: /target:library
public class C<T> {}
public class C<T,U> {}
```

Puis,

```
// C3224b.cpp
// compile with: /clr
#using "C3224.dll"
int main() {
   C<int,int,int>^ c = gcnew C<int,int,int>();   // C3224
   C<int,int>^ c2 = gcnew C<int,int>();   // OK
}
```