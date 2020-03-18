---
title: IDBInitializeImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
- IDBInitializeImpl.IDBInitializeImpl
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
helpviewer_keywords:
- IDBInitializeImpl class
- IDBInitializeImpl constructor
- Initialize method
- Uninitialize method
- m_dwStatus
- m_pCUtlPropInfo
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
ms.openlocfilehash: 1fc60db6db341d0667e24a81ae0f1394f54497ff
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447371"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl, classe

Fournit une implémentation pour l’interface [IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IDBInitializeImpl`.

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[IDBInitializeImpl](#idbinitializeimpl)|Constructeur.|

### <a name="interface-methods"></a>Méthodes d'interface

|||
|-|-|
|[Initialize](#initialize)|Démarre le fournisseur.|
|[Annuler l’initialisation](#uninitialize)|Arrête le fournisseur.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|[m_dwStatus](#dwstatus)|Indicateurs de source de données.|
|[m_pCUtlPropInfo](#pcutlpropinfo)|Pointeur vers l’implémentation des informations de propriétés de la base de données.|

## <a name="remarks"></a>Notes

Interface obligatoire sur les objets de source de données et l’interface facultative sur les énumérateurs.

## <a name="idbinitializeimpl"></a>IDBInitializeImpl :: IDBInitializeImpl

Constructeur.

### <a name="syntax"></a>Syntaxe

```cpp
IDBInitializeImpl();
```

### <a name="remarks"></a>Notes

Initialise tous les membres de données.

## <a name="initialize"></a>IDBInitializeImpl :: Initialize

Initialise l’objet source de données en préparant sa prise en charge des propriétés.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(Initialize)(void);
```

### <a name="remarks"></a>Notes

Consultez [IDBInitialize :: Initialize](/previous-versions/windows/desktop/ms718026(v=vs.85)) dans le *OLE DB Guide de référence du programmeur*.

## <a name="uninitialize"></a>IDBInitializeImpl :: Uninitialize

Place l’objet source de données dans un État non initialisé en libérant des ressources internes telles que la prise en charge des propriétés.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(Uninitialize)(void);
```

### <a name="remarks"></a>Notes

Consultez [IDBInitialize :: Uninitialize](/previous-versions/windows/desktop/ms719648(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="dwstatus"></a>IDBInitializeImpl :: m_dwStatus

Indicateurs de source de données.

### <a name="syntax"></a>Syntaxe

```cpp
DWORD m_dwStatus;
```

### <a name="remarks"></a>Notes

Ces indicateurs spécifient ou indiquent l’état de divers attributs pour l’objet source de données. Contient une ou plusieurs des valeurs d' **énumération** suivantes :

```cpp
enum DATASOURCE_FLAGS {
    DSF_MASK_INIT     = 0xFFFFF00F,
    DSF_PERSIST_DIRTY = 0x00000001,
    DSF_INITIALIZED   = 0x00000010,
};
```

|||
|-|-|
|`DSF_MASK_INIT`|Masque pour activer la restauration de l’état non initialisé.|
|`DSF_PERSIST_DIRTY`|Définit si l’objet source de données nécessite une persistance (autrement dit, si des modifications ont été apportées).|
|`DSF_INITIALIZED`|Définit si la source de données a été initialisée.|

## <a name="pcutlpropinfo"></a>IDBInitializeImpl :: m_pCUtlPropInfo

Pointeur vers l’objet d’implémentation pour les informations sur les propriétés de base de données.

### <a name="syntax"></a>Syntaxe

```cpp
CUtlPropInfo< T >* m_pCUtlPropInfo;
```

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)