---
title: Erreur du compilateur C3299 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3299
dev_langs:
- C++
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecaa0b8d3ee1a3d33a5d750cc559da63e036ff16
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33249899"
---
# <a name="compiler-error-c3299"></a>Erreur du compilateur C3299
'fonction_membre' : impossible de spécifier les contraintes, elles sont héritées de la méthode de base  
  
 Quand vous substituez une fonction membre générique, vous ne pouvez pas spécifier des clauses de contrainte (car la répétition de contraintes sous-entend que les contraintes ne sont pas héritées).  
  
 Les clauses de contrainte de la fonction générique que vous substituez seront héritées.  
  
 Pour plus d’informations, consultez [contraintes sur les paramètres de Type générique (C + c++ / CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3299 :  
  
```  
// C3299.cpp  
// compile with: /clr /c  
public ref struct R {  
   generic<class T>   
   where T : R  
   virtual void f();  
};  
  
public ref struct S : R {  
   generic<class T>   
   where T : R   // C3299  
   virtual void f() override;  
};  
```