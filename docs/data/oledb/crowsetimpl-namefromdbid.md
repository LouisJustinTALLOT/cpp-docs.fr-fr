---
title: CRowsetImpl::NameFromDBID | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
dev_langs: C++
helpviewer_keywords: NameFromDBID method
ms.assetid: 6aa5b074-90c7-4434-adfd-c64c13e76c78
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8eb218546c299ffa95874bd8a3fcb2b16fa07a2a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetimplnamefromdbid"></a>CRowsetImpl::NameFromDBID
Extrait une chaîne à partir d’un **DBID** et la copie à le `bstr` passé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT CRowsetBaseImpl::NameFromDBID(  
   DBID* pDBID,  
   CComBSTR& bstr,  
   bool bIndex   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pDBID*  
 [in] Un pointeur vers le **DBID** à partir de laquelle extraire une chaîne.  
  
 `bstr`  
 [in] A [CComBSTR](../../atl/reference/ccombstr-class.md) référence pour placer une copie de la **DBID** chaîne.  
  
 `bIndex`  
 [in] **true** si un index **DBID**; **false** si une table **DBID**.  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard. Selon que la **DBID** est une table ou un index (indiqué par `bIndex`), la méthode sera soit retour **DB_E_NOINDEX** ou **DB_E_NOTABLE**.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est appelée par le `CRowsetImpl` implémentations de [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) et [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [CRowsetImpl, classe](../../data/oledb/crowsetimpl-class.md)