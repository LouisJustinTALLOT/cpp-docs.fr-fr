---
title: Erreur du compilateur C2053 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2053
dev_langs:
- C++
helpviewer_keywords:
- C2053
ms.assetid: 13324c85-13a8-4996-bd42-a31bfe7ff80f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ace887e096ca0761f08843a033dc6391cb26aa99
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33165293"
---
# <a name="compiler-error-c2053"></a>Erreur du compilateur C2053
'identificateur' : incompatibilité de chaînes étendues  
  
 La chaîne large est assignée à un type incompatible.  
  
 L’exemple suivant génère l’erreur C2053 :  
  
```  
// C2053.c  
int main() {  
   char array[] = L"Rika";   // C2053  
}  
```