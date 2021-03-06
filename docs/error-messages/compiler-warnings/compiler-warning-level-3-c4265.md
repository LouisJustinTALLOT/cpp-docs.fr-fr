---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4265'
title: Avertissement du compilateur (niveau 3) C4265
ms.date: 11/04/2016
f1_keywords:
- C4265
helpviewer_keywords:
- C4265
ms.assetid: 20547159-6f30-4cc4-83aa-927884c8bb4c
ms.openlocfilehash: f7ad04d59b9896ce91f4a135f205664885af8f68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344170"
---
# <a name="compiler-warning-level-3-c4265"></a>Avertissement du compilateur (niveau 3) C4265

'classe' : la classe a des fonctions virtuelles, mais le destructeur n’est pas virtuel

Quand une classe a des fonctions virtuelles mais un destructeur non virtuel, les objets du type peuvent ne pas être détruits correctement lorsque la classe est détruite par le biais d’un pointeur de classe de base.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’C4265 :

```cpp
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
