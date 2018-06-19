---
title: Compilateur avertissement (niveau 4) C4559 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4559
dev_langs:
- C++
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c853fa55482604d97c29653fadb06b0afdd44977
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295348"
---
# <a name="compiler-warning-level-4-c4559"></a>Avertissement du compilateur (niveau 4) C4559
'fonction' : redéfinition ; la fonction gagne __declspec (modifier)  
  
 Une fonction a été redéfinie ou redéclarée et la deuxième définition ou déclaration un __**declspec** modificateur (***modificateur***). Cet avertissement possède un caractère informatif. Pour résoudre cet avertissement, supprimez une des définitions.  
  
 L’exemple suivant génère l’erreur C4559 :  
  
```  
// C4559.cpp  
// compile with: /W4 /LD  
void f();  
__declspec(noalias) void f();   // C4559  
```