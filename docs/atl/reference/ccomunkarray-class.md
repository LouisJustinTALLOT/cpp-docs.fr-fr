---
title: Classe CComUnkArray
ms.date: 11/04/2016
f1_keywords:
- CComUnkArray
- ATLCOM/ATL::CComUnkArray
- ATLCOM/ATL::CComUnkArray::CComUnkArray
- ATLCOM/ATL::CComUnkArray::Add
- ATLCOM/ATL::CComUnkArray::begin
- ATLCOM/ATL::CComUnkArray::end
- ATLCOM/ATL::CComUnkArray::GetCookie
- ATLCOM/ATL::CComUnkArray::GetUnknown
- ATLCOM/ATL::CComUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
ms.openlocfilehash: c1d2f0296394d3979ef4f152e3f902c89adf5b45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327304"
---
# <a name="ccomunkarray-class"></a>Classe CComUnkArray

Cette classe `IUnknown` stocke des pointeurs, et est conçu pour être utilisé comme un paramètre à la classe de modèle [IConnectionPointImpl.](../../atl/reference/iconnectionpointimpl-class.md)

## <a name="syntax"></a>Syntaxe

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>Paramètres

*nMaxSize (en)*<br/>
Le nombre `IUnknown` maximum de pointeurs qui peuvent être conservés dans le tableau statique.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComUnkArray::CComUnkArray](#ccomunkarray)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComUnkArray::Ajouter](#add)|Appelez cette méthode `IUnknown` pour ajouter un pointeur au tableau.|
|[CComUnkArray::commencer](#begin)|Retourne un pointeur `IUnknown` au premier pointeur de la collection.|
|[CComUnkArray::fin](#end)|Retourne un pointeur à `IUnknown` un pointeur passé le dernier pointeur de la collection.|
|[CComUnkArray::GetCookie](#getcookie)|Appelez cette méthode pour obtenir le `IUnknown` cookie associé à un pointeur donné.|
|[CComUnkArray::GetUnknown](#getunknown)|Appelez cette méthode `IUnknown` pour obtenir le pointeur associé à un cookie donné.|
|[CComUnkArray::Supprimer](#remove)|Appelez cette méthode `IUnknown` pour supprimer un pointeur du tableau.|

## <a name="remarks"></a>Notes

`CComUnkArray`détient un nombre `IUnknown` fixe de pointeurs, chacun une interface sur un point de connexion. `CComUnkArray`peut être utilisé comme paramètre pour la classe de modèle [IConnectionPointImpl.](../../atl/reference/iconnectionpointimpl-class.md) `CComUnkArray<1>`est une spécialisation `CComUnkArray` de modèle de qui a été optimisée pour un point de connexion.

Les `CComUnkArray` méthodes [commencent](#begin) et [se terminent](#end) peuvent être utilisées pour boucler tous les points de connexion (par exemple, lorsqu’un événement est déclenché).

Voir [l’ajout de points de connexion à un objet](../../atl/adding-connection-points-to-an-object.md) pour plus de détails sur l’automatisation de la création de procurations de point de connexion.

> [!NOTE]
> **Note** La classe [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md) est utilisée par l’assistant **De classe Add** lors de la création d’un contrôle qui a des points de connexion. Si vous souhaitez spécifier manuellement le nombre `CComDynamicUnkArray` `CComUnkArray<` de points de connexion, modifiez la référence de *n* `>`, où *n* est le nombre de points de connexion requis.

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomunkarrayadd"></a><a name="add"></a>CComUnkArray::Ajouter

Appelez cette méthode `IUnknown` pour ajouter un pointeur au tableau.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
Appelez cette méthode `IUnknown` pour ajouter un pointeur au tableau.

### <a name="return-value"></a>Valeur de retour

Retourne le cookie associé au pointeur nouvellement ajouté, ou 0 si le tableau n’est pas assez grand pour contenir le nouveau pointeur.

## <a name="ccomunkarraybegin"></a><a name="begin"></a>CComUnkArray::commencer

Retourne un pointeur au début `IUnknown` de la collection de pointeurs d’interface.

```
IUnknown**
    begin();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `IUnknown` à un pointeur d’interface.

### <a name="remarks"></a>Notes

La collection contient des indications sur `IUnknown`les interfaces stockées localement sous le titre . Vous lancez chaque `IUnknown` interface sur le type d’interface réelle, puis appelez-la. Vous n’avez pas besoin de poser des questions pour l’interface d’abord.

Avant d’utiliser l’interface, `IUnknown` vous devez vérifier qu’il n’est pas NULL.

## <a name="ccomunkarrayccomunkarray"></a><a name="ccomunkarray"></a>CComUnkArray::CComUnkArray

Constructeur.

```
CComUnkArray();
```

### <a name="remarks"></a>Notes

Définit la collection `nMaxSize` `IUnknown` pour tenir des pointeurs, et initialise les pointeurs à NULL.

## <a name="ccomunkarrayend"></a><a name="end"></a>CComUnkArray::fin

Retourne un pointeur à `IUnknown` un pointeur passé le dernier pointeur de la collection.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `IUnknown` à un pointeur d’interface.

### <a name="remarks"></a>Notes

Les `CComUnkArray` `begin` méthodes `end` et peuvent être utilisées pour boucler tous les points de connexion, par exemple, quand un événement est déclenché.

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

## <a name="ccomunkarraygetcookie"></a><a name="getcookie"></a>CComUnkArray::GetCookie

Appelez cette méthode pour obtenir le `IUnknown` cookie associé à un pointeur donné.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Paramètres

*ppFind*<br/>
Le `IUnknown` pointeur pour lequel le cookie associé est nécessaire.

### <a name="return-value"></a>Valeur de retour

Retourne le cookie `IUnknown` associé au pointeur, `IUnknown` ou 0 si aucun pointeur correspondant n’est trouvé.

### <a name="remarks"></a>Notes

S’il y a plus `IUnknown` d’un cas du même pointeur, cette fonction renvoie le cookie pour le premier.

## <a name="ccomunkarraygetunknown"></a><a name="getunknown"></a>CComUnkArray::GetUnknown

Appelez cette méthode `IUnknown` pour obtenir le pointeur associé à un cookie donné.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Paramètres

*dwCookie*<br/>
Le cookie pour `IUnknown` lequel le pointeur associé est nécessaire.

### <a name="return-value"></a>Valeur de retour

Renvoie `IUnknown` le pointeur, ou NULL si aucun cookie correspondant n’est trouvé.

## <a name="ccomunkarrayremove"></a><a name="remove"></a>CComUnkArray::Supprimer

Appelez cette méthode `IUnknown` pour supprimer un pointeur du tableau.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Paramètres

*dwCookie*<br/>
Le cookie faisant `IUnknown` référence au pointeur à retirer du tableau.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le pointeur est supprimé, FALSE autrement.

## <a name="see-also"></a>Voir aussi

[Classe CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
