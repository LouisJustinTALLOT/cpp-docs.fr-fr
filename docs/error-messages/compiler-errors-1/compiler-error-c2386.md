---
title: Erreur du compilateur C2386 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2386
dev_langs:
- C++
helpviewer_keywords:
- C2386
ms.assetid: aaaa1284-34a0-4da2-8547-9fcbb559dae0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5bcbcb3502dba1497500a9bdd5b46345b729a26
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33223944"
---
# <a name="compiler-error-c2386"></a>Erreur du compilateur C2386
'symbole' : un symbole avec ce nom existe déjà dans la portée actuelle  
  
 Vous avez essayé de créer un alias d’espace de noms, mais le nom que vous avez choisi existe déjà.  
  
 L’exemple suivant génère l’erreur C2386 :  
  
```  
// C2386.cpp  
namespace A {  
   int k;  
}  
  
int i;  
namespace i = A;   // C2386, i already exists  
```