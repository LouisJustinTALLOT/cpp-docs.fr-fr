---
title: Erreur du compilateur C3295 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3295
dev_langs:
- C++
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25fd1a04e0be46943b4fd183b470b369f810a0d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253955"
---
# <a name="compiler-error-c3295"></a>Erreur du compilateur C3295
'#pragma pragma' ne peut être utilisé qu’au niveau de la portée globale ou de la portée espace de noms  
  
 Certains pragmas ne peuvent pas être utilisés dans une fonction.  Consultez [Directives Pragma et mot clé _pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) pour plus d’informations.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3295.  
  
```  
// C3295.cpp  
int main() {  
   #pragma managed   // C3295  
}  
```