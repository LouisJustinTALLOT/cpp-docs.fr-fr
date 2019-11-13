---
title: Avertissement du compilateur (niveau 2) C4150
ms.date: 11/04/2016
f1_keywords:
- C4150
helpviewer_keywords:
- C4150
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
ms.openlocfilehash: 5f55347dbe7843e67a3c6ef0ab83b91c8fa9d283
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052153"
---
# <a name="compiler-warning-level-2-c4150"></a>Avertissement du compilateur (niveau 2) C4150

suppression d’un pointeur vers un type incomplet’type'; aucun destructeur appelé

L’opérateur **Delete** est appelé pour supprimer un type qui a été déclaré mais pas défini, de sorte que le compilateur ne peut pas trouver de destructeur.

L’exemple suivant génère l’C4150 :

```cpp
// C4150.cpp
// compile with: /W2
class  IncClass;

void NoDestruct( IncClass* pIncClass )
{
   delete pIncClass;
} // C4150, define class to resolve

int main()
{
}
```