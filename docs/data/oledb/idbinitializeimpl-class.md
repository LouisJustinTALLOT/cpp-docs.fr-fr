---
title: Idbinitializeimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
- IDBInitializeImpl.IDBInitializeImpl
- IDBInitializeImpl
- IDBInitializeImpl::IDBInitializeImpl
- Initialize
- IDBInitializeImpl::Initialize
- IDBInitializeImpl.Initialize
- IDBInitializeImpl.Uninitialize
- Uninitialize
- IDBInitializeImpl::Uninitialize
- ATL::IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl.m_dwStatus
- ATL.IDBInitializeImpl.m_dwStatus
- IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl<T>::m_dwStatus
- ATL.IDBInitializeImpl<T>.m_dwStatus
- ATL::IDBInitializeImpl<T>::m_dwStatus
- m_dwStatus
- ATL::IDBInitializeImpl<T>::m_pCUtlPropInfo
- m_pCUtlPropInfo
- IDBInitializeImpl::m_pCUtlPropInfo
- ATL.IDBInitializeImpl.m_pCUtlPropInfo
- IDBInitializeImpl<T>::m_pCUtlPropInfo
- IDBInitializeImpl.m_pCUtlPropInfo
- ATL::IDBInitializeImpl::m_pCUtlPropInfo
dev_langs:
- C++
helpviewer_keywords:
- IDBInitializeImpl class
- IDBInitializeImpl constructor
- Initialize method
- Uninitialize method
- m_dwStatus
- m_pCUtlPropInfo
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 92d71bc780e66d4a61d74605aeb5c316b181beba
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081758"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl, classe

Fournit une implémentation pour le [IDBInitialize](/previous-versions/windows/desktop/ms713706) interface.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IDBInitializeImpl`.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[IDBInitializeImpl](#idbinitializeimpl)|Constructeur.|

### <a name="interface-methods"></a>Méthodes d’interface

|||
|-|-|
|[Initialize](#initialize)|Démarre le fournisseur.|
|[Annuler l’initialisation](#uninitialize)|Arrête le fournisseur.|

### <a name="data-members"></a>Membres de données

|||
|-|-|
|[m_dwStatus](#dwstatus)|Indicateurs de source de données.|
|[m_pCUtlPropInfo](#pcutlpropinfo)|Pointeur vers l’implémentation d’informations sur les propriétés de la base de données.|

## <a name="remarks"></a>Notes

Une interface obligatoire sur les objets source de données et une interface facultative sur les énumérateurs.

## <a name="idbinitializeimpl"></a> IDBInitializeImpl::IDBInitializeImpl

Constructeur.

### <a name="syntax"></a>Syntaxe

```cpp
IDBInitializeImpl();
```

### <a name="remarks"></a>Notes

Initialise tous les membres de données.

## <a name="initialize"></a> IDBInitializeImpl::Initialize

Initialise l’objet de source de données en préparation de sa prise en charge de la propriété.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(Initialize)(void);
```

### <a name="remarks"></a>Notes

Consultez [IDBInitialize::Initialize](/previous-versions/windows/desktop/ms718026) dans le *de référence du programmeur OLE DB*.

## <a name="uninitialize"></a> IDBInitializeImpl::Uninitialize

Place les données de source de l’objet dans un état non initialisé en libérant des ressources internes telles que la prise en charge de la propriété.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(Uninitialize)(void);
```

### <a name="remarks"></a>Notes

Consultez [IDBInitialize::Uninitialize](/previous-versions/windows/desktop/ms719648) dans le *de référence du programmeur OLE DB*.

## <a name="dwstatus"></a> IDBInitializeImpl::m_dwStatus

Indicateurs de source de données.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD m_dwStatus;
```

### <a name="remarks"></a>Notes

Ces indicateurs spécifient ou indiquent l’état des différents attributs pour l’objet de source de données. Contient un ou plusieurs des opérations suivantes **enum** valeurs :

```cpp
enum DATASOURCE_FLAGS {
    DSF_MASK_INIT     = 0xFFFFF00F,
    DSF_PERSIST_DIRTY = 0x00000001,
    DSF_INITIALIZED   = 0x00000010,
};
```

|||
|-|-|
|`DSF_MASK_INIT`|Un masque pour activer la restauration de l’état non initialisé.|
|`DSF_PERSIST_DIRTY`|Si l’objet source de données exige persistance (autrement dit, si des modifications ont été apportées).|
|`DSF_INITIALIZED`|Définir si la source de données a été initialisée.|

## <a name="pcutlpropinfo"></a> IDBInitializeImpl::m_pCUtlPropInfo

Pointeur vers l’objet d’implémentation pour les informations de propriétés de la base de données.

### <a name="syntax"></a>Syntaxe

```cpp
CUtlPropInfo< T >* m_pCUtlPropInfo;
```

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)