---
title: Avertissement du compilateur (niveau 3) C4265
ms.date: 11/04/2016
f1_keywords:
- C4265
helpviewer_keywords:
- C4265
ms.assetid: 20547159-6f30-4cc4-83aa-927884c8bb4c
ms.openlocfilehash: f06e70f88bc0a34e2feecba19da8dd9edc630230
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402188"
---
# <a name="compiler-warning-level-3-c4265"></a>Avertissement du compilateur (niveau 3) C4265

'classe' : classe possède des fonctions virtuelles, mais le destructeur n’est pas virtuel

Lorsqu’une classe possède des fonctions virtuelles mais un destructeur non virtuel, les objets du type ne peuvent pas être supprimés correctement quand la classe est détruite via un pointeur de classe de base.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’erreur C4265 :

```
// C4265.cpp
// compile with: /W3 /c
#pragma warning(default : 4265)
class B
{
public:
   virtual void vmf();

   ~B();
   // try the following line instead
   // virtual ~B();
};   // C4265

int main()
{
   B b;
}
```