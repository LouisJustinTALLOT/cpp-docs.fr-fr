---
description: 'En savoir plus sur : erreur du compilateur C2432'
title: Erreur du compilateur C2432
ms.date: 11/04/2016
f1_keywords:
- C2432
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
ms.openlocfilehash: 392108e0fd16952bc8bcf43682dc163c664171ea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190014"
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
