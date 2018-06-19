---
title: Erreur du compilateur C3087 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3087
dev_langs:
- C++
helpviewer_keywords:
- C3087
ms.assetid: 4f5bdd52-a853-4f02-b160-6868e9190b9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6e1446d8d062f97e9161e62fae5052580174c83
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245307"
---
# <a name="compiler-error-c3087"></a>Erreur du compilateur C3087
'argument_nommé' : l’appel de 'attribut' initialise déjà ce membre  
  
 Un argument nommé a été spécifié dans le même bloc d’attributs comme argument sans nom pour la même valeur. Spécifiez uniquement un argument nommé ou sans nom.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3087 :  
  
```  
// C3087.cpp  
// compile with: /c  
[idl_quote("quote1", text="quote2")];   // C3087  
[idl_quote(text="quote3")];   // OK  
[idl_quote("quote4")];   // OK  
```