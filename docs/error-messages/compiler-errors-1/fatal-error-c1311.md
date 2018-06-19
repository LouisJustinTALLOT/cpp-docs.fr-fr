---
title: Erreur irrécupérable 1311 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1311
dev_langs:
- C++
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53b3759a5fec4b072f9a9b300670d61cb0d101c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226673"
---
# <a name="fatal-error-c1311"></a>Erreur irrécupérable 1311
Le format COFF ne peut pas initialiser de manière statique 'var' avec un nombre octet (s) d’une adresse  
  
 Une adresse dont la valeur n’est pas connue au moment de la compilation ne peut pas être affectée de manière statique à une variable dont le type possède un stockage inférieur à quatre octets.  
  
 Cette erreur peut se produire sur du code qui est sinon C++ valide.  
  
 L’exemple suivant montre une condition susceptibles de provoquer 1311.  
  
```  
char c = (char)"Hello, world";   // C1311  
char *d = (char*)"Hello, world";   // OK  
```