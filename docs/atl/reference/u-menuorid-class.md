---
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
ms.openlocfilehash: 419c9e79178db12efe278838ec8630e04ac3c461
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325833"
---
# <a name="_u_menuorid-class"></a>Classe _U_MENUorID

Cette classe fournit `CreateWindow` des `CreateWindowEx`emballages pour et .

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
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|Constructeur.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|Une poignée à un menu.|

## <a name="remarks"></a>Notes

Cette classe d’adaptateur d’argument permet soit aux cartes d’ID (UINT) ou aux poignées de menu (HMENUs) d’être transmises à une fonction sans exiger un casting explicite de la part de l’appelant.

Cette classe est conçue pour la mise en œuvre d’emballages à l’API Windows, en particulier les fonctions [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) et [CreateWindowEx,](/windows/win32/api/winuser/nf-winuser-createwindowexw) qui acceptent tous deux un argument HMENU qui peut être un identifiant de fenêtre pour enfants (UINT) plutôt qu’une poignée de menu. Par exemple, vous pouvez voir cette classe en usage comme un paramètre pour [CWindowImpl::Créer](cwindowimpl-class.md#create).

La classe définit deux surcharges de constructeurs : l’une accepte un argument de l’UINT et l’autre accepte un argument de HMENU. L’argument UINT est juste jeté à un HMENU dans le constructeur et le résultat stocké dans le membre de données unique de la classe, [m_hMenu](#_u_menuorid__m_hmenu). L’argument du constructeur HMENU est stocké directement sans conversion.

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="_u_menuoridm_hmenu"></a><a name="_u_menuorid__m_hmenu"></a>_U_MENUorID::m_hMenu

La classe détient la valeur transmise à l’un de ses constructeurs en tant que membre public des données HMENU.

```
HMENU m_hMenu;
```

## <a name="_u_menuorid_u_menuorid"></a><a name="_u_menuorid___u_menuorid"></a>_U_MENUorID::_U_MENUorID

L’argument UINT est juste jeté à un HMENU dans le constructeur et le résultat stocké dans le membre de données unique de la classe, [m_hMenu](#_u_menuorid__m_hmenu).

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Un identificateur de fenêtre d’enfant.

*hMenu*<br/>
Une poignée de menu.

### <a name="remarks"></a>Notes

L’argument du constructeur HMENU est stocké directement sans conversion.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
