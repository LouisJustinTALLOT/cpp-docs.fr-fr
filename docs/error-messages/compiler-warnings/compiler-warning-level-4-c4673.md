---
title: Avertissement du compilateur (niveau 4) C4673
ms.date: 11/04/2016
f1_keywords:
- C4673
helpviewer_keywords:
- C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
ms.openlocfilehash: cd53aeb7f767b06c017c64caa55c916aa1e2b9c9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990576"
---
# <a name="compiler-warning-level-4-c4673"></a>Avertissement du compilateur (niveau 4) C4673

levée de’identifier’les types suivants ne seront pas pris en compte sur le site d’interception

Un objet Throw ne peut pas être géré dans le bloc **catch** . Chaque type qui ne peut pas être géré est listé dans la sortie d’erreur immédiatement après la ligne contenant cet avertissement. Chaque type non géré a son propre avertissement. Pour plus d’informations, lisez l’avertissement pour chaque type spécifique.

L’exemple suivant génère l’C4673 :

```cpp
// C4673.cpp
// compile with: /EHsc /W4
class Base {
private:
   char * m_chr;
public:
   Base() {
      m_chr = 0;
   }

   ~Base() {
      if(m_chr)
         delete m_chr;
   }
};

class Derv : private Base {
public:
   Derv() {}
   ~Derv() {}
};

int main() {
   try {
      Derv D1;
      // delete previous line, uncomment the next line to resolve
      // Base D1;
      throw D1;   // C4673
   }

   catch(...) {}
}
```
