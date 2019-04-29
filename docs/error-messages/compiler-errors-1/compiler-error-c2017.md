---
title: Erreur du compilateur C2017
ms.date: 11/04/2016
f1_keywords:
- C2017
helpviewer_keywords:
- C2017
ms.assetid: 1083eed9-9906-4a97-883c-54e52d7e82cd
ms.openlocfilehash: f4a17557e5e4ca1eb3f69561c964c9bbe24bb70d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303781"
---
# <a name="compiler-error-c2017"></a>Erreur du compilateur C2017

séquence d’échappement non conforme

Une séquence d’échappement, tels que \t, apparaît en dehors d’un caractère ou une chaîne constante.

L’exemple suivant génère l’erreur C2017 :

```
// C2017.cpp
int main() {
   char test1='a'\n;   // C2017
   char test2='a\n';   // ok
}
```

C2017 peut se produire lorsque l’opérateur stringize est utilisé avec des chaînes qui incluent des séquences d’échappement.

L’exemple suivant génère l’erreur C2017 :

```
// C2017b.cpp
#define TestDfn(x) AfxMessageBox(#x)
TestDfn(CString("\\") + CString(".h\"\n\n"));   // C2017
```