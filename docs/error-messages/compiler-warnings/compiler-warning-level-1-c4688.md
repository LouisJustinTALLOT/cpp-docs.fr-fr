---
title: Compilateur avertissement (niveau 1) C4688 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4688
dev_langs:
- C++
helpviewer_keywords:
- C4688
ms.assetid: a027df3c-b2b8-4c49-8539-c2bc42db74e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 503f7783748407415ecd3a4ddbaafeb601b7c2b1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286576"
---
# <a name="compiler-warning-level-1-c4688"></a>Avertissement du compilateur (niveau 1) C4688
'constraint' : la liste des contraintes contient un type privé d’assembly 'type'  
  
 Une liste de contraintes possède un type privé d’assembly, ce qui signifie qu’il ne sera pas accessible en dehors de l’assembly. Pour plus d’informations, consultez la page [Génériques](../../windows/generics-cpp-component-extensions.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’avertissement C4688.  
  
```  
// C4688.cpp  
// compile with: /clr /c /W1  
ref struct A {};   // private type  
public ref struct B {};  
  
// Delete the following 3 lines to resolve.  
generic <class T>   
where T : A   // C4688  
public ref struct M {};  
  
generic <class T>   
where T : B  
public ref struct N {};  
```