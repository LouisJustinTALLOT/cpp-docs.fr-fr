---
title: Avertissement du compilateur C4355 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4355
dev_langs:
- C++
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 44833c8e640002f2f94d44938641fa3c1fa33db7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115305"
---
# <a name="compiler-warning-c4355"></a>Avertissement du compilateur C4355

'this' : utilisé dans la liste des initialiseurs membre de base

Le **cela** pointeur est valide uniquement dans les fonctions membres non statiques. Il ne peut pas être utilisé dans la liste d’initialiseurs pour une classe de base.

Les constructeurs de classe de base et de membre de classe sont appelées avant **cela** constructeur. En effet, vous avez passé un pointeur vers un objet non construit pour un autre constructeur. Si ces autres constructeurs accéder aux membres ou appellent des fonctions membres cela, le résultat sera non défini. Vous ne devez pas utiliser le **cela** pointeur jusqu'à la fin de la construction.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère C4355 :

```
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