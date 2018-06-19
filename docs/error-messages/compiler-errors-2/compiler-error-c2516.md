---
title: Erreur du compilateur C2516 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2516
dev_langs:
- C++
helpviewer_keywords:
- C2516
ms.assetid: cd3accc1-0179-4a13-9587-616908c4ad1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e8a23eda6aa263cdfbf0ef7b4fb777f4158dd06
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226504"
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