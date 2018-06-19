---
title: Erreur du compilateur C2785 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2785
dev_langs:
- C++
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc0ca6235e0fd4bdd22330e807464e96280ae461
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234027"
---
# <a name="compiler-error-c2785"></a>Erreur du compilateur C2785
'déclaration1' et 'déclaration2' ont des types de retournés différents  
  
 Le type de retour de la spécialisation de modèle de fonction diffère du type de retour du modèle de fonction principal.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Vérifiez toutes les spécialisations du modèle de fonction par souci de cohérence.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C2785 :  
  
```  
// C2785.cpp  
// compile with: /c  
template<class T> void f(T);  
  
template<> int f(int); // C2785  
template<> void f(int); // OK  
```