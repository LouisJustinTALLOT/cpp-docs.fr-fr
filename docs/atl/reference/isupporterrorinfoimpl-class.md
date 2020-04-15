---
title: Classe ISupportErrorInfoImpl
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
ms.openlocfilehash: 4c60b58ba697f00b146077a2cdecd727fe2cac02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326364"
---
# <a name="isupporterrorinfoimpl-class"></a>Classe ISupportErrorInfoImpl

Cette classe fournit une implémentation par défaut de [l’interface ISupportErrorInfo](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) et peut être utilisée lorsqu’une seule interface génère des erreurs sur un objet.

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
Un pointeur à l’IID d’une interface qui prend en charge [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo).

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Indique si l’interface identifiée par `riid` prend en charge l’interface [IErrorInfo.](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)|

## <a name="remarks"></a>Notes

[L’interface ISupportErrorInfo](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) garantit que les informations d’erreur peuvent être retournées au client. Les objets `IErrorInfo` qui `ISupportErrorInfo`utilisent doivent être mis en œuvre .

La `ISupportErrorInfoImpl` classe fournit `ISupportErrorInfo` une implémentation par défaut et peut être utilisée lorsqu’une seule interface génère des erreurs sur un objet. Par exemple :

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="isupporterrorinfoimplinterfacesupportserrorinfo"></a><a name="interfacesupportserrorinfo"></a>ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

Indique si l’interface identifiée par `riid` prend en charge l’interface [IErrorInfo.](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Notes

Voir [ISupportErrorInfo::InterfaceSupportsErrorInfo](/windows/win32/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) dans le Windows SDK.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
