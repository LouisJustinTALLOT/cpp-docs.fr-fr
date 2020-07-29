---
title: Avertissement du compilateur C4355
ms.date: 11/04/2016
f1_keywords:
- C4355
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
ms.openlocfilehash: 2725db0e37f8e60f37ec1b534306f516fe10be33
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223341"
---
# <a name="compiler-warning-c4355"></a>Avertissement du compilateur C4355

'this' : utilisé dans la liste des initialiseurs membre de base

Le **`this`** pointeur est valide uniquement dans les fonctions membres non statiques. Elle ne peut pas être utilisée dans la liste d’initialiseurs pour une classe de base.

Les constructeurs de classe de base et les constructeurs de membre de classe sont appelés avant le **`this`** constructeur. En effet, vous avez passé un pointeur vers un objet non construit à un autre constructeur. Si ces autres constructeurs accèdent à des membres ou appellent des fonctions membres, le résultat n’est pas défini. Vous ne devez pas utiliser le **`this`** pointeur tant que la construction n’est pas terminée.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’C4355 :

```cpp
// C4355.cpp
// compile with: /w14355 /c
#include <tchar.h>

class CDerived;
class CBase {
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function() = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase {
public:
   CDerived() : CBase(this) {};   // C4355 "this" used in derived c'tor
   virtual void function() {};
};

CBase::~CBase() {
   m_pDerived -> function();
}

int main() {
   CDerived myDerived;
}
```
