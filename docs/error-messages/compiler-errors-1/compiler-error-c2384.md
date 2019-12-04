---
title: Erreur du compilateur C2384
ms.date: 11/04/2016
f1_keywords:
- C2384
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
ms.openlocfilehash: 2ce5c2f2540fbd2aca3509fa1dac55073a002abb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745261"
---
# <a name="compiler-error-c2384"></a>Erreur du compilateur C2384

'membre' : impossible d'appliquer __declspec(thread) à un membre d'une classe managée ou WinRT

Le modificateur de `__declspec` de [thread](../../cpp/thread.md) ne peut pas être utilisé sur un membre d’une classe managée ou Windows Runtime.

Le stockage local des threads de type statique dans du code managé peut être utilisé uniquement pour les DLL statiquement chargées. La DLL doit être chargée statiquement au démarrage du processus. Windows Runtime ne prend pas en charge le stockage local des threads.

La ligne suivante génère l'erreur C2384 et montre comment la résoudre dans du code C++/CLI :

```cpp
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
