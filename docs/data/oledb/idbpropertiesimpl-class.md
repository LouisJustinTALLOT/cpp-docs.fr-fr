---
title: Idbpropertiesimpl, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
dev_langs:
- C++
helpviewer_keywords:
- IDBPropertiesImpl class
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3685e6a77e4293ef65b5ee98a0aa326500cfdb2d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105122"
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl, classe
Fournit une implémentation pour la `IDBProperties` interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T>   
class ATL_NO_VTABLE IDBPropertiesImpl   
   : public IDBProperties, public CUtlProps<T>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `IDBPropertiesImpl`.  
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)|Retourne les valeurs des propriétés dans les groupes de propriétés de Source de données, sources de données et d’initialisation qui sont actuellement définies sur l’objet de source de données ou les valeurs des propriétés dans le groupe de propriétés d’initialisation qui sont actuellement définies sur le énumérateur.|  
|[GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)|Retourne des informations sur toutes les propriétés prises en charge par le fournisseur.|  
|[SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)|Définit les propriétés dans les groupes de propriétés de Source de données et de l’initialisation, pour les objets de source de données, ou le groupe de propriétés d’initialisation, pour les énumérateurs.|  
  
## <a name="remarks"></a>Notes  
 [IDBProperties](https://msdn.microsoft.com/en-us/library/ms719607.aspx) est une interface obligatoire pour les objets de source de données et une interface facultative pour les énumérateurs. Toutefois, si un énumérateur expose [IDBInitialize](https://msdn.microsoft.com/en-us/library/ms713706.aspx), elle doit exposer `IDBProperties`. `IDBPropertiesImpl` implémente `IDBProperties` à l’aide d’une fonction statique définie par [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)