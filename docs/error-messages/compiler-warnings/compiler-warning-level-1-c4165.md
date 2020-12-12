---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4165'
title: Avertissement du compilateur (niveau 1) C4165
ms.date: 11/04/2016
f1_keywords:
- C4165
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
ms.openlocfilehash: 7b82db7421493b1687b35e61da988b68a577e8a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267038"
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
