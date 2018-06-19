---
title: Erreur du compilateur C2432 | Documents Microsoft
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
ms.openlocfilehash: 8dfbadf2c7d53cce799efbd5f10286b31bb3cd3b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33196933"
---
# <a name="compiler-error-c2432"></a>Erreur du compilateur C2432
référence non conforme à des données 16 bits dans 'identificateur'  
  
 Un registre 16 bits est utilisé comme un index ou un Registre de base. Le compilateur ne prend pas en charge faisant référence à des données 16 bits. les registres 16 bits ne peut pas servir d’index ou la base de registres lors de la compilation de code 32 bits.  
  
 L’exemple suivant génère l’erreur C2432 :  
  
```  
// C2432.cpp  
// processor: x86  
int main() {  
   _asm mov eax, DWORD PTR [bx]   // C2432  
}  
```