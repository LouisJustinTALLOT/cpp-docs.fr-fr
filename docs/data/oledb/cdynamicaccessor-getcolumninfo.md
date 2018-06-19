---
title: CDynamicAccessor::GetColumnInfo | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetColumnInfo
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- GetColumnInfo method
ms.assetid: 7f2102ea-b7cc-4714-812f-3ca2857f4b9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0c9fe862f08fc9ecfa280dcbb55f48e14427d6ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091892"
---
# <a name="cdynamicaccessorgetcolumninfo"></a>CDynamicAccessor::GetColumnInfo
Retourne les métadonnées de colonne requises par la plupart des consommateurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetColumnInfo(IRowset* pRowset,   
   DBORDINAL* pColumns,   
   DBCOLUMNINFO** ppColumnInfo,   
   OLECHAR** ppStringsBuffer) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRowset`  
 [in] Un pointeur vers le [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) interface.  
  
 *pColumns*  
 [out] Pointeur vers la mémoire dans lequel retourner le nombre de colonnes dans l’ensemble de lignes ; Ce nombre inclut la colonne des signets, si elle existe.  
  
 *ppColumnInfo*  
 [out] Pointeur vers la mémoire dans lequel retourner un tableau de **DBCOLUMNINFO** structures. Consultez la section « Structures DBCOLUMNINFO » dans [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) dans les *de référence du programmeur OLE DB*.  
  
 `ppStringsBuffer`  
 [out] Pointeur vers la mémoire dans lequel retourner un pointeur vers le stockage pour toutes les valeurs de chaîne (noms utilisés au sein de *columnid* ou *pwszName*) dans un bloc d’allocation unique.  
  
## <a name="return-value"></a>Valeur de retour  
 Un de la norme `HRESULT` valeurs.  
  
## <a name="remarks"></a>Notes  
 Consultez [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) dans les *de référence du programmeur OLE DB* pour plus d’informations sur les types de données **DBORDINAL**, **DBCOLUMNINFO**, et **OLECHAR**.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)