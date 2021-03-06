---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4673'
title: Avertissement du compilateur (niveau 4) C4673
ms.date: 11/04/2016
f1_keywords:
- C4673
helpviewer_keywords:
- C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
ms.openlocfilehash: 557a8a0049a5870b0ae824f96a96c12ee01c0842
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134002"
---
# <a name="compiler-warning-level-4-c4673"></a>Avertissement du compilateur (niveau 4) C4673

levée de’identifier’les types suivants ne seront pas pris en compte sur le site d’interception

Un objet Throw ne peut pas être géré dans le **`catch`** bloc. Chaque type qui ne peut pas être géré est listé dans la sortie d’erreur immédiatement après la ligne contenant cet avertissement. Chaque type non géré a son propre avertissement. Pour plus d’informations, lisez l’avertissement pour chaque type spécifique.

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
