---
title: CMenu, classe
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
ms.openlocfilehash: 1cd7be72dc6c9a38fae4f5ccc1a15c184a2d4466
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420805"
---
# <a name="cmenu-class"></a>CMenu, classe

Encapsulation du `HMENU`Windows.

## <a name="syntax"></a>Syntaxe

```
class CMenu : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CMenu :: CMenu](#cmenu)|Construit un objet `CMenu`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CMenu::AppendMenu](#appendmenu)|Ajoute un nouvel élément à la fin de ce menu.|
|[CMenu :: Attach](#attach)|Attache un handle de menu Windows à un objet `CMenu`.|
|[CMenu :: CheckMenuItem](#checkmenuitem)|Place une coche à côté d’un élément de menu dans le menu contextuel ou la supprime d’une coche.|
|[CMenu :: CheckMenuRadioItem](#checkmenuradioitem)|Place une case d’option en regard d’un élément de menu et supprime la case d’option de tous les autres éléments de menu du groupe.|
|[CMenu :: CreateMenu](#createmenu)|Crée un menu vide et l’attache à un objet `CMenu`.|
|[CMenu :: CreatePopupMenu](#createpopupmenu)|Crée un menu contextuel vide et l’attache à un objet `CMenu`.|
|[CMenu ::D eleteMenu](#deletemenu)|Supprime un élément spécifié du menu. Si l’élément de menu est associé à un menu contextuel, détruit le handle dans le menu contextuel et libère la mémoire utilisée par celui-ci.|
|[CMenu ::D eleteTempMap](#deletetempmap)|Supprime tous les objets `CMenu` temporaires créés par la fonction membre `FromHandle`.|
|[CMenu ::D estroyMenu](#destroymenu)|Détruit le menu attaché à un objet `CMenu` et libère toute mémoire occupée par le menu.|
|[CMenu ::D Etach](#detach)|Détache un handle de menu Windows d’un objet `CMenu` et retourne le handle.|
|[CMenu ::D rawItem](#drawitem)|Appelée par l’infrastructure quand un aspect visuel d’un menu owner-drawn change.|
|[CMenu :: EnableMenuItem](#enablemenuitem)|Active, désactive ou estompe (grise) un élément de menu.|
|[CMenu :: FromHandle](#fromhandle)|Retourne un pointeur vers un objet `CMenu` en fonction d’un handle de menu Windows.|
|[CMenu :: GetDefaultItem](#getdefaultitem)|Détermine l’élément de menu par défaut dans le menu spécifié.|
|[CMenu :: GetMenuContextHelpId](#getmenucontexthelpid)|Récupère l’ID de contexte d’aide associé au menu.|
|[CMenu :: GetMenuInfo](#getmenuinfo)|Récupère des informations dans un menu spécifique.|
|[CMenu :: GetMenuItemCount](#getmenuitemcount)|Détermine le nombre d’éléments dans un menu contextuel ou de niveau supérieur.|
|[CMenu :: GetMenuItemID](#getmenuitemid)|Obtient l’identificateur d’élément de menu d’un élément de menu situé à la position spécifiée.|
|[CMenu :: GetMenuItemInfo](#getmenuiteminfo)|Récupère des informations sur un élément de menu.|
|[CMenu :: GetMenuState](#getmenustate)|Retourne l’état de l’élément de menu spécifié ou le nombre d’éléments dans un menu contextuel.|
|[CMenu :: GetMenuString](#getmenustring)|Récupère l’étiquette de l’élément de menu spécifié.|
|[CMenu :: GetSafeHmenu](#getsafehmenu)|Retourne le `m_hMenu` encapsulé par cet objet `CMenu`.|
|[CMenu :: GetSubMenu](#getsubmenu)|Récupère un pointeur désignant un menu contextuel.|
|[CMenu::InsertMenu](#insertmenu)|Insère un nouvel élément de menu à la position spécifiée, en déplaçant d’autres éléments vers le menu.|
|[CMenu :: InsertMenuItem](#insertmenuitem)|Insère un nouvel élément de menu à la position spécifiée dans un menu.|
|[CMenu :: LoadMenu](#loadmenu)|Charge une ressource de menu à partir du fichier exécutable et l’attache à un objet `CMenu`.|
|[CMenu :: LoadMenuIndirect](#loadmenuindirect)|Charge un menu à partir d’un modèle de menu en mémoire et l’attache à un objet `CMenu`.|
|[CMenu :: MeasureItem](#measureitem)|Appelé par l’infrastructure pour déterminer les dimensions de menu lorsqu’un menu owner-drawn est créé.|
|[CMenu::ModifyMenu](#modifymenu)|Modifie un élément de menu existant à la position spécifiée.|
|[CMenu :: RemoveMenu](#removemenu)|Supprime un élément de menu avec un menu contextuel associé dans le menu spécifié.|
|[CMenu :: SetDefaultItem](#setdefaultitem)|Définit l’élément de menu par défaut pour le menu spécifié.|
|[CMenu :: SetMenuContextHelpId](#setmenucontexthelpid)|Définit l’ID de contexte d’aide à associer au menu.|
|[CMenu :: SetMenuInfo](#setmenuinfo)|Définit des informations dans un menu spécifique.|
|[CMenu :: SetMenuItemBitmaps](#setmenuitembitmaps)|Associe les bitmaps de coches spécifiées à un élément de menu.|
|[CMenu :: SetMenuItemInfo](#setmenuiteminfo)|Modifie les informations relatives à un élément de menu.|
|[CMenu :: TrackPopupMenu](#trackpopupmenu)|Affiche un menu contextuel flottant à l’emplacement spécifié et effectue le suivi de la sélection des éléments dans le menu contextuel.|
|[CMenu :: TrackPopupMenuEx](#trackpopupmenuex)|Affiche un menu contextuel flottant à l’emplacement spécifié et effectue le suivi de la sélection des éléments dans le menu contextuel.|

### <a name="public-operators"></a>Opérateurs publics

|Name|Description|
|----------|-----------------|
|[CMenu :: Operator HMENU](#operator_hmenu)|Récupère le handle de l’objet de menu.|
|[CMenu :: Operator ! =](#operator_neq)|Détermine si deux objets de menu ne sont pas égaux.|
|[CMenu :: Operator = =](#operator_eq_eq)|Détermine si deux objets de menu sont égaux.|

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[CMenu :: m_hMenu](#m_hmenu)|Spécifie le handle du menu Windows attaché à l’objet `CMenu`.|

## <a name="remarks"></a>Notes

Il fournit des fonctions membres pour la création, le suivi, la mise à jour et la destruction d’un menu.

Créez un objet `CMenu` sur le frame de pile en tant que local, puis appelez les fonctions membres de `CMenu`pour manipuler le nouveau menu en fonction des besoins. Ensuite, appelez [CWnd :: SetMenu](../../mfc/reference/cwnd-class.md#setmenu) pour définir le menu dans une fenêtre, suivi immédiatement par un appel à la fonction membre [Detach](#detach) de l’objet `CMenu`. La fonction membre `CWnd::SetMenu` définit le menu de la fenêtre sur le nouveau menu, fait en sorte que la fenêtre soit redessinée pour refléter la modification du menu et passe également la propriété du menu à la fenêtre. L’appel à `Detach` détache le HMENU de l’objet `CMenu`, de sorte que lorsque la variable `CMenu` locale est hors de portée, le destructeur d’objet `CMenu` ne tente pas de détruire un menu qu’il ne possède plus. Le menu lui-même est détruit automatiquement lorsque la fenêtre est détruite.

Vous pouvez utiliser la fonction membre [LoadMenuIndirect](#loadmenuindirect) pour créer un menu à partir d’un modèle en mémoire, mais un menu créé à partir d’une ressource par un appel à [LoadMenu](#loadmenu) est plus facile à gérer, et la ressource de menu elle-même peut être créée et modifiée par l’éditeur de menus.

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMenu`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="appendmenu"></a>CMenu :: AppendMenu

Ajoute un nouvel élément à la fin d’un menu.

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
Spécifie les informations relatives à l’état du nouvel élément de menu lorsqu’il est ajouté au menu. Il se compose d’une ou plusieurs des valeurs listées dans la section Notes.

*nIDNewItem*<br/>
Spécifie l’ID de commande du nouvel élément de menu ou, si *nFlags* est défini sur MF_POPUP, le handle de menu (`HMENU`) d’un menu contextuel. Le paramètre *nIDNewItem* est ignoré (inutile) si *nFlags* est défini sur MF_SEPARATOR.

*lpszNewItem*<br/>
Spécifie le contenu du nouvel élément de menu. Le paramètre *nFlags* est utilisé pour interpréter *lpszNewItem* de la façon suivante :

|nFlags|Interprétation de lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Contient une valeur 32 bits fournie par l’application qui peut être utilisée par l’application pour gérer des données supplémentaires associées à l’élément de menu. Cette valeur de 32 bits est disponible pour l’application lors du traitement des messages WM_MEASUREITEM et WM_DRAWITEM. La valeur est stockée dans le membre `itemData` de la structure fournie avec ces messages.|
|MF_STRING|Contient un pointeur vers une chaîne se terminant par null. Il s’agit de l’interprétation par défaut.|
|MF_SEPARATOR|Le paramètre *lpszNewItem* est ignoré (non nécessaire).|

*pBmp*<br/>
Pointe vers un objet `CBitmap` qui sera utilisé comme élément de menu.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

L’application peut spécifier l’état de l’élément de menu en définissant des valeurs dans *nFlags*. Quand *nIDNewItem* spécifie un menu contextuel, il devient une partie du menu auquel il est ajouté. Si ce menu est détruit, le menu ajouté est également détruit. Un menu ajouté doit être détaché d’un objet `CMenu` pour éviter tout conflit. Notez que MF_STRING et MF_OWNERDRAW ne sont pas valides pour la version bitmap de `AppendMenu`.

La liste suivante décrit les indicateurs qui peuvent être définis dans *nFlags*:

- MF_CHECKED agit comme une bascule avec MF_UNCHECKED pour placer la coche par défaut en regard de l’élément. Lorsque l’application fournit des bitmaps de coche (voir la fonction membre [SetMenuItemBitmaps](#setmenuitembitmaps) ), la bitmap « coche activée » s’affiche.

- MF_UNCHECKED agit comme une bascule avec MF_CHECKED pour supprimer une coche en regard de l’élément. Lorsque l’application fournit des bitmaps de coche (voir la fonction membre `SetMenuItemBitmaps`), la bitmap « coche désactivée » s’affiche.

- MF_DISABLED désactive l’élément de menu afin qu’il ne puisse pas être sélectionné, mais pas.

- MF_ENABLED active l’élément de menu afin qu’il puisse être sélectionné et le restaure à partir de son état grisé.

- MF_GRAYED désactive l’élément de menu afin qu’il ne puisse pas être sélectionné et le estompe.

- MF_MENUBARBREAK place l’élément sur une nouvelle ligne dans les menus statiques ou dans une nouvelle colonne dans les menus contextuels. La nouvelle colonne de menu contextuel sera séparée de l’ancienne colonne par une ligne de séparation verticale.

- MF_MENUBREAK place l’élément sur une nouvelle ligne dans les menus statiques ou dans une nouvelle colonne dans les menus contextuels. Aucune ligne de séparation n’est placée entre les colonnes.

- MF_OWNERDRAW spécifie que l’élément est un élément owner-draw. Lorsque le menu est affiché pour la première fois, la fenêtre qui possède le menu reçoit un message WM_MEASUREITEM, qui récupère la hauteur et la largeur de l’élément de menu. Le message WM_DRAWITEM est celui envoyé chaque fois que le propriétaire doit mettre à jour l’apparence visuelle de l’élément de menu. Cette option n’est pas valide pour un élément de menu de niveau supérieur.

- MF_POPUP spécifie que l’élément de menu est associé à un menu contextuel. Le paramètre ID spécifie un handle vers un menu contextuel qui doit être associé à l’élément. Elle est utilisée pour ajouter un menu contextuel de niveau supérieur ou un menu contextuel hiérarchique à un élément de menu contextuel.

- MF_SEPARATOR dessine une ligne de séparation horizontale. Ne peut être utilisé que dans un menu contextuel. Cette ligne ne peut pas être grisée, désactivée ou mise en surbrillance. Les autres paramètres sont ignorés.

- MF_STRING spécifie que l’élément de menu est une chaîne de caractères.

Chacun des groupes suivants répertorie les indicateurs qui s’excluent mutuellement et ne peuvent pas être utilisés ensemble :

- MF_DISABLED, MF_ENABLED et MF_GRAYED

- MF_STRING, MF_OWNERDRAW, MF_SEPARATOR et la version bitmap

- MF_MENUBARBREAK et MF_MENUBREAK

- MF_CHECKED et MF_UNCHECKED

Chaque fois qu’un menu qui réside dans une fenêtre est modifié (que la fenêtre soit affichée ou non), l’application doit appeler [CWnd ::D rawmenubar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: CreateMenu](#createmenu).

##  <a name="attach"></a>CMenu :: Attach

Attache un menu Windows existant à un objet `CMenu`.

```
BOOL Attach(HMENU hMenu);
```

### <a name="parameters"></a>Paramètres

*hMenu*<br/>
Spécifie un handle vers un menu Windows.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’opération a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction ne doit pas être appelée si un menu est déjà attaché à l’objet `CMenu`. Le descripteur de menu est stocké dans le membre de données `m_hMenu`.

Si le menu que vous souhaitez manipuler est déjà associé à une fenêtre, vous pouvez utiliser la fonction [CWnd :: GetMenu](../../mfc/reference/cwnd-class.md#getmenu) pour obtenir un handle vers le menu.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="checkmenuitem"></a>CMenu :: CheckMenuItem

Ajoute des coches ou supprime les coches des éléments de menu dans le menu contextuel.

```
UINT CheckMenuItem(
    UINT nIDCheckItem,
    UINT nCheck);
```

### <a name="parameters"></a>Paramètres

*nIDCheckItem*<br/>
Spécifie l’élément de menu à vérifier, tel que déterminé par *nConsultez*.

*nConsultez*<br/>
Spécifie comment vérifier l’élément de menu et comment déterminer la position de l’élément dans le menu. Le paramètre *nConsultez* peut être une combinaison de MF_CHECKED ou MF_UNCHECKED avec MF_BYPOSITION ou MF_BYCOMMAND indicateurs. Ces indicateurs peuvent être combinés à l’aide de l’opérateur or au niveau du bit. Elles ont les significations suivantes :

- MF_BYCOMMAND spécifie que le paramètre donne l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut.

- MF_BYPOSITION spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.

- MF_CHECKED agit comme une bascule avec MF_UNCHECKED pour placer la coche par défaut en regard de l’élément.

- MF_UNCHECKED agit comme une bascule avec MF_CHECKED pour supprimer une coche en regard de l’élément.

### <a name="return-value"></a>Valeur de retour

État précédent de l’élément : MF_CHECKED ou MF_UNCHECKED, ou 0xFFFFFFFF si l’élément de menu n’existait pas.

### <a name="remarks"></a>Notes

Le paramètre *nIDCheckItem* spécifie l’élément à modifier.

Le paramètre *nIDCheckItem* peut identifier un élément de menu contextuel, ainsi qu’un élément de menu. Aucune étape particulière n’est requise pour vérifier un élément de menu contextuel. Les éléments de menu de niveau supérieur ne peuvent pas être vérifiés. Un élément de menu contextuel doit être vérifié par position, car il n’est associé à aucun identificateur d’élément de menu.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: GetMenuState](#getmenustate).

##  <a name="checkmenuradioitem"></a>CMenu :: CheckMenuRadioItem

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
Spécifie (sous la forme d’un ID ou d’un décalage, selon la valeur de *nFlags*) le premier élément de menu dans le groupe de cases d’option.

*nIDLast*<br/>
Spécifie (sous la forme d’un ID ou d’un décalage, selon la valeur de *nFlags*) le dernier élément de menu dans le groupe de cases d’option.

*nIDItem*<br/>
Spécifie (sous la forme d’un ID ou d’un décalage, en fonction de la valeur de *nFlags*) de l’élément dans le groupe qui sera vérifié par une case d’option.

*nFlags*<br/>
Spécifie l’interprétation de *nIDFirst*, *nIDLast*et *nIDItem* de la manière suivante :

|nFlags|Interprétation|
|------------|--------------------|
|MF_BYCOMMAND|Spécifie que le paramètre donne l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si ni MF_BYCOMMAND ni MF_BYPOSITION n’est défini.|
|MF_BYPOSITION|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon 0

### <a name="remarks"></a>Notes

En même temps, la fonction désactive tous les autres éléments de menu dans le groupe associé et efface l’indicateur de type d’élément radio pour ces éléments. L’élément activé s’affiche à l’aide d’une bitmap de case d’option (ou de puce) au lieu d’une bitmap de coche.

### <a name="example"></a>Exemple

  Consultez l’exemple de [ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range).

##  <a name="cmenu"></a>CMenu :: CMenu

Crée un menu vide et l’attache à un objet `CMenu`.

```
CMenu();
```

### <a name="remarks"></a>Notes

Le menu n’est pas créé tant que vous n’appelez pas l’une des fonctions membres Create ou Load de `CMenu:`

- [CreateMenu](#createmenu)

- [CreatePopupMenu](#createpopupmenu)

- [LoadMenu](#loadmenu)

- [LoadMenuIndirect](#loadmenuindirect)

- [Attacher](#attach)

##  <a name="createmenu"></a>CMenu :: CreateMenu

Crée un menu et l’attache à l’objet `CMenu`.

```
BOOL CreateMenu();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le menu a été créé avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Le menu est initialement vide. Les éléments de menu peuvent être ajoutés à l’aide de la fonction membre `AppendMenu` ou `InsertMenu`.

Si le menu est assigné à une fenêtre, il est automatiquement détruit lorsque la fenêtre est détruite.

Avant de quitter, une application doit libérer des ressources système associées à un menu si le menu n’est pas assigné à une fenêtre. Une application libère un menu en appelant la fonction membre [DestroyMenu](#destroymenu) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]

##  <a name="createpopupmenu"></a>CMenu :: CreatePopupMenu

Crée un menu contextuel et l’attache à l’objet `CMenu`.

```
BOOL CreatePopupMenu();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le menu contextuel a été créé avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Le menu est initialement vide. Les éléments de menu peuvent être ajoutés à l’aide de la fonction membre `AppendMenu` ou `InsertMenu`. L’application peut ajouter le menu contextuel à un menu ou à un menu contextuel existant. La fonction membre `TrackPopupMenu` peut être utilisée pour afficher ce menu sous la forme d’un menu contextuel flottant et pour effectuer le suivi des sélections dans le menu contextuel.

Si le menu est assigné à une fenêtre, il est automatiquement détruit lorsque la fenêtre est détruite. Si le menu est ajouté à un menu existant, il est automatiquement détruit lorsque ce menu est détruit.

Avant de quitter, une application doit libérer des ressources système associées à un menu contextuel si le menu n’est pas affecté à une fenêtre. Une application libère un menu en appelant la fonction membre [DestroyMenu](#destroymenu) .

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: CreateMenu](#createmenu).

##  <a name="deletemenu"></a>CMenu ::D eleteMenu

Supprime un élément du menu.

```
BOOL DeleteMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Paramètres

*nPosition*<br/>
Spécifie l’élément de menu à supprimer, tel que déterminé par *nFlags*.

*nFlags*<br/>
Est utilisé pour interpréter *nPosition* de la façon suivante :

|nFlags|Interprétation de nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Spécifie que le paramètre donne l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si ni MF_BYCOMMAND ni MF_BYPOSITION n’est défini.|
|MF_BYPOSITION|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Si l’élément de menu est associé à un menu contextuel, `DeleteMenu` détruit le handle dans le menu contextuel et libère la mémoire utilisée par le menu contextuel.

Chaque fois qu’un menu qui réside dans une fenêtre est modifié (que la fenêtre soit affichée ou non), l’application doit appeler [CWnd ::D rawmenubar](../../mfc/reference/cwnd-class.md#drawmenubar).

### <a name="example"></a>Exemple

  Consultez l’exemple de [CWnd :: GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

##  <a name="deletetempmap"></a>CMenu ::D eleteTempMap

Appelée automatiquement par le `CWinApp` gestionnaire de temps d’inactivité, supprime tous les objets `CMenu` temporaires créés par la fonction membre [FromHandle](#fromhandle) .

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Notes

`DeleteTempMap` détache l’objet de menu Windows joint à un objet `CMenu` temporaire avant de supprimer l’objet `CMenu`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]

##  <a name="destroymenu"></a>CMenu ::D estroyMenu

Détruit le menu et toutes les ressources Windows qui ont été utilisées.

```
BOOL DestroyMenu();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le menu est détruit ; Sinon, 0.

### <a name="remarks"></a>Notes

Le menu est détaché de l’objet `CMenu` avant d’être détruit. La fonction Windows `DestroyMenu` est appelée automatiquement dans le destructeur `CMenu`.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: CreateMenu](#createmenu).

##  <a name="detach"></a>CMenu ::D Etach

Détache un menu Windows d’un objet `CMenu` et retourne le handle.

```
HMENU Detach();
```

### <a name="return-value"></a>Valeur de retour

Handle, de type HMENU, vers un menu Windows, en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

Le membre de données `m_hMenu` est défini sur NULL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]

##  <a name="drawitem"></a>CMenu ::D rawItem

Appelée par l’infrastructure quand un aspect visuel d’un menu owner-drawn change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Pointeur vers une structure [drawitemstruct,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) qui contient des informations sur le type de dessin requis.

### <a name="remarks"></a>Notes

Le membre `itemAction` de la structure `DRAWITEMSTRUCT` définit l’action de dessin à effectuer. Substituez cette fonction membre pour implémenter le dessin pour un objet `CMenu` owner-draw. L’application doit restaurer tous les objets GDI (Graphics Device Interface) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant l’arrêt de cette fonction membre.

Consultez [CWnd :: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) pour obtenir une description de la structure `DRAWITEMSTRUCT`.

### <a name="example"></a>Exemple

Le code suivant provient de l’exemple [CTRLTEST](../../overview/visual-cpp-samples.md) MFC :

[!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]

##  <a name="enablemenuitem"></a>CMenu :: EnableMenuItem

Active, désactive ou estompe un élément de menu.

```
UINT EnableMenuItem(
    UINT nIDEnableItem,
    UINT nEnable);
```

### <a name="parameters"></a>Paramètres

*nIDEnableItem*<br/>
Spécifie l’élément de menu à activer, tel que déterminé par *nEnable*. Ce paramètre peut spécifier des éléments de menu contextuel, ainsi que des éléments de menu standard.

*nEnable*<br/>
Spécifie l’action à entreprendre. Il peut s’agir d’une combinaison de MF_DISABLED, MF_ENABLED ou MF_GRAYED, avec MF_BYCOMMAND ou MF_BYPOSITION. Ces valeurs peuvent être combinées à l’aide de l’opérateur or au niveau du bit. Ces valeurs ont les significations suivantes :

- MF_BYCOMMAND spécifie que le paramètre donne l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut.

- MF_BYPOSITION spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.

- MF_DISABLED désactive l’élément de menu afin qu’il ne puisse pas être sélectionné, mais pas.

- MF_ENABLED active l’élément de menu afin qu’il puisse être sélectionné et le restaure à partir de son état grisé.

- MF_GRAYED désactive l’élément de menu afin qu’il ne puisse pas être sélectionné et le estompe.

### <a name="return-value"></a>Valeur de retour

État précédent (MF_DISABLED, MF_ENABLED ou MF_GRAYED) ou-1 s’il n’est pas valide.

### <a name="remarks"></a>Notes

Les fonctions membres [CreateMenu](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu)et [LoadMenuIndirect](#loadmenuindirect) peuvent également définir l’État (activé, désactivé ou grisé) d’un élément de menu.

L’utilisation de la valeur MF_BYPOSITION nécessite qu’une application utilise le `CMenu`correct. Si le `CMenu` de la barre de menus est utilisé, un élément de menu de niveau supérieur (élément dans la barre de menus) est affecté. Pour définir l’état d’un élément dans un menu contextuel ou un menu contextuel imbriqué par position, une application doit spécifier la `CMenu` du menu contextuel.

Lorsqu’une application spécifie l’indicateur MF_BYCOMMAND, Windows vérifie tous les éléments de menu contextuel qui sont subordonnés au `CMenu`; par conséquent, à moins que des éléments de menu en double soient présents, l’utilisation de la `CMenu` de la barre de menus suffit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]

##  <a name="fromhandle"></a>CMenu :: FromHandle

Retourne un pointeur vers un objet `CMenu` en fonction d’un handle Windows d’un menu.

```
static CMenu* PASCAL FromHandle(HMENU hMenu);
```

### <a name="parameters"></a>Paramètres

*hMenu*<br/>
Handle Windows d’un menu.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un `CMenu` qui peut être temporaire ou permanent.

### <a name="remarks"></a>Notes

Si un objet `CMenu` n’est pas déjà attaché à l’objet menu Windows, un objet `CMenu` temporaire est créé et attaché.

Cet objet `CMenu` temporaire est valide uniquement jusqu’à la prochaine période d’inactivité de l’application dans sa boucle d’événements, auquel cas tous les objets temporaires sont supprimés.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: CreateMenu](#createmenu).

##  <a name="getdefaultitem"></a>CMenu :: GetDefaultItem

Détermine l’élément de menu par défaut dans le menu spécifié.

```
UINT GetDefaultItem(
    UINT gmdiFlags,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Paramètres

*gmdiFlags*<br/>
Valeur spécifiant comment la fonction recherche les éléments de menu. Ce paramètre peut être None, One ou une combinaison des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|GMDI_GOINTOPOPUPS|Spécifie que, si l’élément par défaut est un élément qui ouvre un sous-menu, la fonction doit effectuer une recherche dans le sous-menu correspondant de manière récursive. Si le sous-menu n’a pas d’élément par défaut, la valeur de retour identifie l’élément qui ouvre le sous-menu.<br /><br /> Par défaut, la fonction retourne le premier élément par défaut dans le menu spécifié, qu’il s’agisse ou non d’un élément qui ouvre un sous-menu.|
|GMDI_USEDISABLED|Spécifie que la fonction doit retourner un élément par défaut, même s’il est désactivé.<br /><br /> Par défaut, la fonction ignore les éléments désactivés ou grisés.|

*fByPos*<br/>
Valeur spécifiant s’il faut récupérer l’identificateur de l’élément de menu ou sa position. Si ce paramètre a la valeur FALSe, l’identificateur est retourné. Dans le cas contraire, la position est retournée.

### <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour est l’identificateur ou la position de l’élément de menu. Si la fonction échoue, la valeur de retour est-1.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la fonction Win32 [GetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-getmenudefaultitem), comme décrit dans la SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: InsertMenu](#insertmenu).

##  <a name="getmenucontexthelpid"></a>CMenu :: GetMenuContextHelpId

Récupère l’ID d’aide contextuelle associé à `CMenu`.

```
DWORD GetMenuContextHelpId() const;
```

### <a name="return-value"></a>Valeur de retour

L’ID d’aide contextuelle actuellement associé à `CMenu` le cas échéant ; Sinon, zéro.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: InsertMenu](#insertmenu).

##  <a name="getmenuinfo"></a>CMenu :: GetMenuInfo

Récupère des informations pour un menu.

```
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;
```

### <a name="parameters"></a>Paramètres

*lpcmi*<br/>
Pointeur vers une structure [MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo) contenant des informations pour le menu.

### <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour est différente de zéro ; Sinon, la valeur de retour est zéro.

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer des informations sur le menu.

##  <a name="getmenuitemcount"></a>CMenu :: GetMenuItemCount

Détermine le nombre d’éléments dans un menu contextuel ou de niveau supérieur.

```
UINT GetMenuItemCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans le menu si la fonction réussit ; sinon-1.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CWnd :: GetMenu](../../mfc/reference/cwnd-class.md#getmenu).

##  <a name="getmenuitemid"></a>CMenu :: GetMenuItemID

Obtient l’identificateur d’élément de menu pour un élément de menu situé à la position définie par *nPos*.

```
UINT GetMenuItemID(int nPos) const;
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Spécifie la position (de base zéro) de l’élément de menu dont l’ID est en cours de récupération.

### <a name="return-value"></a>Valeur de retour

ID d’élément de l’élément spécifié dans un menu contextuel si la fonction est réussie. Si l’élément spécifié est un menu contextuel (par opposition à un élément dans le menu contextuel), la valeur de retour est-1. Si *nPos* correspond à un élément de menu séparateur, la valeur de retour est 0.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: InsertMenu](#insertmenu).

##  <a name="getmenuiteminfo"></a>CMenu :: GetMenuItemInfo

Récupère des informations sur un élément de menu.

```
BOOL GetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Paramètres

*uItem*<br/>
Identificateur ou position de l’élément de menu sur lequel obtenir des informations. La signification de ce paramètre dépend de la valeur de `ByPos`.

*lpMenuItemInfo*<br/>
Pointeur vers un [MENUITEMINFO](/windows/win32/api/winuser/ns-winuser-menuiteminfow), comme décrit dans le SDK Windows, qui contient des informations sur le menu.

*fByPos*<br/>
Valeur spécifiant la signification de `nIDItem`. Par défaut, `ByPos` a la valeur FALSe, ce qui indique que uItem est un identificateur d’élément de menu. Si `ByPos` n’a pas la valeur FALSe, il indique une position d’élément de menu.

### <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour est différente de zéro. Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, utilisez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), comme décrit dans la SDK Windows.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du de la fonction Win32 [GetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-getmenuiteminfow), comme décrit dans la SDK Windows. Notez que dans l’implémentation MFC de `GetMenuItemInfo`, vous n’utilisez pas de handle pour un menu.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]

##  <a name="getmenustate"></a>CMenu :: GetMenuState

Retourne l’état de l’élément de menu spécifié ou le nombre d’éléments dans un menu contextuel.

```
UINT GetMenuState(
    UINT nID,
    UINT nFlags) const;
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
Spécifie l’ID d’élément de menu, tel que déterminé par *nFlags*.

*nFlags*<br/>
Spécifie la nature de *nid*. Ce peut être l’une des valeurs suivantes :

- MF_BYCOMMAND spécifie que le paramètre donne l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut.

- MF_BYPOSITION spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.

### <a name="return-value"></a>Valeur de retour

Valeur 0xFFFFFFFF si l’élément spécifié n’existe pas. Si *nid* identifie un menu contextuel, l’octet de poids fort contient le nombre d’éléments dans le menu contextuel et l’octet de poids faible contient les indicateurs de menu associés au menu contextuel. Dans le cas contraire, la valeur de retour est un masque (booléen ou) des valeurs de la liste suivante (ce masque décrit l’état de l’élément de menu que *nid* identifie) :

- MF_CHECKED agit comme une bascule avec MF_UNCHECKED pour placer la coche par défaut en regard de l’élément. Lorsque l’application fournit des bitmaps de coche (voir la fonction membre `SetMenuItemBitmaps`), la bitmap « coche activée » s’affiche.

- MF_DISABLED désactive l’élément de menu afin qu’il ne puisse pas être sélectionné, mais pas.

- MF_ENABLED active l’élément de menu afin qu’il puisse être sélectionné et le restaure à partir de son état grisé. Notez que la valeur de cette constante est 0 ; une application ne doit pas effectuer de test sur 0 en cas d’échec lors de l’utilisation de cette valeur.

- MF_GRAYED désactive l’élément de menu afin qu’il ne puisse pas être sélectionné et le estompe.

- MF_MENUBARBREAK place l’élément sur une nouvelle ligne dans les menus statiques ou dans une nouvelle colonne dans les menus contextuels. La nouvelle colonne de menu contextuel sera séparée de l’ancienne colonne par une ligne de séparation verticale.

- MF_MENUBREAK place l’élément sur une nouvelle ligne dans les menus statiques ou dans une nouvelle colonne dans les menus contextuels. Aucune ligne de séparation n’est placée entre les colonnes.

- MF_SEPARATOR dessine une ligne de séparation horizontale. Ne peut être utilisé que dans un menu contextuel. Cette ligne ne peut pas être grisée, désactivée ou mise en surbrillance. Les autres paramètres sont ignorés.

- MF_UNCHECKED agit comme une bascule avec MF_CHECKED pour supprimer une coche en regard de l’élément. Lorsque l’application fournit des bitmaps de coche (voir la fonction membre `SetMenuItemBitmaps`), la bitmap « coche désactivée » s’affiche. Notez que la valeur de cette constante est 0 ; une application ne doit pas effectuer de test sur 0 en cas d’échec lors de l’utilisation de cette valeur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]

##  <a name="getmenustring"></a>CMenu :: GetMenuString

Copie l’étiquette de l’élément de menu spécifié dans la mémoire tampon spécifiée.

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

*nIDItem*<br/>
Spécifie l’identificateur entier de l’élément de menu ou le décalage de l’élément de menu dans le menu, en fonction de la valeur de *nFlags*.

*lpString*<br/>
Pointe vers la mémoire tampon qui doit recevoir l’étiquette.

*rString*<br/>
Référence à un objet `CString` qui doit recevoir la chaîne de menu copiée.

*nMaxCount*<br/>
Spécifie la longueur maximale (en caractères) de l’étiquette à copier. Si l’étiquette est plus longue que la valeur maximale spécifiée dans *nMaxCount*, les caractères supplémentaires sont tronqués.

*nFlags*<br/>
Spécifie l’interprétation du paramètre *nIDItem* . Ce peut être l’une des valeurs suivantes :

|nFlags|Interprétation de nIDItem|
|------------|-------------------------------|
|MF_BYCOMMAND|Spécifie que le paramètre donne l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si ni MF_BYCOMMAND ni MF_BYPOSITION n’est défini.|
|MF_BYPOSITION|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|

### <a name="return-value"></a>Valeur de retour

Spécifie le nombre réel de caractères copiés dans la mémoire tampon, à l’exclusion de la marque de fin null.

### <a name="remarks"></a>Notes

Le paramètre *nMaxCount* doit avoir une valeur supérieure au nombre de caractères de l’étiquette pour contenir le caractère null qui termine une chaîne.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: InsertMenu](#insertmenu).

##  <a name="getsafehmenu"></a>CMenu :: GetSafeHmenu

Retourne le HMENU encapsulé par cet objet `CMenu`, ou un pointeur`CMenu` NULL.

```
HMENU GetSafeHmenu() const;
```

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: LoadMenu](#loadmenu).

##  <a name="getsubmenu"></a>CMenu :: GetSubMenu

Récupère l’objet `CMenu` d’un menu contextuel.

```
CMenu* GetSubMenu(int nPos) const;
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Spécifie la position du menu contextuel contenu dans le menu. Les valeurs de position commencent à 0 pour le premier élément de menu. L’identificateur du menu contextuel ne peut pas être utilisé dans cette fonction.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CMenu` dont le membre `m_hMenu` contient un handle vers le menu contextuel si un menu contextuel existe à la position donnée ; Sinon, NULL. Si un objet `CMenu` n’existe pas, un objet temporaire est créé. Le pointeur de `CMenu` retourné ne doit pas être stocké.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: TrackPopupMenu](#trackpopupmenu).

##  <a name="insertmenu"></a>CMenu :: InsertMenu

Insère un nouvel élément de menu à la position spécifiée par *nPosition* et déplace les autres éléments vers le menu.

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
Spécifie l’élément de menu avant lequel le nouvel élément de menu doit être inséré. Le paramètre *nFlags* peut être utilisé pour interpréter *nPosition* des manières suivantes :

|nFlags|Interprétation de nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Spécifie que le paramètre donne l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si ni MF_BYCOMMAND ni MF_BYPOSITION n’est défini.|
|MF_BYPOSITION|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0. Si *nPosition* a la valeur-1, le nouvel élément de menu est ajouté à la fin du menu.|

*nFlags*<br/>
Spécifie la façon dont *nPosition* est interprété et spécifie les informations sur l’état du nouvel élément de menu lorsqu’il est ajouté au menu. Pour obtenir la liste des indicateurs qui peuvent être définis, consultez la fonction membre [AppendMenu](#appendmenu) . Pour spécifier plusieurs valeurs, utilisez l’opérateur or au niveau du bit pour les combiner avec l’indicateur MF_BYCOMMAND ou MF_BYPOSITION.

*nIDNewItem*<br/>
Spécifie l’ID de commande du nouvel élément de menu ou, si *nFlags* est défini sur MF_POPUP, le handle de menu (HMENU) du menu contextuel. Le paramètre *nIDNewItem* est ignoré (inutile) si *nFlags* est défini sur MF_SEPARATOR.

*lpszNewItem*<br/>
Spécifie le contenu du nouvel élément de menu. *nFlags* peut être utilisé pour interpréter *lpszNewItem* des manières suivantes :

|nFlags|Interprétation de lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Contient une valeur 32 bits fournie par l’application qui peut être utilisée par l’application pour gérer des données supplémentaires associées à l’élément de menu. Cette valeur 32 bits est disponible pour l’application dans le membre `itemData` de la structure fournie par les messages [WM_MEASUREITEM](/windows/win32/Controls/wm-measureitem) et [WM_DRAWITEM](/windows/win32/Controls/wm-drawitem) . Ces messages sont envoyés quand l’élément de menu est initialement affiché ou modifié.|
|MF_STRING|Contient un pointeur long vers une chaîne terminée par le caractère null. Il s’agit de l’interprétation par défaut.|
|MF_SEPARATOR|Le paramètre *lpszNewItem* est ignoré (non nécessaire).|

*pBmp*<br/>
Pointe vers un objet `CBitmap` qui sera utilisé comme élément de menu.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

L’application peut spécifier l’état de l’élément de menu en définissant des valeurs dans *nFlags*.

Chaque fois qu’un menu qui réside dans une fenêtre est modifié (que la fenêtre soit affichée ou non), l’application doit appeler `CWnd::DrawMenuBar`.

Quand *nIDNewItem* spécifie un menu contextuel, il devient une partie du menu dans lequel il est inséré. Si ce menu est détruit, le menu inséré sera également détruit. Un menu inséré doit être détaché d’un objet `CMenu` pour éviter tout conflit.

Si la fenêtre enfant MDI (multiple document interface) active est agrandie et qu’une application insère un menu contextuel dans le menu de l’application MDI en appelant cette fonction et en spécifiant l’indicateur MF_BYPOSITION, le menu est inséré une position plus à gauche que fermeture. Cela se produit parce que le menu contrôle de la fenêtre enfant MDI active est inséré à la première position de la barre de menus de la fenêtre frame MDI. Pour positionner correctement le menu, l’application doit ajouter 1 à la valeur de position qui serait autrement utilisée. Une application peut utiliser le message WM_MDIGETACTIVE pour déterminer si la fenêtre enfant actuellement active est agrandie.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]

##  <a name="insertmenuitem"></a>CMenu :: InsertMenuItem

Insère un nouvel élément de menu à la position spécifiée dans un menu.

```
BOOL InsertMenuItem(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Paramètres

*uItem*<br/>
Pour plus d’SDK Windows, consultez la description de *uItem* dans [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw) .

*lpMenuItemInfo*<br/>
Consultez la description de *lpmii* dans `InsertMenuItem` dans le SDK Windows.

*fByPos*<br/>
Consultez la description de *fByPosition* dans `InsertMenuItem` dans le SDK Windows.

### <a name="remarks"></a>Notes

Cette fonction encapsule [InsertMenuItem](/windows/win32/api/winuser/nf-winuser-insertmenuitemw), décrite dans la SDK Windows.

##  <a name="loadmenu"></a>CMenu :: LoadMenu

Charge une ressource de menu à partir du fichier exécutable de l’application et l’attache à l’objet `CMenu`.

```
BOOL LoadMenu(LPCTSTR lpszResourceName);
BOOL LoadMenu(UINT nIDResource);
```

### <a name="parameters"></a>Paramètres

*lpszResourceName*<br/>
Pointe vers une chaîne se terminant par un caractère null qui contient le nom de la ressource de menu à charger.

*nIDResource*<br/>
Spécifie l’ID de menu de la ressource de menu à charger.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la ressource de menu a été chargée avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Avant de quitter, une application doit libérer des ressources système associées à un menu si le menu n’est pas assigné à une fenêtre. Une application libère un menu en appelant la fonction membre [DestroyMenu](#destroymenu) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]

##  <a name="loadmenuindirect"></a>CMenu :: LoadMenuIndirect

Charge une ressource à partir d’un modèle de menu en mémoire et l’attache à l’objet `CMenu`.

```
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```

### <a name="parameters"></a>Paramètres

*lpMenuTemplate*<br/>
Pointe vers un modèle de menu (qui est une structure [MENUITEMTEMPLATEHEADER](/windows/win32/api/winuser/ns-winuser-menuitemtemplateheader) unique et une collection d’une ou plusieurs structures [MENUITEMTEMPLATE](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) ). Pour plus d’informations sur ces deux structures, consultez le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la ressource de menu a été chargée avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Un modèle de menu est un en-tête suivi d’une collection d’une ou de plusieurs structures [MENUITEMTEMPLATE](/windows/win32/api/winuser/ns-winuser-menuitemtemplate) , chacune pouvant contenir un ou plusieurs éléments de menu et menus contextuels.

Le numéro de version doit être 0.

Les indicateurs de `mtOption` doivent inclure des MF_END pour le dernier élément d’une liste contextuelle et pour le dernier élément de la liste principale. Consultez la fonction membre `AppendMenu` pour d’autres indicateurs. Le membre `mtId` doit être omis de la structure MENUITEMTEMPLATE lorsque MF_POPUP est spécifié dans `mtOption`.

L’espace alloué à la structure MENUITEMTEMPLATE doit être suffisamment grand pour que `mtString` contienne le nom de l’élément de menu comme chaîne terminée par le caractère null.

Avant de quitter, une application doit libérer des ressources système associées à un menu si le menu n’est pas assigné à une fenêtre. Une application libère un menu en appelant la fonction membre [DestroyMenu](#destroymenu) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]

##  <a name="m_hmenu"></a>CMenu :: m_hMenu

Spécifie le handle HMENU du menu Windows attaché à l’objet `CMenu`.

```
HMENU m_hMenu;
```

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: LoadMenu](#loadmenu).

##  <a name="measureitem"></a>CMenu :: MeasureItem

Appelé par le Framework lorsqu’un menu avec le style owner-draw est créé.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpMeasureItemStruct*<br/>
Pointeur vers une structure `MEASUREITEMSTRUCT`.

### <a name="remarks"></a>Notes

Par défaut, cette fonction membre ne fait rien. Substituez cette fonction membre et remplissez la structure `MEASUREITEMSTRUCT` pour informer les fenêtres des dimensions du menu.

Consultez [CWnd :: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) pour obtenir une description de la structure `MEASUREITEMSTRUCT`.

### <a name="example"></a>Exemple

Le code suivant provient de l’exemple [CTRLTEST](../../overview/visual-cpp-samples.md) MFC :

[!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]

##  <a name="modifymenu"></a>CMenu :: ModifyMenu

Modifie un élément de menu existant à la position spécifiée par *nPosition*.

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
Spécifie l’élément de menu à modifier. Le paramètre *nFlags* peut être utilisé pour interpréter *nPosition* des manières suivantes :

|nFlags|Interprétation de nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Spécifie que le paramètre donne l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si ni MF_BYCOMMAND ni MF_BYPOSITION n’est défini.|
|MF_BYPOSITION|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|

*nFlags*<br/>
Spécifie la façon dont *nPosition* est interprété et donne des informations sur les modifications à apporter à l’élément de menu. Pour obtenir la liste des indicateurs qui peuvent être définis, consultez la fonction membre [AppendMenu](#appendmenu) .

*nIDNewItem*<br/>
Spécifie l’ID de commande de l’élément de menu modifié ou, si *nFlags* est défini sur MF_POPUP, le handle de menu (HMENU) d’un menu contextuel. Le paramètre *nIDNewItem* est ignoré (inutile) si *nFlags* est défini sur MF_SEPARATOR.

*lpszNewItem*<br/>
Spécifie le contenu du nouvel élément de menu. Le paramètre *nFlags* peut être utilisé pour interpréter *lpszNewItem* des manières suivantes :

|nFlags|Interprétation de lpszNewItem|
|------------|-----------------------------------|
|MF_OWNERDRAW|Contient une valeur 32 bits fournie par l’application qui peut être utilisée par l’application pour gérer des données supplémentaires associées à l’élément de menu. Cette valeur 32 bits est disponible pour l’application lorsqu’elle traite MF_MEASUREITEM et MF_DRAWITEM.|
|MF_STRING|Contient un pointeur long vers une chaîne se terminant par un caractère null ou un `CString`.|
|MF_SEPARATOR|Le paramètre *lpszNewItem* est ignoré (non nécessaire).|

*pBmp*<br/>
Pointe vers un objet `CBitmap` qui sera utilisé comme élément de menu.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

L’application spécifie le nouvel état de l’élément de menu en définissant des valeurs dans *nFlags*. Si cette fonction remplace un menu contextuel associé à l’élément de menu, elle détruit l’ancien menu contextuel et libère la mémoire utilisée par le menu contextuel.

Quand *nIDNewItem* spécifie un menu contextuel, il devient une partie du menu dans lequel il est inséré. Si ce menu est détruit, le menu inséré sera également détruit. Un menu inséré doit être détaché d’un objet `CMenu` pour éviter tout conflit.

Chaque fois qu’un menu qui réside dans une fenêtre est modifié (que la fenêtre soit affichée ou non), l’application doit appeler `CWnd::DrawMenuBar`. Pour modifier les attributs d’éléments de menu existants, il est beaucoup plus rapide d’utiliser les fonctions membres `CheckMenuItem` et `EnableMenuItem`.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: InsertMenu](#insertmenu).

##  <a name="operator_hmenu"></a>CMenu :: Operator HMENU

Utilisez cet opérateur pour récupérer le handle de l’objet `CMenu`.

```
operator HMENU() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de réussite, handle de l’objet `CMenu` ; Sinon, NULL.

### <a name="remarks"></a>Notes

Vous pouvez utiliser le handle pour appeler des API Windows directement.

##  <a name="operator_neq"></a>CMenu :: Operator ! =

Détermine si deux menus sont logiquement inégaux.

```
BOOL operator!=(const CMenu& menu) const;
```

### <a name="parameters"></a>Paramètres

*menus*<br/>
Objet `CMenu` pour la comparaison.

### <a name="remarks"></a>Notes

Teste si un objet menu situé à gauche n’est pas égal à un objet menu situé à droite.

##  <a name="operator_eq_eq"></a>CMenu :: Operator = =

Détermine si deux menus sont logiquement égaux.

```
BOOL operator==(const CMenu& menu) const;
```

### <a name="parameters"></a>Paramètres

*menus*<br/>
Objet `CMenu` pour la comparaison.

### <a name="remarks"></a>Notes

Teste si un objet menu sur le côté gauche est égal (en termes de la valeur HMENU) à un objet menu situé à droite.

##  <a name="removemenu"></a>CMenu :: RemoveMenu

Supprime un élément de menu avec un menu contextuel associé dans le menu.

```
BOOL RemoveMenu(
    UINT nPosition,
    UINT nFlags);
```

### <a name="parameters"></a>Paramètres

*nPosition*<br/>
Spécifie l’élément de menu à supprimer. Le paramètre *nFlags* peut être utilisé pour interpréter *nPosition* des manières suivantes :

|nFlags|Interprétation de nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Spécifie que le paramètre donne l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si ni MF_BYCOMMAND ni MF_BYPOSITION n’est défini.|
|MF_BYPOSITION|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|

*nFlags*<br/>
Spécifie la façon dont *nPosition* est interprété.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Il ne détruit pas le descripteur d’un menu contextuel, le menu peut donc être réutilisé. Avant d’appeler cette fonction, l’application peut appeler la fonction membre `GetSubMenu` pour récupérer l’objet `CMenu` publicitaire en vue de sa réutilisation.

Chaque fois qu’un menu qui réside dans une fenêtre est modifié (que la fenêtre soit affichée ou non), l’application doit appeler `CWnd::DrawMenuBar`.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: InsertMenu](#insertmenu).

##  <a name="setdefaultitem"></a>CMenu :: SetDefaultItem

Définit l’élément de menu par défaut pour le menu spécifié.

```
BOOL SetDefaultItem(
    UINT uItem,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Paramètres

*uItem*<br/>
Identificateur ou position du nouvel élément de menu par défaut ou-1 pour aucun élément par défaut. La signification de ce paramètre dépend de la valeur de *fByPos*.

*fByPos*<br/>
Valeur spécifiant la signification de *uItem*. Si ce paramètre a la valeur FALSe, *uItem* est un identificateur d’élément de menu. Dans le cas contraire, il s’agit d’une position d’élément de menu.

### <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour est différente de zéro. Si la fonction échoue, la valeur de retour est égale à zéro. Pour afficher les informations d’erreur étendues, utilisez la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), comme décrit dans la SDK Windows.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la fonction Win32 [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem), comme décrit dans la SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: InsertMenu](#insertmenu).

##  <a name="setmenucontexthelpid"></a>CMenu :: SetMenuContextHelpId

Associe un ID d’aide contextuelle à `CMenu`.

```
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```

### <a name="parameters"></a>Paramètres

*dwContextHelpId*<br/>
ID d’aide contextuelle à associer à `CMenu`.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon 0

### <a name="remarks"></a>Notes

Tous les éléments du menu partagent cet identificateur : il n’est pas possible de joindre un identificateur de contexte d’aide aux éléments de menu individuels.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMenu :: InsertMenu](#insertmenu).

##  <a name="setmenuinfo"></a>CMenu :: SetMenuInfo

Définit des informations pour un menu.

```
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```

### <a name="parameters"></a>Paramètres

*lpcmi*<br/>
Pointeur vers une structure [MENUINFO](/windows/win32/api/winuser/ns-winuser-menuinfo) contenant des informations pour le menu.

### <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour est différente de zéro ; Sinon, la valeur de retour est zéro.

### <a name="remarks"></a>Notes

Appelez cette fonction pour définir des informations spécifiques sur le menu.

##  <a name="setmenuitembitmaps"></a>CMenu :: SetMenuItemBitmaps

Associe les bitmaps spécifiées à un élément de menu.

```
BOOL SetMenuItemBitmaps(
    UINT nPosition,
    UINT nFlags,
    const CBitmap* pBmpUnchecked,
    const CBitmap* pBmpChecked);
```

### <a name="parameters"></a>Paramètres

*nPosition*<br/>
Spécifie l’élément de menu à modifier. Le paramètre *nFlags* peut être utilisé pour interpréter *nPosition* des manières suivantes :

|nFlags|Interprétation de nPosition|
|------------|---------------------------------|
|MF_BYCOMMAND|Spécifie que le paramètre donne l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si ni MF_BYCOMMAND ni MF_BYPOSITION n’est défini.|
|MF_BYPOSITION|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|

*nFlags*<br/>
Spécifie la façon dont *nPosition* est interprété.

*pBmpUnchecked*<br/>
Spécifie l’image bitmap à utiliser pour les éléments de menu qui ne sont pas vérifiés.

*pBmpChecked*<br/>
Spécifie l’image bitmap à utiliser pour les éléments de menu qui sont activés.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Si l’élément de menu est coché ou non, Windows affiche l’image bitmap appropriée en regard de l’élément de menu.

Si *pBmpUnchecked* ou *pBmpChecked* a la valeur null, Windows n’affiche rien en regard de l’élément de menu pour l’attribut correspondant. Si les deux paramètres ont la valeur NULL, Windows utilise la coche par défaut lorsque l’élément est activé et supprime la coche lorsque l’élément est désactivé.

Lorsque le menu est détruit, ces bitmaps ne sont pas détruites. l’application doit les détruire.

La fonction Windows `GetMenuCheckMarkDimensions` récupère les dimensions de la coche par défaut utilisée pour les éléments de menu. L’application utilise ces valeurs pour déterminer la taille appropriée pour les bitmaps fournies avec cette fonction. Récupérez la taille, créez vos images bitmap, puis définissez-les.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]

[!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]

##  <a name="setmenuiteminfo"></a>CMenu :: SetMenuItemInfo

Modifie les informations relatives à un élément de menu.

```
BOOL SetMenuItemInfo(
    UINT uItem,
    LPMENUITEMINFO lpMenuItemInfo,
    BOOL fByPos = FALSE);
```

### <a name="parameters"></a>Paramètres

*uItem*<br/>
Pour plus d’SDK Windows, consultez la description de *uItem* dans [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow) .

*lpMenuItemInfo*<br/>
Consultez la description de *lpmii* dans `SetMenuItemInfo` dans le SDK Windows.

*fByPos*<br/>
Consultez la description de *fByPosition* dans `SetMenuItemInfo` dans le SDK Windows.

### <a name="remarks"></a>Notes

Cette fonction encapsule [SetMenuItemInfo](/windows/win32/api/winuser/nf-winuser-setmenuiteminfow), décrite dans la SDK Windows.

##  <a name="trackpopupmenu"></a>CMenu :: TrackPopupMenu

Affiche un menu contextuel flottant à l’emplacement spécifié et effectue le suivi de la sélection des éléments dans le menu contextuel.

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
Spécifie les indicateurs de position d’écran et de position de la souris. Pour obtenir la liste des indicateurs disponibles, consultez [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) .

*x*<br/>
Spécifie la position horizontale dans les coordonnées d’écran du menu contextuel. Selon la valeur du paramètre *nFlags* , le menu peut être aligné à gauche, aligné à droite ou centré par rapport à cette position.

*y*<br/>
Spécifie la position verticale en coordonnées d’écran du haut du menu sur l’écran.

*pWnd*<br/>
Identifie la fenêtre qui possède le menu contextuel. Ce paramètre ne peut pas avoir la valeur NULL, même si l’indicateur TPM_NONOTIFY est spécifié. Cette fenêtre reçoit tous les messages de WM_COMMAND à partir du menu. Dans les versions 3,1 et ultérieures de Windows, la fenêtre ne reçoit pas de messages WM_COMMAND tant que `TrackPopupMenu` ne retourne pas. Dans Windows 3,0, la fenêtre reçoit des messages WM_COMMAND avant que `TrackPopupMenu` retourne.

*lpRect*<br/>
Ignoré.

### <a name="return-value"></a>Valeur de retour

Cette méthode retourne le résultat de l’appel de [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) dans le SDK Windows.

### <a name="remarks"></a>Notes

Un menu contextuel flottant peut apparaître n’importe où sur l’écran.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]

##  <a name="trackpopupmenuex"></a>CMenu :: TrackPopupMenuEx

Affiche un menu contextuel flottant à l’emplacement spécifié et effectue le suivi de la sélection des éléments dans le menu contextuel.

```
BOOL TrackPopupMenuEx(
    UINT fuFlags,
    int x,
    int y,
    CWnd* pWnd,
    LPTPMPARAMS lptpm);
```

### <a name="parameters"></a>Paramètres

*fuFlags*<br/>
Spécifie différentes fonctions pour le menu étendu. Pour obtenir la liste de toutes les valeurs et leur signification, consultez [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

*x*<br/>
Spécifie la position horizontale dans les coordonnées d’écran du menu contextuel.

*y*<br/>
Spécifie la position verticale en coordonnées d’écran du haut du menu sur l’écran.

*pWnd*<br/>
Pointeur vers la fenêtre qui possède le menu contextuel et reçoit les messages du menu créé. Cette fenêtre peut être n’importe quelle fenêtre de l’application actuelle, mais elle ne peut pas être NULL. Si vous spécifiez TPM_NONOTIFY dans le paramètre *fuFlags* , la fonction n’envoie pas de messages à *pwnd*. La fonction doit retourner pour la fenêtre vers laquelle pointe *pwnd* pour recevoir le message WM_COMMAND.

*lptpm*<br/>
Pointeur vers une structure [TPMPARAMS](/windows/win32/api/winuser/ns-winuser-tpmparams) qui spécifie une zone de l’écran dans laquelle le menu ne doit pas se chevaucher. Ce paramètre peut avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Si vous spécifiez TPM_RETURNCMD dans le paramètre *fuFlags* , la valeur de retour est l’identificateur d’élément de menu de l’élément sélectionné par l’utilisateur. Si l’utilisateur annule le menu sans effectuer de sélection, ou si une erreur se produit, la valeur de retour est 0.

Si vous ne spécifiez pas TPM_RETURNCMD dans le paramètre *fuFlags* , la valeur de retour est différente de zéro si la fonction réussit et 0 en cas d’échec. Pour afficher les informations d’erreur étendues, appelez [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Notes

Un menu contextuel flottant peut apparaître n’importe où sur l’écran. Pour plus d’informations sur la gestion des erreurs lors de la création du menu contextuel, consultez [TrackPopupMenuEx](/windows/win32/api/winuser/nf-winuser-trackpopupmenuex).

## <a name="see-also"></a>Voir aussi

[Exemple MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC DYNAMENU](../../overview/visual-cpp-samples.md)<br/>
[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CObject, classe](../../mfc/reference/cobject-class.md)
