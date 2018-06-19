---
title: CUtlProps, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CUtlProps
dev_langs:
- C++
helpviewer_keywords:
- CUtlProps class
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6b39edb002c254f5d122d574ac389c2fd4df8b38
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101342"
---
# <a name="cutlprops-class"></a>CUtlProps, classe
Implémente des propriétés pour un large éventail d’interfaces de propriété OLE DB (par exemple, `IDBProperties`, `IDBProperties`, et `IRowsetInfo`).  
  
## <a name="syntax"></a>Syntaxe

```cpp
template < class T >  
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 La classe qui contient la `BEGIN_PROPSET_MAP`.  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[GetPropValue](../../data/oledb/cutlprops-getpropvalue.md)|Obtient une propriété à partir d’un jeu de propriétés.|  
|[IsValidValue](../../data/oledb/cutlprops-isvalidvalue.md)|Permet de valider une valeur avant de définir une propriété.|  
|[OnInterfaceRequested](../../data/oledb/cutlprops-oninterfacerequested.md)|Gère les demandes d’une interface facultative lorsqu’un consommateur appelle une méthode sur une interface de création d’objet.|  
|[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)|Appelé après la définition d’une propriété de gérer des propriétés chaînées.|  
|[SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)|Définit une propriété dans un jeu de propriétés.|  
  
## <a name="remarks"></a>Notes  
 La plupart de cette classe est un détail d’implémentation.  
  
 `CUtlProps` contient deux membres pour définir les propriétés en interne : [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md) et [SetPropValue](../../data/oledb/cutlprops-setpropvalue.md).  
  
 Pour plus d’informations sur les macros utilisées dans un mappage de jeu de propriétés, consultez [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) et [END_PROPSET_MAP](../../data/oledb/end-propset-map.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)