---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4626'
title: Avertissement du compilateur (niveau 4) C4626
ms.date: 11/04/2016
f1_keywords:
- C4626
helpviewer_keywords:
- C4626
ms.assetid: 7f822ff4-a4a3-4f17-b45b-e8b7b4659a14
ms.openlocfilehash: d528cab5a62abb7e91d4b7bb1487368bd44c6b41
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134210"
---
# <a name="compiler-warning-level-4-c4626"></a>Avertissement du compilateur (niveau 4) C4626

'classe dérivée' : l'opérateur d'assignation a été défini de manière implicite comme supprimé car un opérateur d'assignation de la classe de base est inaccessible ou supprimé

Un opérateur d'assignation a été supprimé ou n'était pas accessible dans une classe de base, et il n'a donc pas été généré pour une classe dérivée. Toute tentative pour assigner des objets de ce type provoquera une erreur du compilateur.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L'exemple suivant génère l'avertissement C4626 et montre comment le corriger :

```
// C4626
// compile with: /W4
#pragma warning(default : 4626)
class B
{
// public:
   B& operator = (const B&)
   {
      return *this;
   }
};

class D : public B
{

}; // C4626 - to fix, make B's copy constructor public

int main()
{
   D m;
   D n;
   // m = n;   // this line will cause an error
}
```
