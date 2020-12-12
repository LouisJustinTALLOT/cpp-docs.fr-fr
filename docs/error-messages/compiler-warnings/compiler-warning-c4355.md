---
description: 'En savoir plus sur : avertissement du compilateur C4355'
title: Avertissement du compilateur C4355
ms.date: 11/04/2016
f1_keywords:
- C4355
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
ms.openlocfilehash: fd4d38aae7a3728370c89cb2298438dbc0ba616c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180771"
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
