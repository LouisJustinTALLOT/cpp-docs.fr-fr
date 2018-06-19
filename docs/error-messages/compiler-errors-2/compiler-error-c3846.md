---
title: Erreur du compilateur C3846 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3846
dev_langs:
- C++
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97d5650d1743ba379ce065d4051bfed807a1df71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268024"
---
# <a name="compiler-error-c3846"></a>Erreur du compilateur C3846
'symbole' : Impossible d’importer le symbole de 'assembly2' : car 'symbole' a déjà été importé à partir d’un autre assembly 'assembly1'  
  
 Un symbole n’a pas pu être importé à partir d’un assembly référencé, car il a été précédemment importé à partir d’un assembly référencé.  
  
## <a name="example"></a>Exemple
L’exemple suivant génère l’erreur C3846 :  
  
```  
// C3846a.cpp  
// compile with: /LD /clr  
public ref struct G  
{  
};  
```  
  
 Et ensuite, compilez cela :  
  
```  
// C3846b.cpp  
// compile with: /clr  
#using "c3846a.dll"  
#using "c3846a.obj"   // C3846  
  
int main()  
{  
}  
```  
