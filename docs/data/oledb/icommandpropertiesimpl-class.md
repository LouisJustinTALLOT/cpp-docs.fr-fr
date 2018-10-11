---
title: Icommandpropertiesimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- GetProperties
- ICommandPropertiesImpl.SetProperties
- ICommandPropertiesImpl::SetProperties
- SetProperties
dev_langs:
- C++
helpviewer_keywords:
- ICommandPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 432fb57b1505733b4f9cbda4e558699a8108a3ad
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083994"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl, classe

Fournit une implémentation de la [ICommandProperties](/previous-versions/windows/desktop/ms723044) interface.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ICommandPropertiesImpl   
   : public ICommandProperties, public CUtlProps<PropClass>  
```  
  
### <a name="parameters"></a>Paramètres  

*T*<br/>
Votre classe dérivée  
  
*PropClass*<br/>
Votre classe de propriétés.  

## <a name="requirements"></a>Configuration requise  

**En-tête :** atldb.h  
  
## <a name="members"></a>Membres  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[GetProperties](#getproperties)|Retourne la liste des propriétés dans le groupe de propriétés d’ensemble de lignes qui sont actuellement demandées pour l’ensemble de lignes.|  
|[SetProperties](#setproperties)|Définit les propriétés dans le groupe de propriétés d’ensemble de lignes.|  
  
## <a name="remarks"></a>Notes  

Ce champ est obligatoire sur les commandes. L’implémentation est fournie par une fonction statique définie par le [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) macro.  

## <a name="getproperties"></a> ICommandPropertiesImpl::GetProperties

Retourne tous les jeux de propriété demandée à l’aide du mappage des propriétés de la commande.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(GetProperties)(const ULONG cPropertyIDSets,   
   const DBPROPIDSET rgPropertyIDSets[],   
   ULONG * pcPropertySets,   
   DBPROPSET ** prgPropertySets);  
```  
  
#### <a name="parameters"></a>Paramètres  

Consultez [ICommandProperties::GetProperties](/previous-versions/windows/desktop/ms723119) dans le *de référence du programmeur OLE DB*.  
  
### <a name="remarks"></a>Notes  

Voir [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="setproperties"></a> ICommandPropertiesImpl::SetProperties

Définit les propriétés de l’objet de commande.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>Paramètres  

Consultez [ICommandProperties::SetProperties](/previous-versions/windows/desktop/ms711497) dans le *de référence du programmeur OLE DB*.  
  
## <a name="see-also"></a>Voir aussi  

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)