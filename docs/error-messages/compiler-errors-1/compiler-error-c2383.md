---
title: Erreur du compilateur C2383 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2383
dev_langs:
- C++
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81624ccd7f4857cb2f7d8474d393a9743ab1a2b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33196491"
---
# <a name="compiler-error-c2383"></a>Erreur du compilateur C2383
'*symbole*' : les arguments par défaut ne sont pas autorisés sur ce symbole  
  
 Le compilateur C++ n’autorise pas les arguments par défaut sur les pointeurs vers des fonctions.  
  
 Ce code a été accepté par le compilateur Visual C++ dans les versions antérieures de Visual Studio 2005, mais génère maintenant une erreur. Pour le code qui fonctionne dans toutes les versions de Visual C++, n’assignez pas de valeur par défaut à un argument de pointeur de fonction.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C2383 et illustre une solution possible :  
  
```cpp  
// C2383.cpp  
// compile with: /c   
void (*pf)(int = 0);   // C2383  
void (*pf)(int);   // OK  
```