---
description: 'En savoir plus sur : classe _U_MENUorID'
title: Classe _U_MENUorID
ms.date: 11/04/2016
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
ms.openlocfilehash: 4418e9db455e72643c497925c19900b41c9b9f38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138786"
---
# <a name="_u_menuorid-class"></a>Classe _U_MENUorID

Cette classe fournit des wrappers pour `CreateWindow` et `CreateWindowEx` .

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class _U_MENUorID
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[_U_MENUorID :: _U_MENUorID](#_u_menuorid___u_menuorid)|Constructeur.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[_U_MENUorID :: m_hMenu](#_u_menuorid__m_hmenu)|Handle d’un menu.|

## <a name="remarks"></a>Notes

Cette classe d’adaptateur d’arguments permet de passer des ID (UINT) ou des handles de menu (HMENUs) à une fonction sans avoir besoin d’un cast explicite sur la partie de l’appelant.

Cette classe est conçue pour implémenter des wrappers pour l’API Windows, en particulier les fonctions [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) et [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) , qui acceptent les deux un argument HMENU qui peut être un identificateur de fenêtre enfant (uint) plutôt qu’un handle de menu. Par exemple, vous pouvez voir cette classe en cours d’utilisation en tant que paramètre de [CWindowImpl :: Create](cwindowimpl-class.md#create).

La classe définit deux surcharges de constructeur : l’une accepte un argument UINT et l’autre accepte un argument HMENU. L’argument UINT est simplement casté en un HMENU dans le constructeur et le résultat stocké dans le membre de données unique de la classe, [m_hMenu](#_u_menuorid__m_hmenu). L’argument du constructeur HMENU est stocké directement sans conversion.

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

## <a name="_u_menuoridm_hmenu"></a><a name="_u_menuorid__m_hmenu"></a> _U_MENUorID :: m_hMenu

La classe contient la valeur passée à l’un de ses constructeurs sous la forme d’un membre de données HMENU public.

```
HMENU m_hMenu;
```

## <a name="_u_menuorid_u_menuorid"></a><a name="_u_menuorid___u_menuorid"></a> _U_MENUorID :: _U_MENUorID

L’argument UINT est simplement casté en un HMENU dans le constructeur et le résultat stocké dans le membre de données unique de la classe, [m_hMenu](#_u_menuorid__m_hmenu).

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Identificateur de fenêtre enfant.

*hMenu*<br/>
Handle de menu.

### <a name="remarks"></a>Notes

L’argument du constructeur HMENU est stocké directement sans conversion.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
