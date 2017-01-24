---
title: "is_error_code_enum, structure | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "future/std::is_error_code_enum"
dev_langs: 
  - "C++"
ms.assetid: 84ae4b99-66d2-41ba-9b50-645fcbe14630
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_error_code_enum, structure
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La spécialisation qui indique que l'[future\_errc](../Topic/future_errc%20Enumeration.md) est appropriée pour stocker [error\_code](../standard-library/error-code-class.md).  
  
## Syntaxe  
  
```  
template<>  
struct is_error_code_enum<Future_errc> : public true_type;  
```  
  
## Configuration requise  
 **En\-tête :** future  
  
 **Espace de noms :** std  
  
## Voir aussi  
 [Référence de fichiers d'en\-tête](../standard-library/cpp-standard-library-header-files.md)   
 [\<future\>](../standard-library/future.md)