---
title: L’avertissement de C4165 du compilateur (niveau 1) d’avertissement. | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4165
dev_langs:
- C++
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39487999f2aa74a5600d84d71917712e03b2d626
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277564"
---
# <a name="compiler-warning-level-1-c4165"></a>Avertissement de C4165 du compilateur (niveau 1) d’avertissement.
'HRESULT' est converti en 'bool' ; Êtes-vous sûr que c’est ce que vous voulez ?  
  
Lorsque vous utilisez un HRESULT dans un [si](../../cpp/if-else-statement-cpp.md) instruction, le HRESULT est converti en un [bool](../../cpp/bool-cpp.md) , sauf si vous explicitement un test de la variable comme HRESULT. Cet avertissement est désactivé par défaut.  
  
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