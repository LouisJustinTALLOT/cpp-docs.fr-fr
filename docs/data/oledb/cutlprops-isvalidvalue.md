---
title: CUtlProps::IsValidValue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
dev_langs:
- C++
helpviewer_keywords:
- IsValidValue method
ms.assetid: 1164556e-8d98-429c-a396-fc9a699e0e97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0a37f0e0e9d415f9b7c78c8a619fd7fd66d24f28
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101963"
---
# <a name="cutlpropsisvalidvalue"></a>CUtlProps::IsValidValue
Permet de valider une valeur avant de définir une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,  
   DBPROP* pDBProp);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `iCurSet`  
 L’index dans le tableau de jeu de propriétés ; zéro s’il existe une seule propriété ensemble.  
  
 `pDBProp`  
 L’ID de propriété et la nouvelle valeur dans un [DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx) structure.  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard. La valeur par défaut valeur de retour est `S_OK`.  
  
## <a name="remarks"></a>Notes  
 Si vous avez des routines de validation à exécuter sur une valeur que vous allez utiliser pour définir une propriété, vous devez substituer cette fonction. Par exemple, vous pourriez valider **DBPROP_AUTH_PASSWORD** sur une table de mot de passe pour déterminer une valeur valide.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [CUtlProps, classe](../../data/oledb/cutlprops-class.md)