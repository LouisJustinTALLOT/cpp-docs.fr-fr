---
title: Compilateur Warning (level 1) C4165
ms.date: 11/04/2016
f1_keywords:
- C4165
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
ms.openlocfilehash: 4d6377730e262efafb38f5e714989e9075a77a04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534379"
---
# <a name="compiler-warning-level-1-c4165"></a>Compilateur Warning (level 1) C4165

'HRESULT' est converti en 'bool' ; Êtes-vous sûr que c’est ce que vous voulez ?

Lorsque vous utilisez un HRESULT dans un [si](../../cpp/if-else-statement-cpp.md) instruction, le HRESULT sera converti en un [bool](../../cpp/bool-cpp.md) , sauf si vous explicitement un test de la variable comme HRESULT. Cet avertissement est désactivé par défaut.

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4165.

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