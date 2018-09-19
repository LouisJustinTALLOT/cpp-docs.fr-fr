---
title: Erreur du compilateur C2432 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2432
dev_langs:
- C++
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ca8c2c62415b6ec3c29c820a23677a87a2695c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055908"
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