---
title: Erreur du compilateur C2217 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2217
dev_langs:
- C++
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7c60ac95be1a0b21ed2cb7df43117ff7ece7a39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172262"
---
# <a name="compiler-error-c2217"></a>Erreur du compilateur C2217
'attribut1' requiert 'attribut2'  
  
 Le premier attribut de fonction nécessite le deuxième attribut.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes  
  
1.  Interruption (`__interrupt`) fonction déclarée comme `near`. Interrompre les fonctions doivent être `far`.  
  
2.  Fonction d’interruption déclarée avec `__stdcall`, ou `__fastcall`. Fonctions d’interruption doivent conventions d’appel C d’utilisation.  
  
## <a name="example"></a>Exemple  
 C2217 peut également se produire si vous tentez de lier un délégué à une fonction CLR qui accepte un nombre variable d’arguments. Si la fonction a également la surcharge de tableau param, utilisez à la place. L’exemple suivant génère C2217.  
  
```  
// C2217.cpp  
// compile with: /clr  
using namespace System;  
delegate void MyDel(String^, Object^, Object^, ...);   // C2217  
delegate void MyDel2(String ^, array<Object ^> ^);   // OK  
  
int main() {  
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);  
   array<Object ^ > ^ x = gcnew array<Object ^>(2);  
   x[0] = safe_cast<Object^>(0);  
   x[1] = safe_cast<Object^>(1);  
  
   // wl("{0}, {1}", 0, 1);  
   wl("{0}, {1}", x);  
}  
```