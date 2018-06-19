---
title: Erreur du compilateur C3836 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3836
dev_langs:
- C++
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45a2eda2567e63771ed4c8919945e34ee41be1cb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267392"
---
# <a name="compiler-error-c3836"></a>Erreur du compilateur C3836
constructeur statique n’est pas autorisé à avoir une liste d’initialiseurs de membres  
  
 Une classe managée ne peut pas avoir un constructeur statique qui possède également une liste d’initialisation de membre. Les constructeurs statiques sont appelés par le common language runtime pour l’initialisation, l’initialisation des membres de données statiques de classe.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3836 :  
  
```  
// C3836a.cpp  
// compile with: /clr  
ref class M  
{  
   static int s_i;  
  
public:  
   static M() :  s_i(1234)   // C3836, delete initializer to resolve  
   {  
   }  
};  
  
int main()  
{  
}  
```  
