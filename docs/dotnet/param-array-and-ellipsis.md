---
title: Tableau param et points de suspension | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: function overloading, argument matching
ms.assetid: 492e3f6c-1c4c-4e0c-a358-72f2d39c30be
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f6d256fd48d8c9f206619e6baa9a50a0278d30c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="param-array-and-ellipsis"></a>Tableau Param et points de suspension
Priorité du tableau param pour résoudre des appels de fonction surchargée a été modifiée à partir des Extensions managées pour C++ vers Visual C++.  
  
 Dans les Extensions managées et la nouvelle syntaxe, il n’existe aucune prise en charge explicite du tableau param que c# et Visual Basic prennent en charge. Au lieu de cela, un tableau ordinaire signale avec un attribut, comme suit :  
  
```  
void Trace1( String* format, [ParamArray]Object* args[] );  
void Trace2( String* format, Object* args[] );  
```  
  
 Alors que les deux procédures paraissent identiques, le `ParamArray` attribut marque ceci pour c# ou autres langages de CLR comme un tableau prenant un nombre variable d’éléments à chaque appel. Le changement de comportement des programmes entre les Extensions managées et la nouvelle syntaxe se trouve dans la résolution d’une fonction surchargée définie dans lequel une instance déclare des points de suspension et une seconde déclare un `ParamArray` attribut, comme dans l’exemple suivant fourni par Artur Laksberg.  
  
```  
int fx(...); // 1  
int fx( [ParamArray] Int32[] ); // 2  
```  
  
 Dans les Extensions managées, les points de suspension a priorité sur l’attribut qui est raisonnable, car l’attribut n’est pas un aspect formel du langage. Toutefois, dans la nouvelle syntaxe, le tableau param est maintenant pris en charge directement dans le langage, et il est prioritaire sur les points de suspension, car il est plus fortement typé. Par conséquent, dans les Extensions managées, l’appel  
  
```  
fx( 1, 2 );  
```  
  
 correspond à `fx(...)` dans la nouvelle syntaxe, elle est résolue à la `ParamArray` instance. Dans le cas improbable où le comportement de votre programme dépend de l’appel de l’instance de points de suspension plutôt que du `ParamArray`, vous devez modifier la signature ou l’appel.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications d’ordre général apportées au langage (C++-CLI)](../dotnet/general-language-changes-cpp-cli.md)