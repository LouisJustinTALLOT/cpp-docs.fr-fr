---
title: Classe CHandle
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
ms.openlocfilehash: 7c72ded75298ed69efe73c1a81abf404545ea9b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326922"
---
# <a name="chandle-class"></a>Classe CHandle

Cette classe fournit des méthodes pour créer et utiliser un objet de poignée.

## <a name="syntax"></a>Syntaxe

```
class CHandle
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHandle::CHandle](#chandle)|Constructeur.|
|[CHandle: : CHandle](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHandle::Attach](#attach)|Appelez cette méthode `CHandle` pour attacher l’objet à une poignée existante.|
|[CHandle::Fermer](#close)|Appelez cette méthode `CHandle` pour fermer un objet.|
|[CHandle::Detach](#detach)|Appelez cette méthode pour détacher `CHandle` une poignée d’un objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CHandle::opérateur HANDLE](#operator_handle)|Retourne la valeur de la poignée stockée.|
|[CHandle::opérateur](#operator_eq)|Opérateur d'assignation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CHandle::m_h](#m_h)|La variable de membre qui stocke la poignée.|

## <a name="remarks"></a>Notes

Un `CHandle` objet peut être utilisé chaque fois qu’une `CHandle` poignée est nécessaire : la principale différence est que l’objet sera automatiquement supprimé.

> [!NOTE]
> Certaines fonctions API utiliseront NULL comme poignée vide ou invalide, tandis que d’autres utiliseront INVALID_HANDLE_VALUE. `CHandle`utilise uniquement NULL et traitera INVALID_HANDLE_VALUE comme une vraie poignée. Si vous appelez un API qui peut retourner INVALID_HANDLE_VALUE, vous devriez vérifier cette valeur avant `CHandle` d’appeler [CHandle::Attach](#attach) ou le transmettre au constructeur, et plutôt passer NULL.

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="chandleattach"></a><a name="attach"></a>CHandle::Attach

Appelez cette méthode `CHandle` pour attacher l’objet à une poignée existante.

```
void Attach(HANDLE h) throw();
```

### <a name="parameters"></a>Paramètres

*h*<br/>
`CHandle`prendra possession de la poignée *h*.

### <a name="remarks"></a>Notes

Assigne `CHandle` l’objet à la poignée *h,* puis appelle **h.Detach()**. Dans les constructions de débogaches, un ATLASSERT sera soulevé si *h* est NULL. Aucune autre vérification quant à la validité de la poignée n’est faite.

## <a name="chandlechandle"></a><a name="chandle"></a>CHandle::CHandle

Constructeur.

```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Une poignée `CHandle`existante ou .

### <a name="remarks"></a>Notes

Crée un `CHandle` nouvel objet, en option `CHandle` à l’aide d’une poignée ou d’un objet existant.

## <a name="chandlechandle"></a><a name="dtor"></a>CHandle: : CHandle

Destructeur.

```
~CHandle() throw();
```

### <a name="remarks"></a>Notes

Libère l’objet `CHandle` en appelant [CHandle::Close](#close).

## <a name="chandleclose"></a><a name="close"></a>CHandle::Fermer

Appelez cette méthode `CHandle` pour fermer un objet.

```
void Close() throw();
```

### <a name="remarks"></a>Notes

Ferme une poignée d’objet ouvert. Si la poignée est NULL, ce `Close` qui sera le cas si elle a déjà été appelée, un ATLASSERT sera soulevé dans les constructions de débogé.

## <a name="chandledetach"></a><a name="detach"></a>CHandle::Detach

Appelez cette méthode pour détacher `CHandle` une poignée d’un objet.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la poignée étant détachée.

### <a name="remarks"></a>Notes

Libère la propriété de la poignée.

## <a name="chandlem_h"></a><a name="m_h"></a>CHandle::m_h

La variable de membre qui stocke la poignée.

```
HANDLE m_h;
```

## <a name="chandleoperator-"></a><a name="operator_eq"></a>CHandle::opérateur

L’opérateur de l’affectation.

```
CHandle& operator=(CHandle& h) throw();
```

### <a name="parameters"></a>Paramètres

*h*<br/>
`CHandle`prendra possession de la poignée *h*.

### <a name="return-value"></a>Valeur de retour

Renvoie une référence `CHandle` au nouvel objet.

### <a name="remarks"></a>Notes

Si `CHandle` l’objet contient actuellement une poignée, il sera fermé. L’objet `CHandle` en cours d’adoption aura son ensemble de référence de poignée à NULL. Cela garantit que `CHandle` deux objets ne contiendra jamais la même poignée active.

## <a name="chandleoperator-handle"></a><a name="operator_handle"></a>CHandle::opérateur HANDLE

Retourne la valeur de la poignée stockée.

```
operator HANDLE() const throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur stockée dans [CHandle::m_h](#m_h).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
