---
title: "IErrorRecordsImpl::GetRecordCount | Microsoft Docs"
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
  - "IErrorRecordsImpl::GetRecordCount"
  - "ATL::IErrorRecordsImpl::GetRecordCount"
  - "IErrorRecordsImpl.GetRecordCount"
  - "ATL.IErrorRecordsImpl.GetRecordCount"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetRecordCount (méthode)"
ms.assetid: 44388bc3-1c64-4491-a1c5-28f3497ef040
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IErrorRecordsImpl::GetRecordCount
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Retourne le nombre d'enregistrements dans l'objet d'enregistrement OLE DB.  
  
## Syntaxe  
  
```  
  
      STDMETHOD( GetRecordCount )(  
   ULONG *pcRecords   
);  
```  
  
#### Paramètres  
 Consultez [IErrorRecords::GetRecordCount](https://msdn.microsoft.com/en-us/library/ms722724.aspx) du *Guide de référence du programmeur OLE DB*.  
  
## Configuration requise  
 **En\-tête :** atldb.h  
  
## Voir aussi  
 [IErrorRecordsImpl, classe](../../data/oledb/ierrorrecordsimpl-class.md)