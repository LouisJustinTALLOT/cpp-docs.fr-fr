---
title: Erreur du compilateur C3412 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3412
dev_langs:
- C++
helpviewer_keywords:
- C3412
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c5b2c86b91160eb7ae342b39ea6a63ffad364bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250641"
---
# <a name="compiler-error-c3412"></a>Erreur du compilateur C3412
'template' : Impossible de spécialiser le modèle dans la portée actuelle  
  
 Impossible de spécialiser un modèle à la portée de la classe dans global ou de la portée espace de noms.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3412.  
  
```  
// C3412.cpp  
template <class T>  
struct S {  
   template <>  
   struct S<int> {};   // C3412 in a class  
};  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre une résolution possible.  
  
```  
// C3412b.cpp  
// compile with: /c  
template <class T>  
struct S {};  
  
template <>  
struct S<int> {};  
```