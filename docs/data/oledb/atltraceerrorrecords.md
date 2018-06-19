---
title: AtlTraceErrorRecords | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
dev_langs:
- C++
helpviewer_keywords:
- AtlTraceErrorRecords function
ms.assetid: b83970b3-dc2a-445c-9142-f52218719905
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: afea3c3ef1f169e5f1cb5fc675c74b54da1be0d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093345"
---
# <a name="atltraceerrorrecords"></a>AtlTraceErrorRecords
Exporte les informations d’enregistrement de l’erreur OLE DB à l’unité de vidage si une erreur est retournée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hErr`  
 [in] Un `HRESULT` retourné par une fonction membre de modèles du consommateur OLE DB.  
  
## <a name="remarks"></a>Notes  
 Si `hErr` n’est pas `S_OK`, `AtlTraceErrorRecords` exporte les informations de l’enregistrement d’erreur OLE DB à l’unité de vidage (le **déboguer** onglet de la fenêtre de sortie ou un fichier). Les informations de l’enregistrement d’erreur, qui sont obtenues à partir du fournisseur, incluent le numéro de ligne, la source, description, fichier d’aide, contexte et GUID pour chaque entrée enregistrement d’erreur. `AtlTraceErrorRecords` exporte ces informations uniquement dans les versions debug. Dans les versions release, il s’agit d’un stub vide qui est optimisé out.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et fonctions globales pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [CDBErrorInfo, classe](../../data/oledb/cdberrorinfo-class.md)