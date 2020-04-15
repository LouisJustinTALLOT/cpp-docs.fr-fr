---
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
ms.openlocfilehash: 8a4d5b2a770b3f0ecfe10be0fbad22a702aa0531
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325811"
---
# <a name="_u_rect-class"></a>Classe _U_RECT

Cette classe d’adaptateur d’argument permet soit `RECT` des pointeurs ou des références à passer à une fonction qui est implémentée en termes de pointeurs.

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
|[_U_RECT::_U_RECT](#_u_rect___u_rect)|Constructeur.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|Pointeur `RECT`à un .|

## <a name="remarks"></a>Notes

La classe définit deux surcharges de constructeurs : l’une accepte un ARGUMENT `LPRECT` **reCT&** et l’autre accepte un argument. Le premier constructeur stocke l’adresse de l’argument de référence dans le seul membre de la classe, [m_lpRect](#_u_rect__m_lprect). L’argument du constructeur de pointeur est stocké directement sans conversion.

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="_u_rectm_lprect"></a><a name="_u_rect__m_lprect"></a>_U_RECT::m_lpRect

La classe détient la valeur transmise à l’un de ses constructeurs en tant que membre public `LPRECT` des données.

```
LPRECT m_lpRect;
```

## <a name="_u_rect_u_rect"></a><a name="_u_rect___u_rect"></a>_U_RECT::_U_RECT

L’adresse de l’argument de référence est stockée dans le seul membre de la donnée de la classe, [m_lpRect](#_u_rect__m_lprect).

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*Rc*<br/>
Une référence `RECT`.

*lpRect*<br/>
Un `RECT` pointeur.

### <a name="remarks"></a>Notes

L’argument du constructeur de pointeur est stocké directement sans conversion.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
