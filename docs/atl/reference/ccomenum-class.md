---
title: CComEnum, classe
ms.date: 11/04/2016
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
ms.openlocfilehash: 4d83b06f37c132c0d2325304e2cc155ccb490690
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290363"
---
# <a name="ccomenum-class"></a>CComEnum, classe

Cette classe définit un objet d’énumérateur COM basé sur un tableau.

## <a name="syntax"></a>Syntaxe

```
template <class Base,
    const IID* piid, class T, class Copy, class ThreadModel = CcomObjectThreadModel>
class ATL_NO_VTABLE CComEnum : public CComEnumImpl<Base, piid,
T,
    Copy>,
public CComObjectRootEx<ThreadModel>
```

#### <a name="parameters"></a>Paramètres

*Base*<br/>
Une interface COM de l’énumérateur. Consultez [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) pour obtenir un exemple.

*piid*<br/>
Pointeur vers l’ID d’interface de l’interface de l’énumérateur.

*T*<br/>
Le type d’élément exposé par l’interface de l’énumérateur.

*Copier*<br/>
Un homogènes [copier la classe de stratégie](../../atl/atl-copy-policy-classes.md).

*ThreadModel*<br/>
Le modèle de thread de la classe. Ce paramètre par défaut est le modèle de thread d’objet global utilisé dans votre projet.

## <a name="remarks"></a>Notes

`CComEnum` définit un objet d’énumérateur COM basé sur un tableau. Cette classe est analogue à [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) qui implémente un énumérateur basé sur un conteneur de bibliothèque C++ Standard. Procédure standard d’utilisation de cette classe est décrites ci-dessous. Pour plus d’informations, consultez [Collections et énumérateurs ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="to-use-this-class"></a>Pour utiliser cette classe :

- **typedef** une spécialisation de cette classe.

- Utilisez le **typedef** comme argument de modèle dans une spécialisation de `CComObject`.

- Créez une instance de la `CComObject` spécialisation.

- Initialiser l’objet énumérateur en appelant [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init).

- Retourner l’interface de l’énumérateur au client.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)

`CComEnum`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom.h

## <a name="example"></a>Exemple

Le code ci-dessous fournit une fonction réutilisable pour la création et initialisation d’un objet énumérateur.

[!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]

Cette fonction de modèle peut être utilisée pour implémenter le `_NewEnum` propriété d’une interface de collection, comme indiqué ci-dessous :

[!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]

Ce code crée un **typedef** pour `CComEnum` qui expose un vecteur de variantes via le `IEnumVariant` interface. Le `CVariantArrayCollection` classe spécialisée simplement `CreateEnumerator` pour travailler avec des objets d’énumérateur de ce type et la transmet les arguments nécessaires.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[CComEnumImpl, classe](../../atl/reference/ccomenumimpl-class.md)<br/>
[CComObjectRootEx, classe](../../atl/reference/ccomobjectrootex-class.md)
