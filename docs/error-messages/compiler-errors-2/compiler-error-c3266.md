---
title: Erreur du compilateur C3266
ms.date: 11/04/2016
f1_keywords:
- C3266
helpviewer_keywords:
- C3266
ms.assetid: 7375c099-acb7-42f6-898d-57cfefa010b8
ms.openlocfilehash: d93056116ebf2f4646dc34f848b073fe6401b9db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365856"
---
# <a name="compiler-error-c3266"></a>Erreur du compilateur C3266

'classe' : un constructeur de classe doit avoir une liste de paramètres 'void'

Les constructeurs de classe dans une classe qui utilise la programmation /clr ne peuvent pas prendre de paramètres.

L’exemple suivant génère l’erreur C3266 :

```
// C3266.cpp
// compile with: /clr

ref class X {
   static X(int i) { // C3266
   // try the following line instead
   // static X() {
   }
};

int main() {
}
```
