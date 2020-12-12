---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4792'
title: Avertissement du compilateur (niveau 3) C4792
ms.date: 11/04/2016
f1_keywords:
- C4792
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
ms.openlocfilehash: 37dc805477e3150eedaffe7eb5d900b7903b1d48
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332134"
---
# <a name="compiler-warning-level-3-c4792"></a>Avertissement du compilateur (niveau 3) C4792

fonction 'function' déclarée à l’aide de sysimport et référencée à partir du code natif ; bibliothèque d’importation requise pour établir la liaison

Une fonction native qui a été importée dans le programme avec DllImport a été appelée à partir d’une fonction non managée. Vous devez donc établir une liaison à la bibliothèque d’importation pour la DLL.

Vous ne pouvez pas résoudre cet avertissement en modifiant le code ou le mode de compilation. Pour désactiver cet avertissement, utilisez le pragma [warning](../../preprocessor/warning.md) .

L’exemple suivant génère l’avertissement C4792 :

```cpp
// C4792.cpp
// compile with: /clr /W3
// C4792 expected
using namespace System::Runtime::InteropServices;
[DllImport("msvcrt")]
extern "C" int __cdecl puts(const char *);
int main() {}

// Uncomment the following line to resolve.
// #pragma warning(disable : 4792)
#pragma unmanaged
void func(void){
   puts("test");
}
```
