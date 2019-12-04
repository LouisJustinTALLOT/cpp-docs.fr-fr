---
title: Erreur du compilateur C3397
ms.date: 11/04/2016
f1_keywords:
- C3397
helpviewer_keywords:
- C3397
ms.assetid: a8536e87-79c4-4ed7-bd96-42704d06391f
ms.openlocfilehash: 1e00b5cb63d97e023c092f675dbe07a68d9a2548
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737528"
---
# <a name="compiler-error-c3397"></a>Erreur du compilateur C3397

L'initialisation d'agrégats n'est pas autorisée dans les arguments par défaut

Un tableau a été déclaré de manière incorrecte.  Pour plus d’informations, consultez [tableaux](../../extensions/arrays-cpp-component-extensions.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3397 :

```cpp
// C3397.cpp
// compile with: /clr
// /clr /c
void Func(array<int> ^p = gcnew array<int> { 1, 2, 3 });   // C3397
void Func2(array<int> ^p = gcnew array<int> (3));   // OK

int main() {
   array<int> ^p = gcnew array<int> { 1, 2, 3};   // OK
}
```
