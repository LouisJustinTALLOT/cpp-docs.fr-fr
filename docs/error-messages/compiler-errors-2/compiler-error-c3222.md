---
title: Erreur du compilateur C3222 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3222
dev_langs:
- C++
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 424c0f1011d984dff59d3d952347ad4f7b90f515
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33249952"
---
# <a name="compiler-error-c3222"></a>Erreur du compilateur C3222
’paramètre’ : impossible de déclarer des arguments par défaut pour des fonctions membres d’un type managé ou WinRT ou des fonctions génériques  
  
Il n’est pas autorisé de déclarer un paramètre de méthode avec un argument par défaut. Une forme surchargée de la méthode est une façon de contourner ce problème. Autrement dit, définissez une méthode portant le même nom sans paramètres, puis initialisez la variable dans le corps de la méthode.  
  
L'exemple suivant génère l'erreur C3222 :  
  
```  
// C3222_2.cpp  
// compile with: /clr  
public ref class G {  
   void f( int n = 0 );   // C3222  
};  
```  
