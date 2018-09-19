---
title: Erreur du compilateur C3628 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3628
dev_langs:
- C++
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a65dc33c5381b063c3adb01072e930075108649
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037370"
---
# <a name="compiler-error-c3628"></a>Erreur du compilateur C3628

'base' classe' : géré ou WinRTclasses prennent uniquement en charge l’héritage public

Une tentative a tenté d’utiliser un managé ou WinRT classe en tant qu’un [privé](../../cpp/private-cpp.md) ou [protégé](../../cpp/protected-cpp.md) classe de base. Managé ou WinRT classe peut uniquement être utilisée comme classe de base avec [public](../../cpp/public-cpp.md) accès.

L'exemple suivant génère l'erreur C3628 et montre comment la corriger :

```
// C3628a.cpp
// compile with: /clr
ref class B {
};

ref class D : private B {   // C3628

// The following line resolves the error.
// ref class D : public B {
};

int main() {
}
```
