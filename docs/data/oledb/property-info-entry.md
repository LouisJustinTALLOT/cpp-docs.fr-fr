---
title: PROPERTY_INFO_ENTRY | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- PROPERTY_INFO_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- PROPERTY_INFO_ENTRY macro
ms.assetid: f7bd23d6-52b4-4d6a-aa9a-1fca9834c8dc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 763eeff3611817b591d4dcbe1f6197f774d4016d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="propertyinfoentry"></a>PROPERTY_INFO_ENTRY
Représente une propriété spécifique dans un jeu de propriétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
PROPERTY_INFO_ENTRY(dwPropID)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *dwPropID*  
 [in] Valeur [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) qui peut être utilisée en combinaison avec le GUID du jeu de propriétés pour identifier une propriété.  
  
## <a name="remarks"></a>Notes  
 Cette macro attribue à la propriété de type `DWORD` une valeur par défaut définie dans ATLDB.H. Pour attribuer à la propriété une valeur de votre choix, utilisez [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md). Pour définir en même temps [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) et [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx) pour la propriété, utilisez [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).  
  
## <a name="example"></a>Exemple  
 Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros pour les modèles du fournisseur OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)