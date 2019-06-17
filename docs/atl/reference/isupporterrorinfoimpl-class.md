---
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
ms.openlocfilehash: 650d90c9ec98754e11586f63e0871b70ebbe34f3
ms.sourcegitcommit: e79188287189b76b34eb7e8fb1bfe646bdb586bc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141705"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl, classe

Cette classe fournit une implémentation par défaut de la [ISupportErrorInfo Interface](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) et peuvent être utilisés lors d’une seule interface génère des erreurs sur un objet.

> [!IMPORTANT]
> Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>Paramètres

*piid*<br/>
Un pointeur vers l’IID d’une interface qui prend en charge [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo).

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Indique si l’interface identifié par `riid` prend en charge la [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) interface.|

## <a name="remarks"></a>Notes

Le [ISupportErrorInfo Interface](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) garantit que les informations d’erreur peuvent être retournées au client. Objets qui utilisent `IErrorInfo` doit implémenter `ISupportErrorInfo`.

Classe `ISupportErrorInfoImpl` fournit une implémentation par défaut de `ISupportErrorInfo` et peuvent être utilisés lors d’une seule interface génère des erreurs sur un objet. Exemple :

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

Indique si l’interface identifié par `riid` prend en charge la [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) interface.

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Notes

Consultez [ISupportErrorInfo::InterfaceSupportsErrorInfo](/windows/desktop/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
