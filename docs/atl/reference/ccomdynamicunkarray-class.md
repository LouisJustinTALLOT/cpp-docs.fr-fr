---
title: CComDynamicUnkArray, classe
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
ms.openlocfilehash: d55a6d6bfbcc6921fa0633753365f5799388dc27
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497250"
---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkArray, classe

Cette classe stocke un tableau `IUnknown` de pointeurs.

## <a name="syntax"></a>Syntaxe

```
class CComDynamicUnkArray
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|Constructeur. Initialise les valeurs de la collection à NULL et la taille de la collection à zéro.|
|[CComDynamicUnkArray::~CComDynamicUnkArray](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComDynamicUnkArray::Add](#add)|Appelez cette méthode pour ajouter un `IUnknown` pointeur au tableau.|
|[CComDynamicUnkArray::begin](#begin)|Retourne un pointeur vers le premier `IUnknown` pointeur de la collection.|
|[CComDynamicUnkArray::clear](#clear)|Vide le tableau.|
|[CComDynamicUnkArray::end](#end)|Retourne un pointeur vers un point après le `IUnknown` dernier pointeur de la collection.|
|[CComDynamicUnkArray::GetAt](#getat)|Récupère l’élément à l’index spécifié.|
|[CComDynamicUnkArray::GetCookie](#getcookie)|Appelez cette méthode pour obtenir le cookie associé à un pointeur `IUnknown` donné.|
|[CComDynamicUnkArray::GetSize](#getsize)|Retourne la longueur d’un tableau.|
|[CComDynamicUnkArray::GetUnknown](#getunknown)|Appelez cette méthode pour obtenir le `IUnknown` pointeur associé à un cookie donné.|
|[CComDynamicUnkArray::Remove](#remove)|Appelez cette méthode pour supprimer un `IUnknown` pointeur du tableau.|

## <a name="remarks"></a>Notes

`CComDynamicUnkArray`contient un tableau de `IUnknown` pointeurs alloués dynamiquement, chaque interface sur un point de connexion. `CComDynamicUnkArray`peut être utilisé comme paramètre de la classe de modèle [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .

Les `CComDynamicUnkArray` méthodes [Begin](#begin) et [end](#end) peuvent être utilisées pour effectuer une boucle sur tous les points de connexion (par exemple, lorsqu’un événement est déclenché).

Pour plus d’informations sur l’automatisation de la création de proxys de points de connexion, consultez [Ajout de points de connexion à un objet](../../atl/adding-connection-points-to-an-object.md) .

> [!NOTE]
> **Remarque** La classe `CComDynamicUnkArray` est utilisée par l’Assistant Ajout d’une **classe** lors de la création d’un contrôle qui a des points de connexion. Si vous souhaitez spécifier manuellement le nombre de points de connexion, modifiez la référence de `CComDynamicUnkArray` à `CComUnkArray<` *n* `>`, où *n* est le nombre de points de connexion requis.

## <a name="requirements"></a>Configuration requise

**En-tête:** atlcom. h

##  <a name="add"></a>  CComDynamicUnkArray::Add

Appelez cette méthode pour ajouter un `IUnknown` pointeur au tableau.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Paramètres

*pUnk*<br/>
`IUnknown` Pointeur à ajouter au tableau.

### <a name="return-value"></a>Valeur de retour

Retourne le cookie associé au pointeur qui vient d’être ajouté.

##  <a name="begin"></a>  CComDynamicUnkArray::begin

Retourne un pointeur vers le début de la collection de `IUnknown` pointeurs d’interface.

```
IUnknown**
    begin();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un `IUnknown` pointeur d’interface.

### <a name="remarks"></a>Notes

La collection contient des pointeurs vers des interfaces stockées `IUnknown`localement sous la forme. Vous effectuez un `IUnknown` cast de chaque interface vers le type d’interface réel, puis vous appelez. Vous n’avez pas besoin d’interroger d’abord l’interface.

Avant d’utiliser `IUnknown` l’interface, vous devez vérifier qu’elle n’est pas null.

##  <a name="clear"></a>  CComDynamicUnkArray::clear

Vide le tableau.

```
void clear();
```

##  <a name="ccomdynamicunkarray"></a>  CComDynamicUnkArray::CComDynamicUnkArray

Constructeur.

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>Notes

Affecte à la taille de la collection la valeur zéro et initialise les valeurs à la valeur NULL. Le destructeur libère la collection, si nécessaire.

##  <a name="dtor"></a>  CComDynamicUnkArray::~CComDynamicUnkArray

Destructeur.

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>Notes

Libère les ressources allouées par le constructeur de classe.

##  <a name="end"></a>  CComDynamicUnkArray::end

Retourne un pointeur vers un point après le `IUnknown` dernier pointeur de la collection.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un `IUnknown` pointeur d’interface.

##  <a name="getat"></a>  CComDynamicUnkArray::GetAt

Récupère l’élément à l’index spécifié.

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l'élément à récupérer.

### <a name="return-value"></a>Valeur de retour

Pointeur vers une interface [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) .

##  <a name="getcookie"></a>  CComDynamicUnkArray::GetCookie

Appelez cette méthode pour obtenir le cookie associé à un pointeur `IUnknown` donné.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Paramètres

*ppFind*<br/>
`IUnknown` Pointeur pour lequel le cookie associé est requis.

### <a name="return-value"></a>Valeur de retour

Retourne le cookie associé au `IUnknown` pointeur, ou zéro si aucun pointeur correspondant `IUnknown` n’est trouvé.

### <a name="remarks"></a>Notes

S’il existe plusieurs instances du même `IUnknown` pointeur, cette fonction retourne le cookie du premier.

##  <a name="getsize"></a>  CComDynamicUnkArray::GetSize

Retourne la longueur d’un tableau.

```
int GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur du tableau.

##  <a name="getunknown"></a>  CComDynamicUnkArray::GetUnknown

Appelez cette méthode pour obtenir le `IUnknown` pointeur associé à un cookie donné.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Paramètres

*dwCookie*<br/>
Cookie pour lequel le pointeur associé `IUnknown` est requis.

### <a name="return-value"></a>Valeur de retour

Retourne le `IUnknown` pointeur, ou null si aucun cookie correspondant n’est trouvé.

##  <a name="remove"></a>  CComDynamicUnkArray::Remove

Appelez cette méthode pour supprimer un `IUnknown` pointeur du tableau.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Paramètres

*dwCookie*<br/>
Cookie qui référence le `IUnknown` pointeur à supprimer du tableau.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le pointeur est supprimé; Sinon, FALSe.

## <a name="see-also"></a>Voir aussi

[CComUnkArray, classe](../../atl/reference/ccomunkarray-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
