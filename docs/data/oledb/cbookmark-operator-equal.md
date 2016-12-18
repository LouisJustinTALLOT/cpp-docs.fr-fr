---
title: "CBookmark::operator = | Microsoft Docs"
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
  - "CBookmark<0>::operator="
  - "CBookmark<0>.operator="
  - "ATL.CBookmark.operator="
  - "CBookmark::operator="
  - "ATL.CBookmark<0>.operator="
  - "ATL::CBookmark<0>::operator="
  - "CBookmark.operator="
  - "ATL::CBookmark::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "= (opérateur), avec les modèles OLE DB (C++)"
  - "opérateur =, signets"
  - "= (opérateur), signets"
ms.assetid: 23805af4-aedd-47ad-bef4-21d902463797
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBookmark::operator =
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Attribue un objet de `CBookmark` à un autre objet.  
  
## Syntaxe  
  
```  
  
      CBookmark& operator =(   
   const CBookmark& bookmark    
) throw( );  
```  
  
## Notes  
 Cet opérateur est nécessaire uniquement dans **CBookmark\<0\>**.  
  
## Configuration requise  
 **En\-tête :** atldbcli.h  
  
## Voir aussi  
 [CBookmark, classe](../../data/oledb/cbookmark-class.md)