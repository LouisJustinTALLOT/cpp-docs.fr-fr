---
title: Erreur du compilateur C2766 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2766
dev_langs:
- C++
helpviewer_keywords:
- C2766
ms.assetid: 8032f4ca-6827-4f04-9c61-c44643c85cc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0cd83bc18e30fb9b183e27597b1c5902f734c88a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234210"
---
# <a name="compiler-error-c2766"></a>Erreur du compilateur C2766
spécialisation explicite ; 'specialization' a déjà été définie  
  
 Les spécialisations explicites en double ne sont pas autorisées. Pour plus d’informations, consultez [spécialisation explicite des modèles de fonction](../../cpp/explicit-specialization-of-function-templates.md).  
  
 L’exemple suivant génère l’erreur C2766 :  
  
```  
// C2766.cpp  
// compile with: /c  
template<class T>   
struct A {};  
  
template<>   
struct A<int> {};  
  
template<>   
struct A<int> {};   // C2766  
// try the following line instead  
// struct A<char> {};  
```