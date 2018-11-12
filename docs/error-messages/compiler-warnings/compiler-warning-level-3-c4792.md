---
title: Avertissement du compilateur (niveau 3) C4792
ms.date: 11/04/2016
f1_keywords:
- C4792
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
ms.openlocfilehash: adf233673c4b654927aa9488565adf6ceef5d3e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501190"
---
# <a name="compiler-warning-level-3-c4792"></a>Avertissement du compilateur (niveau 3) C4792

fonction 'function' déclarée à l’aide de sysimport et référencée à partir du code natif ; bibliothèque d’importation requise pour établir la liaison

Une fonction native qui a été importée dans le programme avec DllImport a été appelée à partir d’une fonction non managée. Vous devez donc établir une liaison à la bibliothèque d’importation pour la DLL.

Vous ne pouvez pas résoudre cet avertissement en modifiant le code ou le mode de compilation. Pour désactiver cet avertissement, utilisez le pragma [warning](../../preprocessor/warning.md) .

L’exemple suivant génère l’avertissement C4792 :

```
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