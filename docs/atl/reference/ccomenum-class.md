---
description: 'En savoir plus sur : classe CComEnum'
title: CComEnum, classe
ms.date: 11/04/2016
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
ms.openlocfilehash: 0cee4129c0bc5129313b92e144c22de9d161c9cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146690"
---
# <a name="ccomenum-class"></a>CComEnum, classe

Cette classe définit un objet énumérateur COM basé sur un tableau.

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
Interface d’énumérateur COM. Pour obtenir un exemple, consultez [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) .

*piid*<br/>
Pointeur vers l’ID d’interface de l’interface de l’énumérateur.

*T*<br/>
Type d’élément exposé par l’interface de l’énumérateur.

*Copy*<br/>
Classe de [stratégie de copie](../../atl/atl-copy-policy-classes.md)homogène.

*ThreadModel*<br/>
Modèle de thread de la classe. Par défaut, ce paramètre est le modèle de thread d’objet global utilisé dans votre projet.

## <a name="remarks"></a>Notes

`CComEnum` définit un objet énumérateur COM basé sur un tableau. Cette classe est analogue à [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) qui implémente un énumérateur basé sur un conteneur de bibliothèque standard C++. Les étapes classiques de l’utilisation de cette classe sont présentées ci-dessous. Pour plus d’informations, consultez [collections et énumérateurs ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="to-use-this-class"></a>Pour utiliser cette classe :

- **`typedef`** spécialisation de cette classe.

- Utilisez **`typedef`** comme argument template dans une spécialisation de `CComObject` .

- Créez une instance de la `CComObject` spécialisation.

- Initialisez l’objet énumérateur en appelant [CComEnumImpl :: init](../../atl/reference/ccomenumimpl-class.md#init).

- Retourne l’interface de l’énumérateur au client.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)

`CComEnum`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="example"></a>Exemple

Le code présenté ci-dessous fournit une fonction réutilisable pour créer et initialiser un objet énumérateur.

[!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]

Cette fonction de modèle peut être utilisée pour implémenter la `_NewEnum` propriété d’une interface de collection comme indiqué ci-dessous :

[!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]

Ce code crée un **`typedef`** pour `CComEnum` qui expose un vecteur de variants via l' `IEnumVariant` interface. La `CVariantArrayCollection` classe est simplement spécialisée `CreateEnumerator` pour travailler avec des objets Enumerator de ce type et passe les arguments nécessaires.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[CComEnumImpl, classe](../../atl/reference/ccomenumimpl-class.md)<br/>
[CComObjectRootEx (classe)](../../atl/reference/ccomobjectrootex-class.md)
