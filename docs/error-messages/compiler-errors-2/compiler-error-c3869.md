---
title: "Erreur du compilateur C3869 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3869"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3869"
ms.assetid: 85b2ad72-95c1-4ed6-9761-6ef66c3802b7
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Erreur du compilateur C3869
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La contrainte gcnew ne contient pas de liste de paramètres vide '\(\)'  
  
 La contrainte spéciale `gcnew` a été spécifiée sans la liste de paramètres vide.  Pour plus d'informations, consultez [Constraints on Generic Type Parameters \(C\+\+\/CLI\)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
## Exemple  
 L'exemple suivant génère l'erreur C3869 :  
  
```  
// C3869.cpp  
// compile with: /c /clr  
using namespace System;  
generic <typename T>  
where T : gcnew   // C3869  
// try the following line instead  
// where T : gcnew()  
ref class List {};  
```