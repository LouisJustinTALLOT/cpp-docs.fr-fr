---
title: _U_rect, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
ms.openlocfilehash: 306092a00a1e119263f4563eea181d7d3ee2b4b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274523"
---
# <a name="urect-class"></a>_U_rect, classe

Permet à cette classe d’adaptateur argument soit `RECT` les pointeurs ou références à passer à une fonction qui est implémentée en termes de pointeurs.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|Pointeur vers un `RECT`.|

## <a name="remarks"></a>Notes

La classe définit deux surcharges de constructeur : une accepte un **RECT &** argument et l’autre accepte un `LPRECT` argument. Le premier constructeur stocke l’adresse de l’argument de référence dans le membre de données unique de la classe, [m_lpRect](#_u_rect__m_lprect). L’argument du constructeur de pointeur est stocké directement, sans conversion.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlwin.h

##  <a name="_u_rect__m_lprect"></a>  _U_RECT::m_lpRect

La classe contient la valeur passée à un de ses constructeurs comme publique `LPRECT` membre de données.

```
LPRECT m_lpRect;
```

##  <a name="_u_rect___u_rect"></a>  _U_RECT::_U_RECT

L’adresse de l’argument de référence est stockée dans le membre de données unique de la classe, [m_lpRect](#_u_rect__m_lprect).

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*rc*<br/>
Un `RECT` référence.

*lpRect*<br/>
Un `RECT` pointeur.

### <a name="remarks"></a>Notes

L’argument du constructeur de pointeur est stocké directement, sans conversion.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
