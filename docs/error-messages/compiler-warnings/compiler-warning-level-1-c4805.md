---
title: Avertissement du compilateur (niveau 1) C4805
ms.date: 11/04/2016
f1_keywords:
- C4805
helpviewer_keywords:
- C4805
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
ms.openlocfilehash: c724af59b0654ae0f212eea038c48cb57f991aa3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175062"
---
# <a name="compiler-warning-level-1-c4805"></a>Avertissement du compilateur (niveau 1) C4805

'operation' : mélange risqué de type 'type' et type 'type' dans l’opération

Cet avertissement est généré pour les opérations de comparaison entre [bool](../../cpp/bool-cpp.md) et [int](../../c-language/integer-types.md). L’exemple suivant génère l’C4805 :

```cpp
// C4805.cpp
// compile with: /W1
int main() {
   int i = 1;
   bool b = true;

   if (i == b) {   // C4805, comparing bool and int variables
   }
}
```
