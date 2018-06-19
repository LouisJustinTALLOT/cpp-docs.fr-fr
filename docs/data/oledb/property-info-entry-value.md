---
title: PROPERTY_INFO_ENTRY_VALUE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- PROPERTY_INFO_ENTRY_VALUE
dev_langs:
- C++
helpviewer_keywords:
- PROPERTY_INFO_ENTRY_VALUE macro
ms.assetid: 9690f7f3-fb20-4a7e-a75f-8a3a1cb1ce0d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cbd216a3358385a0a0c1c61e8e3f31a1fd3c8946
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104657"
---
# <a name="propertyinfoentryvalue"></a>PROPERTY_INFO_ENTRY_VALUE
Représente une propriété spécifique dans un jeu de propriétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID  
, value )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *dwPropID*  
 [in] Valeur [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) qui peut être utilisée en combinaison avec le GUID du jeu de propriétés pour identifier une propriété.  
  
 *valeur*  
 [in] Valeur de propriété de type `DWORD`.  
  
## <a name="remarks"></a>Notes  
 Avec cette macro, vous pouvez spécifier directement la valeur de propriété de type `DWORD`. Pour définir la propriété valeur par défaut définie dans ATLDB. H, utilisez [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Pour définir la valeur, les indicateurs et les options de la propriété, utilisez [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).  
  
## <a name="example"></a>Exemple  
 Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros pour les modèles du fournisseur OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)