---
title: Erreur du compilateur C3539 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3539
dev_langs:
- C++
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f704bd283ab5228a8988d587707e978aa5b49e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256400"
---
# <a name="compiler-error-c3539"></a>Erreur du compilateur C3539
'type' : un argument template ne peut pas être un type contenant 'auto'  
  
 Le type d’argument template indiqué ne peut pas contenir une utilisation de la `auto` (mot clé).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Ne spécifiez pas l’argument template avec le `auto` (mot clé).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant donne C3539.  
  
```  
// C3539.cpp  
// Compile with /Zc:auto  
template<class T> class C{};  
int main()  
{  
   C<auto> c;   // C3539  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [auto, mot clé](../../cpp/auto-keyword.md)