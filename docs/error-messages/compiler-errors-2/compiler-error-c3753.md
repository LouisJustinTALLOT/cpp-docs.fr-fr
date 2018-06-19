---
title: Erreur du compilateur C3753 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3753
dev_langs:
- C++
helpviewer_keywords:
- C3753
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0d9cb2db2729e5ccb1787e2505fdf0aed1f7a12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271958"
---
# <a name="compiler-error-c3753"></a>Erreur du compilateur C3753
une propriété générique n’est pas autorisée.  
  
 Listes de paramètres génériques peuvent uniquement apparaître sur les classes managées, des structures ou fonctions.  
  
 Pour plus d’informations, consultez [génériques](../../windows/generics-cpp-component-extensions.md) et [propriété](../../windows/property-cpp-component-extensions.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3753.  
  
```  
// C3753.cpp  
// compile with: /clr /c  
ref struct A {  
   generic <typename T>  
   property int i;   // C3753 error  
};  
```