---
title: Classe CComDynamicUnkArray
ms.date: 11/04/2016
f1_keywords:
- CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::Add
- ATLCOM/ATL::CComDynamicUnkArray::begin
- ATLCOM/ATL::CComDynamicUnkArray::clear
- ATLCOM/ATL::CComDynamicUnkArray::end
- ATLCOM/ATL::CComDynamicUnkArray::GetAt
- ATLCOM/ATL::CComDynamicUnkArray::GetCookie
- ATLCOM/ATL::CComDynamicUnkArray::GetSize
- ATLCOM/ATL::CComDynamicUnkArray::GetUnknown
- ATLCOM/ATL::CComDynamicUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
ms.openlocfilehash: 51b1d7e81c98bd5dbcf957b1705e7a717bfb9ab0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747978"
---
# <a name="ccomdynamicunkarray-class"></a>Classe CComDynamicUnkArray

Cette classe stocke `IUnknown` un éventail de pointeurs.

## <a name="syntax"></a>Syntaxe

```
class CComDynamicUnkArray
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|Constructeur. Initialise les valeurs de collecte à NULL et la taille de la collection à zéro.|
|[CComDynamicUnkArray::CComDynamicUnkArray](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComDynamicUnkArray::Ajouter](#add)|Appelez cette méthode `IUnknown` pour ajouter un pointeur au tableau.|
|[CComDynamicUnkArray::début](#begin)|Retourne un pointeur `IUnknown` au premier pointeur de la collection.|
|[CComDynamicUnkArray::clair](#clear)|Vide le tableau.|
|[CComDynamicUnkArray::fin](#end)|Retourne un pointeur à `IUnknown` un pointeur passé le dernier pointeur de la collection.|
|[CComDynamicUnkArray::GetAt](#getat)|Récupère l'élément au niveau de l'index spécifié.|
|[CComDynamicUnkArray::GetCookie](#getcookie)|Appelez cette méthode pour obtenir le `IUnknown` cookie associé à un pointeur donné.|
|[CComDynamicUnkArray::GetSize](#getsize)|Retourne la longueur d’un tableau.|
|[CComDynamicUnkArray::GetUnknown](#getunknown)|Appelez cette méthode `IUnknown` pour obtenir le pointeur associé à un cookie donné.|
|[CComDynamicUnkArray::Supprimer](#remove)|Appelez cette méthode `IUnknown` pour supprimer un pointeur du tableau.|

## <a name="remarks"></a>Notes

`CComDynamicUnkArray`détient un tableau dynamiquement `IUnknown` attribué de pointeurs, chacun une interface sur un point de connexion. `CComDynamicUnkArray`peut être utilisé comme paramètre pour la classe de modèle [IConnectionPointImpl.](../../atl/reference/iconnectionpointimpl-class.md)

Les `CComDynamicUnkArray` méthodes [commencent](#begin) et [se terminent](#end) peuvent être utilisées pour boucler tous les points de connexion (par exemple, lorsqu’un événement est déclenché).

Voir [l’ajout de points de connexion à un objet](../../atl/adding-connection-points-to-an-object.md) pour plus de détails sur l’automatisation de la création de procurations de point de connexion.

> [!NOTE]
> **Note** La `CComDynamicUnkArray` classe est utilisée par l’assistant **De classe Add** lors de la création d’un contrôle qui a des points de connexion. Si vous souhaitez spécifier manuellement le nombre `CComDynamicUnkArray` `CComUnkArray<` de points de connexion, modifiez la référence de *n* `>`, où *n* est le nombre de points de connexion requis.

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomdynamicunkarrayadd"></a><a name="add"></a>CComDynamicUnkArray::Ajouter

Appelez cette méthode `IUnknown` pour ajouter un pointeur au tableau.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
Le `IUnknown` pointeur à ajouter au tableau.

### <a name="return-value"></a>Valeur de retour

Retourne le cookie associé au pointeur nouvellement ajouté.

## <a name="ccomdynamicunkarraybegin"></a><a name="begin"></a>CComDynamicUnkArray::début

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

## <a name="ccomdynamicunkarrayclear"></a><a name="clear"></a>CComDynamicUnkArray::clair

Vide le tableau.

```cpp
void clear();
```

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="ccomdynamicunkarray"></a>CComDynamicUnkArray::CComDynamicUnkArray

Constructeur.

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>Notes

Définit la taille de la collection à zéro et initialise les valeurs à NULL. Le destructeur libère la collection, si nécessaire.

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="dtor"></a>CComDynamicUnkArray::CComDynamicUnkArray

Destructeur.

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>Notes

Libère les ressources allouées par le constructeur de classe.

## <a name="ccomdynamicunkarrayend"></a><a name="end"></a>CComDynamicUnkArray::fin

Retourne un pointeur à `IUnknown` un pointeur passé le dernier pointeur de la collection.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `IUnknown` à un pointeur d’interface.

## <a name="ccomdynamicunkarraygetat"></a><a name="getat"></a>CComDynamicUnkArray::GetAt

Récupère l'élément au niveau de l'index spécifié.

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l'élément à récupérer.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers une interface [IUnknown.](/windows/win32/api/unknwn/nn-unknwn-iunknown)

## <a name="ccomdynamicunkarraygetcookie"></a><a name="getcookie"></a>CComDynamicUnkArray::GetCookie

Appelez cette méthode pour obtenir le `IUnknown` cookie associé à un pointeur donné.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Paramètres

*ppFind*<br/>
Le `IUnknown` pointeur pour lequel le cookie associé est nécessaire.

### <a name="return-value"></a>Valeur de retour

Retourne le cookie `IUnknown` associé au pointeur, `IUnknown` ou zéro si aucun pointeur correspondant n’est trouvé.

### <a name="remarks"></a>Notes

S’il y a plus `IUnknown` d’un cas du même pointeur, cette fonction renvoie le cookie pour le premier.

## <a name="ccomdynamicunkarraygetsize"></a><a name="getsize"></a>CComDynamicUnkArray::GetSize

Retourne la longueur d’un tableau.

```
int GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur du tableau.

## <a name="ccomdynamicunkarraygetunknown"></a><a name="getunknown"></a>CComDynamicUnkArray::GetUnknown

Appelez cette méthode `IUnknown` pour obtenir le pointeur associé à un cookie donné.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Paramètres

*dwCookie*<br/>
Le cookie pour `IUnknown` lequel le pointeur associé est nécessaire.

### <a name="return-value"></a>Valeur de retour

Renvoie `IUnknown` le pointeur, ou NULL si aucun cookie correspondant n’est trouvé.

## <a name="ccomdynamicunkarrayremove"></a><a name="remove"></a>CComDynamicUnkArray::Supprimer

Appelez cette méthode `IUnknown` pour supprimer un pointeur du tableau.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Paramètres

*dwCookie*<br/>
Le cookie faisant `IUnknown` référence au pointeur à retirer du tableau.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le pointeur est supprimé; autrement FALSE.

## <a name="see-also"></a>Voir aussi

[Classe CComUnkArray](../../atl/reference/ccomunkarray-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
