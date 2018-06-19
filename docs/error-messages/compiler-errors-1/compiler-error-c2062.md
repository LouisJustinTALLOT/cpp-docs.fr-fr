---
title: C2062 d’erreur du compilateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2062
dev_langs:
- C++
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d11151a8e842796e4a5a8d45956782421daa1c70
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168657"
---
# <a name="compiler-error-c2062"></a>C2062 d’erreur du compilateur
type inattendu ' type'  
  
 Le compilateur ne vous attendiez pas un nom de type.  
  
 L’exemple suivant génère l’erreur C2062 :  
  
```  
// C2062.cpp  
// compile with: /c  
struct A {  : int l; };   // C2062  
struct B { private: int l; };   // OK  
```  
  
 L’erreur C2062 peut également se produire en raison de la façon dont le compilateur gère les types indéfinis dans la liste de paramètres d’un constructeur. Si le compilateur rencontre un type indéfini de (mal orthographié ?), il suppose que le constructeur est une expression et émet l’erreur C2062. Pour résoudre, utilisez uniquement des types définis dans une liste de paramètres du constructeur.