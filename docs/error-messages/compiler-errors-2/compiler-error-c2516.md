---
title: Erreur du compilateur C2516 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2516
dev_langs: C++
helpviewer_keywords: C2516
ms.assetid: cd3accc1-0179-4a13-9587-616908c4ad1d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5df8d59b8e812e2c3eeb450f4ea811b6c837f085
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2516"></a>Erreur du compilateur C2516
'nom' : n’est pas une classe de base juridique  
  
 La classe est dérivée d’un nom de type défini par un `typedef` instruction.  
  
 L’exemple suivant génère l’erreur C2516 :  
  
```  
// C2516.cpp  
typedef unsigned long ulong;  
class C : public ulong {}; // C2516  
```