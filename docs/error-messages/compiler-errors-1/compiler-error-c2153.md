---
title: Erreur du compilateur C2153
ms.date: 11/04/2016
f1_keywords:
- C2153
helpviewer_keywords:
- C2153
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
ms.openlocfilehash: 1f03b196b7ddaae80dac1941cdde5be16acace5f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748682"
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
