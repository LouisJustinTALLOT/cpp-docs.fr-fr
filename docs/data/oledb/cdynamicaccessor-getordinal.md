---
title: CDynamicAccessor::GetOrdinal | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicAccessor.GetOrdinal
- ATL::CDynamicAccessor::GetOrdinal
- CDynamicAccessor::GetOrdinal
- ATL.CDynamicAccessor.GetOrdinal
- GetOrdinal
dev_langs:
- C++
helpviewer_keywords:
- GetOrdinal method
ms.assetid: 2095b71c-a7a4-4034-89a1-77a78cb9633f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e935340265d0239240ce47169aecb4f3210a106f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094395"
---
# <a name="cdynamicaccessorgetordinal"></a>CDynamicAccessor::GetOrdinal
Récupère le numéro de colonne donné un nom de colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      bool GetOrdinal(const CHAR* pColumnName,  
   DBORDINAL* pOrdinal) const throw();  

bool GetOrdinal(const WCHAR* pColumnName,  
   DBORDINAL* pOrdinal) const throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pColumnName`  
 [in] Pointeur vers une chaîne de caractères contenant le nom de colonne.  
  
 *pOrdinal*  
 [out] Pointeur vers le numéro de colonne.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne **true** si une colonne portant le nom spécifié est trouvée. Sinon, cette fonction retourne **false**.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)