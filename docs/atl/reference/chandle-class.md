---
title: CHandle, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 64c2cb1531d9330e075a06c65ff022115d0fb6b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499916"
---
# <a name="chandle-class"></a>CHandle, classe

Cette classe fournit des méthodes pour la création et utilisation d’un objet de handle.

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
|[CHandle::Attach](#attach)|Appelez cette méthode pour attacher le `CHandle` objet vers un handle existant.|
|[CHandle::Close](#close)|Appelez cette méthode pour fermer un `CHandle` objet.|
|[CHandle::Detach](#detach)|Appelez cette méthode pour détacher un handle à partir d’un `CHandle` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CHandle::operator HANDLE](#operator_handle)|Retourne la valeur du handle stockée.|
|[CHandle::operator =](#operator_eq)|Opérateur d'assignation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CHandle::m_h](#m_h)|La variable de membre qui stocke le handle.|

## <a name="remarks"></a>Notes

Un `CHandle` objet peut être utilisé chaque fois qu’un handle est nécessaire : la principale différence est que le `CHandle` objet sera automatiquement supprimé.

> [!NOTE]
>  Certaines fonctions d’API utilise NULL comme un handle non valide ou vide, tandis que d’autres utilisent INVALID_HANDLE_VALUE. `CHandle` utilise uniquement NULL et va traite INVALID_HANDLE_VALUE comme un handle réel. Si vous appelez une API qui peut retourner INVALID_HANDLE_VALUE, vous devez rechercher cette valeur avant d’appeler [CHandle::Attach](#attach) ou en le passant à la `CHandle` constructeur et passer à la place la valeur NULL.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="attach"></a>  CHandle::Attach

Appelez cette méthode pour attacher le `CHandle` objet vers un handle existant.

```
void Attach(HANDLE h) throw();
```

### <a name="parameters"></a>Paramètres

*h*<br/>
`CHandle` prend possession du handle *h*.

### <a name="remarks"></a>Notes

Assigne le `CHandle` de l’objet à la *h* gérer. Dans les versions débogue une ATLASSERT ; sera déclenchée si *h* a la valeur NULL. Aucune autre vérification quant à la validité de la poignée est effectuée.

##  <a name="chandle"></a>  CHandle::CHandle

Constructeur.

```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Un handle existant ou `CHandle`.

### <a name="remarks"></a>Notes

Crée un `CHandle` de l’objet, si vous le souhaitez à l’aide d’un handle existant ou `CHandle` objet.

##  <a name="dtor"></a>  CHandle :: ~ CHandle

Destructeur.

```
~CHandle() throw();
```

### <a name="remarks"></a>Notes

Libère le `CHandle` objet en appelant [CHandle::Close](#close).

##  <a name="close"></a>  CHandle::Close

Appelez cette méthode pour fermer un `CHandle` objet.

```
void Close() throw();
```

### <a name="remarks"></a>Notes

Ferme le handle d’objet ouvert. Si le handle est NULL, ce qui sera le cas si `Close` a déjà été appelée, un ATLASSERT ; sera déclenché dans les versions debug.

##  <a name="detach"></a>  CHandle::Detach

Appelez cette méthode pour détacher un handle à partir d’un `CHandle` objet.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le handle en cours de détachement.

### <a name="remarks"></a>Notes

Libère la propriété de la poignée.

##  <a name="m_h"></a>  CHandle::m_h

La variable de membre qui stocke le handle.

```
HANDLE m_h;
```

##  <a name="operator_eq"></a>  CHandle::operator =

L’opérateur d’assignation.

```
CHandle& operator=(CHandle& h) throw();
```

### <a name="parameters"></a>Paramètres

*h*<br/>
`CHandle` prend possession du handle *h*.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la nouvelle `CHandle` objet.

### <a name="remarks"></a>Notes

Si le `CHandle` objet contient actuellement un handle, il va être fermée. Le `CHandle` de l’objet passé dans aura sa référence de la poignée de la valeur NULL. Cela garantit que deux `CHandle` objets ne contiendra jamais le même handle actif.

##  <a name="operator_handle"></a>  CHandle::operator HANDLE

Retourne la valeur du handle stockée.

```
operator HANDLE() const throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur stockée dans [CHandle::m_h](#m_h).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
