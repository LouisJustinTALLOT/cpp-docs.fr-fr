---
title: CComEnumOnSTL (classe)
ms.date: 11/04/2016
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
ms.openlocfilehash: b0674d64b471318d972d209373e0d74af0fa77f5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226592"
---
# <a name="ccomenumonstl-class"></a>CComEnumOnSTL (classe)

Cette classe définit un objet énumérateur COM basé sur une collection de bibliothèques standard C++.

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
Énumérateur COM. Pour obtenir un exemple, consultez [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) .

*piid*<br/>
Pointeur vers l’ID d’interface de l’interface de l’énumérateur.

*T*<br/>
Type d’élément exposé par l’interface de l’énumérateur.

*Copier*<br/>
Classe de [stratégie de copie](../../atl/atl-copy-policy-classes.md) .

*CollType*<br/>
Classe de conteneur de la bibliothèque standard C++.

## <a name="remarks"></a>Notes

`CComEnumOnSTL`définit un objet énumérateur COM basé sur une collection de bibliothèques standard C++. Cette classe peut être utilisée seule ou conjointement avec [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md). Les étapes classiques de l’utilisation de cette classe sont présentées ci-dessous. Pour plus d’informations, consultez [collections et énumérateurs ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="to-use-this-class-with-icollectiononstlimpl"></a>Pour utiliser cette classe avec ICollectionOnSTLImpl :

- **`typedef`** spécialisation de cette classe.

- Utilisez **`typedef`** en tant qu’argument template final dans une spécialisation de `ICollectionOnSTLImpl` .

Pour obtenir un exemple [, consultez Collections et énumérateurs ATL](../../atl/atl-collections-and-enumerators.md) .

## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>Pour utiliser cette classe indépendamment de ICollectionOnSTLImpl :

- **`typedef`** spécialisation de cette classe.

- Utilisez **`typedef`** comme argument template dans une spécialisation de `CComObject` .

- Créez une instance de la `CComObject` spécialisation.

- Initialisez l’objet énumérateur en appelant [IEnumOnSTLImpl :: init](../../atl/reference/ienumonstlimpl-class.md#init).

- Retourne l’interface de l’énumérateur au client.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)

`CComEnumOnSTL`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="example"></a>Exemple

Le code présenté ci-dessous fournit une fonction générique permettant de gérer la création et l’initialisation d’un objet énumérateur :

[!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]

Cette fonction de modèle peut être utilisée pour implémenter la `_NewEnum` propriété d’une interface de collection comme indiqué ci-dessous :

[!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]

Ce code crée un **`typedef`** pour `CComEnumOnSTL` qui expose un vecteur de `CComVariant` s à l’aide de l' `IEnumVariant` interface. La `CVariantCollection` classe est simplement spécialisée `CreateSTLEnumerator` pour travailler avec des objets Enumerator de ce type.

## <a name="see-also"></a>Voir aussi

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)<br/>
[Exemple ATLCollections : illustre les classes de stratégie de copie de ICollectionOnSTLImpl, CComEnumOnSTL et personnalisées](../../overview/visual-cpp-samples.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[CComObjectRootEx (classe)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[IEnumOnSTLImpl, classe](../../atl/reference/ienumonstlimpl-class.md)
