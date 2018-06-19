---
title: Compilateur avertissement (niveau 4) C4366 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4366
dev_langs:
- C++
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12410a567cb55d6dea74b8e5e595009e56b1071f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293700"
---
# <a name="compiler-warning-level-4-c4366"></a>Avertissement du compilateur (niveau 4) C4366
Le résultat de l’opérateur 'opérateur' unaire peut être non aligné  
  
 Si un membre de structure ne peut jamais être non aligné en raison de la compression, le compilateur vous avertit que son adresse est attribué à un pointeur aligné. Par défaut, tous les pointeurs sont alignées.  
  
 Pour résoudre l’erreur C4366, modifiez l’alignement de la structure ou déclarez le pointeur avec le [__unaligned](../../cpp/unaligned.md) (mot clé).  
  
 Pour plus d’informations, consultez __unaligned et [pack](../../preprocessor/pack.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4366.  
  
```  
// C4366.cpp  
// compile with: /W4 /c  
// processor: IPF x64  
#pragma pack(1)  
struct X {  
   short s1;  
   int s2;  
};  
  
int main() {  
   X x;  
   short * ps1 = &x.s1;   // OK  
   int * ps2 = &x.s2;   // C4366  
}  
```