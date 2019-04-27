---
title: Erreur du compilateur C3628
ms.date: 11/04/2016
f1_keywords:
- C3628
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
ms.openlocfilehash: 581aae7e1f979b3dd39caf2ce3d263fdb856c56a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221683"
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
