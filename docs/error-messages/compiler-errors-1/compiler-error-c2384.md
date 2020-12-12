---
description: 'En savoir plus sur : erreur du compilateur C2384'
title: Erreur du compilateur C2384
ms.date: 11/04/2016
f1_keywords:
- C2384
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
ms.openlocfilehash: f72db8d5beb871bbb9adf1cdc234769705db2b9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272511"
---
# <a name="compiler-error-c2384"></a>Erreur du compilateur C2384

'membre' : impossible d'appliquer __declspec(thread) à un membre d'une classe managée ou WinRT

Le [](../../cpp/thread.md) **`__declspec`** modificateur de thread ne peut pas être utilisé sur un membre d’une classe managée ou Windows Runtime.

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
