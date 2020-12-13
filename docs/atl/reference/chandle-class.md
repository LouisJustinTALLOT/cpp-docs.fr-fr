---
description: 'En savoir plus sur : classe CHandle'
title: CHandle, classe
ms.date: 07/09/2019
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
ms.openlocfilehash: 01c3b281daf829bc6488df35114c6cb853640ed1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141672"
---
# <a name="chandle-class"></a>CHandle, classe

Cette classe fournit des méthodes pour créer et utiliser un objet descripteur.

## <a name="syntax"></a>Syntaxe

```
class CHandle
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHandle::CHandle](#chandle)|Constructeur.|
|[CHandle :: ~ CHandle](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHandle :: Attach](#attach)|Appelez cette méthode pour attacher l' `CHandle` objet à un handle existant.|
|[CHandle :: Close](#close)|Appelez cette méthode pour fermer un `CHandle` objet.|
|[CHandle ::D Etach](#detach)|Appelez cette méthode pour détacher un handle d’un `CHandle` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[HANDLE CHandle :: Operator](#operator_handle)|Retourne la valeur du handle stocké.|
|[CHandle :: Operator =](#operator_eq)|Opérateur d'assignation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CHandle :: m_h](#m_h)|Variable membre qui stocke le descripteur.|

## <a name="remarks"></a>Notes

Un `CHandle` objet peut être utilisé chaque fois qu’un handle est requis : la principale différence réside dans le fait que l' `CHandle` objet sera automatiquement supprimé.

> [!NOTE]
> Certaines fonctions d’API utilisent NULL comme handle vide ou non valide, tandis que d’autres utilisent INVALID_HANDLE_VALUE. `CHandle` utilise uniquement la valeur NULL et traite INVALID_HANDLE_VALUE comme un handle réel. Si vous appelez une API qui peut retourner INVALID_HANDLE_VALUE, vous devez vérifier cette valeur avant d’appeler [CHandle :: Attach](#attach) ou de la passer au `CHandle` constructeur, et passer NULL à la place.

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="chandleattach"></a><a name="attach"></a> CHandle :: Attach

Appelez cette méthode pour attacher l' `CHandle` objet à un handle existant.

```cpp
void Attach(HANDLE h) throw();
```

### <a name="parameters"></a>Paramètres

*h*<br/>
`CHandle` prendra possession du handle *h*.

### <a name="remarks"></a>Notes

Assigne l' `CHandle` objet au handle *h* , puis appelle **h. Detach ()**. Dans les builds de débogues, un ATLASSERT est déclenché si *h* a la valeur null. Aucune autre vérification de la validité du descripteur n’est effectuée.

## <a name="chandlechandle"></a><a name="chandle"></a> CHandle::CHandle

Constructeur.

```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Handle existant ou `CHandle` .

### <a name="remarks"></a>Notes

Crée un `CHandle` objet, éventuellement à l’aide d’un handle ou d’un `CHandle` objet existant.

## <a name="chandlechandle"></a><a name="dtor"></a> CHandle :: ~ CHandle

Destructeur.

```
~CHandle() throw();
```

### <a name="remarks"></a>Notes

Libère l' `CHandle` objet en appelant [CHandle :: Close](#close).

## <a name="chandleclose"></a><a name="close"></a> CHandle :: Close

Appelez cette méthode pour fermer un `CHandle` objet.

```cpp
void Close() throw();
```

### <a name="remarks"></a>Notes

Ferme un handle d’objet ouvert. Si le handle a la valeur NULL, ce qui est le cas si `Close` a déjà été appelé, un ATLASSERT est déclenché dans les versions Debug.

## <a name="chandledetach"></a><a name="detach"></a> CHandle ::D Etach

Appelez cette méthode pour détacher un handle d’un `CHandle` objet.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le handle en cours de détachement.

### <a name="remarks"></a>Notes

Libère la propriété du descripteur.

## <a name="chandlem_h"></a><a name="m_h"></a> CHandle :: m_h

Variable membre qui stocke le descripteur.

```
HANDLE m_h;
```

## <a name="chandleoperator-"></a><a name="operator_eq"></a> CHandle :: Operator =

Opérateur d’assignation.

```
CHandle& operator=(CHandle& h) throw();
```

### <a name="parameters"></a>Paramètres

*h*<br/>
`CHandle` prendra possession du handle *h*.

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence au nouvel `CHandle` objet.

### <a name="remarks"></a>Notes

Si l' `CHandle` objet contient actuellement un handle, il est fermé. La `CHandle` référence de handle de l’objet passé est définie sur null. Cela permet de garantir que deux `CHandle` objets ne contiendront jamais le même handle actif.

## <a name="chandleoperator-handle"></a><a name="operator_handle"></a> HANDLE CHandle :: Operator

Retourne la valeur du handle stocké.

```
operator HANDLE() const throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur stockée dans [CHandle :: m_H](#m_h).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
