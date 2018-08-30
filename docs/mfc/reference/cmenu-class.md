---
title: CMenu, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c94542fdac3734644771f2659d894d1c8c6f907
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220800"
---
# <a name="cmenu-class"></a>CMenu (classe)
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
|[CMenu::AppendMenu](#appendmenu)|Ajoute un nouvel élément à la fin de ce menu.|  
|[CMenu::Attach](#attach)|Attache un handle de menu Windows vers un `CMenu` objet.|  
|[CMenu::CheckMenuItem](#checkmenuitem)|Place une coche à côté ou supprime une case à cocher d’un élément de menu dans le menu contextuel.|  
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|Place un bouton radio en regard d’un élément de menu et supprime tous les autres éléments de menu dans le groupe de la case d’option.|  
|[CMenu::CreateMenu](#createmenu)|Crée un menu vide et l’attache à un `CMenu` objet.|  
|[CMenu::CreatePopupMenu](#createpopupmenu)|Crée un menu contextuel vide et l’attache à un `CMenu` objet.|  
|[CMenu::DeleteMenu](#deletemenu)|Supprime un élément spécifié dans le menu. Si l’élément de menu possède un menu contextuel associé, détruit le handle pour le menu contextuel et libère la mémoire utilisée par celui-ci.|  
|[CMenu::DeleteTempMap](#deletetempmap)|Supprime tout temporaire `CMenu` objets créés par le `FromHandle` fonction membre.|  
|[CMenu::DestroyMenu](#destroymenu)|Supprime le menu attaché à un `CMenu` de l’objet et libère la mémoire par le menu occupé.|  
|[CMenu::Detach](#detach)|Détache un handle de menu Windows à partir d’un `CMenu` de l’objet et retourne le handle.|  
|[CMenu::DrawItem](#drawitem)|Appelé par l’infrastructure lorsqu’un aspect visuel d’une modification de menu owner-drawn.|  
|[CMenu::EnableMenuItem](#enablemenuitem)|Active, désactive ou s’estompe (gris) un élément de menu.|  
|[CMenu::FromHandle](#fromhandle)|Retourne un pointeur vers un `CMenu` objet un handle de menu Windows.|  
|[CMenu::GetDefaultItem](#getdefaultitem)|Détermine l’élément de menu par défaut dans le menu spécifié.|  
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|Récupère l’ID de contexte d’aide associée au menu.|  
|[CMenu::GetMenuInfo](#getmenuinfo)|Récupère des informations sur un menu spécifique.|  
|[CMenu::GetMenuItemCount](#getmenuitemcount)|Détermine le nombre d’éléments dans un menu contextuel ou de niveau supérieur.|  
|[CMenu::GetMenuItemID](#getmenuitemid)|Obtient l’identificateur d’élément de menu pour un élément de menu situé à la position spécifiée.|  
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|Récupère des informations sur un élément de menu.|  
|[CMenu::GetMenuState](#getmenustate)|Retourne l’état de l’élément de menu spécifié ou le nombre d’éléments dans un menu contextuel.|  
|[CMenu::GetMenuString](#getmenustring)|Récupère l’étiquette de l’élément de menu spécifié.|  
|[CMenu::GetSafeHmenu](#getsafehmenu)|Retourne le `m_hMenu` encapsulé par cette `CMenu` objet.|  
|[CMenu::GetSubMenu](#getsubmenu)|Récupère un pointeur vers un menu contextuel.|  
|[CMenu::InsertMenu](#insertmenu)|Insère un nouvel élément de menu à la position spécifiée, déplacement d’autres éléments du menu déroulant.|  
|[CMenu::InsertMenuItem](#insertmenuitem)|Insère un nouvel élément de menu à la position spécifiée dans un menu.|  
|[CMenu::LoadMenu](#loadmenu)|Charge une ressource de menu à partir du fichier exécutable et l’attache à un `CMenu` objet.|  
|[CMenu::LoadMenuIndirect](#loadmenuindirect)|Charge un menu à partir d’un modèle de menu dans la mémoire et l’attache à un `CMenu` objet.|  
|[CMenu::MeasureItem](#measureitem)|Appelé par l’infrastructure pour déterminer les dimensions de menu lorsqu’un menu owner-drawn est créé.|  
|[CMenu::ModifyMenu](#modifymenu)|Modifie un élément de menu existant à la position spécifiée.|  
|[CMenu::RemoveMenu](#removemenu)|Supprime un élément de menu avec un menu contextuel dans le menu spécifié.|  
|[CMenu::SetDefaultItem](#setdefaultitem)|Définit l’élément de menu par défaut pour le menu spécifié.|  
|[CMenu::SetMenuContextHelpId](#setmenucontexthelpid)|Définit l’ID de contexte d’aide à associer avec le menu.|  
|[CMenu::SetMenuInfo](#setmenuinfo)|Définit les informations dans un menu spécifique.|  
|[CMenu::SetMenuItemBitmaps](#setmenuitembitmaps)|Associe les bitmaps de coche spécifié à un élément de menu.|  
|[CMenu::SetMenuItemInfo](#setmenuiteminfo)|Modifie les informations sur un élément de menu.|  
|[CMenu::TrackPopupMenu](#trackpopupmenu)|Affiche un menu contextuel flottante à l’emplacement spécifié et effectue le suivi de la sélection des éléments dans le menu contextuel.|  
|[CMenu::TrackPopupMenuEx](#trackpopupmenuex)|Affiche un menu contextuel flottante à l’emplacement spécifié et effectue le suivi de la sélection des éléments dans le menu contextuel.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMenu::operator HMENU](#operator_hmenu)|Récupère le handle de l’objet de menu.|  
|[CMenu::operator ! =](#operator_neq)|Détermine si deux objets de menu ne sont pas égaux.|  
|[CMenu::operator ==](#operator_eq_eq)|Détermine si deux objets de menu sont égaux.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMenu::m_hMenu](#m_hmenu)|Spécifie le handle vers le menu Windows attaché à la `CMenu` objet.|  
  
## <a name="remarks"></a>Notes  
 Il fournit des fonctions membres pour la création, de suivi, la mise à jour et la destruction d’un menu.  
  
 Créer un `CMenu` objet sur le frame de pile comme une variable locale, puis appelez `CMenu`de fonctions de membre pour manipuler le nouveau menu en fonction des besoins. Ensuite, appelez [CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu) pour définir le menu à une fenêtre, immédiatement suivi d’un appel à la `CMenu` l’objet [détachement](#detach) fonction membre. Le `CWnd::SetMenu` fonction membre définit le menu de la fenêtre sur le nouveau menu, provoque la fenêtre à être redessiné pour refléter la modification de menu et passe également la propriété du menu dans la fenêtre. L’appel à `Detach` détache le HMENU de le `CMenu` de l’objet, ainsi qu’au moment où local `CMenu` variable passe hors de portée, la `CMenu` destructeur d’objet ne tente pas de détruire un menu, il ne le possède plus. Le menu lui-même est automatiquement détruit la fenêtre est détruite.  
  
 Vous pouvez utiliser la [LoadMenuIndirect](#loadmenuindirect) fonction membre pour créer un menu à partir d’un modèle en mémoire, mais un menu créé à partir d’une ressource par un appel à [LoadMenu](#loadmenu) est plus faciles à gérer et la ressource de menu lui-même peut être créée et modifiée par l’éditeur de menus.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenu`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxwin.h  
  
##  <a name="appendmenu"></a>  CMenu::AppendMenu  
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
 *nIndicateurs*  
 Spécifie les informations sur l’état du nouvel élément de menu lorsqu’il est ajouté au menu. Il se compose d’un ou plusieurs des valeurs répertoriées dans la section Notes.  
  
 *nIDNewItem*  
 Spécifie l’ID de commande du nouvel élément de menu ou, si *nIndicateurs* MF_POPUP, le handle de menu a la valeur ( `HMENU`) d’un menu contextuel. Le *nIDNewItem* paramètre est ignoré (non nécessaire) si *nIndicateurs* est définie sur MF_SEPARATOR.  
  
 *lpszNewItem*  
 Spécifie le contenu du nouvel élément de menu. Le *nIndicateurs* paramètre est utilisé pour interpréter *lpszNewItem* de la façon suivante :  
  
|nIndicateurs|Interprétation de lpszNewItem|  
|------------|-----------------------------------|  
|MF_OWNERDRAW|Contient une valeur de 32 bits fournie par l’application que l’application peut utiliser pour mettre à jour les données supplémentaires associées à l’élément de menu. Cette valeur de 32 bits est disponible à l’application lorsqu’elle traite les messages WM_MEASUREITEM et WM_DRAWITEM. La valeur est stockée dans le `itemData` membre de la structure fournie avec ces messages.|  
|MF_STRING|Contient un pointeur vers une chaîne se terminant par null. Il s’agit de l’interprétation par défaut.|  
|MF_SEPARATOR|Le *lpszNewItem* paramètre est ignoré (ne pas nécessaire).|  
  
 *pBmp*  
 Pointe vers un `CBitmap` objet qui sera utilisé comme l’élément de menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’application peut spécifier l’état de l’élément de menu en définissant des valeurs dans *nIndicateurs*. Lorsque *nIDNewItem* spécifie un menu contextuel, il devient partie intégrante du menu auquel il est ajouté. Si ce menu est détruit, le menu ajouté sera également détruit. Un menu ajouté doit être détaché un `CMenu` objet pour éviter tout conflit. Notez que MF_STRING et MF_OWNERDRAW ne sont pas valides pour la version de la bitmap de `AppendMenu`.  
  
 Le tableau suivant répertorie les indicateurs qui peuvent être définies dans *nIndicateurs*:  
  
- MF_CHECKED joue un bouton bascule avec MF_UNCHECKED pour placer la valeur par défaut Cochez la case en regard de l’élément. Lorsque l’application fournisse des images bitmap de coche (voir la [SetMenuItemBitmaps](#setmenuitembitmaps) fonction membre), la bitmap de la case à cocher « sur » s’affiche.  
  
- MF_UNCHECKED agit comme un bouton bascule avec MF_CHECKED pour supprimer une case à cocher en regard de l’élément. Lorsque l’application fournisse des images bitmap de coche (voir la `SetMenuItemBitmaps` fonction membre), la bitmap de la case à cocher « désactivé » s’affiche.  
  
- MF_DISABLED désactive l’élément de menu afin qu’il ne peut pas être sélectionné mais n’est pas estomper.  
  
- MF_ENABLED permet à l’élément de menu afin qu’il peut être sélectionné et le restaure à partir de son état estompé.  
  
- MF_GRAYED désactive l’élément de menu afin qu’il ne peut pas être sélectionné et s’il s’estompe.  
  
- MF_MENUBARBREAK place l’élément sur une nouvelle ligne dans les menus statiques, ou dans une nouvelle colonne dans les menus contextuels. La nouvelle colonne de menu contextuel doivent être séparée de l’ancienne par une ligne de démarcation verticale.  
  
- MF_MENUBREAK place l’élément sur une nouvelle ligne dans les menus statiques, ou dans une nouvelle colonne dans les menus contextuels. Aucune ligne de démarcation n’est placé entre les colonnes.  
  
- MF_OWNERDRAW Spécifie que l’élément est un élément en mode owner-draw. Lorsque le menu s’affiche pour la première fois, la fenêtre qui possède le menu reçoit un message WM_MEASUREITEM, qui Récupère la hauteur et la largeur de l’élément de menu. Le message WM_DRAWITEM est celui envoyé chaque fois que le propriétaire doit mettre à jour l’apparence visuelle de l’élément de menu. Cette option n’est pas valide pour un élément de menu de niveau supérieur.  
  
- MF_POPUP Spécifie que l’élément de menu a un menu contextuel associé. Le paramètre ID spécifie un handle à un menu contextuel qui doit être associé à l’élément. Cela est utilisé pour l’ajout d’un menu contextuel de niveau supérieur ou un menu contextuel hiérarchique à un élément de menu contextuel.  
  
- MF_SEPARATOR Dessine une ligne de démarcation horizontale. Peut uniquement être utilisé dans un menu contextuel. Cette ligne ne peut pas être estompée, désactivée ou mis en surbrillance. Autres paramètres sont ignorés.  
  
- MF_STRING Spécifie que l’élément de menu est une chaîne de caractères.  
  
 Chacun des groupes suivants répertorie les indicateurs qui s’excluent mutuellement et ne peut pas être utilisés ensemble :  
  
- MF_DISABLED, MF_ENABLED et MF_GRAYED  
  
- MF_STRING, MF_OWNERDRAW, MF_SEPARATOR et la version de bitmap  
  
- MF_MENUBARBREAK et MF_MENUBREAK  
  
- MF_CHECKED et MF_UNCHECKED  
  
 Chaque fois qu’un menu qui se trouvent dans une fenêtre est modifiée (si la fenêtre est affichée), l’application doit appeler [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::CreateMenu](#createmenu).  
  
##  <a name="attach"></a>  CMenu::Attach  
 Attache un menu Windows existant à un `CMenu` objet.  
  
```  
BOOL Attach(HMENU hMenu);
```  
  
### <a name="parameters"></a>Paramètres  
 *hMenu*  
 Spécifie un handle à un menu de Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’opération a réussi ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction ne doit pas être appelée si un menu est déjà attaché à la `CMenu` objet. Le handle de menu est stocké dans le `m_hMenu` membre de données.  
  
 Si le menu que vous voulez manipuler est déjà associé à une fenêtre, vous pouvez utiliser la [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu) fonction pour obtenir un handle pour le menu.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="checkmenuitem"></a>  CMenu::CheckMenuItem  
 Ajoute les coches à ou supprime des coches des éléments de menu dans le menu contextuel.  
  
```  
UINT CheckMenuItem(
    UINT nIDCheckItem,  
    UINT nCheck);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIDCheckItem*  
 Spécifie l’élément de menu doit être vérifié, comme déterminé par *nVérifiez*.  
  
 *nVérifiez*  
 Spécifie la vérification de l’élément de menu et comment déterminer la position de l’élément dans le menu. Le *nVérifiez* paramètre peut être une combinaison de MF_CHECKED ou MF_UNCHECKED avec indicateurs MF_BYPOSITION ou MF_BYCOMMAND. Ces indicateurs peuvent être combinés à l’aide de l’opérateur OR au niveau du bit. Ils ont les significations suivantes :  
  
- MF_BYCOMMAND Spécifie que le paramètre fournit l’ID de commande de l’élément de menu existant. Il s'agit de la valeur par défaut.  
  
- MF_BYPOSITION Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.  
  
- MF_CHECKED joue un bouton bascule avec MF_UNCHECKED pour placer la valeur par défaut Cochez la case en regard de l’élément.  
  
- MF_UNCHECKED agit comme un bouton bascule avec MF_CHECKED pour supprimer une case à cocher en regard de l’élément.  
  
### <a name="return-value"></a>Valeur de retour  
 L’état précédent de l’élément : MF_CHECKED ou MF_UNCHECKED, ou 0xFFFFFFFF si l’élément de menu n’existait pas.  
  
### <a name="remarks"></a>Notes  
 Le *nIDCheckItem* paramètre spécifie l’élément à modifier.  
  
 Le *nIDCheckItem* paramètre peut identifier un élément de menu contextuel ainsi que d’un élément de menu. Aucune des étapes spéciales ne sont requises pour rechercher un élément de menu contextuel. Impossible de vérifier les éléments de menu de niveau supérieur. Un élément de menu contextuel doit être vérifié par position dans la mesure où il n’a pas un identificateur d’élément de menu associé.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::GetMenuState](#getmenustate).  
  
##  <a name="checkmenuradioitem"></a>  CMenu::CheckMenuRadioItem  
 Vérifie un élément de menu spécifié et le rend un élément de case d’option.  
  
```  
BOOL CheckMenuRadioItem(
    UINT nIDFirst,  
    UINT nIDLast,  
    UINT nIDItem,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIDFirst*  
 Spécifie (en tant qu’ID ou offset, en fonction de la valeur de *nIndicateurs*) le premier élément de menu dans le groupe de cases d’option.  
  
 *nIDLast*  
 Spécifie (en tant qu’ID ou offset, en fonction de la valeur de *nIndicateurs*) le dernier élément de menu dans le groupe de cases d’option.  
  
 *nIDItem*  
 Spécifie (en tant qu’ID ou offset, en fonction de la valeur de *nIndicateurs*) l’élément dans le groupe qui sera vérifié avec un bouton radio.  
  
 *nIndicateurs*  
 Spécifie l’interprétation de *nIDFirst*, *nIDLast*, et *nIDItem* de la façon suivante :  
  
|nIndicateurs|Interprétation|  
|------------|--------------------|  
|MF_BYCOMMAND|Spécifie que le paramètre fournit l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si aucune MF_BYCOMMAND ou MF_BYPOSITION est définie.|  
|MF_BYPOSITION|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite ; sinon 0  
  
### <a name="remarks"></a>Notes  
 En même temps, la fonction désactive tous les autres éléments de menu dans le groupe associé et efface l’indicateur de type d’élément de case d’option pour ces éléments. L’élément activé s’affiche à l’aide d’une bitmap de bouton (ou à puces) de case d’option au lieu d’une image bitmap de coche.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range).  
  
##  <a name="cmenu"></a>  CMenu::CMenu  
 Crée un menu vide et l’attache à un `CMenu` objet.  
  
```  
CMenu();
```  
  
### <a name="remarks"></a>Notes  
 Le menu n’est pas créé tant que vous appelez une de créer ou chargez des fonctions membres de `CMenu:`  
  
- [CreateMenu](#createmenu)  
  
- [CreatePopupMenu](#createpopupmenu)  
  
- [LoadMenu](#loadmenu)  
  
- [LoadMenuIndirect](#loadmenuindirect)  
  
- [Attacher](#attach)  
  
##  <a name="createmenu"></a>  CMenu::CreateMenu  
 Crée un menu et l’attache à la `CMenu` objet.  
  
```  
BOOL CreateMenu();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le menu a été créé avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Le menu est initialement vide. Éléments de menu peuvent être ajoutés à l’aide de la `AppendMenu` ou `InsertMenu` fonction membre.  
  
 Si le menu est assigné à une fenêtre, il est automatiquement détruit la fenêtre est détruite.  
  
 Avant de quitter, l’application doit libérer les ressources système associées à un menu si le menu n’est pas affecté à une fenêtre. Une application libère un menu en appelant le [DestroyMenu](#destroymenu) fonction membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]  
  
##  <a name="createpopupmenu"></a>  CMenu::CreatePopupMenu  
 Crée un menu contextuel et l’attache à la `CMenu` objet.  
  
```  
BOOL CreatePopupMenu();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le menu contextuel a été créé avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Le menu est initialement vide. Éléments de menu peuvent être ajoutés à l’aide de la `AppendMenu` ou `InsertMenu` fonction membre. L’application peut ajouter le menu contextuel à un menu existant ou un menu contextuel. Le `TrackPopupMenu` fonction membre peut être utilisée pour afficher ce menu sous la forme d’un menu contextuel flottante et pour effectuer le suivi des sélections dans le menu contextuel.  
  
 Si le menu est assigné à une fenêtre, il est automatiquement détruit la fenêtre est détruite. Si le menu est ajouté à un menu existant, il est automatiquement détruit lorsque ce menu est détruit.  
  
 Avant de quitter, l’application doit libérer les ressources système associées à un menu contextuel si le menu n’est pas affecté à une fenêtre. Une application libère un menu en appelant le [DestroyMenu](#destroymenu) fonction membre.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::CreateMenu](#createmenu).  
  
##  <a name="deletemenu"></a>  CMenu::DeleteMenu  
 Supprime un élément dans le menu.  
  
```  
BOOL DeleteMenu(
    UINT nPosition,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 *nPosition*  
 Spécifie l’élément de menu qui doit être supprimé, comme déterminé par *nIndicateurs*.  
  
 *nIndicateurs*  
 Est utilisé pour interpréter *nPosition* de la façon suivante :  
  
|nIndicateurs|Interprétation de nPosition|  
|------------|---------------------------------|  
|MF_BYCOMMAND|Spécifie que le paramètre fournit l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si aucune MF_BYCOMMAND ou MF_BYPOSITION est définie.|  
|MF_BYPOSITION|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si l’élément de menu a un menu contextuel associé, `DeleteMenu` détruit le handle pour le menu contextuel et libère la mémoire utilisée par le menu contextuel.  
  
 Chaque fois qu’un menu qui se trouvent dans une fenêtre est modifiée (si la fenêtre est affichée), l’application doit appeler [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).  
  
##  <a name="deletetempmap"></a>  CMenu::DeleteTempMap  
 Appelé automatiquement par le `CWinApp` Gestionnaire de durée d’inactivité, supprime temporaires `CMenu` objets créés par le [FromHandle](#fromhandle) fonction membre.  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>Notes  
 `DeleteTempMap` Détache l’objet de menu Windows attachée à une table temporaire `CMenu` objet avant de supprimer le `CMenu` objet.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]  
  
##  <a name="destroymenu"></a>  CMenu::DestroyMenu  
 Détruit le menu et toutes les ressources de Windows qui ont été utilisés.  
  
```  
BOOL DestroyMenu();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le menu est détruit ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Le menu est détaché de la `CMenu` avant d’être détruit l’objet. Le Windows `DestroyMenu` fonction est appelée automatiquement le `CMenu` destructeur.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::CreateMenu](#createmenu).  
  
##  <a name="detach"></a>  CMenu::Detach  
 Détache un menu Windows à partir d’un `CMenu` de l’objet et retourne le handle.  
  
```  
HMENU Detach();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle de type HMENU, à un menu Windows, en cas de réussite ; Sinon, NULL.  
  
### <a name="remarks"></a>Notes  
 Le `m_hMenu` membre de données est défini sur NULL.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="drawitem"></a>  CMenu::DrawItem  
 Appelé par l’infrastructure lorsqu’un aspect visuel d’une modification de menu owner-drawn.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpDrawItemStruct*  
 Un pointeur vers un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) structure qui contient des informations sur le type de dessin requis.  
  
### <a name="remarks"></a>Notes  
 Le `itemAction` membre de la `DRAWITEMSTRUCT` structure définit l’action de dessin qui doit être effectuée. Remplacez cette fonction membre pour implémenter le dessin pour un mode owner-draw `CMenu` objet. L’application doit restaurer tous les objets interface (GDI) périphérique graphique sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant l’arrêt de cette fonction membre.  
  
 Consultez [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) pour obtenir une description de la `DRAWITEMSTRUCT` structure.  
  
### <a name="example"></a>Exemple  
 Le code suivant présente de la bibliothèque MFC [CTRLTEST](../../visual-cpp-samples.md) exemple :  
  
 [!code-cpp[NVC_MFCWindowing#24](../../mfc/reference/codesnippet/cpp/cmenu-class_4.cpp)]  
  
##  <a name="enablemenuitem"></a>  CMenu::EnableMenuItem  
 Active, désactive ou efface un élément de menu.  
  
```  
UINT EnableMenuItem(
    UINT nIDEnableItem,  
    UINT nEnable);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIDEnableItem*  
 Spécifie l’élément de menu doit être activé, comme déterminé par *nEnable*. Ce paramètre peut spécifier les éléments de menu contextuel, ainsi que des éléments de menu standard.  
  
 *nEnable*  
 Spécifie l’action à entreprendre. Il peut être une combinaison de MF_DISABLED, MF_ENABLED ou MF_GRAYED, avec MF_BYCOMMAND ou MF_BYPOSITION. Ces valeurs peuvent être combinées à l’aide de l’opérateur OR au niveau du bit. Ces valeurs ont les significations suivantes :  
  
- MF_BYCOMMAND Spécifie que le paramètre fournit l’ID de commande de l’élément de menu existant. Il s'agit de la valeur par défaut.  
  
- MF_BYPOSITION Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.  
  
- MF_DISABLED désactive l’élément de menu afin qu’il ne peut pas être sélectionné mais n’est pas estomper.  
  
- MF_ENABLED permet à l’élément de menu afin qu’il peut être sélectionné et le restaure à partir de son état estompé.  
  
- MF_GRAYED désactive l’élément de menu afin qu’il ne peut pas être sélectionné et s’il s’estompe.  
  
### <a name="return-value"></a>Valeur de retour  
 État précédent (MF_DISABLED, MF_ENABLED ou MF_GRAYED) ou -1 si non valide.  
  
### <a name="remarks"></a>Notes  
 Le [CreateMenu](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu), et [LoadMenuIndirect](#loadmenuindirect) fonctions membres peuvent également définir l’état (activé, désactivé, ou estompés) d’un élément de menu.  
  
 À l’aide de la valeur MF_BYPOSITION requiert une application pour utiliser la bonne `CMenu`. Si le `CMenu` du menu barre est utilisée, un élément de menu de niveau supérieur (il s’agit d’un élément dans la barre de menus) est affecté. Pour définir l’état d’un élément dans un menu déroulant contextuel ou imbriqué par position, une application doit spécifier le `CMenu` du menu contextuel.  
  
 Lorsqu’une application spécifie l’indicateur MF_BYCOMMAND, Windows vérifie tous les éléments de menu contextuel qui sont subordonnés à le `CMenu`; par conséquent, sauf si les éléments de menu en double sont présentes, à l’aide du `CMenu` du menu barre est suffisante.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#25](../../mfc/reference/codesnippet/cpp/cmenu-class_5.cpp)]  
  
##  <a name="fromhandle"></a>  CMenu::FromHandle  
 Retourne un pointeur vers un `CMenu` objet en fonction d’un handle Windows à un menu.  
  
```  
static CMenu* PASCAL FromHandle(HMENU hMenu);
```  
  
### <a name="parameters"></a>Paramètres  
 *hMenu*  
 Handle Windows d’un menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `CMenu` qui peut être temporaire ou permanent.  
  
### <a name="remarks"></a>Notes  
 Si un `CMenu` objet n’est pas déjà attaché à l’objet de menu Windows, une table temporaire `CMenu` objet est créé et attaché.  
  
 Ce fichier temporaire `CMenu` objet est valide uniquement jusqu'à la prochaine fois que l’application a un temps d’inactivité dans sa boucle d’événement, moment auquel tous les objets temporaires sont supprimés.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::CreateMenu](#createmenu).  
  
##  <a name="getdefaultitem"></a>  CMenu::GetDefaultItem  
 Détermine l’élément de menu par défaut dans le menu spécifié.  
  
```  
UINT GetDefaultItem(
    UINT gmdiFlags,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 *gmdiFlags*  
 Valeur spécifiant la façon dont la fonction recherche des éléments de menu. Ce paramètre peut être none, une ou une combinaison des valeurs suivantes :  
  
|Value|Signification|  
|-----------|-------------|  
|GMDI_GOINTOPOPUPS|Spécifie que, si la valeur par défaut est un élément qui ouvre un sous-menu, la fonction doit effectuer une recherche dans le sous-menu correspondant de manière récursive. Si le sous-menu ne contient aucun élément par défaut, la valeur de retour identifie l’élément qui s’ouvre le sous-menu.<br /><br /> Par défaut, la fonction retourne le premier élément par défaut dans le menu spécifié, qu’il s’agisse d’un élément qui s’ouvre un sous-menu.|  
|GMDI_USEDISABLED|Spécifie que la fonction doit retourner un élément par défaut, même si elle est désactivée.<br /><br /> Par défaut, la fonction ignore les éléments désactivés ou grisées.|  
  
 *fByPos*  
 Valeur qui spécifie s’il faut récupérer l’identificateur de l’élément de menu ou de sa position. Si ce paramètre est FALSE, l’identificateur est retourné. Sinon, la position est retournée.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, la valeur de retour est l’identificateur ou la position de l’élément de menu. Si la fonction échoue, la valeur de retour est - 1.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la fonction Win32 [GetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-getmenudefaultitem), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="getmenucontexthelpid"></a>  CMenu::GetMenuContextHelpId  
 Récupère l’aide du contexte associé à un ID `CMenu`.  
  
```  
DWORD GetMenuContextHelpId() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’aide du contexte ID actuellement associé à `CMenu` si elle en a un, zéro sinon.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="getmenuinfo"></a>  CMenu::GetMenuInfo  
 Récupère des informations pour un menu.  
  
```  
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *lpcmi*  
 Un pointeur vers un [MENUINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuinfo) structure contenant des informations pour le menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, la valeur de retour est différent de zéro ; Sinon, la valeur de retour est zéro.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour récupérer des informations sur le menu.  
  
##  <a name="getmenuitemcount"></a>  CMenu::GetMenuItemCount  
 Détermine le nombre d’éléments dans un menu contextuel ou de niveau supérieur.  
  
```  
UINT GetMenuItemCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans le menu si la fonction a réussi ; sinon -1.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).  
  
##  <a name="getmenuitemid"></a>  CMenu::GetMenuItemID  
 Obtient l’identificateur d’élément de menu pour un élément de menu situé à la position définie par *nPos*.  
  
```  
UINT GetMenuItemID(int nPos) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nPos*  
 Spécifie la position (base zéro) de l’élément de menu dont l’ID est récupérée.  
  
### <a name="return-value"></a>Valeur de retour  
 ID d’élément pour l’élément spécifié dans un menu contextuel si la fonction réussite. Si l’élément spécifié est un menu contextuel (par opposition à un élément dans le menu contextuel), la valeur de retour est -1. Si *nPos* correspond à un élément de menu séparateur, la valeur de retour est 0.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="getmenuiteminfo"></a>  CMenu::GetMenuItemInfo  
 Récupère des informations sur un élément de menu.  
  
```  
BOOL GetMenuItemInfo(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 *uItem*  
 Identificateur ou la position de l’élément de menu pour obtenir des informations. La signification de ce paramètre dépend de la valeur de `ByPos`.  
  
 *lpMenuItemInfo*  
 Un pointeur vers un [MENUITEMINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuiteminfoa), comme décrit dans le SDK Windows, qui contient des informations sur le menu.  
  
 *fByPos*  
 Valeur spécifiant la signification de `nIDItem`. Par défaut, `ByPos` est FALSE, ce qui indique qu’uItem est un identificateur d’élément de menu. Si `ByPos` n’est pas définie sur FALSE, cette propriété indique une position d’élément de menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, la valeur de retour est différent de zéro. Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir les informations d’erreur étendues, utilisez la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360), comme décrit dans le SDK Windows.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la de la fonction Win32 [GetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-getmenuiteminfoa), comme décrit dans le SDK Windows. Notez que dans l’implémentation MFC de `GetMenuItemInfo`, vous n’utilisez pas un handle à un menu.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#26](../../mfc/reference/codesnippet/cpp/cmenu-class_6.cpp)]  
  
##  <a name="getmenustate"></a>  CMenu::GetMenuState  
 Retourne l’état de l’élément de menu spécifié ou le nombre d’éléments dans un menu contextuel.  
  
```  
UINT GetMenuState(
    UINT nID,  
    UINT nFlags) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nID*  
 Spécifie l’ID d’élément de menu, comme déterminé par *nIndicateurs*.  
  
 *nIndicateurs*  
 Spécifie la nature de *nID*. Il peut prendre l’une des valeurs suivantes :  
  
- MF_BYCOMMAND Spécifie que le paramètre fournit l’ID de commande de l’élément de menu existant. Il s'agit de la valeur par défaut.  
  
- MF_BYPOSITION Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur 0xFFFFFFFF si l’élément spécifié n’existe pas. Si *nId* identifie un menu contextuel, l’octet de poids fort contient le nombre d’éléments dans le menu contextuel et l’octet de poids faible contient les indicateurs de menu associés le menu contextuel. Sinon, la valeur de retour est un masque (ou booléenne) des valeurs dans la liste suivante (ce masque décrit l’état du menu d’élément qui *nId* identifie) :  
  
- MF_CHECKED joue un bouton bascule avec MF_UNCHECKED pour placer la valeur par défaut Cochez la case en regard de l’élément. Lorsque l’application fournisse des images bitmap de coche (voir la `SetMenuItemBitmaps` fonction membre), la bitmap de la case à cocher « sur » s’affiche.  
  
- MF_DISABLED désactive l’élément de menu afin qu’il ne peut pas être sélectionné mais n’est pas estomper.  
  
- MF_ENABLED permet à l’élément de menu afin qu’il peut être sélectionné et le restaure à partir de son état estompé. Notez que la valeur de cette constante est 0 ; une application ne doit pas tester par rapport à 0 pour l’échec lors de l’utilisation de cette valeur.  
  
- MF_GRAYED désactive l’élément de menu afin qu’il ne peut pas être sélectionné et s’il s’estompe.  
  
- MF_MENUBARBREAK place l’élément sur une nouvelle ligne dans les menus statiques, ou dans une nouvelle colonne dans les menus contextuels. La nouvelle colonne de menu contextuel doivent être séparée de l’ancienne par une ligne de démarcation verticale.  
  
- MF_MENUBREAK place l’élément sur une nouvelle ligne dans les menus statiques, ou dans une nouvelle colonne dans les menus contextuels. Aucune ligne de démarcation n’est placé entre les colonnes.  
  
- MF_SEPARATOR Dessine une ligne de démarcation horizontale. Peut uniquement être utilisé dans un menu contextuel. Cette ligne ne peut pas être estompée, désactivée ou mis en surbrillance. Autres paramètres sont ignorés.  
  
- MF_UNCHECKED agit comme un bouton bascule avec MF_CHECKED pour supprimer une case à cocher en regard de l’élément. Lorsque l’application fournisse des images bitmap de coche (voir la `SetMenuItemBitmaps` fonction membre), la bitmap de la case à cocher « désactivé » s’affiche. Notez que la valeur de cette constante est 0 ; une application ne doit pas tester par rapport à 0 pour l’échec lors de l’utilisation de cette valeur.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#27](../../mfc/reference/codesnippet/cpp/cmenu-class_7.cpp)]  
  
##  <a name="getmenustring"></a>  CMenu::GetMenuString  
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
 *nIDItem*  
 Spécifie l’identificateur entier de l’élément de menu ou le décalage de l’élément de menu dans le menu, en fonction de la valeur de *nIndicateurs*.  
  
 *lpString*  
 Pointe vers la mémoire tampon qui doit recevoir l’étiquette.  
  
 *rString*  
 Une référence à un `CString` objet devant recevoir la chaîne de menu copié.  
  
 *nMaxCount*  
 Spécifie la longueur maximale (en caractères) de l’étiquette doit être copié. Si l’étiquette est plus longue que le maximum spécifié dans *nMaxCount*, les caractères supplémentaires sont tronqués.  
  
 *nIndicateurs*  
 Spécifie l’interprétation de la *nIDItem* paramètre. Il peut prendre l’une des valeurs suivantes :  
  
|nIndicateurs|Interprétation de nIDItem|  
|------------|-------------------------------|  
|MF_BYCOMMAND|Spécifie que le paramètre fournit l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si aucune MF_BYCOMMAND ou MF_BYPOSITION est définie.|  
|MF_BYPOSITION|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|  
  
### <a name="return-value"></a>Valeur de retour  
 Spécifie le nombre réel de caractères copiés vers la mémoire tampon, non compris le terminateur null.  
  
### <a name="remarks"></a>Notes  
 Le *nMaxCount* paramètre doit être une plus grande que le nombre de caractères dans l’étiquette en fonction du caractère null qui met fin à une chaîne.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="getsafehmenu"></a>  CMenu::GetSafeHmenu  
 Retourne le HMENU encapsulé par cette `CMenu` objet ou une valeur NULL`CMenu` pointeur.  
  
```  
HMENU GetSafeHmenu() const;  
```  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::LoadMenu](#loadmenu).  
  
##  <a name="getsubmenu"></a>  CMenu::GetSubMenu  
 Récupère le `CMenu` objet d’un menu contextuel.  
  
```  
CMenu* GetSubMenu(int nPos) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nPos*  
 Spécifie la position du menu contextuel contenue dans le menu. Valeurs de position commencent à 0 pour le premier élément de menu. Identificateur du menu contextuel ne peut pas être utilisé dans cette fonction.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `CMenu` de l’objet dont la propriété `m_hMenu` membre contient un handle vers le menu contextuel si un menu contextuel existe à la position donnée ; sinon, NULL. Si un `CMenu` objet n’existe pas, puis un temporaire est créé. Le `CMenu` pointeur retourné ne doit pas être stockée.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::TrackPopupMenu](#trackpopupmenu).  
  
##  <a name="insertmenu"></a>  CMenu::InsertMenu  
 Insère un nouvel élément de menu à la position spécifiée par *nPosition* et déplace les autres éléments du menu déroulant.  
  
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
 *nPosition*  
 Spécifie l’élément de menu avant laquelle le nouvel élément de menu doit être inséré. Le *nIndicateurs* paramètre peut être utilisé pour interpréter *nPosition* comme suit :  
  
|nIndicateurs|Interprétation de nPosition|  
|------------|---------------------------------|  
|MF_BYCOMMAND|Spécifie que le paramètre fournit l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si aucune MF_BYCOMMAND ou MF_BYPOSITION est définie.|  
|MF_BYPOSITION|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0. Si *nPosition* est -1, le nouvel élément de menu est ajouté à la fin du menu.|  
  
 *nIndicateurs*  
 Spécifie comment *nPosition* est interprété et spécifie des informations sur l’état du nouvel élément de menu lorsqu’il est ajouté au menu. Pour obtenir la liste des indicateurs qui peuvent être définies, consultez le [AppendMenu](#appendmenu) fonction membre. Pour spécifier plusieurs valeurs, utilisez l’opérateur OR au niveau du bit de les combiner avec l’indicateur MF_BYCOMMAND ou MF_BYPOSITION.  
  
 *nIDNewItem*  
 Spécifie l’ID de commande du nouvel élément de menu ou, si *nIndicateurs* est défini sur MF_POPUP, le handle de menu (HMENU) du menu contextuel. Le *nIDNewItem* paramètre est ignoré (non nécessaire) si *nIndicateurs* est définie sur MF_SEPARATOR.  
  
 *lpszNewItem*  
 Spécifie le contenu du nouvel élément de menu. *nIndicateurs* peut être utilisé pour interpréter *lpszNewItem* comme suit :  
  
|nIndicateurs|Interprétation de lpszNewItem|  
|------------|-----------------------------------|  
|MF_OWNERDRAW|Contient une valeur de 32 bits fournie par l’application que l’application peut utiliser pour mettre à jour les données supplémentaires associées à l’élément de menu. Cette valeur de 32 bits est disponible à l’application dans le `itemData` membre de la structure fournie par le [WM_MEASUREITEM](/windows/desktop/Controls/wm-measureitem) et [WM_DRAWITEM](/windows/desktop/Controls/wm-drawitem) messages. Ces messages sont envoyés lorsque l’élément de menu est initialement affiché ou est modifié.|  
|MF_STRING|Contient un pointeur long vers une chaîne se terminant par null. Il s’agit de l’interprétation par défaut.|  
|MF_SEPARATOR|Le *lpszNewItem* paramètre est ignoré (ne pas nécessaire).|  
  
 *pBmp*  
 Pointe vers un `CBitmap` objet qui sera utilisé comme l’élément de menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’application peut spécifier l’état de l’élément de menu en définissant des valeurs dans *nIndicateurs*.  
  
 Chaque fois qu’un menu qui se trouvent dans une fenêtre est modifiée (si la fenêtre est affichée), l’application doit appeler `CWnd::DrawMenuBar`.  
  
 Lorsque *nIDNewItem* spécifie un menu contextuel, il devient partie intégrante du menu dans lequel elle est insérée. Si ce menu est détruit, le menu inséré sera également détruit. Un menu inséré doit être détaché un `CMenu` objet pour éviter tout conflit.  
  
 Si la fenêtre interface multidocument (MDI) enfant est agrandie actif et une application insère un menu contextuel dans le menu de l’application MDI en appelant cette fonction et en spécifiant que l’indicateur MF_BYPOSITION, le menu est inséré une position gauche plus loin que attendu. Cela se produit parce que le menu de contrôle de la fenêtre MDI enfant active est inséré dans la première position de la barre de menus de la fenêtre frame MDI. Pour positionner le menu correctement, l’application doit ajouter 1 à la valeur de position qui serait utilisée sinon. Une application peut utiliser le message WM_MDIGETACTIVE pour déterminer si la fenêtre enfant active est agrandie.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#28](../../mfc/reference/codesnippet/cpp/cmenu-class_8.cpp)]  
  
##  <a name="insertmenuitem"></a>  CMenu::InsertMenuItem  
 Insère un nouvel élément de menu à la position spécifiée dans un menu.  
  
```  
BOOL InsertMenuItem(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 *uItem*  
 Consultez la description de *uItem* dans [InsertMenuItem](/windows/desktop/api/winuser/nf-winuser-insertmenuitema) dans le SDK Windows.  
  
 *lpMenuItemInfo*  
 Consultez la description de *lpmii* dans `InsertMenuItem` dans le SDK Windows.  
  
 *fByPos*  
 Consultez la description de *fByPosition* dans `InsertMenuItem` dans le SDK Windows.  
  
### <a name="remarks"></a>Notes  
 Cette fonction encapsule [InsertMenuItem](/windows/desktop/api/winuser/nf-winuser-insertmenuitema), comme décrit dans le SDK Windows.  
  
##  <a name="loadmenu"></a>  CMenu::LoadMenu  
 Charge une ressource de menu à partir du fichier exécutable de l’application et l’attache à la `CMenu` objet.  
  
```  
BOOL LoadMenu(LPCTSTR lpszResourceName);  
BOOL LoadMenu(UINT nIDResource);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszResourceName*  
 Pointe vers une chaîne se terminant par null qui contient le nom de la ressource de menu à charger.  
  
 *nIDResource*  
 Spécifie l’ID de menu de la ressource de menu à charger.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la ressource de menu a été chargée avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Avant de quitter, l’application doit libérer les ressources système associées à un menu si le menu n’est pas affecté à une fenêtre. Une application libère un menu en appelant le [DestroyMenu](#destroymenu) fonction membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]  
  
##  <a name="loadmenuindirect"></a>  CMenu::LoadMenuIndirect  
 Charge une ressource à partir d’un modèle de menu dans la mémoire et l’attache à la `CMenu` objet.  
  
```  
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpMenuTemplate*  
 Pointe vers un modèle de menu (c'est-à-dire un seul [MENUITEMTEMPLATEHEADER](/windows/desktop/api/winuser/ns-winuser-menuitemtemplateheader) structure et une collection d’un ou plusieurs [MENUITEMTEMPLATE](/windows/desktop/api/winuser/ns-winuser-menuitemtemplate) structures). Pour plus d’informations sur ces deux structures, consultez le Kit de développement Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la ressource de menu a été chargée avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Un modèle de menu est un en-tête suivi d’une collection d’un ou plusieurs [MENUITEMTEMPLATE](/windows/desktop/api/winuser/ns-winuser-menuitemtemplate) structures, chacun d’eux peut contenir un ou plusieurs éléments de menu et les menus contextuels.  
  
 Le numéro de version doit être 0.  
  
 Le `mtOption` indicateurs doivent inclure MF_END pour le dernier élément dans une liste contextuelle et pour le dernier élément dans la liste principale. Consultez le `AppendMenu` fonction membre pour les autres indicateurs. Le `mtId` membre doit être omis de la structure MENUITEMTEMPLATE lorsque MF_POPUP est spécifié dans `mtOption`.  
  
 L’espace alloué pour la structure MENUITEMTEMPLATE doit être suffisamment grande pour `mtString` pour contenir le nom de l’élément de menu sous forme de chaîne se terminant par null.  
  
 Avant de quitter, l’application doit libérer les ressources système associées à un menu si le menu n’est pas affecté à une fenêtre. Une application libère un menu en appelant le [DestroyMenu](#destroymenu) fonction membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]  
  
##  <a name="m_hmenu"></a>  CMenu::m_hMenu  
 Spécifie le handle HMENU du menu Windows attaché à la `CMenu` objet.  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::LoadMenu](#loadmenu).  
  
##  <a name="measureitem"></a>  CMenu::MeasureItem  
 Appelé par l’infrastructure lors de la création d’un menu avec le style de dessin owner-drawn.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpMeasureItemStruct*  
 Un pointeur vers un `MEASUREITEMSTRUCT` structure.  
  
### <a name="remarks"></a>Notes  
 Par défaut, cette fonction membre ne fait rien. Remplacez cette fonction membre et renseignez la `MEASUREITEMSTRUCT` structure afin d’informer Windows de dimensions du menu.  
  
 Consultez [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) pour obtenir une description de la `MEASUREITEMSTRUCT` structure.  
  
### <a name="example"></a>Exemple  
 Le code suivant présente de la bibliothèque MFC [CTRLTEST](../../visual-cpp-samples.md) exemple :  
  
 [!code-cpp[NVC_MFCWindowing#31](../../mfc/reference/codesnippet/cpp/cmenu-class_11.cpp)]  
  
##  <a name="modifymenu"></a>  CMenu::ModifyMenu  
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
 *nPosition*  
 Spécifie l’élément de menu à modifier. Le *nIndicateurs* paramètre peut être utilisé pour interpréter *nPosition* comme suit :  
  
|nIndicateurs|Interprétation de nPosition|  
|------------|---------------------------------|  
|MF_BYCOMMAND|Spécifie que le paramètre fournit l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si aucune MF_BYCOMMAND ou MF_BYPOSITION est définie.|  
|MF_BYPOSITION|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|  
  
 *nIndicateurs*  
 Spécifie comment *nPosition* est interprété et donne des informations sur les modifications à apporter à l’élément de menu. Pour obtenir la liste d’indicateurs qui peuvent être définies, consultez le [AppendMenu](#appendmenu) fonction membre.  
  
 *nIDNewItem*  
 Spécifie l’ID de commande de l’élément de menu modifié ou si *nIndicateurs* est défini sur MF_POPUP, le handle de menu (HMENU) d’un menu contextuel. Le *nIDNewItem* paramètre est ignoré (non nécessaire) si *nIndicateurs* est définie sur MF_SEPARATOR.  
  
 *lpszNewItem*  
 Spécifie le contenu du nouvel élément de menu. Le *nIndicateurs* paramètre peut être utilisé pour interpréter *lpszNewItem* comme suit :  
  
|nIndicateurs|Interprétation de lpszNewItem|  
|------------|-----------------------------------|  
|MF_OWNERDRAW|Contient une valeur de 32 bits fournie par l’application que l’application peut utiliser pour mettre à jour les données supplémentaires associées à l’élément de menu. Cette valeur de 32 bits est disponible à l’application lorsqu’il traite MF_MEASUREITEM et MF_DRAWITEM.|  
|MF_STRING|Contient un pointeur long vers une chaîne se terminant par null ou à un `CString`.|  
|MF_SEPARATOR|Le *lpszNewItem* paramètre est ignoré (ne pas nécessaire).|  
  
 *pBmp*  
 Pointe vers un `CBitmap` objet qui sera utilisé comme l’élément de menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’application spécifie le nouvel état de l’élément de menu en définissant des valeurs dans *nIndicateurs*. Si cette fonction remplace un menu contextuel associé à l’élément de menu, il supprime le menu contextuel ancien et libère la mémoire utilisée par le menu contextuel.  
  
 Lorsque *nIDNewItem* spécifie un menu contextuel, il devient partie intégrante du menu dans lequel elle est insérée. Si ce menu est détruit, le menu inséré sera également détruit. Un menu inséré doit être détaché un `CMenu` objet pour éviter tout conflit.  
  
 Chaque fois qu’un menu qui se trouvent dans une fenêtre est modifiée (si la fenêtre est affichée), l’application doit appeler `CWnd::DrawMenuBar`. Pour modifier les attributs d’éléments de menu existant, il est beaucoup plus rapide d’utiliser le `CheckMenuItem` et `EnableMenuItem` fonctions membres.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="operator_hmenu"></a>  CMenu::operator HMENU  
 Utilisez cet opérateur pour récupérer le descripteur de la `CMenu` objet.  
  
```  
operator HMENU() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 En cas de réussite, le handle de la `CMenu` de l’objet ; sinon, NULL.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser le handle d’appeler directement les API de Windows.  
  
##  <a name="operator_neq"></a>  CMenu::operator ! =  
 Détermine si deux menus sont logiquement pas égaux.  
  
```  
BOOL operator!=(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *Menu*  
 Un `CMenu` objet pour la comparaison.  
  
### <a name="remarks"></a>Notes  
 Teste si un objet de menu sur le côté gauche n’est pas égal à un objet de menu sur le côté droit.  
  
##  <a name="operator_eq_eq"></a>  CMenu::operator ==  
 Détermine si deux menus sont logiquement égales.  
  
```  
BOOL operator==(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *Menu*  
 Un `CMenu` objet pour la comparaison.  
  
### <a name="remarks"></a>Notes  
 Teste si un objet de menu sur le côté gauche est égal (en termes de la valeur HMENU) à un objet de menu sur le côté droit.  
  
##  <a name="removemenu"></a>  CMenu::RemoveMenu  
 Supprime un élément de menu avec un menu contextuel dans le menu.  
  
```  
BOOL RemoveMenu(
    UINT nPosition,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 *nPosition*  
 Spécifie l’élément de menu à supprimer. Le *nIndicateurs* paramètre peut être utilisé pour interpréter *nPosition* comme suit :  
  
|nIndicateurs|Interprétation de nPosition|  
|------------|---------------------------------|  
|MF_BYCOMMAND|Spécifie que le paramètre fournit l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si aucune MF_BYCOMMAND ou MF_BYPOSITION est définie.|  
|MF_BYPOSITION|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|  
  
 *nIndicateurs*  
 Spécifie comment *nPosition* est interprétée.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Elle ne supprime pas le handle d’un menu contextuel, le menu peut donc être réutilisé. Avant d’appeler cette fonction, l’application peut appeler le `GetSubMenu` fonction membre pour récupérer la fenêtre contextuelle `CMenu` objet pour une réutilisation.  
  
 Chaque fois qu’un menu qui se trouvent dans une fenêtre est modifiée (si la fenêtre est affichée), l’application doit appeler `CWnd::DrawMenuBar`.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="setdefaultitem"></a>  CMenu::SetDefaultItem  
 Définit l’élément de menu par défaut pour le menu spécifié.  
  
```  
BOOL SetDefaultItem(
    UINT uItem,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 *uItem*  
 Identificateur ou la position du nouvel élément de menu par défaut ou - 1 pour aucun élément par défaut. La signification de ce paramètre dépend de la valeur de *fByPos*.  
  
 *fByPos*  
 Valeur spécifiant la signification de *uItem*. Si ce paramètre est FALSE, *uItem* est un identificateur d’élément de menu. Sinon, il est une position d’élément de menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, la valeur de retour est différent de zéro. Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir les informations d’erreur étendues, utilisez la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360), comme décrit dans le SDK Windows.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la fonction Win32 [SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="setmenucontexthelpid"></a>  CMenu::SetMenuContextHelpId  
 Associe un ID d’aide de contexte avec `CMenu`.  
  
```  
BOOL SetMenuContextHelpId(DWORD dwContextHelpId);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwContextHelpId*  
 ID de contexte d’aide à associer à `CMenu`.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite ; sinon 0  
  
### <a name="remarks"></a>Notes  
 Tous les éléments dans le menu partagent cet identificateur, il n’est pas possible de joindre un identificateur de contexte d’aide pour les éléments de menu individuels.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="setmenuinfo"></a>  CMenu::SetMenuInfo  
 Définit les informations pour un menu.  
  
```  
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpcmi*  
 Un pointeur vers un [MENUINFO](/windows/desktop/api/winuser/ns-winuser-tagmenuinfo) structure contenant des informations pour le menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, la valeur de retour est différent de zéro ; Sinon, la valeur de retour est zéro.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour définir des informations spécifiques sur le menu.  
  
##  <a name="setmenuitembitmaps"></a>  CMenu::SetMenuItemBitmaps  
 Associe les bitmaps spécifiés à un élément de menu.  
  
```  
BOOL SetMenuItemBitmaps(
    UINT nPosition,  
    UINT nFlags,  
    const CBitmap* pBmpUnchecked,  
    const CBitmap* pBmpChecked);
```  
  
### <a name="parameters"></a>Paramètres  
 *nPosition*  
 Spécifie l’élément de menu à modifier. Le *nIndicateurs* paramètre peut être utilisé pour interpréter *nPosition* comme suit :  
  
|nIndicateurs|Interprétation de nPosition|  
|------------|---------------------------------|  
|MF_BYCOMMAND|Spécifie que le paramètre fournit l’ID de commande de l’élément de menu existant. Il s’agit de la valeur par défaut si aucune MF_BYCOMMAND ou MF_BYPOSITION est définie.|  
|MF_BYPOSITION|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|  
  
 *nIndicateurs*  
 Spécifie comment *nPosition* est interprétée.  
  
 *pBmpUnchecked*  
 Spécifie l’image bitmap à utiliser pour les éléments de menu qui ne sont pas vérifiées.  
  
 *pBmpChecked*  
 Spécifie l’image bitmap à utiliser pour les éléments de menu sont activés.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si l’élément de menu est activée ou désactivée, Windows affiche l’image bitmap appropriée en regard de l’élément de menu.  
  
 Si *pBmpUnchecked* ou *pBmpChecked* est NULL, Windows n’affiche rien en regard de l’élément de menu pour l’attribut correspondant. Si les deux paramètres sont NULL, Windows utilise la case à cocher par défaut lorsque l’élément est activé et supprime la case à cocher lorsque l’élément est désactivée.  
  
 Lorsque le menu est détruit, ces bitmaps ne sont pas détruits ; l’application doit détruire les.  
  
 Le Windows `GetMenuCheckMarkDimensions` fonction récupère les dimensions de la case à cocher par défaut utilisé pour les éléments de menu. L’application utilise ces valeurs pour déterminer la taille appropriée pour les bitmaps fournis avec cette fonction. Obtenir la taille, créer vos images bitmap, puis de les définir.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]  
  
##  <a name="setmenuiteminfo"></a>  CMenu::SetMenuItemInfo  
 Modifie les informations sur un élément de menu.  
  
```  
BOOL SetMenuItemInfo(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 *uItem*  
 Consultez la description de *uItem* dans [SetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-setmenuiteminfoa) dans le SDK Windows.  
  
 *lpMenuItemInfo*  
 Consultez la description de *lpmii* dans `SetMenuItemInfo` dans le SDK Windows.  
  
 *fByPos*  
 Consultez la description de *fByPosition* dans `SetMenuItemInfo` dans le SDK Windows.  
  
### <a name="remarks"></a>Notes  
 Cette fonction encapsule [SetMenuItemInfo](/windows/desktop/api/winuser/nf-winuser-setmenuiteminfoa), comme décrit dans le SDK Windows.  
  
##  <a name="trackpopupmenu"></a>  CMenu::TrackPopupMenu  
 Affiche un menu contextuel flottante à l’emplacement spécifié et effectue le suivi de la sélection des éléments dans le menu contextuel.  
  
```  
BOOL TrackPopupMenu(
    UINT nFlags,  
    int x,  
    int y,  
    CWnd* pWnd,  
    LPCRECT lpRect = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIndicateurs*  
 Spécifie les indicateurs de position à l’écran et la position de la souris. Consultez [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) pour obtenir la liste des indicateurs disponibles.  
  
 *x*  
 Spécifie la position horizontale, en coordonnées d’écran du menu contextuel. Selon la valeur de la *nIndicateurs* paramètre, le menu peut être aligné à gauche, aligné à droite ou centré par rapport à cette position.  
  
 *y*  
 Spécifie la position verticale, en coordonnées d’écran du haut du menu sur l’écran.  
  
 *pWnd*  
 Identifie la fenêtre propriétaire de la liste déroulante. Ce paramètre ne peut pas être NULL, même si l’indicateur TPM_NONOTIFY est spécifié. Cette fenêtre reçoit tous les messages WM_COMMAND à partir du menu. Dans Windows 3.1 et versions ultérieures, la fenêtre ne reçoit pas de messages WM_COMMAND jusqu'à ce que `TrackPopupMenu` retourne. Dans Windows 3.0, la fenêtre reçoit des messages WM_COMMAND avant `TrackPopupMenu` retourne.  
  
 *lpRect*  
 Ignoré.  
  
### <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne le résultat de l’appel [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) dans le SDK Windows.  
  
### <a name="remarks"></a>Notes  
 Un menu contextuel flottante peut apparaître n’importe où sur l’écran.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]  
  
##  <a name="trackpopupmenuex"></a>  CMenu::TrackPopupMenuEx  
 Affiche un menu contextuel flottante à l’emplacement spécifié et effectue le suivi de la sélection des éléments dans le menu contextuel.  
  
```  
BOOL TrackPopupMenuEx(
    UINT fuFlags,  
    int x,  
    int y,  
    CWnd* pWnd,  
    LPTPMPARAMS lptpm);
```  
  
### <a name="parameters"></a>Paramètres  
 *fuFlags*  
 Spécifie les diverses fonctions de menu étendu. Pour obtenir la liste de toutes les valeurs et leur signification, consultez [TrackPopupMenuEx du fait](/windows/desktop/api/winuser/nf-winuser-trackpopupmenuex).  
  
 *x*  
 Spécifie la position horizontale, en coordonnées d’écran du menu contextuel.  
  
 *y*  
 Spécifie la position verticale, en coordonnées d’écran du haut du menu sur l’écran.  
  
 *pWnd*  
 Pointeur vers la fenêtre propriétaire de la liste déroulante et la réception des messages à partir du menu créé. Cette fenêtre peut être n’importe quelle fenêtre à partir de l’application actuelle mais ne peut pas être NULL. Si vous spécifiez TPM_NONOTIFY dans le *fuFlags* paramètre, la fonction n’envoie pas de tous les messages à *pWnd*. La fonction doit retourner pour la fenêtre vers laquelle pointée *pWnd* pour recevoir le message WM_COMMAND.  
  
 *lptpm*  
 Pointeur vers un [TPMPARAMS](/windows/desktop/api/winuser/ns-winuser-tagtpmparams) structure qui spécifie une zone de l’écran du menu ne doit pas se chevaucher. Ce paramètre peut être NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Si vous spécifiez TPM_RETURNCMD dans le *fuFlags* paramètre, la valeur de retour est l’identificateur d’élément de menu de l’élément sélectionné par l’utilisateur. Si l’utilisateur annule le menu sans effectuer de sélection, ou si une erreur se produit, la valeur de retour est 0.  
  
 Si vous ne spécifiez pas TPM_RETURNCMD dans le *fuFlags* paramètre, la valeur de retour est différent de zéro si la fonction réussit et 0 en cas d’échec. Pour obtenir les informations d’erreur étendues, appelez [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Notes  
 Un menu contextuel flottante peut apparaître n’importe où sur l’écran. Pour plus d’informations sur la gestion des erreurs lors de la création du menu contextuel, consultez [TrackPopupMenuEx du fait](/windows/desktop/api/winuser/nf-winuser-trackpopupmenuex).  
  
## <a name="see-also"></a>Voir aussi  
 [CTRLTEST MFC, exemple](../../visual-cpp-samples.md)   
 [Exemple MFC DYNAMENU](../../visual-cpp-samples.md)   
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CObject, classe](../../mfc/reference/cobject-class.md)
