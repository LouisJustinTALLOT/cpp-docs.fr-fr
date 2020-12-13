---
description: 'En savoir plus sur : classe ISupportErrorInfoImpl'
title: ISupportErrorInfoImpl, classe
ms.date: 06/13/2019
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
ms.openlocfilehash: 182f55f7d7c288e4c8679c3e8cc1df7bb5cd79bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139137"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl, classe

Cette classe fournit une implémentation par défaut de l' [interface ISupportErrorInfo](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) et peut être utilisée quand une seule interface génère des erreurs sur un objet.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>Paramètres

*piid*<br/>
Pointeur vers l’IID d’une interface qui prend en charge [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo).

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ISupportErrorInfoImpl :: InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Indique si l’interface identifiée par `riid` prend en charge l’interface [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo) .|

## <a name="remarks"></a>Notes

L' [interface ISupportErrorInfo](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) garantit que les informations d’erreur peuvent être retournées au client. Les objets qui utilisent `IErrorInfo` doivent implémenter `ISupportErrorInfo` .

`ISupportErrorInfoImpl`La classe fournit une implémentation par défaut de `ISupportErrorInfo` et peut être utilisée quand une seule interface génère des erreurs sur un objet. Par exemple :

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="isupporterrorinfoimplinterfacesupportserrorinfo"></a><a name="interfacesupportserrorinfo"></a> ISupportErrorInfoImpl :: InterfaceSupportsErrorInfo

Indique si l’interface identifiée par `riid` prend en charge l’interface [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo) .

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Notes

Consultez [ISupportErrorInfo :: InterfaceSupportsErrorInfo](/windows/win32/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) dans la SDK Windows.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
