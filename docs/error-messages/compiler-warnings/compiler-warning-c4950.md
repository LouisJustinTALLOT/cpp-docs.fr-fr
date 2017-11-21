---
title: Avertissement du compilateur C4950 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4950
dev_langs: C++
helpviewer_keywords: C4950
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6a922a0ee324afcf5f263abe2189e4071c5575c7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4950"></a>Avertissement du compilateur C4950
'type_or_member' : marqué comme obsolète  
  
Un membre ou type a été marqué comme obsolète avec la <xref:System.ObsoleteAttribute> attribut.  
  
L’avertissement C4950 est toujours présenté comme une erreur. Vous pouvez désactiver cet avertissement à l’aide de la [avertissement](../../preprocessor/warning.md) directive pragma ou [/wd](../../build/reference/compiler-option-warning-level.md) option du compilateur.  
  
## <a name="example"></a>Exemple  
L’exemple suivant génère l’erreur C4950 :  
  
```cpp  
// C4950.cpp  
// compile with: /clr  
using namespace System;  
  
// Any reference to Func3 should generate an error with message  
[System::ObsoleteAttribute("Will be removed in next version", true)]  
Int32 Func3(Int32 a, Int32 b) {  
   return (a + b);  
}  
  
int main() {  
   Int32 MyInt3 = ::Func3(2, 2);   // C4950  
}  
```