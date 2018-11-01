---
title: Erreur du compilateur C2432
ms.date: 11/04/2016
f1_keywords:
- C2432
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
ms.openlocfilehash: e2983d966a6290ce19713c63feb502c8ffc74bf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631235"
---
# <a name="compiler-error-c2432"></a>Erreur du compilateur C2432

référence non conforme à des données de 16 bits dans 'identificateur'

Un registre 16 bits est utilisé comme un index ou d’un Registre de base. Le compilateur ne prend pas en charge le référencement des données 16 bits. registres 16 bits ne peut pas servir de registres de base ou d’index lors de la compilation de code 32 bits.

L’exemple suivant génère l’erreur C2432 :

```
// C2432.cpp
// processor: x86
int main() {
   _asm mov eax, DWORD PTR [bx]   // C2432
}
```