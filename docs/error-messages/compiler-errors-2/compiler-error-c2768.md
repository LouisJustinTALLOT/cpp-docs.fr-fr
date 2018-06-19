---
title: Erreur du compilateur C2768 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2768
dev_langs:
- C++
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ee0fd3fa213639e70199cfe5653ee2034bc39b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233381"
---
# <a name="compiler-error-c2768"></a>Erreur du compilateur C2768
'fonction' : utilisation non conforme d’arguments template explicites  
  
 Le compilateur n’a pas pu déterminer si une définition de fonction est censé pour être une spécialisation explicite d’un modèle de fonction ou si la définition de fonction est censé pour être d’une nouvelle fonction.  
  
 Cette erreur a été introduite dans Visual Studio .NET 2003, dans le cadre de ces améliorations de mise en conformité du compilateur.  
  
 L’exemple suivant génère l’erreur C2768 :  
  
```  
// C2768.cpp  
template<typename T>  
void f(T) {}  
  
void f<int>(int) {}   // C2768  
  
// an explicit specialization  
template<>  
void f<int>(int) {}   
  
// global nontemplate function overload  
void f(int) {}  
```