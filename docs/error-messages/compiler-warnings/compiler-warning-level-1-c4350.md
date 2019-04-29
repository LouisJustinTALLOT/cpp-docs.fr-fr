---
title: Avertissement du compilateur (niveau 1) C4350
ms.date: 11/04/2016
f1_keywords:
- C4350
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
ms.openlocfilehash: 8f23751151d8d83c68608d926ef422d56dde41a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384203"
---
# <a name="compiler-warning-level-1-c4350"></a>Avertissement du compilateur (niveau 1) C4350

changement de comportement : 'membre1' appelé à la place de 'membre2'

Une rvalue ne peut pas être liée à une référence non const. Dans les versions de Visual C++ antérieures à Visual Studio 2003, il était possible de lier une rvalue à une référence non const dans une initialisation directe. Ce code génère désormais un avertissement.

Pour la compatibilité descendante, il est toujours possible de lier des rvalues à des références non const, mais les conversions standards sont préférables autant que possible.

Cet avertissement représente une modification du comportement du compilateur Visual C++ .NET 2002. Si activé, cet avertissement peut être généré pour le code correct. Par exemple, il peut être modifiée lorsque vous utilisez le **std::auto_ptr** modèle de classe.

Si vous obtenez cet avertissement, examinez votre code pour voir s’il dépend de liaison de rvalue à des références non const. Ajout d’une variable const à la référence ou en fournissant une surcharge de référence const supplémentaire peut résoudre le problème.

Cet avertissement est désactivé par défaut. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

L’exemple suivant génère l’erreur C4350 :

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