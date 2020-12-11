---
description: 'En savoir plus sur : classe _U_RECT'
title: Classe _U_RECT
ms.date: 11/04/2016
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
ms.openlocfilehash: b3720107d1b64f930b4c64dff269de041d9b928c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157605"
---
# <a name="_u_rect-class"></a>Classe _U_RECT

Cette classe d’adaptateur d’arguments permet `RECT` de passer des pointeurs ou des références à une fonction implémentée en termes de pointeurs.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class _U_RECT
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[_U_RECT :: _U_RECT](#_u_rect___u_rect)|Constructeur.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[_U_RECT :: m_lpRect](#_u_rect__m_lprect)|Pointeur vers un `RECT` .|

## <a name="remarks"></a>Notes

La classe définit deux surcharges de constructeur : l’une accepte un argument **RECT&** et l’autre accepte un `LPRECT` argument. Le premier constructeur stocke l’adresse de l’argument de référence dans le membre de données unique de la classe, [m_lpRect](#_u_rect__m_lprect). L’argument du constructeur de pointeur est stocké directement sans conversion.

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

## <a name="_u_rectm_lprect"></a><a name="_u_rect__m_lprect"></a> _U_RECT :: m_lpRect

La classe contient la valeur passée à l’un de ses constructeurs en tant que `LPRECT` membre de données public.

```
LPRECT m_lpRect;
```

## <a name="_u_rect_u_rect"></a><a name="_u_rect___u_rect"></a> _U_RECT :: _U_RECT

L’adresse de l’argument de référence est stockée dans le membre de données unique de la classe, [m_lpRect](#_u_rect__m_lprect).

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*Release*<br/>
Une référence `RECT`.

*lpRect*<br/>
`RECT`Pointeur.

### <a name="remarks"></a>Notes

L’argument du constructeur de pointeur est stocké directement sans conversion.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
