---
title: Erreur du compilateur C3065 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3065
dev_langs:
- C++
helpviewer_keywords:
- C3065
ms.assetid: e7a0bc69-1c68-459e-a7c4-93c65609ff7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7a6bb966fd973a9ede675e98761e8649ca20c27
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246955"
---
# <a name="compiler-error-c3065"></a>Erreur du compilateur C3065
la déclaration de propriété au niveau d'une portée sans classe n'est pas autorisée  
  
 Le modificateur __declspec de [property](../../cpp/property-cpp.md) a été utilisé en dehors d’une classe.  Une propriété ne peut être déclarée qu’à l’intérieur d’une classe.  
  
 L’exemple suivant génère l’erreur C3065 :  
  
```  
// C3065.cpp  
// compile with: /c  
__declspec(property(get=get_i)) int i;   // C3065  
  
class x {  
public:  
   __declspec(property(get=get_i)) int i;   // OK  
};  
```