---
description: 'En savoir plus sur : erreur du compilateur C2153'
title: Erreur du compilateur C2153
ms.date: 11/04/2016
f1_keywords:
- C2153
helpviewer_keywords:
- C2153
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
ms.openlocfilehash: 0b5ded0908f3c12033f1c2b3b034b41b52e847cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181291"
---
# <a name="compiler-error-c2153"></a>Erreur du compilateur C2153

les constantes hex doivent avoir au moins un chiffre hexadécimal

Les constantes hexadécimales 0x, 0X et \x ne sont pas valides. Au moins un chiffre hexadécimal doit suivre x ou X.

L’exemple suivant génère l’C2153 :

```cpp
// C2153.cpp
int main() {
   int a= 0x;    // C2153
   int b= 0xA;   // OK
}
```
