---
title: Erreur du compilateur C2891 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2891
dev_langs:
- C++
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01741d1cc67f0045c46ab392212625b9e1a2d8ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246368"
---
# <a name="compiler-error-c2891"></a>Erreur du compilateur C2891
'paramètre' : ne peut pas prendre l’adresse d’un paramètre de modèle  
  
 Vous ne pouvez pas prendre l’adresse d’un paramètre de modèle, sauf si elle est une lvalue. Paramètres de type ne sont pas lvalues, car ils n’ont aucun adresse. Également, les valeurs non-type dans les listes de paramètres de modèle qui ne sont pas des valeurs lvalues n’ont pas d’une adresse. Il s’agit d’un exemple de code qui provoque l’erreur du compilateur C2891, car la valeur passée comme paramètre de modèle est une copie généré par le compilateur de l’argument de modèle.  
  
```  
template <int i> int* f() { return &i; }  
```  
  
 Les paramètres de modèle sont des lvalues, tels que des types référence, permettre avoir leur adresse effectuées.  
  
```  
template <int& r> int* f() { return &r; }  
```  
  
 Pour corriger cette erreur, ne prennent pas l’adresse d’un paramètre de modèle, sauf si elle est une lvalue.