---
title: Avertissement du compilateur (niveau 1) C4350
ms.date: 11/04/2016
f1_keywords:
- C4350
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
ms.openlocfilehash: 890ecd4fcec1212fa04a58b0eaab8c2eb4206763
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187217"
---
# <a name="compiler-warning-level-1-c4350"></a>Avertissement du compilateur (niveau 1) C4350

changement de comportement : 'membre1' appelé à la place de 'membre2'

Une rvalue ne peut pas être liée à une référence non const. Dans les versions de C++ Visual antérieures à visual studio 2003, il était possible de lier une rvalue à une référence non const dans une initialisation directe. Ce code émet désormais un avertissement.

Pour la compatibilité descendante, il est toujours possible de lier rvalues à des références non const, mais les conversions standard sont préférables dans la mesure du possible.

Cet avertissement représente un changement de comportement du compilateur Visual C++ .NET 2002. S’il est activé, cet avertissement peut être fourni pour le code correct. Par exemple, elle peut être fournie lors de l’utilisation du modèle de classe **std :: auto_ptr** .

Si vous obtenez cet avertissement, examinez votre code pour voir s’il dépend de la liaison de rvalues à des références non const. L’ajout d’un const à la référence ou la fourniture d’une surcharge const-Reference supplémentaire peut résoudre le problème.

Cet avertissement est désactivé par défaut. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

L’exemple suivant génère l’C4350 :

```cpp
// C4350.cpp
// compile with: /W1
#pragma warning (default : 4350)
class A {};

class B
{
public:
   B(B&){}
   // try the following instead:
   // B(const B&){}

   B(A){}
   operator A(){ return A();}
};

B source() { return A(); }

int main()
{
   B ap(source());   // C4350
}
```
