---
title: Erreur du compilateur C3141 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3141
dev_langs:
- C++
helpviewer_keywords:
- C3141
ms.assetid: b4fd65c3-50cc-46cd-8de0-6a6d24cb9cda
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 00266db4fde48b175b9374ca31a89b15ca13ced2
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3141"></a>Erreur du compilateur C3141
'nom_interface' : les interfaces ne prennent en charge que l’héritage public  
  
 Les interfaces définies avec la [interface (ou __interface)](../../cpp/interface.md) mot clé prennent uniquement en charge l’héritage public.  
  
 L’exemple suivant génère l’erreur C3141 :  
  
```  
// C3141.cpp  
__interface IBase {};  
__interface IDerived1 : protected IBase {};  // C3141  
__interface IDerived2 : private IBase {};    // C3141  
```
