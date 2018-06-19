---
title: Erreur du compilateur C3381 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3381
dev_langs:
- C++
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a27961694bc5fad4080d8aceaf2f1cb65404319c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251096"
---
# <a name="compiler-error-c3381"></a>Erreur du compilateur C3381
'assembly' : les spécificateurs d’accès assembly ne sont disponibles dans le code compilé avec l’option /clr  
  
 Les types natifs peuvent être visibles à l’extérieur de l’assembly, mais vous pouvez spécifier uniquement l’accès à l’assembly pour les types natifs dans un **/CLR** compilation.  
  
 Pour plus d’informations, consultez [visibilité de Type](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) et [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3381.  
  
```  
// C3381.cpp  
// compile with: /c  
public class A {};   // C3381  
```