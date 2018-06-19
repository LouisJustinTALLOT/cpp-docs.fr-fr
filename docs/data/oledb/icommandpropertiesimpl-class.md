---
title: Icommandpropertiesimpl, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
dev_langs:
- C++
helpviewer_keywords:
- ICommandPropertiesImpl class
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 25be1548bd41f832a007f102c138fc01f8818774
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098999"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl, classe
Fournit une implémentation de la [ICommandProperties](https://msdn.microsoft.com/en-us/library/ms723044.aspx) interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ICommandPropertiesImpl   
   : public ICommandProperties, public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe dérivée  
  
 `PropClass`  
 Votre classe de propriétés.  
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/icommandpropertiesimpl-getproperties.md)|Retourne la liste des propriétés dans le groupe de propriétés d’ensemble de lignes qui sont actuellement demandé pour l’ensemble de lignes.|  
|[SetProperties](../../data/oledb/icommandpropertiesimpl-setproperties.md)|Définit les propriétés dans le groupe de propriétés d’ensemble de lignes.|  
  
## <a name="remarks"></a>Notes  
 Ce champ est obligatoire sur les commandes. L’implémentation est fournie par une fonction statique définie par le [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) (macro).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)