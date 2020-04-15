---
title: Classe _U_STRINGorID
ms.date: 11/04/2016
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
ms.openlocfilehash: 4e46ceec077b8daf8ef2a76110d2fc19dd39ae26
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325825"
---
# <a name="_u_stringorid-class"></a>Classe _U_STRINGorID

Cette classe d’adaptateur d’argument permet soit que les noms de ressources (LPCTSTR) ou les identifiants de ressources (UINT) soient transmis à une fonction sans exiger de l’appelant qu’il convertisse l’ID en chaîne à l’aide de la macro MAKEINTRESOURCE.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class _U_STRINGorID
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|Constructeur.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|L’identifiant de ressource.|

## <a name="remarks"></a>Notes

Cette classe est conçue pour la mise en œuvre d’emballages à l’API de gestion des ressources Windows tels que les fonctions [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea), [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)et [LoadMenu,](/windows/win32/api/winuser/nf-winuser-loadmenuw) qui acceptent un argument LPCTSTR qui peut être soit le nom d’une ressource ou son ID.

La classe définit deux surcharges de constructeurs : l’une accepte un argument LPCTSTR et l’autre accepte un argument UINT. L’argument UINT est converti en un type de ressources compatible avec les fonctions de gestion des ressources Windows à l’aide de la macro MAKEINTRESOURCE et le résultat stocké dans le membre de données unique de la classe, [m_lpstr](#_u_stringorid__m_lpstr). L’argument du constructeur LPCTSTR est stocké directement sans conversion.

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="_u_stringoridm_lpstr"></a><a name="_u_stringorid__m_lpstr"></a>_U_STRINGorID::m_lpstr

La classe détient la valeur transmise à l’un de ses constructeurs en tant que membre public des données du LPCTSTR.

```
LPCTSTR m_lpstr;
```

## <a name="_u_stringorid_u_stringorid"></a><a name="_u_stringorid___u_stringorid"></a>_U_STRINGorID::_U_STRINGorID

Le constructeur UINT convertit son argument en un type de ressources compatible avec les fonctions de gestion des ressources Windows à l’aide de la macro MAKEINTRESOURCE et le résultat est stocké dans le seul membre de la donnée de la classe, [m_lpstr](#_u_stringorid__m_lpstr).

```
_U_STRINGorID(UINT nID);
_U_STRINGorID(LPCTSTR lpString);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Une pièce d’identité de ressource.

*lpString (lpString)*<br/>
Un nom de ressource.

### <a name="remarks"></a>Notes

L’argument du constructeur LPCTSTR est stocké directement sans conversion.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
