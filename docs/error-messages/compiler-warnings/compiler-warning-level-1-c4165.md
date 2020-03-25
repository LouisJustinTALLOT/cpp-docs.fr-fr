---
title: Avertissement du compilateur (niveau 1) C4165
ms.date: 11/04/2016
f1_keywords:
- C4165
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
ms.openlocfilehash: bb036f7672a074e859d3e19083e256bd80c93578
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176095"
---
# <a name="compiler-warning-level-1-c4165"></a>Avertissement du compilateur (niveau 1) C4165

'HRESULT’est en cours de conversion en’bool'; êtes-vous sûr de vouloir cela ?

Lors de l’utilisation d’un HRESULT dans une instruction [If](../../cpp/if-else-statement-cpp.md) , la valeur HRESULT est convertie en valeur [booléenne](../../cpp/bool-cpp.md) , sauf si vous testez explicitement la variable en tant que HRESULT. Cet avertissement est désactivé par défaut.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4165

```cpp
// C4165.cpp
// compile with: /W1
#include <windows.h>
#pragma warning(1:4165)

extern HRESULT hr;
int main() {
   if (hr) {
   // try either of the following ...
   // if (FAILED(hr)) { // C4165 expected
   // if (hr != S_OK) {
   }
}
```
