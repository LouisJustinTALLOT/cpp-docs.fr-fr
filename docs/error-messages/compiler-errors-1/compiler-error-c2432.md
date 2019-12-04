---
title: Erreur du compilateur C2432
ms.date: 11/04/2016
f1_keywords:
- C2432
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
ms.openlocfilehash: d4234626bc246d6da87be68b03d44562dd5990ff
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744509"
---
# <a name="compiler-error-c2432"></a>Erreur du compilateur C2432

référence non conforme à des données 16 bits dans’identifier'

Un registre 16 bits est utilisé comme un registre d’index ou de base. Le compilateur ne prend pas en charge le référencement de données 16 bits. les registres 16 bits ne peuvent pas être utilisés comme registres de base ou d’index lors de la compilation pour du code 32 bits.

L’exemple suivant génère l’C2432 :

```cpp
// C2432.cpp
// processor: x86
int main() {
   _asm mov eax, DWORD PTR [bx]   // C2432
}
```
