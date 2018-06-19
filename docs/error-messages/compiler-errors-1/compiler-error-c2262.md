---
title: Erreur du compilateur C2262 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2262
dev_langs:
- C++
helpviewer_keywords:
- C2262
ms.assetid: 727d1c6e-53e8-40e5-b7b8-6a7ac2011727
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 199c5d109cf994a8f69e29f893cd13dd7028ca82
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170763"
---
# <a name="compiler-error-c2262"></a>Erreur du compilateur C2262
'spécificateurs_attributs' : aucune version, culture ou architecture de processeur ne peut être spécifiée pour les déclarations InternalsVisible  
  
 L’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> n’a pas été spécifié correctement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C2262 :  
  
```  
// C2262.cpp  
// compile with: /clr /c  
using namespace System::Runtime::CompilerServices;  
[assembly: InternalsVisibleTo("assembly_name, version=1.2.3.7")];   // C2262  
[assembly: InternalsVisibleTo("assembly_name ")];   // OK  
```