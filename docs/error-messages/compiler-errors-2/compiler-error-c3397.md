---
description: 'En savoir plus sur : erreur du compilateur C3397'
title: Erreur du compilateur C3397
ms.date: 11/04/2016
f1_keywords:
- C3397
helpviewer_keywords:
- C3397
ms.assetid: a8536e87-79c4-4ed7-bd96-42704d06391f
ms.openlocfilehash: 2d450e11849b58af55e34396674597fa3a60166d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313175"
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
