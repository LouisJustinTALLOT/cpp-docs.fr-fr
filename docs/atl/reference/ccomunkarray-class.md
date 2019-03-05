---
title: CComUnkArray, classe
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
ms.openlocfilehash: 7a73158e407279b529f76484e4c32f0a8a7a63c2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259371"
---
# <a name="ccomunkarray-class"></a>CComUnkArray, classe

Cette classe stocke `IUnknown` des pointeurs et est conçu pour être utilisé en tant que paramètre à la [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) classe de modèle.

## <a name="syntax"></a>Syntaxe

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>Paramètres

*nMaxSize*<br/>
Le nombre maximal de `IUnknown` pointeurs peuvent être conservées dans le tableau statique.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComUnkArray::CComUnkArray](#ccomunkarray)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComUnkArray::Add](#add)|Appelez cette méthode pour ajouter un `IUnknown` pointeur vers le tableau.|
|[CComUnkArray::begin](#begin)|Retourne un pointeur vers le premier `IUnknown` pointeur dans la collection.|
|[CComUnkArray::end](#end)|Retourne un pointeur vers la position au-delà de la dernière `IUnknown` pointeur dans la collection.|
|[CComUnkArray::GetCookie](#getcookie)|Appelez cette méthode pour obtenir le cookie associé à une donnée `IUnknown` pointeur.|
|[CComUnkArray::GetUnknown](#getunknown)|Appelez cette méthode pour obtenir le `IUnknown` pointeur associé à un cookie donné.|
|[CComUnkArray::Remove](#remove)|Appelez cette méthode pour supprimer un `IUnknown` pointeur à partir du tableau.|

## <a name="remarks"></a>Notes

`CComUnkArray` contient un nombre fixe de `IUnknown` des pointeurs, chaque point d’interface sur une connexion. `CComUnkArray` peut être utilisé en tant que paramètre à la [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) classe de modèle. `CComUnkArray<1>` est une spécialisation de modèle de `CComUnkArray` qui a été optimisé pour un point de connexion.

Le `CComUnkArray` méthodes [commencer](#begin) et [fin](#end) peut être utilisé pour itérer sur tous les points de connexion (par exemple, lorsqu’un événement est déclenché).

Consultez [Ajout des Points de connexion à un objet](../../atl/adding-connection-points-to-an-object.md) pour plus d’informations sur l’automatisation de la création d’une connexion point proxys.

> [!NOTE]
> **Remarque** la classe [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md) est utilisé par le **ajouter une classe** Assistant lors de la création d’un contrôle qui a des Points de connexion. Si vous souhaitez spécifier manuellement le nombre de Points de connexion, modifiez la référence à partir de `CComDynamicUnkArray` à `CComUnkArray<` *n* `>`, où *n* est le nombre de points de connexion Obligatoire.

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom.h

##  <a name="add"></a>  CComUnkArray::Add

Appelez cette méthode pour ajouter un `IUnknown` pointeur vers le tableau.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Paramètres

*pUnk*<br/>
Appelez cette méthode pour ajouter un `IUnknown` pointeur vers le tableau.

### <a name="return-value"></a>Valeur de retour

Retourne le cookie associé avec le pointeur nouvellement ajouté, ou 0 si le tableau n’est pas assez grand pour contenir le nouveau pointeur.

##  <a name="begin"></a>  CComUnkArray::begin

Retourne un pointeur vers le début de la collection de `IUnknown` pointeurs d’interface.

```
IUnknown**
    begin();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un `IUnknown` pointeur d’interface.

### <a name="remarks"></a>Notes

La collection contient des pointeurs aux interfaces stockés localement sous `IUnknown`. Vous effectuez un cast `IUnknown` interface pour le type d’interface réelle et puis appel via celui-ci. Il est inutile d’interroger tout d’abord pour l’interface.

Avant d’utiliser le `IUnknown` interface, vous devez vérifier qu’il n’est pas NULL.

##  <a name="ccomunkarray"></a>  CComUnkArray::CComUnkArray

Constructeur.

```
CComUnkArray();
```

### <a name="remarks"></a>Notes

Définit la collection pour contenir `nMaxSize` `IUnknown` des pointeurs et initialise les pointeurs NULL.

##  <a name="end"></a>  CComUnkArray::end

Retourne un pointeur vers la position au-delà de la dernière `IUnknown` pointeur dans la collection.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un `IUnknown` pointeur d’interface.

### <a name="remarks"></a>Notes

Le `CComUnkArray` méthodes `begin` et `end` peut être utilisé pour itérer sur tous les points de connexion, par exemple, lorsqu’un événement est déclenché.

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

##  <a name="getcookie"></a>  CComUnkArray::GetCookie

Appelez cette méthode pour obtenir le cookie associé à une donnée `IUnknown` pointeur.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Paramètres

*ppFind*<br/>
Le `IUnknown` pointeur pour lequel le cookie associé est requis.

### <a name="return-value"></a>Valeur de retour

Retourne le cookie associé à la `IUnknown` pointeur, ou 0 si aucune correspondance `IUnknown` pointeur est trouvé.

### <a name="remarks"></a>Notes

S’il existe plusieurs instances du même `IUnknown` pointeur, cette fonction retourne le cookie pour le premier.

##  <a name="getunknown"></a>  CComUnkArray::GetUnknown

Appelez cette méthode pour obtenir le `IUnknown` pointeur associé à un cookie donné.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Paramètres

*dwCookie*<br/>
Le cookie pour lequel associé `IUnknown` pointeur est requis.

### <a name="return-value"></a>Valeur de retour

Retourne le `IUnknown` pointeur, ou NULL si aucun cookie n’est trouvée.

##  <a name="remove"></a>  CComUnkArray::Remove

Appelez cette méthode pour supprimer un `IUnknown` pointeur à partir du tableau.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Paramètres

*dwCookie*<br/>
Le référencement de cookie le `IUnknown` pointeur à supprimer à partir du tableau.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le pointeur est supprimé, FALSE sinon.

## <a name="see-also"></a>Voir aussi

[CComDynamicUnkArray, classe](../../atl/reference/ccomdynamicunkarray-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
