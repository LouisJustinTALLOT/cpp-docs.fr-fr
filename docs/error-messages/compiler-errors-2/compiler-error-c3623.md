---
description: 'En savoir plus sur : erreur du compilateur C3623'
title: Erreur du compilateur C3623
ms.date: 11/04/2016
f1_keywords:
- C3623
helpviewer_keywords:
- C3623
ms.assetid: a0341b45-062a-4f67-beb9-ba74201ed1ed
ms.openlocfilehash: 042e530dc1529307c90b05771d662aaed4b60775
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222981"
---
# <a name="compiler-error-c3623"></a>Erreur du compilateur C3623

'variable' : champs de bits non pris en charge dans les types managés ou WinRT

L'utilisation de champs de bits n'est pas autorisée sur les variables dans une classe managée ou WinRT.

L'exemple suivant génère l'erreur C3623 :

```cpp
// C3623.cpp
// compile with: /clr
using namespace System;
ref class CMyClass {
public:
   int i : 1;   // C3623
};

int main() {
   CMyClass^ pMyClass = gcnew CMyClass();
   pMyClass->i = 3;
   Console::Out->WriteLine(pMyClass->i);
}
```
