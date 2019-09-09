---
title: _U_STRINGorID, classe
ms.date: 11/04/2016
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
ms.openlocfilehash: c57d983e9680ce6d2cab375e427b80f4d3b6c2d6
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739577"
---
# <a name="_u_stringorid-class"></a>_U_STRINGorID, classe

Cette classe d’adaptateur d’arguments permet de passer des noms de ressource (LPCTSTRs) ou des ID de ressource (UINT) à une fonction sans obliger l’appelant à convertir l’ID en une chaîne à l’aide de la macro MAKEINTRESOURCE.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|Identificateur de ressource.|

## <a name="remarks"></a>Notes

Cette classe est conçue pour implémenter des wrappers à l’API de gestion des ressources Windows, telles que les fonctions [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea), [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)et [LoadMenu](/windows/win32/api/winuser/nf-winuser-loadmenuw) , qui acceptent un argument LPCTSTR qui peut être le nom d’une ressource ou son ID.

La classe définit deux surcharges de constructeur : l’une accepte un argument LPCTSTR et l’autre accepte un argument UINT. L’argument UINT est converti en un type de ressource compatible avec les fonctions de gestion de ressources de Windows à l’aide de la macro MAKEINTRESOURCE et le résultat stocké dans le membre de données unique de la classe, [m_lpstr](#_u_stringorid__m_lpstr). L’argument du constructeur LPCTSTR est stocké directement sans conversion.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlwin. h

##  <a name="_u_stringorid__m_lpstr"></a>  _U_STRINGorID::m_lpstr

La classe contient la valeur passée à l’un de ses constructeurs en tant que membre de données LPCTSTR public.

```
LPCTSTR m_lpstr;
```

##  <a name="_u_stringorid___u_stringorid"></a>  _U_STRINGorID::_U_STRINGorID

Le constructeur UINT convertit son argument en un type de ressource compatible avec les fonctions de gestion de ressources de Windows à l’aide de la macro MAKEINTRESOURCE et le résultat est stocké dans le membre de données unique de la classe, [m_lpstr](#_u_stringorid__m_lpstr).

```
_U_STRINGorID(UINT nID);
_U_STRINGorID(LPCTSTR lpString);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
ID de ressource.

*lpString*<br/>
Nom de ressource.

### <a name="remarks"></a>Notes

L’argument du constructeur LPCTSTR est stocké directement sans conversion.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
