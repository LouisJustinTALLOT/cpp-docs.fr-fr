---
title: Erreur du compilateur C2384
ms.date: 11/04/2016
f1_keywords:
- C2384
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
ms.openlocfilehash: 1909fb999dd0f60224029b726f773c11fa69ee40
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460318"
---
# <a name="compiler-error-c2384"></a>Erreur du compilateur C2384

'membre' : impossible d'appliquer __declspec(thread) à un membre d'une classe managée ou WinRT

Le [thread](../../cpp/thread.md) `__declspec` modificateur ne peut pas être utilisé sur un membre d’un objet ou de la classe Windows Runtime.

Le stockage local des threads de type statique dans du code managé peut être utilisé uniquement pour les DLL statiquement chargées. La DLL doit être chargée statiquement au démarrage du processus. Windows Runtime ne prend pas en charge le stockage local des threads.

La ligne suivante génère l'erreur C2384 et montre comment la résoudre dans du code C++/CLI :

```
// C2384.cpp
// compile with: /clr /c
public ref class B {
public:
   __declspec( thread ) static int tls_i = 1;   // C2384

   // OK - declare with attribute instead
   [System::ThreadStaticAttribute]
   static int tls_j;
};
```