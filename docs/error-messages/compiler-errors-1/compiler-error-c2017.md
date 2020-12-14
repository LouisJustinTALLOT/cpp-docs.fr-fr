---
description: 'En savoir plus sur : erreur du compilateur C2017'
title: Erreur du compilateur C2017
ms.date: 11/04/2016
f1_keywords:
- C2017
helpviewer_keywords:
- C2017
ms.assetid: 1083eed9-9906-4a97-883c-54e52d7e82cd
ms.openlocfilehash: c70bd39cb15a0eff5d209a6fc76e3dc44b990d8e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220901"
---
# <a name="compiler-error-c2017"></a>Erreur du compilateur C2017

séquence d’échappement non conforme

Une séquence d’échappement, telle que \t, apparaît en dehors d’une constante de chaîne ou de caractère.

L’exemple suivant génère l’C2017 :

```cpp
// C2017.cpp
int main() {
   char test1='a'\n;   // C2017
   char test2='a\n';   // ok
}
```

C2017 peut se produire lorsque l’opérateur String est utilisé avec des chaînes qui incluent des séquences d’échappement.

L’exemple suivant génère l’C2017 :

```cpp
// C2017b.cpp
#define TestDfn(x) AfxMessageBox(#x)
TestDfn(CString("\\") + CString(".h\"\n\n"));   // C2017
```
