---
title: Avertissement du compilateur (niveau 2) C4150
ms.date: 11/04/2016
f1_keywords:
- C4150
helpviewer_keywords:
- C4150
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
ms.openlocfilehash: a3993d2b993205c98de968ca893f24f703b3b635
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218141"
---
# <a name="compiler-warning-level-2-c4150"></a>Avertissement du compilateur (niveau 2) C4150

suppression d’un pointeur vers un type incomplet’type'; aucun destructeur appelé

L' **`delete`** opérateur est appelé pour supprimer un type qui a été déclaré mais pas défini, de sorte que le compilateur ne peut pas trouver de destructeur.

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
