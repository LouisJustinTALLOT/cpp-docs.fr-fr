---
description: 'En savoir plus sur : classe CComUnkArray'
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
ms.openlocfilehash: e03022fb751b487debb9f81d9e3d99ce46f1b9e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142140"
---
# <a name="ccomunkarray-class"></a>CComUnkArray, classe

Cette classe stocke des `IUnknown` pointeurs et est conçue pour être utilisée comme paramètre de la classe de modèle [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .

## <a name="syntax"></a>Syntaxe

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>Paramètres

*nMaxSize*<br/>
Nombre maximal de `IUnknown` pointeurs qui peuvent être contenus dans le tableau statique.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComUnkArray::CComUnkArray](#ccomunkarray)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComUnkArray :: Add](#add)|Appelez cette méthode pour ajouter un `IUnknown` pointeur au tableau.|
|[CComUnkArray :: Begin](#begin)|Retourne un pointeur vers le premier `IUnknown` pointeur de la collection.|
|[CComUnkArray :: fin](#end)|Retourne un pointeur vers un point après le dernier `IUnknown` pointeur de la collection.|
|[CComUnkArray :: GetCookie](#getcookie)|Appelez cette méthode pour obtenir le cookie associé à un `IUnknown` pointeur donné.|
|[CComUnkArray::GetUnknown](#getunknown)|Appelez cette méthode pour obtenir le `IUnknown` pointeur associé à un cookie donné.|
|[CComUnkArray :: Remove](#remove)|Appelez cette méthode pour supprimer un `IUnknown` pointeur du tableau.|

## <a name="remarks"></a>Notes

`CComUnkArray` contient un nombre fixe de `IUnknown` pointeurs, chaque interface sur un point de connexion. `CComUnkArray` peut être utilisé comme paramètre de la classe de modèle [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) . `CComUnkArray<1>` est une spécialisation de modèle de `CComUnkArray` qui a été optimisée pour un point de connexion.

Les `CComUnkArray` méthodes [Begin](#begin) et [end](#end) peuvent être utilisées pour effectuer une boucle sur tous les points de connexion (par exemple, lorsqu’un événement est déclenché).

Pour plus d’informations sur l’automatisation de la création de proxys de points de connexion, consultez [Ajout de points de connexion à un objet](../../atl/adding-connection-points-to-an-object.md) .

> [!NOTE]
> **Remarque** La classe [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md) est utilisée par l’Assistant Ajout d’une **classe** lors de la création d’un contrôle qui a des points de connexion. Si vous souhaitez spécifier manuellement le nombre de points de connexion, modifiez la référence de `CComDynamicUnkArray` à `CComUnkArray<` *n* `>` , où *n* est le nombre de points de connexion requis.

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="ccomunkarrayadd"></a><a name="add"></a> CComUnkArray :: Add

Appelez cette méthode pour ajouter un `IUnknown` pointeur au tableau.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Paramètres

*pUnk*<br/>
Appelez cette méthode pour ajouter un `IUnknown` pointeur au tableau.

### <a name="return-value"></a>Valeur renvoyée

Retourne le cookie associé au pointeur qui vient d’être ajouté, ou 0 si le tableau n’est pas assez grand pour contenir le nouveau pointeur.

## <a name="ccomunkarraybegin"></a><a name="begin"></a> CComUnkArray :: Begin

Retourne un pointeur vers le début de la collection de `IUnknown` pointeurs d’interface.

```
IUnknown**
    begin();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un `IUnknown` pointeur d’interface.

### <a name="remarks"></a>Notes

La collection contient des pointeurs vers des interfaces stockées localement sous la forme `IUnknown` . Vous effectuez un cast `IUnknown` de chaque interface vers le type d’interface réel, puis vous appelez. Vous n’avez pas besoin d’interroger d’abord l’interface.

Avant d’utiliser l' `IUnknown` interface, vous devez vérifier qu’elle n’est pas null.

## <a name="ccomunkarrayccomunkarray"></a><a name="ccomunkarray"></a> CComUnkArray::CComUnkArray

Constructeur.

```
CComUnkArray();
```

### <a name="remarks"></a>Notes

Définit la collection pour contenir des `nMaxSize` `IUnknown` pointeurs et initialise les pointeurs sur la valeur null.

## <a name="ccomunkarrayend"></a><a name="end"></a> CComUnkArray :: fin

Retourne un pointeur vers un point après le dernier `IUnknown` pointeur de la collection.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un `IUnknown` pointeur d’interface.

### <a name="remarks"></a>Notes

Les `CComUnkArray` méthodes `begin` et `end` peuvent être utilisées pour parcourir tous les points de connexion, par exemple, lorsqu’un événement est déclenché.

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

## <a name="ccomunkarraygetcookie"></a><a name="getcookie"></a> CComUnkArray :: GetCookie

Appelez cette méthode pour obtenir le cookie associé à un `IUnknown` pointeur donné.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Paramètres

*ppFind*<br/>
`IUnknown`Pointeur pour lequel le cookie associé est requis.

### <a name="return-value"></a>Valeur renvoyée

Retourne le cookie associé au `IUnknown` pointeur, ou 0 si aucun pointeur correspondant `IUnknown` n’est trouvé.

### <a name="remarks"></a>Notes

S’il existe plusieurs instances du même `IUnknown` pointeur, cette fonction retourne le cookie du premier.

## <a name="ccomunkarraygetunknown"></a><a name="getunknown"></a> CComUnkArray::GetUnknown

Appelez cette méthode pour obtenir le `IUnknown` pointeur associé à un cookie donné.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Paramètres

*dwCookie*<br/>
Cookie pour lequel le pointeur associé `IUnknown` est requis.

### <a name="return-value"></a>Valeur renvoyée

Retourne le `IUnknown` pointeur, ou null si aucun cookie correspondant n’est trouvé.

## <a name="ccomunkarrayremove"></a><a name="remove"></a> CComUnkArray :: Remove

Appelez cette méthode pour supprimer un `IUnknown` pointeur du tableau.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Paramètres

*dwCookie*<br/>
Cookie qui référence le `IUnknown` pointeur à supprimer du tableau.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si le pointeur est supprimé ; sinon, FALSe.

## <a name="see-also"></a>Voir aussi

[CComDynamicUnkArray, classe](../../atl/reference/ccomdynamicunkarray-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
