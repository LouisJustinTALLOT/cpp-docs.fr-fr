---
title: "Erreur du compilateur C3412 | Microsoft Docs"
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
  - "C3412"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3412"
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Erreur du compilateur C3412
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'modèle' : impossible de spécialiser le modèle dans la portée actuelle  
  
 Un modèle ne peut pas être spécialisé au niveau de la portée d'une classe, seulement au niveau de la portée globale ou de l'espace de noms.  
  
## Exemple  
 L'exemple suivant génère l'erreur C3412 :  
  
```  
// C3412.cpp  
template <class T>  
struct S {  
   template <>  
   struct S<int> {};   // C3412 in a class  
};  
```  
  
## Exemple  
 L'exemple suivant illustre une résolution possible.  
  
```  
// C3412b.cpp  
// compile with: /c  
template <class T>  
struct S {};  
  
template <>  
struct S<int> {};  
```