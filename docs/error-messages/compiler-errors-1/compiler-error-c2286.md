---
title: Erreur du compilateur C2286 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2286
dev_langs:
- C++
helpviewer_keywords:
- C2286
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ddfb523252572fb985b660f1d4dbf5b1d790df1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171924"
---
# <a name="compiler-error-c2286"></a>Erreur du compilateur C2286
pointeurs vers des membres de la représentation sous forme de 'identificateur' est déjà définie à 'héritage' - déclaration ignorée  
  
 Il existe deux représentations différentes de pointeurs vers membres pour la classe.  
  
 Pour plus d’informations, consultez [mots clés d’héritage](../../cpp/inheritance-keywords.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C2286 :  
  
```  
// C2286.cpp  
// compile with: /c  
class __single_inheritance X;  
class __multiple_inheritance X;   // C2286  
class  __multiple_inheritance Y;   // OK  
```