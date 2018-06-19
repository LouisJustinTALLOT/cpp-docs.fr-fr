---
title: Erreur du compilateur C3665 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3665
dev_langs:
- C++
helpviewer_keywords:
- C3665
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e55be277f5016be2440987864e67dfc54f4cd094
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263906"
---
# <a name="compiler-error-c3665"></a>Erreur du compilateur C3665
'destructeur' : spécificateur 'mot_clé' non autorisé sur un destructeur/finaliseur de substitution  
  
 Un mot clé a été utilisé qui n’est pas autorisé sur un destructeur ou un finaliseur.  
  
 Par exemple, un nouvel emplacement ne peut pas être demandé sur un destructeur ou un finaliseur.  Pour plus d’informations, consultez [substitutions explicites](../../windows/explicit-overrides-cpp-component-extensions.md) et [destructeurs et finaliseurs](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
 L’exemple suivant génère l’erreur C3665 :  
  
```  
// C3665.cpp  
// compile with: /clr  
public ref struct R {  
   virtual ~R() { }  
   virtual void a() { }  
};  
  
public ref struct S : R {  
   virtual ~S() new {}   // C3665  
   virtual void a() new {}   // OK  
};  
```