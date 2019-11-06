---
title: Avertissement du compilateur (niveau 1) C4162
ms.date: 11/04/2016
f1_keywords:
- C4162
helpviewer_keywords:
- C4162
ms.assetid: 21ae3c92-501d-4689-ad7d-13753cb65eff
ms.openlocfilehash: 7e70898065a40a965b08b090bc59263acd918515
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624852"
---
# <a name="compiler-warning-level-1-c4162"></a>Avertissement du compilateur (niveau 1) C4162

'identificateur' : aucune fonction avec liaison C n’a été trouvée

Une fonction avec une liaison C est déclarée, mais est introuvable.

Pour résoudre cet avertissement, compilez dans un fichier. c (appelez le compilateur C).  Si vous devez appeler le C++ compilateur, placez extern "C" avant la déclaration de la fonction.

L’exemple suivant génère l’C4162

```cpp
// C4162.cpp
// compile with: /c /W1
unsigned char _bittest(long* a, long b);
#pragma intrinsic (_bittest)   // C4162

int main() {
   bool bit;
   long num = 78002;
   bit = _bittest(&num, 5);
}
```

Solution possible :

```cpp
// C4162b.cpp
// compile with: /c
extern "C"
unsigned char _bittest(long* a, long b);
#pragma intrinsic (_bittest)

int main() {
   bool bit;
   long num = 78002;
   bit = _bittest(&num, 5);
}
```