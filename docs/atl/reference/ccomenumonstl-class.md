---
title: CComEnumOnSTL, classe
ms.date: 11/04/2016
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
ms.openlocfilehash: f9bf9c227984b2fdbf460f970357f395934b238c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58779857"
---
# <a name="ccomenumonstl-class"></a>CComEnumOnSTL, classe

Cette classe définit un objet d’énumérateur COM selon une collection de la bibliothèque C++ Standard.

## <a name="syntax"></a>Syntaxe

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType, class ThreadModel = CComObjectThreadModel>
class ATL_NO_VTABLE CComEnumOnSTL : public IEnumOnSTLImpl<Base, piid,
T,
    Copy,
CollType>,
    public CComObjectRootEx<ThreadModel>
```

#### <a name="parameters"></a>Paramètres

*Base*<br/>
Un énumérateur COM. Consultez [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) pour obtenir un exemple.

*piid*<br/>
Pointeur vers l’ID d’interface de l’interface de l’énumérateur.

*T*<br/>
Le type d’élément exposé par l’interface de l’énumérateur.

*Copier*<br/>
Un [Copier stratégie](../../atl/atl-copy-policy-classes.md) classe.

*CollType*<br/>
Une classe de conteneur de bibliothèque C++ Standard.

## <a name="remarks"></a>Notes

`CComEnumOnSTL` définit un objet d’énumérateur COM selon une collection de la bibliothèque C++ Standard. Cette classe peut être utilisée sur sa propre ou conjointement avec [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md). Procédure standard d’utilisation de cette classe est décrites ci-dessous. Pour plus d’informations, consultez [Collections et énumérateurs ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="to-use-this-class-with-icollectiononstlimpl"></a>Pour utiliser cette classe avec ICollectionOnSTLImpl :

- **typedef** une spécialisation de cette classe.

- Utilisez le **typedef** en tant que l’argument template final dans une spécialisation de `ICollectionOnSTLImpl`.

Consultez [Collections et énumérateurs ATL](../../atl/atl-collections-and-enumerators.md) pour obtenir un exemple.

## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>Pour utiliser cette classe indépendamment ICollectionOnSTLImpl :

- **typedef** une spécialisation de cette classe.

- Utilisez le **typedef** comme argument de modèle dans une spécialisation de `CComObject`.

- Créez une instance de la `CComObject` spécialisation.

- Initialiser l’objet énumérateur en appelant [IEnumOnSTLImpl::Init](../../atl/reference/ienumonstlimpl-class.md#init).

- Retourner l’interface de l’énumérateur au client.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)

`CComEnumOnSTL`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

## <a name="example"></a>Exemple

Le code ci-dessous fournit une fonction pour gérer la création et l’initialisation d’un objet énumérateur générique :

[!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]

Cette fonction de modèle peut être utilisée pour implémenter le `_NewEnum` propriété d’une interface de collection, comme indiqué ci-dessous :

[!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]

Ce code crée un **typedef** pour `CComEnumOnSTL` qui expose un vecteur de `CComVariant`s au moyen de la `IEnumVariant` interface. Le `CVariantCollection` classe spécialisée simplement `CreateSTLEnumerator` pour travailler avec des objets d’énumérateur de ce type.

## <a name="see-also"></a>Voir aussi

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)<br/>
[Exemple ATLCollections : Montre comment ICollectionOnSTLImpl, CComEnumOnSTL et des Classes de stratégie de copie personnalisées](../../overview/visual-cpp-samples.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[CComObjectRootEx, classe](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[IEnumOnSTLImpl, classe](../../atl/reference/ienumonstlimpl-class.md)
