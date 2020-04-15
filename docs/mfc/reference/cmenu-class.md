---
title: Classe CMenu
ms.date: 11/04/2016
f1_keywords:
- CMenu
- AFXWIN/CMenu
- AFXWIN/CMenu::CMenu
- AFXWIN/CMenu::AppendMenu
- AFXWIN/CMenu::Attach
- AFXWIN/CMenu::CheckMenuItem
- AFXWIN/CMenu::CheckMenuRadioItem
- AFXWIN/CMenu::CreateMenu
- AFXWIN/CMenu::CreatePopupMenu
- AFXWIN/CMenu::DeleteMenu
- AFXWIN/CMenu::DeleteTempMap
- AFXWIN/CMenu::DestroyMenu
- AFXWIN/CMenu::Detach
- AFXWIN/CMenu::DrawItem
- AFXWIN/CMenu::EnableMenuItem
- AFXWIN/CMenu::FromHandle
- AFXWIN/CMenu::GetDefaultItem
- AFXWIN/CMenu::GetMenuContextHelpId
- AFXWIN/CMenu::GetMenuInfo
- AFXWIN/CMenu::GetMenuItemCount
- AFXWIN/CMenu::GetMenuItemID
- AFXWIN/CMenu::GetMenuItemInfo
- AFXWIN/CMenu::GetMenuState
- AFXWIN/CMenu::GetMenuString
- AFXWIN/CMenu::GetSafeHmenu
- AFXWIN/CMenu::GetSubMenu
- AFXWIN/CMenu::InsertMenu
- AFXWIN/CMenu::InsertMenuItem
- AFXWIN/CMenu::LoadMenu
- AFXWIN/CMenu::LoadMenuIndirect
- AFXWIN/CMenu::MeasureItem
- AFXWIN/CMenu::ModifyMenu
- AFXWIN/CMenu::RemoveMenu
- AFXWIN/CMenu::SetDefaultItem
- AFXWIN/CMenu::SetMenuContextHelpId
- AFXWIN/CMenu::SetMenuInfo
- AFXWIN/CMenu::SetMenuItemBitmaps
- AFXWIN/CMenu::SetMenuItemInfo
- AFXWIN/CMenu::TrackPopupMenu
- AFXWIN/CMenu::TrackPopupMenuEx
- AFXWIN/CMenu::m_hMenu
helpviewer_keywords:
- CMenu [MFC], CMenu
- CMenu [MFC], AppendMenu
- CMenu [MFC], Attach
- CMenu [MFC], CheckMenuItem
- CMenu [MFC], CheckMenuRadioItem
- CMenu [MFC], CreateMenu
- CMenu [MFC], CreatePopupMenu
- CMenu [MFC], DeleteMenu
- CMenu [MFC], DeleteTempMap
- CMenu [MFC], DestroyMenu
- CMenu [MFC], Detach
- CMenu [MFC], DrawItem
- CMenu [MFC], EnableMenuItem
- CMenu [MFC], FromHandle
- CMenu [MFC], GetDefaultItem
- CMenu [MFC], GetMenuContextHelpId
- CMenu [MFC], GetMenuInfo
- CMenu [MFC], GetMenuItemCount
- CMenu [MFC], GetMenuItemID
- CMenu [MFC], GetMenuItemInfo
- CMenu [MFC], GetMenuState
- CMenu [MFC], GetMenuString
- CMenu [MFC], GetSafeHmenu
- CMenu [MFC], GetSubMenu
- CMenu [MFC], InsertMenu
- CMenu [MFC], InsertMenuItem
- CMenu [MFC], LoadMenu
- CMenu [MFC], LoadMenuIndirect
- CMenu [MFC], MeasureItem
- CMenu [MFC], ModifyMenu
- CMenu [MFC], RemoveMenu
- CMenu [MFC], SetDefaultItem
- CMenu [MFC], SetMenuContextHelpId
- CMenu [MFC], SetMenuInfo
- CMenu [MFC], SetMenuItemBitmaps
- CMenu [MFC], SetMenuItemInfo
- CMenu [MFC], TrackPopupMenu
- CMenu [MFC], TrackPopupMenuEx
- CMenu [MFC], m_hMenu
ms.assetid: 40cacfdc-d45c-4ec7-bf28-991c72812499
ms.openlocfilehash: 5ec97d8cf039034078f29b38fb6a41d6ff9a5e53
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369980"
---
# <a name="cmenu-class"></a>Classe CMenu

Encapsulation du `HMENU`Windows.

## <a name="syntax"></a>Syntaxe

```
class CMenu : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMenu::CMenu](#cmenu)|Construit un objet `CMenu`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMenu::AppendMenu](#appendmenu)|Annexe d’un nouvel article à la fin de ce menu.|
|[CMenu::Attach](#attach)|Attache une poignée de `CMenu` menu Windows à un objet.|
|[CMenu::CheckMenuItem](#checkmenuitem)|Place une marque de contrôle à côté ou supprime une marque de contrôle d’un élément de menu dans le menu pop-up.|
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|Place un bouton radio à côté d’un élément de menu et supprime le bouton radio de tous les autres éléments du menu du groupe.|
|[CMenu::CreateMenu](#createmenu)|Crée un menu vide et `CMenu` le fixe à un objet.|
|[CMenu::CreatePopupMenu](#createpopupmenu)|Crée un menu pop-up vide et `CMenu` le fixe à un objet.|
|[CMenu::DeleteMenu](#deletemenu)|Supprime un élément spécifié du menu. Si l’élément menu a un menu pop-up associé, détruit la poignée au menu pop-up et libère la mémoire utilisée par elle.|
|[CMenu::DeleteTempMap](#deletetempmap)|Supprime tous `CMenu` les objets `FromHandle` temporaires créés par la fonction membre.|
|[CMenu::DestroyMenu](#destroymenu)|Détruit le menu attaché `CMenu` à un objet et libère tout souvenir que le menu occupait.|
|[CMenu::Detach](#detach)|Détache une poignée de menu `CMenu` Windows d’un objet et renvoie la poignée.|
|[CMenu::DrawItem](#drawitem)|Appelé par le cadre quand un aspect visuel d’un menu dessiné par le propriétaire change.|
|[CMenu::EnableMenuItem](#enablemenuitem)|Permet, désactive ou s’assombrit (gris) un élément de menu.|
|[CMenu::DeHandle](#fromhandle)|Retourne un pointeur à un `CMenu` objet donné une poignée de menu Windows.|
|[CMenu::GetDefaultItem](#getdefaultitem)|Détermine l’élément de menu par défaut sur le menu spécifié.|
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|Récupère l’ID contextuelle d’aide associé au menu.|
|[CMenu::GetMenuInfo](#getmenuinfo)|Récupère des informations sur un menu spécifique.|
|[CMenu::GetMenuItemCount](#getmenuitemcount)|Détermine le nombre d’éléments dans un menu pop-up ou haut de gamme.|
|[CMenu::GetMenuItemID](#getmenuitemid)|Obtient l’identifiant de menu-élément pour un élément de menu situé à la position spécifiée.|
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|Récupère des informations sur un élément de menu.|
|[CMenu::GetMenuState](#getmenustate)|Retourne l’état de l’élément de menu spécifié ou le nombre d’éléments dans un menu pop-up.|
|[CMenu::GetMenuString](#getmenustring)|Récupère l’étiquette de l’élément de menu spécifié.|
|[CMenu::GetSafeHmenu](#getsafehmenu)|Retourne `m_hMenu` l’enveloppe `CMenu` par cet objet.|
|[CMenu::GetSubMenu](#getsubmenu)|Récupère un pointeur sur un menu pop-up.|
|[CMenu::InsertMenu](#insertmenu)|Insère un nouvel élément de menu à la position spécifiée, déplaçant d’autres éléments dans le menu.|
|[CMenu::InsertMenuItem](#insertmenuitem)|Insère un nouvel élément de menu à la position spécifiée dans un menu.|
|[CMenu::LoadMenu](#loadmenu)|Charge une ressource de menu à partir du `CMenu` fichier exécutable et la fixe à un objet.|
|[CMenu::LoadMenuIndirect](#loadmenuindirect)|Charge un menu à partir d’un modèle `CMenu` de menu en mémoire et le fixe à un objet.|
|[CMenu::MeasureItem](#measureitem)|Appelé par le cadre pour déterminer les dimensions du menu lors de la création d’un menu dessiné par le propriétaire.|
|[CMenu::ModifyMenu](#modifymenu)|Modifications d’un élément de menu existant à la position spécifiée.|
|[CMenu::RemoveMenu](#removemenu)|Supprime un élément de menu avec un menu pop-up associé du menu spécifié.|
|[CMenu::SetDefaultItem](#setdefaultitem)|Définit l’élément de menu par défaut pour le menu spécifié.|
|[CMenu::SetMenuContextHelpId](#setmenucontexthelpid)|Définit l’ID contextuelle d’aide à associer au menu.|
|[CMenu::SetMenuInfo](#setmenuinfo)|Définit des informations sur un menu spécifique.|
|[CMenu::SetMenuItemBitmaps](#setmenuitembitmaps)|Associe les bitmaps de check-mark spécifiés à un élément de menu.|
|[CMenu::SetMenuItemInfo](#setmenuiteminfo)|Modifications de l’information sur un élément de menu.|
|[CMenu::TrackPopupMenu](#trackpopupmenu)|Affiche un menu pop-up flottant à l’emplacement spécifié et suit la sélection d’articles sur le menu pop-up.|
|[CMenu::TrackPopupMenuEx](#trackpopupmenuex)|Affiche un menu pop-up flottant à l’emplacement spécifié et suit la sélection d’articles sur le menu pop-up.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CMenu::opérateur HMENU](#operator_hmenu)|Récupère la poignée de l’objet du menu.|
|[CMenu::opérateur !](#operator_neq)|Détermine si deux objets de menu ne sont pas égaux.|
|[CMenu::opérateur](#operator_eq_eq)|Détermine si deux objets de menu sont égaux.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CMenu::m_hMenu](#m_hmenu)|Spécifie la poignée du `CMenu` menu Windows attaché à l’objet.|

## <a name="remarks"></a>Notes

Il fournit des fonctions de membre pour créer, suivre, mettre à jour et détruire un menu.

Créez `CMenu` un objet sur le cadre de `CMenu`pile comme un local, puis appelez les fonctions des membres pour manipuler le nouveau menu au besoin. Ensuite, appelez [CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu) pour définir le menu à une `CMenu` fenêtre, suivie immédiatement d’un appel à la fonction membre [de l’objet Detach.](#detach) La `CWnd::SetMenu` fonction membre définit le menu de la fenêtre pour le nouveau menu, provoque la fenêtre à redessiner pour refléter le changement de menu, et passe également la propriété du menu à la fenêtre. L’appel `Detach` à détacher le HMENU de l’objet, `CMenu` de sorte que lorsque la variable locale `CMenu` passe hors de portée, le `CMenu` destructeur d’objet ne tente pas de détruire un menu qu’il ne possède plus. Le menu lui-même est automatiquement détruit lorsque la fenêtre est détruite.

Vous pouvez utiliser la fonction de membre [LoadMenuIndirect](#loadmenuindirect) pour créer un menu à partir d’un modèle en mémoire, mais un menu créé à partir d’une ressource par un appel à [LoadMenu](#loadmenu) est plus facilement entretenu, et la ressource de menu elle-même peut être créée et modifiée par l’éditeur de menu.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cmenuappendmenu"></a><a name="appendmenu"></a>CMenu::AppendMenu

Annexe d’un nouvel article à la fin d’un menu.

```
BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL AppendMenu(
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>Paramètres

*nFlags*<br/>
Spécifie des informations sur l’état du nouvel élément de menu lorsqu’il est ajouté au menu. Il se compose d’une ou plusieurs des valeurs énumérées dans la section Remarques.

*nIDNewItem (en)*<br/>
Spécifie soit l’ID de commande du nouvel élément de menu ou, si `HMENU` *nFlags* est réglé pour MF_POPUP, la poignée de menu ( ) d’un menu pop-up. Le *paramètre nIDNewItem* est ignoré (pas nécessaire) si *nFlags* est réglé pour MF_SEPARATOR.

*lpszNewItem*<br/>
Spécifie le contenu du nouvel élément de menu. Le *paramètre nFlags* est utilisé pour interpréter *lpszNewItem* de la manière suivante:

|nFlags|Interprétation de lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Contient une valeur 32 bits fournie par l’application que l’application peut utiliser pour maintenir des données supplémentaires associées à l’élément de menu. Cette valeur 32 bits est disponible pour l’application lorsqu’elle traite les messages WM_MEASUREITEM et WM_DRAWITEM. La valeur est `itemData` stockée dans le membre de la structure fournie avec ces messages.|
|MF_STRING|Contient un pointeur à une corde non terminée. C’est l’interprétation par défaut.|
|MF_SEPARATOR|Le *paramètre lpszNewItem* est ignoré (non nécessaire).|

*pBmp (pBmp)*<br/>
Points à `CBitmap` un objet qui sera utilisé comme élément de menu.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

L’application peut spécifier l’état de l’élément de menu en fixant des valeurs dans *nFlags*. Lorsque *nIDNewItem* spécifie un menu pop-up, il devient une partie du menu auquel il est annexé. Si ce menu est détruit, le menu annexé sera également détruit. Un menu appendice doit `CMenu` être détaché d’un objet pour éviter tout conflit. Notez que MF_STRING et MF_OWNERDRAW ne sont pas valables `AppendMenu`pour la version bitmap de .

La liste suivante décrit les drapeaux qui peuvent être placés en *nFlags*:

- MF_CHECKED agit comme une bascule avec MF_UNCHECKED de placer la marque de contrôle par défaut à côté de l’élément. Lorsque l’application fournit des bitmaps de check-mark (voir la fonction membre [SetMenuItemBitmaps),](#setmenuitembitmaps) le bitmap de « check mark on » est affiché.

- MF_UNCHECKED agit comme une bascule avec MF_CHECKED pour supprimer une marque de contrôle à côté de l’élément. Lorsque l’application fournit des bitmaps `SetMenuItemBitmaps` de check-mark (voir la fonction membre), le bitmap "check mark off" est affiché.

- MF_DISABLED désactive l’élément de menu de sorte qu’il ne peut pas être sélectionné, mais ne l’affaiblit pas.

- MF_ENABLED permet l’élément de menu afin qu’il puisse être sélectionné et le restaure de son état tamisé.

- MF_GRAYED désactive l’élément de menu afin qu’il ne puisse pas être sélectionné et l’assombrit.

- MF_MENUBARBREAK Place l’article sur une nouvelle ligne dans des menus statiques ou dans une nouvelle colonne dans les menus pop-up. La nouvelle colonne de menu pop-up sera séparée de l’ancienne colonne par une ligne de démarcation verticale.

- MF_MENUBREAK Place l’article sur une nouvelle ligne dans des menus statiques ou dans une nouvelle colonne dans les menus pop-up. Aucune ligne de démarcation n’est placée entre les colonnes.

- MF_OWNERDRAW précise que l’article est un élément de tirage au propriétaire. Lorsque le menu est affiché pour la première fois, la fenêtre qui possède le menu reçoit un message WM_MEASUREITEM, qui récupère la hauteur et la largeur de l’élément de menu. Le message WM_DRAWITEM est celui envoyé chaque fois que le propriétaire doit mettre à jour l’apparence visuelle de l’élément du menu. Cette option n’est pas valable pour un élément de menu de haut niveau.

- MF_POPUP précise que l’élément menu a un menu pop-up associé à celui-ci. Le paramètre d’identification spécifie une poignée à un menu pop-up qui doit être associé à l’élément. Ceci est utilisé pour ajouter soit un menu pop-up de haut niveau ou un menu pop-up hiérarchique à un élément de menu pop-up.

- MF_SEPARATOR dessine une ligne de démarcation horizontale. Ne peut être utilisé que dans un menu pop-up. Cette ligne ne peut pas être tamisée, désactivée ou mise en surbrillance. D’autres paramètres sont ignorés.

- MF_STRING précise que l’élément du menu est une chaîne de caractères.

Chacun des groupes suivants énumère les drapeaux qui s’excluent mutuellement et ne peuvent pas être utilisés ensemble :

- MF_DISABLED, MF_ENABLED et MF_GRAYED

- MF_STRING, MF_OWNERDRAW, MF_SEPARATOR, et la version bitmap

- MF_MENUBARBREAK et MF_MENUBREAK

- MF_CHECKED et MF_UNCHECKED

Chaque fois qu’un menu qui réside dans une fenêtre est changé (que la fenêtre soit affichée ou non), l’application doit appeler [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:CreateMenu](#createmenu).

## <a name="cmenuattach"></a><a name="attach"></a>CMenu::Attach

Attache un menu Windows `CMenu` existant à un objet.

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>Paramètres

*hMenu*<br/>
Spécifie une poignée à un menu Windows.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’opération a été couronnée de succès; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction ne doit pas être appelée `CMenu` si un menu est déjà attaché à l’objet. La poignée de menu `m_hMenu` est stockée dans le membre de données.

Si le menu que vous souhaitez manipuler est déjà associé à une fenêtre, vous pouvez utiliser la fonction [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu) pour obtenir une poignée au menu.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenucheckmenuitem"></a><a name="checkmenuitem"></a>CMenu::CheckMenuItem

Ajoute des marques de contrôle ou supprime les points de contrôle des éléments de menu dans le menu pop-up.

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>Paramètres

*nIDCheckItem (en)*<br/>
Spécifie l’élément de menu à vérifier, tel que déterminé par *nCheck*.

*nCheck (en)*<br/>
Précise comment vérifier l’élément du menu et comment déterminer la position de l’élément dans le menu. Le *paramètre nCheck* peut être une combinaison de MF_CHECKED ou de MF_UNCHECKED avec des drapeaux MF_BYPOSITION ou MF_BYCOMMAND. Ces drapeaux peuvent être combinés en utilisant l’opérateur BITwise OU. Ils ont les significations suivantes :

- MF_BYCOMMAND précise que le paramètre donne l’id de commande de l’élément de menu existant. Il s’agit de la valeur par défaut.

- MF_BYPOSITION précise que le paramètre donne la position de l’élément de menu existant. Le premier élément est à la position 0.

- MF_CHECKED agit comme une bascule avec MF_UNCHECKED de placer la marque de contrôle par défaut à côté de l’élément.

- MF_UNCHECKED agit comme une bascule avec MF_CHECKED pour supprimer une marque de contrôle à côté de l’élément.

### <a name="return-value"></a>Valeur de retour

L’état précédent de l’article: MF_CHECKED ou MF_UNCHECKED, ou 0xFFFFFFFFFF si l’élément de menu n’existait pas.

### <a name="remarks"></a>Notes

Le *paramètre nIDCheckItem* spécifie l’élément à modifier.

Le *paramètre nIDCheckItem* peut identifier un élément de menu pop-up ainsi qu’un élément de menu. Aucune étape spéciale n’est requise pour vérifier un élément de menu pop-up. Les éléments de menu de haut niveau ne peuvent pas être vérifiés. Un élément de menu pop-up doit être vérifié par position car il n’a pas d’identifiant de menu-élément associé à celui-ci.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:GetMenuState](#getmenustate).

## <a name="cmenucheckmenuradioitem"></a><a name="checkmenuradioitem"></a>CMenu::CheckMenuRadioItem

Vérifie un élément de menu spécifié et en fait un élément radio.

```
BOOL CheckMenuRadioItem(
    UINT nIDFirst,
    UINT nIDLast,
    UINT nIDItem,
    UINT nFlags);
```

### <a name="parameters"></a>Paramètres

*nIDFirst*<br/>
Spécifie (en tant qu’ID ou décalage, selon la valeur de *nFlags*) le premier élément de menu dans le groupe de boutons radio.

*nIDLast (en)*<br/>
Spécifie (en tant qu’ID ou décalage, selon la valeur de *nFlags*) le dernier élément de menu dans le groupe de boutons radio.

*nIDItem (en)*<br/>
Spécifie (en tant qu’ID ou décalage, selon la valeur de *nFlags)* l’élément du groupe qui sera vérifié avec un bouton radio.

*nFlags*<br/>
Spécifie l’interprétation de *nIDFirst*, *nIDLast*, et *nIDItem* de la manière suivante:

|nFlags|Interprétation|
|------------|--------------------|
|MF_BYCOMMAND|Précise que le paramètre donne l’id de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si ni MF_BYCOMMAND ni MF_BYPOSITION n’est définie.|
|MF_BYPOSITION|Précise que le paramètre donne la position de l’élément de menu existant. Le premier élément est à la position 0.|

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès; sinon 0

### <a name="remarks"></a>Notes

Dans le même temps, la fonction décochait tous les autres éléments de menu dans le groupe associé et efface le drapeau de type radio-élément pour ces éléments. L’article vérifié est affiché à l’aide d’un bouton radio (ou balle) bitmap au lieu d’un bitmap de marque de contrôle.

### <a name="example"></a>Exemple

  Voir l’exemple pour [ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range).

## <a name="cmenucmenu"></a><a name="cmenu"></a>CMenu::CMenu

Crée un menu vide et `CMenu` le fixe à un objet.

```
CMenu();
```

### <a name="remarks"></a>Notes

Le menu n’est pas créé tant que vous n’avez pas appelé l’une des fonctions de membre de la création ou de la charge`CMenu:`

- [Createmenu](#createmenu)

- [CréerPopupMenu](#createpopupmenu)

- [LoadMenu (LoadMenu)](#loadmenu)

- [LoadMenuIndirect](#loadmenuindirect)

- [Attach](#attach)

## <a name="cmenucreatemenu"></a><a name="createmenu"></a>CMenu::CreateMenu

Crée un menu et le `CMenu` fixe à l’objet.

```
BOOL CreateMenu();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le menu a été créé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Le menu est d’abord vide. Les éléments du menu `AppendMenu` peuvent `InsertMenu` être ajoutés en utilisant la fonction ou la fonction membre.

Si le menu est attribué à une fenêtre, il est automatiquement détruit lorsque la fenêtre est détruite.

Avant de sortir, une application doit libérer les ressources du système associées à un menu si le menu n’est pas attribué à une fenêtre. Une application libère un menu en appelant la fonction membre [DestroyMenu.](#destroymenu)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

## <a name="cmenucreatepopupmenu"></a><a name="createpopupmenu"></a>CMenu::CreatePopupMenu

Crée un menu pop-up et `CMenu` le fixe à l’objet.

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le menu pop-up a été créé avec succès; sinon 0.

### <a name="remarks"></a>Notes

Le menu est d’abord vide. Les éléments du menu `AppendMenu` peuvent `InsertMenu` être ajoutés en utilisant la fonction ou la fonction membre. L’application peut ajouter le menu pop-up à un menu existant ou un menu pop-up. La `TrackPopupMenu` fonction membre peut être utilisée pour afficher ce menu comme un menu pop-up flottant et pour suivre les sélections sur le menu pop-up.

Si le menu est attribué à une fenêtre, il est automatiquement détruit lorsque la fenêtre est détruite. Si le menu est ajouté à un menu existant, il est automatiquement détruit lorsque ce menu est détruit.

Avant de sortir, une application doit libérer les ressources système associées à un menu pop-up si le menu n’est pas attribué à une fenêtre. Une application libère un menu en appelant la fonction membre [DestroyMenu.](#destroymenu)

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:CreateMenu](#createmenu).

## <a name="cmenudeletemenu"></a><a name="deletemenu"></a>CMenu::DeleteMenu

Supprime un élément du menu.

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Paramètres

*nPosition*<br/>
Spécifie l’élément de menu qui doit être supprimé, tel que déterminé par *nFlags*.

*nFlags*<br/>
Est utilisé pour interpréter *nPosition* de la manière suivante:

|nFlags|Interprétation de nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Précise que le paramètre donne l’id de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si ni MF_BYCOMMAND ni MF_BYPOSITION n’est définie.|
|MF_BYPOSITION|Précise que le paramètre donne la position de l’élément de menu existant. Le premier élément est à la position 0.|

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Si l’élément menu a un `DeleteMenu` menu pop-up associé, détruit la poignée au menu pop-up et libère la mémoire utilisée par le menu pop-up.

Chaque fois qu’un menu qui réside dans une fenêtre est changé (que la fenêtre soit affichée ou non), l’application doit appeler [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Exemple

  Voir l’exemple pour [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

## <a name="cmenudeletetempmap"></a><a name="deletetempmap"></a>CMenu::DeleteTempMap

Appelé automatiquement `CWinApp` par le gestionnaire de temps `CMenu` d’arrêt, supprime tous les objets temporaires créés par la fonction [membre FromHandle.](#fromhandle)

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Notes

`DeleteTempMap`détache l’objet du menu Windows `CMenu` attaché à un `CMenu` objet temporaire avant de supprimer l’objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

## <a name="cmenudestroymenu"></a><a name="destroymenu"></a>CMenu::DestroyMenu

Détruit le menu et toutes les ressources Windows qui ont été utilisées.

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le menu est détruit; sinon 0.

### <a name="remarks"></a>Notes

Le menu est `CMenu` détaché de l’objet avant qu’il ne soit détruit. La `DestroyMenu` fonction Windows est `CMenu` automatiquement appelée dans le destructeur.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:CreateMenu](#createmenu).

## <a name="cmenudetach"></a><a name="detach"></a>CMenu::Detach

Détache un menu Windows `CMenu` d’un objet et renvoie la poignée.

```
HMENU Detach();
```

### <a name="return-value"></a>Valeur de retour

La poignée, de type HMENU, à un menu Windows, si elle est réussie; autrement NULL.

### <a name="remarks"></a>Notes

Le `m_hMenu` membre des données est réglé sur NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

## <a name="cmenudrawitem"></a><a name="drawitem"></a>CMenu::DrawItem

Appelé par le cadre quand un aspect visuel d’un menu dessiné par le propriétaire change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Un pointeur vers une structure [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) qui contient des informations sur le type de dessin requis.

### <a name="remarks"></a>Notes

Le `itemAction` membre `DRAWITEMSTRUCT` de la structure définit l’action de dessin qui doit être effectuée. Remplacer cette fonction de membre pour implémenter le dessin d’un objet de dessin du `CMenu` propriétaire. L’application doit restaurer tous les objets d’interface graphique (GDI) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant la fin de cette fonction de membre.

Voir [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) pour une `DRAWITEMSTRUCT` description de la structure.

### <a name="example"></a>Exemple

Le code suivant provient de l’échantillon MFC [CTRLTEST](../../overview/visual-cpp-samples.md) :

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

## <a name="cmenuenablemenuitem"></a><a name="enablemenuitem"></a>CMenu::EnableMenuItem

Permet, désactive ou assombrit un élément de menu.

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>Paramètres

*nIDEnableItem*<br/>
Spécifie l’élément de menu à activer, tel que déterminé par *nEnable*. Ce paramètre peut spécifier les éléments du menu pop-up ainsi que les éléments de menu standard.

*nEnable*<br/>
Spécifie les mesures à prendre. Il peut s’agir d’une combinaison de MF_DISABLED, de MF_ENABLED ou de MF_GRAYED, avec MF_BYCOMMAND ou MF_BYPOSITION. Ces valeurs peuvent être combinées en utilisant l’opérateur BITwise OR. Ces valeurs ont les significations suivantes :

- MF_BYCOMMAND précise que le paramètre donne l’id de commande de l’élément de menu existant. Il s’agit de la valeur par défaut.

- MF_BYPOSITION précise que le paramètre donne la position de l’élément de menu existant. Le premier élément est à la position 0.

- MF_DISABLED désactive l’élément de menu de sorte qu’il ne peut pas être sélectionné, mais ne l’affaiblit pas.

- MF_ENABLED permet l’élément de menu afin qu’il puisse être sélectionné et le restaure de son état tamisé.

- MF_GRAYED désactive l’élément de menu afin qu’il ne puisse pas être sélectionné et l’assombrit.

### <a name="return-value"></a>Valeur de retour

État précédent (MF_DISABLED, MF_ENABLED ou MF_GRAYED) ou -1 s’il n’est pas valide.

### <a name="remarks"></a>Notes

Les fonctions des membres [CreateMenu](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu)et [LoadMenuIndirect](#loadmenuindirect) peuvent également définir l’état (activé, désactivé ou tamisé) d’un élément de menu.

L’utilisation de la valeur MF_BYPOSITION nécessite `CMenu`une application pour utiliser le correct . Si `CMenu` la barre de menu est utilisée, un élément de menu de haut niveau (un élément de la barre de menu) est affecté. Pour définir l’état d’un élément dans un menu pop-up ou imbriqué par position, une application doit spécifier le `CMenu` menu pop-up.

Lorsqu’une application spécifie le drapeau MF_BYCOMMAND, Windows vérifie tous les `CMenu`éléments du menu pop-up qui sont subordonnés à la ; par conséquent, à moins que `CMenu` des éléments de menu en double ne soient présents, l’utilisation de la barre de menu est suffisante.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

## <a name="cmenufromhandle"></a><a name="fromhandle"></a>CMenu::DeHandle

Retourne un pointeur à un `CMenu` objet donné une poignée Windows à un menu.

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>Paramètres

*hMenu*<br/>
Une poignée Windows à un menu.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CMenu` à un qui peut être temporaire ou permanent.

### <a name="remarks"></a>Notes

Si `CMenu` un objet n’est pas déjà attaché `CMenu` à l’objet du menu Windows, un objet temporaire est créé et joint.

Cet `CMenu` objet temporaire n’est valable que jusqu’à la prochaine fois que l’application a un temps d’inactivité dans sa boucle d’événement, date à laquelle tous les objets temporaires sont supprimés.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:CreateMenu](#createmenu).

## <a name="cmenugetdefaultitem"></a><a name="getdefaultitem"></a>CMenu::GetDefaultItem

Détermine l’élément de menu par défaut sur le menu spécifié.

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Paramètres

*gmdiFlags*<br/>
Valeur spécifiant comment la fonction recherche les éléments du menu. Ce paramètre ne peut être ni, un ou une combinaison des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|Spécifie que, si l’élément par défaut est celui qui ouvre un sous-mois, la fonction est de rechercher dans le sous-million correspondant récursivement. Si le sous-mois n’a pas d’élément par défaut, la valeur de retour identifie l’élément qui ouvre le sous-mois.<br /><br /> Par défaut, la fonction renvoie le premier élément par défaut sur le menu spécifié, qu’il s’agisse d’un élément qui ouvre un sous-mois.|
|GMDI_USEDISABLED|Précise que la fonction est de retourner un élément par défaut, même s’il est désactivé.<br /><br /> Par défaut, la fonction saute les éléments désactivés ou grisés.|

*fByPos*<br/>
Valeur spécifiant s’il faut récupérer l’identifiant de l’élément du menu ou sa position. Si ce paramètre est FALSE, l’identifiant est retourné. Sinon, la position est retournée.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de retour est l’identifiant ou la position de l’élément de menu. Si la fonction échoue, la valeur de retour est - 1.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la fonction Win32 [GetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-getmenudefaultitem), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:InsertMenu](#insertmenu).

## <a name="cmenugetmenucontexthelpid"></a><a name="getmenucontexthelpid"></a>CMenu::GetMenuContextHelpId

Récupère l’id d’aide contextuelle associé `CMenu`à .

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>Valeur de retour

Le contexte aide ID `CMenu` actuellement associé à si elle en a une; zéro autrement.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:InsertMenu](#insertmenu).

## <a name="cmenugetmenuinfo"></a><a name="getmenuinfo"></a>CMenu::GetMenuInfo

Récupère des informations pour un menu.

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>Paramètres

*lpcmi*<br/>
Un pointeur vers une structure [MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo) contenant des informations pour le menu.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de rendement est non zéro; sinon, la valeur de rendement est nulle.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer des informations sur le menu.

## <a name="cmenugetmenuitemcount"></a><a name="getmenuitemcount"></a>CMenu::GetMenuItemCount

Détermine le nombre d’éléments dans un menu pop-up ou haut de gamme.

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans le menu si la fonction est réussie; sinon -1.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

## <a name="cmenugetmenuitemid"></a><a name="getmenuitemid"></a>CMenu::GetMenuItemID

Obtient l’identifiant menu-élément pour un élément de menu situé à la position définie par *nPos*.

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
Spécifie la position (zéro à base) de l’élément de menu dont l’ID est récupéré.

### <a name="return-value"></a>Valeur de retour

L’ID d’élément pour l’élément spécifié dans un menu pop-up si la fonction est réussie. Si l’élément spécifié est un menu pop-up (par opposition à un élément dans le menu pop-up), la valeur de retour est de -1. Si *nPos* correspond à un élément de menu SEPARATOR, la valeur de retour est de 0.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:InsertMenu](#insertmenu).

## <a name="cmenugetmenuiteminfo"></a><a name="getmenuiteminfo"></a>CMenu::GetMenuItemInfo

Récupère des informations sur un élément de menu.

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Paramètres

*uItem (en)*<br/>
Identifiant ou position de l’élément de menu pour obtenir des informations sur. Le sens de ce paramètre `ByPos`dépend de la valeur de .

*lpMenuItemInfo*<br/>
Un pointeur à un [MENUITEMINFO](/windows/win32/api/winuser/ns-winuser-menuiteminfow), tel que décrit dans le Windows SDK, qui contient des informations sur le menu.

*fByPos*<br/>
Valeur spécifiant `nIDItem`le sens de . Par défaut, `ByPos` est FALSE, qui indique que uItem est un élément de menu identifiant. S’il `ByPos` n’est pas réglé sur FALSE, il indique une position d’élément de menu.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de retour est non zéro. Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations d’erreur étendues, utilisez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), telle que décrite dans le SDK Windows.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la fonction Win32 [GetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-getmenuiteminfow), tel que décrit dans le SDK Windows. Notez que dans la `GetMenuItemInfo`mise en œuvre MFC de , vous n’utilisez pas une poignée à un menu.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

## <a name="cmenugetmenustate"></a><a name="getmenustate"></a>CMenu::GetMenuState

Retourne l’état de l’élément de menu spécifié ou le nombre d’éléments dans un menu pop-up.

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Spécifie l’ID de l’élément de menu, tel que déterminé par *nFlags*.

*nFlags*<br/>
Spécifie la nature de *nID*. Ce peut être l’une des valeurs suivantes :

- MF_BYCOMMAND précise que le paramètre donne l’id de commande de l’élément de menu existant. Il s’agit de la valeur par défaut.

- MF_BYPOSITION précise que le paramètre donne la position de l’élément de menu existant. Le premier élément est à la position 0.

### <a name="return-value"></a>Valeur de retour

La valeur 0xFFFFFFFFFF si l’élément spécifié n’existe pas. Si *nId* identifie un menu pop-up, le byte de haute commande contient le nombre d’articles dans le menu pop-up et le byte de faible commande contient les drapeaux du menu associé au menu pop-up. Sinon, la valeur de retour est un masque (Boolean OU) des valeurs de la liste suivante (ce masque décrit l’état de l’élément de menu que *nId* identifie):

- MF_CHECKED agit comme une bascule avec MF_UNCHECKED de placer la marque de contrôle par défaut à côté de l’élément. Lorsque l’application fournit des bitmaps `SetMenuItemBitmaps` de check-mark (voir la fonction membre), le bitmap "check mark on" est affiché.

- MF_DISABLED désactive l’élément de menu de sorte qu’il ne peut pas être sélectionné, mais ne l’affaiblit pas.

- MF_ENABLED permet l’élément de menu afin qu’il puisse être sélectionné et le restaure de son état tamisé. Notez que la valeur de cette constante est de 0; une application ne doit pas tester contre 0 pour l’échec lors de l’utilisation de cette valeur.

- MF_GRAYED désactive l’élément de menu afin qu’il ne puisse pas être sélectionné et l’assombrit.

- MF_MENUBARBREAK Place l’article sur une nouvelle ligne dans des menus statiques ou dans une nouvelle colonne dans les menus pop-up. La nouvelle colonne de menu pop-up sera séparée de l’ancienne colonne par une ligne de démarcation verticale.

- MF_MENUBREAK Place l’article sur une nouvelle ligne dans des menus statiques ou dans une nouvelle colonne dans les menus pop-up. Aucune ligne de démarcation n’est placée entre les colonnes.

- MF_SEPARATOR dessine une ligne de démarcation horizontale. Ne peut être utilisé que dans un menu pop-up. Cette ligne ne peut pas être tamisée, désactivée ou mise en surbrillance. D’autres paramètres sont ignorés.

- MF_UNCHECKED agit comme une bascule avec MF_CHECKED pour supprimer une marque de contrôle à côté de l’élément. Lorsque l’application fournit des bitmaps `SetMenuItemBitmaps` de check-mark (voir la fonction membre), le bitmap "check mark off" est affiché. Notez que la valeur de cette constante est de 0; une application ne doit pas tester contre 0 pour l’échec lors de l’utilisation de cette valeur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

## <a name="cmenugetmenustring"></a><a name="getmenustring"></a>CMenu::GetMenuString

Copie de l’étiquette de l’élément de menu spécifié au tampon spécifié.

```
int GetMenuString(
    UINT nIDItem,
    LPTSTR lpString,
    int nMaxCount,
    UINT nFlags) const;

int GetMenuString(
    UINT nIDItem,
    CString& rString,
    UINT nFlags) const;
```

### <a name="parameters"></a>Paramètres

*nIDItem (en)*<br/>
Spécifie l’identifiant integer de l’élément du menu ou le décalage de l’élément du menu dans le menu, en fonction de la valeur de *nFlags*.

*lpString (lpString)*<br/>
Points à la mémoire tampon qui est de recevoir l’étiquette.

*rString (en)*<br/>
Une référence `CString` à un objet qui doit recevoir la chaîne de menu copiée.

*nMaxCount (en)*<br/>
Spécifie la longueur maximale (en caractères) de l’étiquette à copier. Si l’étiquette est plus longue que le maximum spécifié dans *nMaxCount*, les caractères supplémentaires sont tronqués.

*nFlags*<br/>
Spécifie l’interprétation du paramètre *nIDItem.* Ce peut être l’une des valeurs suivantes :

|nFlags|Interprétation de nIDItem|
|------------|-------------------------------|
|MF_BYCOMMAND|Précise que le paramètre donne l’id de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si ni MF_BYCOMMAND ni MF_BYPOSITION n’est définie.|
|MF_BYPOSITION|Précise que le paramètre donne la position de l’élément de menu existant. Le premier élément est à la position 0.|

### <a name="return-value"></a>Valeur de retour

Spécifie le nombre réel de caractères copiés sur le tampon, sans compter le terminateur nul.

### <a name="remarks"></a>Notes

Le *paramètre nMaxCount* doit être un plus grand que le nombre de caractères dans l’étiquette pour accueillir le caractère nul qui met fin à une chaîne.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:InsertMenu](#insertmenu).

## <a name="cmenugetsafehmenu"></a><a name="getsafehmenu"></a>CMenu::GetSafeHmenu

Retourne le HMENU `CMenu` enveloppé par cet`CMenu` objet, ou un pointeur NULL.

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:LoadMenu](#loadmenu).

## <a name="cmenugetsubmenu"></a><a name="getsubmenu"></a>CMenu::GetSubMenu

Récupère l’objet `CMenu` d’un menu pop-up.

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
Spécifie la position du menu pop-up contenu dans le menu. Les valeurs de position commencent à 0 pour le premier élément de menu. L’identifiant du menu pop-up ne peut pas être utilisé dans cette fonction.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CMenu` à `m_hMenu` un objet dont le membre contient une poignée au menu pop-up si un menu pop-up existe à la position donnée; autrement NULL. Si `CMenu` un objet n’existe pas, alors un objet temporaire est créé. Le `CMenu` pointeur retourné ne doit pas être stocké.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:TrackPopupMenu](#trackpopupmenu).

## <a name="cmenuinsertmenu"></a><a name="insertmenu"></a>CMenu::InsertMenu

Insère un nouvel élément de menu à la position spécifiée par *nPosition* et déplace d’autres éléments dans le menu.

```
BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL InsertMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>Paramètres

*nPosition*<br/>
Spécifie l’élément de menu avant lequel le nouvel élément de menu doit être inséré. Le *paramètre nFlags* peut être utilisé pour interpréter *nPosition* de la manière suivante :

|nFlags|Interprétation de nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Précise que le paramètre donne l’id de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si ni MF_BYCOMMAND ni MF_BYPOSITION n’est définie.|
|MF_BYPOSITION|Précise que le paramètre donne la position de l’élément de menu existant. Le premier élément est à la position 0. Si *nPosition* est de -1, le nouvel élément de menu est annexé à la fin du menu.|

*nFlags*<br/>
Précise comment *nPosition* est interprété et spécifie des informations sur l’état du nouvel élément de menu lorsqu’il est ajouté au menu. Pour une liste des drapeaux qui peuvent être fixés, consultez la fonction membre [de l’AnnexeMenu.](#appendmenu) Pour spécifier plus d’une valeur, utilisez l’opérateur BITwise OU pour les combiner avec le drapeau MF_BYCOMMAND ou MF_BYPOSITION.

*nIDNewItem (en)*<br/>
Spécifie soit l’ID de commande du nouvel élément de menu ou, si *nFlags* est configuré pour MF_POPUP, la poignée de menu (HMENU) du menu pop-up. Le *paramètre nIDNewItem* est ignoré (pas nécessaire) si *nFlags* est réglé pour MF_SEPARATOR.

*lpszNewItem*<br/>
Spécifie le contenu du nouvel élément de menu. *nFlags* peut être utilisé pour interpréter *lpszNewItem* de la manière suivante:

|nFlags|Interprétation de lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Contient une valeur 32 bits fournie par l’application que l’application peut utiliser pour maintenir des données supplémentaires associées à l’élément de menu. Cette valeur 32 bits est disponible `itemData` pour l’application dans le membre de la structure fournie par les [WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem) et [WM_DRAWITEM](/windows/win32/Controls/wm-drawitem) messages. Ces messages sont envoyés lorsque l’élément de menu est initialement affiché ou est modifié.|
|MF_STRING|Contient un long pointeur à une corde non terminée. C’est l’interprétation par défaut.|
|MF_SEPARATOR|Le *paramètre lpszNewItem* est ignoré (non nécessaire).|

*pBmp (pBmp)*<br/>
Points à `CBitmap` un objet qui sera utilisé comme élément de menu.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

L’application peut spécifier l’état de l’élément de menu en fixant des valeurs dans *nFlags*.

Chaque fois qu’un menu qui réside dans une fenêtre est modifié `CWnd::DrawMenuBar`(que la fenêtre soit affichée ou non), l’application doit appeler .

Lorsque *nIDNewItem* spécifie un menu pop-up, il devient une partie du menu dans lequel il est inséré. Si ce menu est détruit, le menu inséré sera également détruit. Un menu inséré doit être `CMenu` détaché d’un objet pour éviter tout conflit.

Si la fenêtre d’enfant active à interface de plusieurs documents (MDI) est maximisée et qu’une application insère un menu pop-up dans le menu de l’application MDI en appelant cette fonction et en spécifiant le drapeau MF_BYPOSITION, le menu est inséré une position plus éloignée que prévu. Cela se produit parce que le menu de contrôle de la fenêtre active de l’enfant MDI est inséré dans la première position de la barre de menu de la fenêtre de cadre MDI. Pour positionner correctement le menu, l’application doit ajouter 1 à la valeur de position qui serait autrement utilisée. Une application peut utiliser le WM_MDIGETACTIVE message pour déterminer si la fenêtre de l’enfant actuellement active est maximisée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

## <a name="cmenuinsertmenuitem"></a><a name="insertmenuitem"></a>CMenu::InsertMenuItem

Insère un nouvel élément de menu à la position spécifiée dans un menu.

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Paramètres

*uItem (en)*<br/>
Voir la description de *uItem* dans [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw) dans le SDK Windows.

*lpMenuItemInfo*<br/>
Voir la description de `InsertMenuItem` *lpmii* dans le Windows SDK.

*fByPos*<br/>
Voir la description de `InsertMenuItem` *fByPosition* dans le Windows SDK.

### <a name="remarks"></a>Notes

Cette fonction enveloppe [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw), décrit dans le SDK Windows.

## <a name="cmenuloadmenu"></a><a name="loadmenu"></a>CMenu::LoadMenu

Charge une ressource de menu à partir du fichier exécutable de l’application et la fixe à l’objet. `CMenu`

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>Paramètres

*lpszResourceName (en)*<br/>
Indique une chaîne non terminée qui contient le nom de la ressource de menu à charger.

*nIDResource (en)*<br/>
Spécifie l’ID du menu de la ressource du menu à charger.

### <a name="return-value"></a>Valeur de retour

Nonzero si la ressource de menu a été chargée avec succès; sinon 0.

### <a name="remarks"></a>Notes

Avant de sortir, une application doit libérer les ressources du système associées à un menu si le menu n’est pas attribué à une fenêtre. Une application libère un menu en appelant la fonction membre [DestroyMenu.](#destroymenu)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

## <a name="cmenuloadmenuindirect"></a><a name="loadmenuindirect"></a>CMenu::LoadMenuIndirect

Charge une ressource à partir d’un modèle `CMenu` de menu en mémoire et la fixe à l’objet.

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>Paramètres

*lpMenuTemplate*<br/>
Indique un modèle de menu (qui est une seule structure [MENUITEMTEMPLATEHEADER](/windows/win32/api/winuser/ns-winuser-menuitemtemplateheader) et une collection d’une ou plusieurs structures [MENUITEMTEMPLATE).](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) Pour plus d’informations sur ces deux structures, voir le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Nonzero si la ressource de menu a été chargée avec succès; sinon 0.

### <a name="remarks"></a>Notes

Un modèle de menu est un en-tête suivi d’une collection d’une ou plusieurs structures [MENUITEMTEMPLATE,](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) chacune pouvant contenir un ou plusieurs éléments de menu et des menus contextuels.

Le numéro de version doit être 0.

Les `mtOption` drapeaux doivent inclure MF_END pour le dernier élément dans une liste pop-up et pour le dernier élément de la liste principale. Voir `AppendMenu` la fonction membre pour d’autres drapeaux. Le `mtId` membre doit être omis de la structure MENUITEMTEMPLATE `mtOption`lorsque MF_POPUP est spécifiée dans .

L’espace alloué à la structure MENUITEMTEMPLATE `mtString` doit être suffisamment grand pour contenir le nom de l’élément du menu en tant que chaîne non terminée.

Avant de sortir, une application doit libérer les ressources du système associées à un menu si le menu n’est pas attribué à une fenêtre. Une application libère un menu en appelant la fonction membre [DestroyMenu.](#destroymenu)

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

## <a name="cmenum_hmenu"></a><a name="m_hmenu"></a>CMenu::m_hMenu

Spécifie la poignée HMENU du `CMenu` menu Windows attaché à l’objet.

```
HMENU m_hMenu;
```

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:LoadMenu](#loadmenu).

## <a name="cmenumeasureitem"></a><a name="measureitem"></a>CMenu::MeasureItem

Appelé par le cadre quand un menu avec le style propriétaire-tirage est créé.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpMeasureItemStruct*<br/>
Un pointeur `MEASUREITEMSTRUCT` vers une structure.

### <a name="remarks"></a>Notes

Par défaut, cette fonction de membre ne fait rien. Remplacez cette fonction de `MEASUREITEMSTRUCT` membre et remplissez la structure pour informer Windows des dimensions du menu.

Voir [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) pour une `MEASUREITEMSTRUCT` description de la structure.

### <a name="example"></a>Exemple

Le code suivant provient de l’échantillon MFC [CTRLTEST](../../overview/visual-cpp-samples.md) :

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

## <a name="cmenumodifymenu"></a><a name="modifymenu"></a>CMenu::ModifierMenu

Modifications d’un élément de menu existant à la position spécifiée par *nPosition*.

```
BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem = 0,
    LPCTSTR lpszNewItem = NULL);

BOOL ModifyMenu(
    UINT nPosition,
    UINT nFlags,
    UINT_PTR nIDNewItem,
    const CBitmap* pBmp);
```

### <a name="parameters"></a>Paramètres

*nPosition*<br/>
Spécifie l’élément de menu à changer. Le *paramètre nFlags* peut être utilisé pour interpréter *nPosition* de la manière suivante :

|nFlags|Interprétation de nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Précise que le paramètre donne l’id de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si ni MF_BYCOMMAND ni MF_BYPOSITION n’est définie.|
|MF_BYPOSITION|Précise que le paramètre donne la position de l’élément de menu existant. Le premier élément est à la position 0.|

*nFlags*<br/>
Précise comment *nPosition* est interprété et donne des informations sur les modifications à apporter à l’élément du menu. Pour une liste de drapeaux qui peuvent être définis, consultez la fonction membre [de l’Annexe.](#appendmenu)

*nIDNewItem (en)*<br/>
Spécifie soit l’ID de commande de l’élément de menu modifié ou, si *nFlags* est réglé pour MF_POPUP, la poignée de menu (HMENU) d’un menu pop-up. Le *paramètre nIDNewItem* est ignoré (pas nécessaire) si *nFlags* est réglé pour MF_SEPARATOR.

*lpszNewItem*<br/>
Spécifie le contenu du nouvel élément de menu. Le *paramètre nFlags* peut être utilisé pour interpréter *lpszNewItem* de la manière suivante :

|nFlags|Interprétation de lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Contient une valeur 32 bits fournie par l’application que l’application peut utiliser pour maintenir des données supplémentaires associées à l’élément de menu. Cette valeur 32 bits est disponible pour l’application lorsqu’elle traite MF_MEASUREITEM et MF_DRAWITEM.|
|MF_STRING|Contient un long pointeur à une `CString`corde non terminée ou à un .|
|MF_SEPARATOR|Le *paramètre lpszNewItem* est ignoré (non nécessaire).|

*pBmp (pBmp)*<br/>
Points à `CBitmap` un objet qui sera utilisé comme élément de menu.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

L’application spécifie le nouvel état de l’élément de menu en fixant des valeurs dans *nFlags*. Si cette fonction remplace un menu pop-up associé à l’élément de menu, elle détruit l’ancien menu pop-up et libère la mémoire utilisée par le menu pop-up.

Lorsque *nIDNewItem* spécifie un menu pop-up, il devient une partie du menu dans lequel il est inséré. Si ce menu est détruit, le menu inséré sera également détruit. Un menu inséré doit être `CMenu` détaché d’un objet pour éviter tout conflit.

Chaque fois qu’un menu qui réside dans une fenêtre est modifié `CWnd::DrawMenuBar`(que la fenêtre soit affichée ou non), l’application doit appeler . Pour modifier les attributs des éléments de menu `CheckMenuItem` existants, il est beaucoup plus rapide d’utiliser les fonctions et `EnableMenuItem` les fonctions des membres.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:InsertMenu](#insertmenu).

## <a name="cmenuoperator-hmenu"></a><a name="operator_hmenu"></a>CMenu::opérateur HMENU

Utilisez cet opérateur pour récupérer `CMenu` la poignée de l’objet.

```
operator HMENU() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, la poignée de l’objet; `CMenu` autrement, NULL.

### <a name="remarks"></a>Notes

Vous pouvez utiliser la poignée pour appeler directement les API Windows.

## <a name="cmenuoperator-"></a><a name="operator_neq"></a>CMenu::opérateur !

Détermine si deux menus ne sont logiquement pas égaux.

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>Paramètres

*Menu*<br/>
Objet `CMenu` pour la comparaison.

### <a name="remarks"></a>Notes

Test si un objet de menu sur le côté gauche n’est pas égal à un objet de menu sur le côté droit.

## <a name="cmenuoperator-"></a><a name="operator_eq_eq"></a>CMenu::opérateur

Détermine si deux menus sont logiquement égaux.

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>Paramètres

*Menu*<br/>
Objet `CMenu` pour la comparaison.

### <a name="remarks"></a>Notes

Test si un objet de menu sur le côté gauche est égal (en termes de valeur HMENU) à un objet de menu sur le côté droit.

## <a name="cmenuremovemenu"></a><a name="removemenu"></a>CMenu::RemoveMenu

Supprime un élément de menu avec un menu pop-up associé du menu.

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Paramètres

*nPosition*<br/>
Spécifie l’élément de menu à supprimer. Le *paramètre nFlags* peut être utilisé pour interpréter *nPosition* de la manière suivante :

|nFlags|Interprétation de nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Précise que le paramètre donne l’id de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si ni MF_BYCOMMAND ni MF_BYPOSITION n’est définie.|
|MF_BYPOSITION|Précise que le paramètre donne la position de l’élément de menu existant. Le premier élément est à la position 0.|

*nFlags*<br/>
Précise comment *nPosition* est interprété.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Il ne détruit pas la poignée pour un menu pop-up, de sorte que le menu peut être réutilisé. Avant d’appeler cette fonction, `GetSubMenu` l’application peut appeler `CMenu` la fonction membre pour récupérer l’objet pop-up pour la réutilisation.

Chaque fois qu’un menu qui se trouve dans une fenêtre est `CWnd::DrawMenuBar`modifié (que la fenêtre soit affichée ou non), l’application doit appeler .

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:InsertMenu](#insertmenu).

## <a name="cmenusetdefaultitem"></a><a name="setdefaultitem"></a>CMenu::SetDefaultItem

Définit l’élément de menu par défaut pour le menu spécifié.

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Paramètres

*uItem (en)*<br/>
Identifiant ou position du nouvel élément de menu par défaut ou - 1 pour aucun élément par défaut. Le sens de ce paramètre dépend de la valeur de *fByPos*.

*fByPos*<br/>
Valeur spécifiant le sens de *uItem*. Si ce paramètre est FALSE, *uItem* est un identifiant d’élément de menu. Sinon, il s’agit d’une position d’élément de menu.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de retour est non zéro. Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations d’erreur étendues, utilisez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), telle que décrite dans le SDK Windows.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la fonction Win32 [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:InsertMenu](#insertmenu).

## <a name="cmenusetmenucontexthelpid"></a><a name="setmenucontexthelpid"></a>CMenu::SetMenuContextHelpId

Associe un contexte `CMenu`aider ID avec .

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>Paramètres

*dwContextHelpId dwContextHelpId*<br/>
Contexte aider ID `CMenu`à s’associer avec .

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès; sinon 0

### <a name="remarks"></a>Notes

Tous les éléments du menu partagent cet identifiant — il n’est pas possible d’attacher un identifiant de contexte d’aide aux différents éléments du menu.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMenu:InsertMenu](#insertmenu).

## <a name="cmenusetmenuinfo"></a><a name="setmenuinfo"></a>CMenu::SetMenuInfo

Définit des informations pour un menu.

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>Paramètres

*lpcmi*<br/>
Un pointeur vers une structure [MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo) contenant des informations pour le menu.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de rendement est non zéro; sinon, la valeur de rendement est nulle.

### <a name="remarks"></a>Notes

Appelez cette fonction pour définir des informations spécifiques sur le menu.

## <a name="cmenusetmenuitembitmaps"></a><a name="setmenuitembitmaps"></a>CMenu::SetMenuItemBitmaps

Associe les bitmaps spécifiés à un élément de menu.

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>Paramètres

*nPosition*<br/>
Spécifie l’élément de menu à changer. Le *paramètre nFlags* peut être utilisé pour interpréter *nPosition* de la manière suivante :

|nFlags|Interprétation de nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Précise que le paramètre donne l’id de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si ni MF_BYCOMMAND ni MF_BYPOSITION n’est définie.|
|MF_BYPOSITION|Précise que le paramètre donne la position de l’élément de menu existant. Le premier élément est à la position 0.|

*nFlags*<br/>
Précise comment *nPosition* est interprété.

*pBmpUnchecked*<br/>
Spécifie la bitmap à utiliser pour les éléments de menu qui ne sont pas vérifiés.

*pBmpChecked*<br/>
Spécifie la bitmap à utiliser pour les éléments de menu qui sont vérifiés.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Que l’élément du menu soit vérifié ou non coché, Windows affiche la bitmap appropriée à côté de l’élément du menu.

Si *pBmpUnchecked* ou *pBmpChecked* est NULL, puis Windows n’affiche rien à côté de l’élément de menu pour l’attribut correspondant. Si les deux paramètres sont NULL, Windows utilise la marque de contrôle par défaut lorsque l’élément est vérifié et supprime la marque de contrôle lorsque l’élément n’est pas coché.

Lorsque le menu est détruit, ces bitmaps ne sont pas détruits; l’application doit les détruire.

La `GetMenuCheckMarkDimensions` fonction Windows récupère les dimensions de la marque de contrôle par défaut utilisée pour les éléments de menu. L’application utilise ces valeurs pour déterminer la taille appropriée pour les bitmaps fournis avec cette fonction. Obtenez la taille, créez vos bitmaps, puis réglez-les.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

## <a name="cmenusetmenuiteminfo"></a><a name="setmenuiteminfo"></a>CMenu::SetMenuItemInfo

Modifications de l’information sur un élément de menu.

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Paramètres

*uItem (en)*<br/>
Voir la description de *uItem* dans [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow) dans le SDK Windows.

*lpMenuItemInfo*<br/>
Voir la description de `SetMenuItemInfo` *lpmii* dans le Windows SDK.

*fByPos*<br/>
Voir la description de `SetMenuItemInfo` *fByPosition* dans le Windows SDK.

### <a name="remarks"></a>Notes

Cette fonction enveloppe [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow), décrit dans le Windows SDK.

## <a name="cmenutrackpopupmenu"></a><a name="trackpopupmenu"></a>CMenu::TrackPopupMenu

Affiche un menu pop-up flottant à l’emplacement spécifié et suit la sélection d’articles sur le menu pop-up.

```
BOOL TrackPopupMenu(
    UINT nFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPCRECT lpRect = 0);
```

### <a name="parameters"></a>Paramètres

*nFlags*<br/>
Spécifie les drapeaux de position d’écran et de position de souris. Voir [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) pour une liste de drapeaux disponibles.

*X*<br/>
Spécifie la position horizontale dans les coordonnées d’écran du menu pop-up. Selon la valeur du paramètre *nFlags,* le menu peut être aligné à gauche, aligné à droite ou centré par rapport à cette position.

*y*<br/>
Spécifie la position verticale dans les coordonnées d’écran du haut du menu sur l’écran.

*Pwnd*<br/>
Identifie la fenêtre qui possède le menu pop-up. Ce paramètre ne peut pas être NULL, même si le drapeau TPM_NONOTIFY est spécifié. Cette fenêtre reçoit tous les WM_COMMAND messages du menu. Dans les versions Windows 3.1 et plus tard, la `TrackPopupMenu` fenêtre ne reçoit pas de messages WM_COMMAND avant de les retourner. Dans Windows 3.0, la fenêtre reçoit `TrackPopupMenu` WM_COMMAND messages avant les retours.

*lpRect*<br/>
Ignoré.

### <a name="return-value"></a>Valeur de retour

Cette méthode renvoie le résultat de l’appel [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) dans le SDK Windows.

### <a name="remarks"></a>Notes

Un menu pop-up flottant peut apparaître n’importe où à l’écran.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

## <a name="cmenutrackpopupmenuex"></a><a name="trackpopupmenuex"></a>CMenu::TrackPopupMenuEx

Affiche un menu pop-up flottant à l’emplacement spécifié et suit la sélection d’articles sur le menu pop-up.

```
BOOL TrackPopupMenuEx(
    UINT fuFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPTPMPARAMS lptpm);
```

### <a name="parameters"></a>Paramètres

*fuFlags fuFlags*<br/>
Spécifie différentes fonctions pour le menu étendu. Pour une liste de toutes les valeurs et de leur signification, voir [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

*X*<br/>
Spécifie la position horizontale dans les coordonnées d’écran du menu pop-up.

*y*<br/>
Spécifie la position verticale dans les coordonnées d’écran du haut du menu sur l’écran.

*Pwnd*<br/>
Un pointeur à la fenêtre possédant le menu pop-up et de recevoir les messages du menu créé. Cette fenêtre peut être n’importe quelle fenêtre de l’application actuelle mais ne peut pas être NULL. Si vous spécifiez TPM_NONOTIFY dans le *paramètre fuFlags,* la fonction n’envoie aucun message à *pWnd*. La fonction doit revenir pour la fenêtre pointée par *pWnd* pour recevoir le message WM_COMMAND.

*lptpm lptpm*<br/>
Pointeur vers une structure [TPMPARAMS](/windows/win32/api/winuser/ns-winuser-tpmparams) qui spécifie une zone de l’écran, le menu ne doit pas se chevaucher. Ce paramètre peut être NULL.

### <a name="return-value"></a>Valeur de retour

Si vous spécifiez TPM_RETURNCMD dans le *paramètre fuFlags,* la valeur de retour est l’identifiant de menu-élément de l’élément que l’utilisateur a choisi. Si l’utilisateur annule le menu sans faire de sélection, ou si une erreur se produit, alors la valeur de retour est de 0.

Si vous ne spécifiez pas TPM_RETURNCMD dans le *paramètre fuFlags,* la valeur de retour est nonzero si la fonction réussit et 0 si elle échoue. Pour obtenir des informations d’erreur étendues, appelez [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Notes

Un menu pop-up flottant peut apparaître n’importe où à l’écran. Pour plus d’informations sur la manipulation des erreurs lors de la création du menu pop-up, voir [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)
