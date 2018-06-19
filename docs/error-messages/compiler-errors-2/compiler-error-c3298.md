---
title: Erreur du compilateur C3298 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3298
dev_langs:
- C++
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a67e155fb6cf0eab1ea085839d075d4d835de101
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250874"
---
# <a name="compiler-error-c3298"></a>Erreur du compilateur C3298
'contrainte_1' : impossible d’utiliser 'contrainte_2' en tant que contrainte, car 'contrainte_2' a la contrainte ref et 'contrainte_1' a la contrainte de valeur  
  
 Vous ne pouvez pas spécifier des caractéristiques mutuellement exclusives pour une contrainte. Par exemple, un paramètre de type générique ne peut pas être limité à la fois à un type valeur et à un type référence.  
  
 Pour plus d’informations, consultez [contraintes sur les paramètres de Type générique (C + c++ / CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3298.  
  
```  
// C3298.cpp  
// compile with: /clr /c   
generic<class T, class U>  
where T : ref class  
where U : T, value class   // C3298  
public ref struct R {};  
```