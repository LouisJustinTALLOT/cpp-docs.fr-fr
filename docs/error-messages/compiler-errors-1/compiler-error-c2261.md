---
title: Erreur du compilateur C2261 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2261
dev_langs:
- C++
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45050daf3149cd813fb23b5814be5fe49c375f03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170464"
---
# <a name="compiler-error-c2261"></a>Erreur du compilateur C2261
'string' : référence d’assembly n’est pas valide et ne peut pas être résolue  
  
 Une valeur n’est pas valide.  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> est utilisé pour spécifier un assembly friend. Par exemple, si.dll souhaite spécifier b.dll comme assembly friend, vous devez spécifier (dans.dll) : InternalsVisibleTo("b"). Le runtime permet ensuite à b.dll accéder à tous les éléments de.dll (à l’exception des types privés).  
  
 Pour plus d’informations sur la syntaxe correcte lors de la spécification des assemblys friend, consultez [assemblys Friend (C++)](../../dotnet/friend-assemblies-cpp.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C2261.  
  
```  
// C2261.cpp  
// compile with: /clr /c  
using namespace System::Runtime::CompilerServices;  
[assembly: InternalsVisibleTo("a,a,a")];   // C2261  
[assembly: InternalsVisibleTo("a.a")];   // OK  
[assembly: InternalsVisibleTo("a")];   // OK  
```