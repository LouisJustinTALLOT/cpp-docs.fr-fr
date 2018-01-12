---
title: Erreur du compilateur C2724 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2724
dev_langs: C++
helpviewer_keywords: C2724
ms.assetid: 4e4664bc-8c96-4156-b79f-03436f532ea8
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22808821d94502e414867e1fc8b96d40f5b79d1c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2724"></a>Erreur du compilateur C2724
'identificateur' : 'static' ne doit pas être utilisé sur les fonctions membres définies au niveau de la portée du fichier  
  
 Les fonctions membres statiques doivent être déclarées avec une liaison externe.  
  
 L’exemple suivant génère l’erreur C2724 :  
  
```  
// C2724.cpp  
class C {  
   static void func();  
};  
  
static void C::func(){};   // C2724  
// try the following line instead  
// void C::func(){};  
```