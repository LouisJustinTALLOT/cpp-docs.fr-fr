---
title: CMenu (classe) | Documents Microsoft
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
ms.openlocfilehash: ab829aeae9858fda830ebf2f15823c4e9c3c2f1c
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039295"
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
|[CMenu::CheckMenuItem](#checkmenuitem)|Place une coche à côté, ou supprime une coche à partir d’un élément de menu dans le menu contextuel.|  
|[CMenu::CheckMenuRadioItem](#checkmenuradioitem)|Place un bouton radio en regard d’un élément de menu et supprime tous les autres éléments de menu dans le groupe de la case d’option.|  
|[CMenu::CreateMenu](#createmenu)|Crée un menu vide et l’attache à un `CMenu` objet.|  
|[CMenu::CreatePopupMenu](#createpopupmenu)|Crée un menu contextuel vide et l’attache à un `CMenu` objet.|  
|[CMenu::DeleteMenu](#deletemenu)|Supprime un élément spécifié à partir du menu. Si l’élément de menu possède un menu contextuel associé, détruit le handle pour le menu contextuel et libère la mémoire utilisée par celui-ci.|  
|[CMenu::DeleteTempMap](#deletetempmap)|Supprime tout temporaire `CMenu` les objets créés par le `FromHandle` fonction membre.|  
|[CMenu::DestroyMenu](#destroymenu)|Supprime le menu attaché à un `CMenu` de l’objet et libère la mémoire occupée par le menu.|  
|[CMenu::Detach](#detach)|Détache un handle de menu Windows d’un `CMenu` de l’objet et retourne le handle.|  
|[CMenu::DrawItem](#drawitem)|Appelé par le framework lorsqu’un aspect visuel d’une modification de menu owner-drawn.|  
|[CMenu::EnableMenuItem](#enablemenuitem)|Active, désactive ou estompe (gris) un élément de menu.|  
|[CMenu::FromHandle](#fromhandle)|Retourne un pointeur vers un `CMenu` objet un handle de menu Windows.|  
|[CMenu::GetDefaultItem](#getdefaultitem)|Détermine l’élément de menu par défaut dans le menu spécifié.|  
|[CMenu::GetMenuContextHelpId](#getmenucontexthelpid)|Récupère l’ID de contexte d’aide associé au menu.|  
|[CMenu::GetMenuInfo](#getmenuinfo)|Récupère des informations sur un menu spécifique.|  
|[CMenu::GetMenuItemCount](#getmenuitemcount)|Détermine le nombre d’éléments dans un menu contextuel ou de niveau supérieur.|  
|[CMenu::GetMenuItemID](#getmenuitemid)|Obtient l’identificateur de l’élément de menu pour un élément de menu situé à la position spécifiée.|  
|[CMenu::GetMenuItemInfo](#getmenuiteminfo)|Récupère des informations sur un élément de menu.|  
|[CMenu::GetMenuState](#getmenustate)|Retourne l’état de l’élément de menu spécifié ou le nombre d’éléments dans un menu contextuel.|  
|[CMenu::GetMenuString](#getmenustring)|Récupère l’étiquette de l’élément de menu spécifié.|  
|[CMenu::GetSafeHmenu](#getsafehmenu)|Retourne le `m_hMenu` encapsulé par `CMenu` objet.|  
|[CMenu::GetSubMenu](#getsubmenu)|Récupère un pointeur vers un menu contextuel.|  
|[CMenu::InsertMenu](#insertmenu)|Insère un nouvel élément de menu à la position spécifiée, déplacement d’autres éléments du menu déroulant.|  
|[CMenu::InsertMenuItem](#insertmenuitem)|Insère un nouvel élément de menu à la position spécifiée dans un menu.|  
|[CMenu::LoadMenu](#loadmenu)|Charge une ressource de menu à partir du fichier exécutable et l’attache à un `CMenu` objet.|  
|[CMenu::LoadMenuIndirect](#loadmenuindirect)|Charge un menu à partir d’un modèle de menu dans la mémoire et l’attache à un `CMenu` objet.|  
|[CMenu::MeasureItem](#measureitem)|Appelé par l’infrastructure pour déterminer les dimensions de menu lors de la création d’un menu owner-drawn.|  
|[CMenu::ModifyMenu](#modifymenu)|Modifie un élément de menu existant à la position spécifiée.|  
|[CMenu::RemoveMenu](#removemenu)|Supprime un élément de menu avec un menu contextuel dans le menu spécifié.|  
|[CMenu::SetDefaultItem](#setdefaultitem)|Définit l’élément de menu par défaut pour le menu spécifié.|  
|[CMenu::SetMenuContextHelpId](#setmenucontexthelpid)|Définit l’ID de contexte d’aide à associer à l’aide du menu.|  
|[CMenu::SetMenuInfo](#setmenuinfo)|Définit les informations dans un menu spécifique.|  
|[CMenu::SetMenuItemBitmaps](#setmenuitembitmaps)|Associe les images bitmap de coche spécifié à un élément de menu.|  
|[CMenu::SetMenuItemInfo](#setmenuiteminfo)|Modifie les informations relatives à un élément de menu.|  
|[CMenu::TrackPopupMenu](#trackpopupmenu)|Affiche un menu contextuel flottant à l’emplacement spécifié et effectue le suivi de la sélection d’éléments dans le menu contextuel.|  
|[CMenu::TrackPopupMenuEx](#trackpopupmenuex)|Affiche un menu contextuel flottant à l’emplacement spécifié et effectue le suivi de la sélection d’éléments dans le menu contextuel.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMenu::operator HMENU](#operator_hmenu)|Récupère le handle de l’objet menu.|  
|[CMenu::operator ! =](#operator_neq)|Détermine si deux objets de menu ne sont pas égales.|  
|[CMenu::operator ==](#operator_eq_eq)|Détermine si deux objets de menu sont égaux.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMenu::m_hMenu](#m_hmenu)|Spécifie le handle vers le menu Windows attaché à la `CMenu` objet.|  
  
## <a name="remarks"></a>Notes  
 Il fournit des fonctions membres pour créer, de suivi, la mise à jour et la destruction d’un menu.  
  
 Créer un `CMenu` objet sur le frame de pile comme local, puis appelez `CMenu`de fonctions de membre pour manipuler le nouveau menu, en fonction des besoins. Ensuite, appelez [CWnd::SetMenu](../../mfc/reference/cwnd-class.md#setmenu) pour définir le menu à une fenêtre, suivi immédiatement par un appel à la `CMenu` l’objet [détachement](#detach) fonction membre. Le `CWnd::SetMenu` fonction membre définit le menu fenêtre pour le nouveau menu, la fenêtre à être redessiné pour refléter la modification de menu et le passe également la propriété du menu dans la fenêtre. L’appel à `Detach` détache le `HMENU` à partir de la `CMenu` de l’objet, ainsi que quand local `CMenu` variable passe hors de portée, le `CMenu` destructeur d’objet ne tente pas détruire un menu, il ne possède plus. Le menu en question est automatiquement détruit lorsque la fenêtre est détruite.  
  
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
 Spécifie des informations sur l’état du nouvel élément de menu lorsqu’il est ajouté au menu. Il se compose d’un ou plusieurs des valeurs répertoriées dans la section Notes.  
  
 *nIDNewItem*  
 Spécifie l’ID de commande du nouvel élément de menu ou, si *nIndicateurs* a la valeur **MF_POPUP**, le handle de menu ( `HMENU`) d’un menu contextuel. Le *nIDNewItem* paramètre est ignoré (non nécessaire) si *nIndicateurs* a la valeur **MF_SEPARATOR**.  
  
 *lpszNewItem*  
 Spécifie le contenu du nouvel élément de menu. Le *nIndicateurs* paramètre est utilisé pour interpréter *lpszNewItem* de la façon suivante :  
  
|nIndicateurs|Interprétation de lpszNewItem|  
|------------|-----------------------------------|  
|`MF_OWNERDRAW`|Contient une valeur de 32 bits fournie par l’application que l’application peut utiliser pour mettre à jour les données supplémentaires associées à l’élément de menu. Cette valeur de 32 bits est disponible à l’application lors du traitement de `WM_MEASUREITEM` et `WM_DRAWITEM` messages. La valeur est stockée dans le **itemData** membre de la structure fournie avec ces messages.|  
|`MF_STRING`|Contient un pointeur vers une chaîne se terminant par null. Il s’agit de l’interprétation par défaut.|  
|`MF_SEPARATOR`|Le *lpszNewItem* paramètre est ignoré (ne pas nécessaire).|  
  
 *pBmp*  
 Pointe vers un `CBitmap` objet qui sera utilisé en tant que l’élément de menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’application peut spécifier l’état de l’élément de menu en définissant les valeurs de *nIndicateurs*. Lorsque *nIDNewItem* spécifie un menu contextuel, il devient partie intégrante du menu auquel il est ajouté. Si ce menu est détruit, le menu ajouté sera également détruit. Un menu ajouté doit être détaché d’un `CMenu` objet pour éviter tout conflit. Notez que **MF_STRING** et `MF_OWNERDRAW` ne sont pas valides pour la version de l’image bitmap de `AppendMenu`.  
  
 La liste suivante décrit les indicateurs qui peuvent être définis dans *nIndicateurs*:  
  
- **MF_CHECKED** agit comme un bouton bascule avec **MF_UNCHECKED** pour placer la case à cocher en regard de l’élément par défaut. Lorsque l’application fournit des images bitmap de coche (consultez la [SetMenuItemBitmaps](#setmenuitembitmaps) fonction membre), l’image de la case à cocher « sur » s’affiche.  
  
- **MF_UNCHECKED** agit comme un bouton bascule avec **MF_CHECKED** pour supprimer une case à cocher en regard de l’élément. Lorsque l’application fournit des images bitmap de coche (consultez la `SetMenuItemBitmaps` fonction membre), l’image de la case à cocher « désactivé » s’affiche.  
  
- **MF_DISABLED** désactive l’élément de menu afin qu’il ne peut pas être sélectionné, mais n’est pas estomper.  
  
- **MF_ENABLED** permet à l’élément de menu pour qu’il peut être sélectionné et le restaure à partir de son état estompé.  
  
- **MF_GRAYED** désactive l’élément de menu pour qu’il ne peut pas être sélectionné et il estompe.  
  
- **MF_MENUBARBREAK** place l’élément sur une nouvelle ligne dans les menus statiques ou dans une nouvelle colonne dans les menus contextuels. La nouvelle colonne de menu contextuel doivent être séparée de l’ancienne par une ligne de séparation verticale.  
  
- **MF_MENUBREAK** place l’élément sur une nouvelle ligne dans les menus statiques ou dans une nouvelle colonne dans les menus contextuels. Aucune ligne de démarcation n’est placé entre les colonnes.  
  
- **MF_OWNERDRAW** Spécifie que l’élément est un élément en mode owner-draw. Lorsque le menu s’affiche pour la première fois, la fenêtre qui détient le menu reçoit un message WM_MEASUREITEM, qui Récupère la hauteur et la largeur de l’élément de menu. Le message WM_DRAWITEM est celui envoyé chaque fois que le propriétaire doit mettre à jour l’apparence visuelle de l’élément de menu. Cette option n’est pas valide pour un élément de menu de niveau supérieur.  
  
- **MF_POPUP** Spécifie qu’un menu contextuel associé à l’élément de menu. Le paramètre ID spécifie un handle d’un menu contextuel qui doit être associé à l’élément. Cela est utilisé pour l’ajout d’un menu contextuel de niveau supérieur ou d’un menu contextuel hiérarchique à un élément de menu contextuel.  
  
- **MF_SEPARATOR** Dessine une ligne de démarcation horizontale. Peut uniquement être utilisé dans un menu contextuel. Cette ligne ne peut pas être estompée, désactivée ou mis en surbrillance. Autres paramètres sont ignorés.  
  
- **MF_STRING** Spécifie que l’élément de menu est une chaîne de caractères.  
  
 Chacun des groupes suivants répertorie les indicateurs qui s’excluent mutuellement et ne peuvent pas être utilisées ensemble :  
  
- **MF_DISABLED**, **MF_ENABLED**, et **MF_GRAYED**  
  
- **MF_STRING**, **MF_OWNERDRAW**, **MF_SEPARATOR**et la version de l’image bitmap  
  
- **MF_MENUBARBREAK** et **MF_MENUBREAK**  
  
- **MF_CHECKED** et **MF_UNCHECKED**  
  
 Chaque fois qu’un menu qui réside dans une fenêtre est modifiée (ou non la fenêtre s’affiche), l’application doit appeler [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::CreateMenu](#createmenu).  
  
##  <a name="attach"></a>  CMenu::Attach  
 Attache un menu Windows existant à un `CMenu` objet.  
  
```  
BOOL Attach(HMENU hMenu);
```  
  
### <a name="parameters"></a>Paramètres  
 *hMenu*  
 Spécifie un handle à un menu Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’opération a réussi ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction ne doit pas être appelée si un menu est déjà attaché à la `CMenu` objet. Le handle de menu est stocké dans le `m_hMenu` membre de données.  
  
 Si le menu que vous souhaitez manipuler est déjà associé à une fenêtre, vous pouvez utiliser la [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu) fonction permettant d’obtenir un handle vers le menu.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="checkmenuitem"></a>  CMenu::CheckMenuItem  
 Ajoute des coches à ou supprime des cases à cocher des éléments de menu dans le menu contextuel.  
  
```  
UINT CheckMenuItem(
    UINT nIDCheckItem,  
    UINT nCheck);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIDCheckItem*  
 Spécifie l’élément de menu doit être vérifiée, comme déterminé par *nVérifiez*.  
  
 *nVérifiez*  
 Spécifie la vérification de l’élément de menu et comment déterminer la position de l’élément dans le menu. Le *nVérifiez* paramètre peut être une combinaison de **MF_CHECKED** ou **MF_UNCHECKED** avec **MF_BYPOSITION** ou **MF_ BYCOMMAND** indicateurs. Ces indicateurs peuvent être combinées à l’aide de l’opérateur OR au niveau du bit. Ils ont les significations suivantes :  
  
- **MF_BYCOMMAND** Spécifie que le paramètre indique l’ID de commande de l’élément de menu existant. Il s'agit de la valeur par défaut.  
  
- **MF_BYPOSITION** Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.  
  
- **MF_CHECKED** agit comme un bouton bascule avec **MF_UNCHECKED** pour placer la case à cocher en regard de l’élément par défaut.  
  
- **MF_UNCHECKED** agit comme un bouton bascule avec **MF_CHECKED** pour supprimer une case à cocher en regard de l’élément.  
  
### <a name="return-value"></a>Valeur de retour  
 L’état précédent de l’élément : **MF_CHECKED** ou **MF_UNCHECKED**, ou 0xFFFFFFFF si l’élément de menu n’existe pas.  
  
### <a name="remarks"></a>Notes  
 Le *nIDCheckItem* paramètre spécifie l’élément à modifier.  
  
 Le *nIDCheckItem* paramètre peut identifier un élément de menu contextuel ainsi que d’un élément de menu. Aucune des étapes spéciales ne sont requises pour rechercher un élément de menu contextuel. Les éléments de menu de niveau supérieur ne peut pas être vérifiées. Un élément de menu contextuel doit être vérifié par position, car il n’a pas un identificateur d’élément de menu associé.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::GetMenuState](#getmenustate).  
  
##  <a name="checkmenuradioitem"></a>  CMenu::CheckMenuRadioItem  
 Vérifie un élément de menu spécifié et en fait un élément de case d’option.  
  
```  
BOOL CheckMenuRadioItem(
    UINT nIDFirst,  
    UINT nIDLast,  
    UINT nIDItem,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIDFirst*  
 Spécifie (en tant qu’un ID ou un décalage, en fonction de la valeur de *nIndicateurs*) le premier élément de menu dans le groupe de cases d’option.  
  
 *nIDLast*  
 Spécifie (en tant qu’un ID ou un décalage, en fonction de la valeur de *nIndicateurs*) du dernier élément de menu dans le groupe de cases d’option.  
  
 *nIDItem*  
 Spécifie (en tant qu’un ID ou un décalage, en fonction de la valeur de *nIndicateurs*) l’élément dans le groupe qui sera vérifié avec une case d’option.  
  
 *nIndicateurs*  
 Spécifie l’interprétation de *nIDFirst*, *nIDLast*, et *nIDItem* de la façon suivante :  
  
|nIndicateurs|Interprétation|  
|------------|--------------------|  
|**MF_BYCOMMAND**|Spécifie que le paramètre indique l’ID de commande de l’élément de menu existant. Ceci est la valeur par défaut si aucune **MF_BYCOMMAND** ni **MF_BYPOSITION** est défini.|  
|**MF_BYPOSITION**|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’opération a réussi ; Sinon, 0  
  
### <a name="remarks"></a>Notes  
 En même temps, la fonction désactive tous les autres éléments de menu dans le groupe associé et efface l’indicateur de type d’élément de case d’option correspondant à ces éléments. Les éléments cochés s’affiche à l’aide d’un bitmap de cases d’option bouton (ou puce) au lieu d’une image bitmap de coche.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [ON_COMMAND_RANGE](message-map-macros-mfc.md#on_command_range).  
  
##  <a name="cmenu"></a>  CMenu::CMenu  
 Crée un menu vide et l’attache à un `CMenu` objet.  
  
```  
CMenu();
```  
  
### <a name="remarks"></a>Notes  
 Le menu n’est pas créé tant que vous appelez l’une des fonctions membres create ou charge de **CMenu :**  
  
- [CreateMenu](#createmenu)  
  
- [CreatePopupMenu](#createpopupmenu)  
  
- [LoadMenu](#loadmenu)  
  
- [LoadMenuIndirect](#loadmenuindirect)  
  
- [Attacher](#attach)  
  
##  <a name="createmenu"></a>  CMenu::CreateMenu  
 Crée un menu et l’attache à le `CMenu` objet.  
  
```  
BOOL CreateMenu();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le menu a été créé avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le menu est initialement vide. Éléments de menu peuvent être ajoutés à l’aide de la `AppendMenu` ou `InsertMenu` fonction membre.  
  
 Si le menu est assigné à une fenêtre, il est automatiquement détruit la fenêtre est détruite.  
  
 Avant de quitter, l’application doit libérer les ressources système associées à un menu si le menu n’est pas assigné à une fenêtre. Une application libère un menu en appelant le [DestroyMenu](#destroymenu) fonction membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#22](../../mfc/reference/codesnippet/cpp/cmenu-class_2.cpp)]  
  
##  <a name="createpopupmenu"></a>  CMenu::CreatePopupMenu  
 Crée un menu contextuel et l’attache à le `CMenu` objet.  
  
```  
BOOL CreatePopupMenu();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le menu contextuel a été créé avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le menu est initialement vide. Éléments de menu peuvent être ajoutés à l’aide de la `AppendMenu` ou `InsertMenu` fonction membre. L’application peut ajouter le menu contextuel à un menu existant ou un menu contextuel. Le `TrackPopupMenu` fonction membre peut être utilisée pour afficher ce menu comme un menu contextuel flottant et pour effectuer le suivi des sélections dans le menu contextuel.  
  
 Si le menu est assigné à une fenêtre, il est automatiquement détruit la fenêtre est détruite. Si le menu est ajouté à un menu existant, il est automatiquement détruite lorsque ce menu est détruit.  
  
 Avant de quitter, l’application doit libérer les ressources système associées à un menu contextuel si le menu n’est pas assigné à une fenêtre. Une application libère un menu en appelant le [DestroyMenu](#destroymenu) fonction membre.  
  
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
 Utilisé pour interpréter *nPosition* de la façon suivante :  
  
|nIndicateurs|Interprétation de nPosition|  
|------------|---------------------------------|  
|**MF_BYCOMMAND**|Spécifie que le paramètre indique l’ID de commande de l’élément de menu existant. Ceci est la valeur par défaut si aucune **MF_BYCOMMAND** ni **MF_BYPOSITION** est défini.|  
|**MF_BYPOSITION**|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si l’élément de menu possède un menu contextuel associé, `DeleteMenu` détruit le handle pour le menu contextuel et libère la mémoire utilisée par le menu contextuel.  
  
 Chaque fois qu’un menu qui réside dans une fenêtre est modifiée (ou non la fenêtre s’affiche), l’application doit appeler [CWnd::DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).  
  
##  <a name="deletetempmap"></a>  CMenu::DeleteTempMap  
 Appelé automatiquement par le `CWinApp` Gestionnaire de durée d’inactivité, supprime toute temporaire `CMenu` les objets créés par le [FromHandle](#fromhandle) fonction membre.  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>Notes  
 `DeleteTempMap` Détache l’objet de menu Windows attachée à une valeur temporaire `CMenu` objet avant de supprimer le `CMenu` objet.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#23](../../mfc/reference/codesnippet/cpp/cmenu-class_3.cpp)]  
  
##  <a name="destroymenu"></a>  CMenu::DestroyMenu  
 Détruit le menu et toutes les ressources de Windows qui ont été utilisés.  
  
```  
BOOL DestroyMenu();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le menu est détruit ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le menu est détaché de la `CMenu` de l’objet avant d’être détruit. Les fenêtres `DestroyMenu` fonction est appelée automatiquement dans le `CMenu` destructeur.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::CreateMenu](#createmenu).  
  
##  <a name="detach"></a>  CMenu::Detach  
 Détache un menu Windows un `CMenu` de l’objet et retourne le handle.  
  
```  
HMENU Detach();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle, de type `HMENU`, à un menu Windows, en cas de réussite ; **NULL**.  
  
### <a name="remarks"></a>Notes  
 Le `m_hMenu` membre de données est défini **NULL**.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#21](../../mfc/reference/codesnippet/cpp/cmenu-class_1.cpp)]  
  
##  <a name="drawitem"></a>  CMenu::DrawItem  
 Appelé par le framework lorsqu’un aspect visuel d’une modification de menu owner-drawn.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpDrawItemStruct*  
 Un pointeur vers un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) structure qui contient des informations sur le type de dessin nécessaire.  
  
### <a name="remarks"></a>Notes  
 Le `itemAction` membre de la `DRAWITEMSTRUCT` structure définit l’action de dessin qui doit être effectuée. Remplacez cette fonction membre pour implémenter le dessin pour un mode owner-draw `CMenu` objet. L’application doit restaurer tous les objets interface GDI périphérique graphique sélectionnés pour le contexte d’affichage fournie dans *lpDrawItemStruct* avant l’arrêt de cette fonction membre.  
  
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
 Spécifie l’action à entreprendre. Il peut être une combinaison de **MF_DISABLED**, **MF_ENABLED**, ou **MF_GRAYED**, avec **MF_BYCOMMAND** ou **MF_BYPOSITION** . Ces valeurs peuvent être combinées à l’aide de l’opérateur OR au niveau du bit. Ces valeurs ont les significations suivantes :  
  
- **MF_BYCOMMAND** Spécifie que le paramètre indique l’ID de commande de l’élément de menu existant. Il s'agit de la valeur par défaut.  
  
- **MF_BYPOSITION** Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.  
  
- **MF_DISABLED** désactive l’élément de menu afin qu’il ne peut pas être sélectionné, mais n’est pas estomper.  
  
- **MF_ENABLED** permet à l’élément de menu pour qu’il peut être sélectionné et le restaure à partir de son état estompé.  
  
- **MF_GRAYED** désactive l’élément de menu pour qu’il ne peut pas être sélectionné et il estompe.  
  
### <a name="return-value"></a>Valeur de retour  
 État précédent ( **MF_DISABLED**, **MF_ENABLED**, ou **MF_GRAYED**) ou -1 si elle est non valide.  
  
### <a name="remarks"></a>Notes  
 Le [CreateMenu](#createmenu), [InsertMenu](#insertmenu), [ModifyMenu](#modifymenu), et [LoadMenuIndirect](#loadmenuindirect) fonctions membres peuvent également définir l’état (activé, désactivé ou grisé) d’un élément de menu.  
  
 À l’aide de la **MF_BYPOSITION** valeur requiert une application pour utiliser le bon `CMenu`. Si le `CMenu` du menu barre est utilisée, un élément de menu de niveau supérieur (il s’agit d’un élément dans la barre de menus) est affecté. Pour définir l’état d’un élément dans un menu contextuel ou imbriqué par position, une application doit spécifier le `CMenu` du menu contextuel.  
  
 Lorsqu’une application spécifie la **MF_BYCOMMAND** indicateur, Windows vérifie tous les éléments de menu contextuel qui dépendent de la `CMenu`; par conséquent, sauf si les éléments de menu en double sont présentes, à l’aide la `CMenu` du menu barre est suffisant.  
  
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
 Si un `CMenu` objet n’est pas déjà attaché à l’objet menu Windows, une valeur temporaire `CMenu` objet est créé et attaché.  
  
 Ce fichier temporaire `CMenu` objet est uniquement valide jusqu'à la prochaine fois que l’application a des temps d’inactivité dans sa boucle d’événements, auquel cas tous les objets temporaires sont supprimés.  
  
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
 Valeur qui spécifie la façon dont la fonction de recherche des éléments de menu. Ce paramètre peut être none, une ou une combinaison des valeurs suivantes :  
  
|Value|Signification|  
|-----------|-------------|  
|**GMDI_GOINTOPOPUPS**|Spécifie que, si la valeur par défaut est un élément qui ouvre un sous-menu, la fonction à rechercher dans le sous-menu correspondant de manière récursive. Si le sous-menu a pas de valeur par défaut, la valeur de retour identifie l’élément qui ouvre le sous-menu.<br /><br /> Par défaut, la fonction retourne le premier élément de la valeur par défaut dans le menu spécifié, qu’il s’agisse d’un élément qui ouvre un sous-menu.|  
|**GMDI_USEDISABLED**|Spécifie que la fonction doit renvoyer un élément par défaut, même si elle est désactivée.<br /><br /> Par défaut, la fonction ignore les éléments désactivées et grisées.|  
  
 *fByPos*  
 Valeur qui spécifie s’il faut récupérer l’identificateur de l’élément de menu ou de sa position. Si ce paramètre est **FALSE**, l’identificateur est retourné. Dans le cas contraire, la position est retournée.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, la valeur de retour est l’identificateur ou la position de l’élément de menu. Si la fonction échoue, la valeur de retour est - 1.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la fonction Win32 [GetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647976), comme décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="getmenucontexthelpid"></a>  CMenu::GetMenuContextHelpId  
 Récupère l’aide du contexte associé à un ID `CMenu`.  
  
```  
DWORD GetMenuContextHelpId() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’aide contextuelle ID associé actuellement `CMenu` le cas échéant ; sinon, de zéro.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="getmenuinfo"></a>  CMenu::GetMenuInfo  
 Récupère les informations pour un menu.  
  
```  
BOOL GetMenuInfo(LPMENUINFO lpcmi) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *lpcmi*  
 Un pointeur vers un [MENUINFO](http://msdn.microsoft.com/library/windows/desktop/ms647575) structure contenant des informations pour le menu.  
  
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
 Le nombre d’éléments dans le menu si la fonction réussit ; Sinon,-1.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CWnd::GetMenu](../../mfc/reference/cwnd-class.md#getmenu).  
  
##  <a name="getmenuitemid"></a>  CMenu::GetMenuItemID  
 Obtient l’identificateur de l’élément de menu pour un élément de menu situé à l’emplacement défini par *nPos*.  
  
```  
UINT GetMenuItemID(int nPos) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nPos*  
 Spécifie la position (base zéro) de l’élément de menu dont l’ID est en cours de récupération.  
  
### <a name="return-value"></a>Valeur de retour  
 L’ID d’élément pour l’élément spécifié dans un menu contextuel si la fonction réussit. Si l’élément spécifié est un menu déroulant (par opposition à un élément dans le menu contextuel), la valeur de retour est -1. Si *nPos* correspond à un **séparateur** élément de menu, la valeur de retour est 0.  
  
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
 Un pointeur vers un [MENUITEMINFO](http://msdn.microsoft.com/library/windows/desktop/ms647578), comme décrit dans le Kit de développement logiciel Windows, qui contient des informations sur le menu.  
  
 *fByPos*  
 Valeur spécifiant la signification de `nIDItem`. Par défaut, `ByPos` est **FALSE**, ce qui signifie qu’uItem est un identificateur d’élément de menu. Si `ByPos` n’est pas définie **FALSE**, il indique la position d’un élément de menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, la valeur de retour est différente de zéro. Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations d’erreur plus complètes, utilisez la fonction Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360), comme décrit dans le Kit de développement logiciel Windows.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la de la fonction Win32 [GetMenuItemInfo](http://msdn.microsoft.com/library/windows/desktop/ms647980), comme décrit dans le Kit de développement logiciel Windows. Notez que dans l’implémentation MFC de `GetMenuItemInfo`, vous n’utilisez pas un handle à un menu.  
  
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
  
- **MF_BYCOMMAND** Spécifie que le paramètre indique l’ID de commande de l’élément de menu existant. Il s'agit de la valeur par défaut.  
  
- **MF_BYPOSITION** Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur 0xFFFFFFFF si l’élément spécifié n’existe pas. Si *nId* identifie un menu contextuel, l’octet de poids fort contient le nombre d’éléments dans le menu contextuel et l’octet de poids faible contient les indicateurs de menu associés à la liste déroulante. Sinon, la valeur de retour est un masque (ou booléenne) des valeurs dans la liste suivante (ce masque décrit l’état du menu élément *nId* identifie) :  
  
- **MF_CHECKED** agit comme un bouton bascule avec **MF_UNCHECKED** pour placer la case à cocher en regard de l’élément par défaut. Lorsque l’application fournit des images bitmap de coche (consultez la `SetMenuItemBitmaps` fonction membre), l’image de la case à cocher « sur » s’affiche.  
  
- **MF_DISABLED** désactive l’élément de menu afin qu’il ne peut pas être sélectionné, mais n’est pas estomper.  
  
- **MF_ENABLED** permet à l’élément de menu pour qu’il peut être sélectionné et le restaure à partir de son état estompé. Notez que la valeur de cette constante est 0 ; une application doit tester pas 0 pour un échec lors de l’utilisation de cette valeur.  
  
- **MF_GRAYED** désactive l’élément de menu pour qu’il ne peut pas être sélectionné et il estompe.  
  
- **MF_MENUBARBREAK** place l’élément sur une nouvelle ligne dans les menus statiques ou dans une nouvelle colonne dans les menus contextuels. La nouvelle colonne de menu contextuel doivent être séparée de l’ancienne par une ligne de séparation verticale.  
  
- **MF_MENUBREAK** place l’élément sur une nouvelle ligne dans les menus statiques ou dans une nouvelle colonne dans les menus contextuels. Aucune ligne de démarcation n’est placé entre les colonnes.  
  
- **MF_SEPARATOR** Dessine une ligne de démarcation horizontale. Peut uniquement être utilisé dans un menu contextuel. Cette ligne ne peut pas être estompée, désactivée ou mis en surbrillance. Autres paramètres sont ignorés.  
  
- **MF_UNCHECKED** agit comme un bouton bascule avec **MF_CHECKED** pour supprimer une case à cocher en regard de l’élément. Lorsque l’application fournit des images bitmap de coche (consultez la `SetMenuItemBitmaps` fonction membre), l’image de la case à cocher « désactivé » s’affiche. Notez que la valeur de cette constante est 0 ; une application doit tester pas 0 pour un échec lors de l’utilisation de cette valeur.  
  
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
 Spécifie l’identificateur entier de l’élément de menu ou le décalage de l’élément de menu dans le menu, selon la valeur de *nIndicateurs*.  
  
 *lpString*  
 Pointe vers la mémoire tampon qui reçoit l’étiquette.  
  
 *rString*  
 Une référence à un `CString` objet qui doit recevoir la chaîne copiée de menu.  
  
 *nMaxCount*  
 Spécifie la longueur maximale (en caractères) de l’étiquette doit être copié. Si l’étiquette est plus longue que le maximum spécifié dans *nMaxCount*, les caractères supplémentaires sont tronqués.  
  
 *nIndicateurs*  
 Spécifie l’interprétation de la *nIDItem* paramètre. Il peut prendre l’une des valeurs suivantes :  
  
|nIndicateurs|Interprétation de nIDItem|  
|------------|-------------------------------|  
|**MF_BYCOMMAND**|Spécifie que le paramètre indique l’ID de commande de l’élément de menu existant. Ceci est la valeur par défaut si aucune **MF_BYCOMMAND** ni **MF_BYPOSITION** est défini.|  
|**MF_BYPOSITION**|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|  
  
### <a name="return-value"></a>Valeur de retour  
 Spécifie le nombre réel de caractères copiés dans la mémoire tampon, non compris le terminateur null.  
  
### <a name="remarks"></a>Notes  
 Le *nMaxCount* paramètre doit être supérieure au nombre de caractères dans l’étiquette en fonction du caractère null qui met fin à une chaîne.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="getsafehmenu"></a>  CMenu::GetSafeHmenu  
 Retourne le `HMENU` encapsulé par `CMenu` objet, ou un **NULL** `CMenu` pointeur.  
  
```  
HMENU GetSafeHmenu() const;  
```  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::LoadMenu](#loadmenu).  
  
##  <a name="getsubmenu"></a>  CMenu::GetSubMenu  
 Récupère le `CMenu` l’objet d’un menu contextuel.  
  
```  
CMenu* GetSubMenu(int nPos) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nPos*  
 Spécifie la position du menu contextuel contenu dans le menu. Valeurs de position commencent à 0 pour le premier élément de menu. Identificateur du menu contextuel ne peut pas être utilisé dans cette fonction.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `CMenu` dont l’objet `m_hMenu` membre contient un handle vers le menu contextuel si un menu contextuel existe à la position donnée ; sinon **NULL**. Si un `CMenu` objet n’existe pas, puis un objet temporaire est créé. Le `CMenu` pointeur retourné ne doit pas être stocké.  
  
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
|**MF_BYCOMMAND**|Spécifie que le paramètre indique l’ID de commande de l’élément de menu existant. Ceci est la valeur par défaut si aucune **MF_BYCOMMAND** ni **MF_BYPOSITION** est défini.|  
|**MF_BYPOSITION**|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0. Si *nPosition* est -1, le nouvel élément de menu est ajouté à la fin du menu.|  
  
 *nIndicateurs*  
 Spécifie comment *nPosition* est interprété et spécifie des informations sur l’état du nouvel élément de menu lorsqu’il est ajouté au menu. Pour obtenir la liste des indicateurs qui peuvent être définis, consultez la [AppendMenu](#appendmenu) fonction membre. Pour spécifier plusieurs valeurs, utilisez l’opérateur OR au niveau du bit pour les combiner avec le **MF_BYCOMMAND** ou **MF_BYPOSITION** indicateur.  
  
 *nIDNewItem*  
 Spécifie l’ID de commande du nouvel élément de menu ou, si *nIndicateurs* a la valeur **MF_POPUP**, le handle de menu ( `HMENU`) du menu contextuel. Le *nIDNewItem* paramètre est ignoré (non nécessaire) si *nIndicateurs* a la valeur **MF_SEPARATOR**.  
  
 *lpszNewItem*  
 Spécifie le contenu du nouvel élément de menu. *nIndicateurs* peut être utilisé pour interpréter *lpszNewItem* comme suit :  
  
|nIndicateurs|Interprétation de lpszNewItem|  
|------------|-----------------------------------|  
|**MF_OWNERDRAW**|Contient une valeur de 32 bits fournie par l’application que l’application peut utiliser pour mettre à jour les données supplémentaires associées à l’élément de menu. Cette valeur de 32 bits est disponible à l’application dans le **itemData** membre de la structure fournie par le [WM_MEASUREITEM](http://msdn.microsoft.com/library/windows/desktop/bb775925) et [WM_DRAWITEM](http://msdn.microsoft.com/library/windows/desktop/bb775923) messages. Ces messages sont envoyés lors de l’élément de menu est initialement affiché ou est modifié.|  
|**MF_STRING**|Contient un pointeur long vers une chaîne se terminant par null. Il s’agit de l’interprétation par défaut.|  
|**MF_SEPARATOR**|Le *lpszNewItem* paramètre est ignoré (ne pas nécessaire).|  
  
 *pBmp*  
 Pointe vers un `CBitmap` objet qui sera utilisé en tant que l’élément de menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’application peut spécifier l’état de l’élément de menu en définissant les valeurs de *nIndicateurs*.  
  
 Chaque fois qu’un menu qui réside dans une fenêtre est modifiée (ou non la fenêtre s’affiche), l’application doit appeler `CWnd::DrawMenuBar`.  
  
 Lorsque *nIDNewItem* spécifie un menu contextuel, il devient partie intégrante du menu dans lequel elle est insérée. Si ce menu est détruit, le menu inséré sera également détruit. Un menu inséré doit être détaché d’un `CMenu` objet pour éviter tout conflit.  
  
 Si la fenêtre interface multidocument (MDI) enfant est agrandie actif et une application insère un menu contextuel dans le menu de l’application MDI en appelant cette fonction et en spécifiant le **MF_BYPOSITION** indicateur, le menu est inséré. une position plus à gauche que prévu. Cela se produit parce que le menu de contrôle de la fenêtre enfant MDI active est inséré dans la première position de la barre de menus de la fenêtre frame MDI. Pour positionner le menu correctement, l’application doit ajouter 1 à la valeur de position qui serait utilisée sinon. Une application peut utiliser le **WM_MDIGETACTIVE** message afin de déterminer si la fenêtre enfant active est agrandie.  
  
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
 Consultez la description de *uItem* dans [InsertMenuItem](http://msdn.microsoft.com/library/windows/desktop/ms647988) dans le Kit de développement logiciel Windows.  
  
 *lpMenuItemInfo*  
 Consultez la description de *lpmii* dans **InsertMenuItem** dans le Kit de développement logiciel Windows.  
  
 *fByPos*  
 Consultez la description de *fByPosition* dans **InsertMenuItem** dans le Kit de développement logiciel Windows.  
  
### <a name="remarks"></a>Notes  
 Cette fonction encapsule [InsertMenuItem](http://msdn.microsoft.com/library/windows/desktop/ms647988), comme décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="loadmenu"></a>  CMenu::LoadMenu  
 Charge une ressource de menu à partir du fichier exécutable de l’application et l’attache à le `CMenu` objet.  
  
```  
BOOL LoadMenu(LPCTSTR lpszResourceName);  
BOOL LoadMenu(UINT nIDResource);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszResourceName*  
 Pointe vers une chaîne terminée par le caractère null qui contient le nom de la ressource de menu à charger.  
  
 *nIDResource*  
 Spécifie l’ID de menu de la ressource de menu à charger.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la ressource de menu a été chargée avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Avant de quitter, l’application doit libérer les ressources système associées à un menu si le menu n’est pas assigné à une fenêtre. Une application libère un menu en appelant le [DestroyMenu](#destroymenu) fonction membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#29](../../mfc/reference/codesnippet/cpp/cmenu-class_9.cpp)]  
  
##  <a name="loadmenuindirect"></a>  CMenu::LoadMenuIndirect  
 Charge une ressource à partir d’un modèle de menu dans la mémoire et l’attache à le `CMenu` objet.  
  
```  
BOOL LoadMenuIndirect(const void* lpMenuTemplate);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpMenuTemplate*  
 Pointe vers un modèle de menu (c'est-à-dire un seul [MENUITEMTEMPLATEHEADER](http://msdn.microsoft.com/library/windows/desktop/ms647583) structure et une collection d’un ou plusieurs [MENUITEMTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms647581) structures). Pour plus d’informations sur ces deux structures, consultez le Kit de développement logiciel Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la ressource de menu a été chargée avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Un modèle de menu est un en-tête suivi d’une collection d’un ou plusieurs [MENUITEMTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms647581) structures, chacun d’eux peut contenir un ou plusieurs éléments de menu et les menus contextuels.  
  
 Le numéro de version doit être 0.  
  
 Le **mtOption** doivent inclure des indicateurs **MF_END** pour le dernier élément dans une liste déroulante et du dernier élément dans la liste principale. Consultez le `AppendMenu` fonction membre pour les autres indicateurs. Le **mtId** membre doit être omis de la **MENUITEMTEMPLATE** lors de la structure **MF_POPUP** est spécifié dans **mtOption**.  
  
 L’espace alloué pour le **MENUITEMTEMPLATE** structure doit être suffisamment grande pour **mtString** pour contenir le nom de l’élément de menu sous forme de chaîne se terminant par null.  
  
 Avant de quitter, l’application doit libérer les ressources système associées à un menu si le menu n’est pas assigné à une fenêtre. Une application libère un menu en appelant le [DestroyMenu](#destroymenu) fonction membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#30](../../mfc/reference/codesnippet/cpp/cmenu-class_10.cpp)]  
  
##  <a name="m_hmenu"></a>  CMenu::m_hMenu  
 Spécifie le `HMENU` handle du menu Windows attachée à la `CMenu` objet.  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::LoadMenu](#loadmenu).  
  
##  <a name="measureitem"></a>  CMenu::MeasureItem  
 Appelé par l’infrastructure lors de la création d’un menu avec le style mode owner-draw.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpMeasureItemStruct*  
 Un pointeur vers un `MEASUREITEMSTRUCT` structure.  
  
### <a name="remarks"></a>Notes  
 Par défaut, cette fonction membre ne fait rien. Remplacez cette fonction membre et renseignez la `MEASUREITEMSTRUCT` structure pour informer Windows de dimensions du menu.  
  
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
|**MF_BYCOMMAND**|Spécifie que le paramètre indique l’ID de commande de l’élément de menu existant. Ceci est la valeur par défaut si aucune **MF_BYCOMMAND** ni **MF_BYPOSITION** est défini.|  
|**MF_BYPOSITION**|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|  
  
 *nIndicateurs*  
 Spécifie comment *nPosition* est interprété et fournit des informations sur les modifications à apporter à l’élément de menu. Pour obtenir la liste des indicateurs qui peuvent être définis, consultez la [AppendMenu](#appendmenu) fonction membre.  
  
 *nIDNewItem*  
 Spécifie l’ID de commande de l’élément de menu modifié ou si *nIndicateurs* a la valeur **MF_POPUP**, le handle de menu ( `HMENU`) d’un menu contextuel. Le *nIDNewItem* paramètre est ignoré (non nécessaire) si *nIndicateurs* a la valeur **MF_SEPARATOR**.  
  
 *lpszNewItem*  
 Spécifie le contenu du nouvel élément de menu. Le *nIndicateurs* paramètre peut être utilisé pour interpréter *lpszNewItem* comme suit :  
  
|nIndicateurs|Interprétation de lpszNewItem|  
|------------|-----------------------------------|  
|**MF_OWNERDRAW**|Contient une valeur de 32 bits fournie par l’application que l’application peut utiliser pour mettre à jour les données supplémentaires associées à l’élément de menu. Cette valeur de 32 bits est disponible à l’application lors du traitement de **MF_MEASUREITEM** et **MF_DRAWITEM**.|  
|**MF_STRING**|Contient un pointeur long vers une chaîne se terminant par null ou à un `CString`.|  
|**MF_SEPARATOR**|Le *lpszNewItem* paramètre est ignoré (ne pas nécessaire).|  
  
 *pBmp*  
 Pointe vers un `CBitmap` objet qui sera utilisé en tant que l’élément de menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’application spécifie le nouvel état de l’élément de menu en définissant les valeurs de *nIndicateurs*. Si cette fonction remplace un menu contextuel associé à l’élément de menu, il supprime le menu contextuel ancien et libère la mémoire utilisée par le menu contextuel.  
  
 Lorsque *nIDNewItem* spécifie un menu contextuel, il devient partie intégrante du menu dans lequel elle est insérée. Si ce menu est détruit, le menu inséré sera également détruit. Un menu inséré doit être détaché d’un `CMenu` objet pour éviter tout conflit.  
  
 Chaque fois qu’un menu qui réside dans une fenêtre est modifiée (ou non la fenêtre s’affiche), l’application doit appeler `CWnd::DrawMenuBar`. Pour modifier les attributs d’éléments de menu existant, il est beaucoup plus rapide d’utiliser le `CheckMenuItem` et `EnableMenuItem` fonctions membres.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="operator_hmenu"></a>  CMenu::operator HMENU  
 Utilisez cet opérateur pour récupérer le descripteur de la `CMenu` objet.  
  
```  
operator HMENU() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 En cas de réussite, le handle de la `CMenu` de l’objet ; sinon, **NULL**.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser le handle d’appeler directement des API Windows.  
  
##  <a name="operator_neq"></a>  CMenu::operator ! =  
 Détermine si deux menus sont logiquement pas égaux.  
  
```  
BOOL operator!=(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *menu*  
 A `CMenu` objet pour la comparaison.  
  
### <a name="remarks"></a>Notes  
 Teste si un objet de menu sur le côté gauche n’est pas égal à un objet de menu située à droite.  
  
##  <a name="operator_eq_eq"></a>  CMenu::operator ==  
 Détermine si deux menus sont logiquement égales.  
  
```  
BOOL operator==(const CMenu& menu) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *menu*  
 A `CMenu` objet pour la comparaison.  
  
### <a name="remarks"></a>Notes  
 Teste si un objet de menu sur le côté gauche est égal (en termes de la `HMENU` valeur) à un objet de menu située à droite.  
  
##  <a name="removemenu"></a>  CMenu::RemoveMenu  
 Supprime un élément de menu avec un menu contextuel à partir du menu.  
  
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
|**MF_BYCOMMAND**|Spécifie que le paramètre indique l’ID de commande de l’élément de menu existant. Ceci est la valeur par défaut si aucune **MF_BYCOMMAND** ni **MF_BYPOSITION** est défini.|  
|**MF_BYPOSITION**|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|  
  
 *nIndicateurs*  
 Spécifie comment *nPosition* est interprété.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Elle ne supprime pas le handle d’un menu contextuel, le menu peut donc être réutilisé. Avant d’appeler cette fonction, l’application peut appeler le `GetSubMenu` fonction membre pour récupérer la fenêtre contextuelle `CMenu` objet pour une réutilisation.  
  
 Chaque fois qu’un menu qui réside dans une fenêtre est modifiée (ou non la fenêtre s’affiche), l’application doit appeler `CWnd::DrawMenuBar`.  
  
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
 Valeur spécifiant la signification de *uItem*. Si ce paramètre est **FALSE**, *uItem* est un identificateur d’élément de menu. Sinon, elle est une position d’élément de menu.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, la valeur de retour est différente de zéro. Si la fonction échoue, la valeur de retour est égale à zéro. Pour obtenir des informations d’erreur plus complètes, utilisez la fonction Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360), comme décrit dans le Kit de développement logiciel Windows.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la fonction Win32 [SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996), comme décrit dans le Kit de développement logiciel Windows.  
  
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
 Différent de zéro si l’opération a réussi ; Sinon, 0  
  
### <a name="remarks"></a>Notes  
 Tous les éléments dans le menu partagent cet identificateur, il n’est pas possible d’attacher un identificateur de contexte d’aide pour les éléments de menu individuels.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CMenu::InsertMenu](#insertmenu).  
  
##  <a name="setmenuinfo"></a>  CMenu::SetMenuInfo  
 Définit les informations d’un menu.  
  
```  
BOOL SetMenuInfo(LPCMENUINFO lpcmi);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpcmi*  
 Un pointeur vers un [MENUINFO](http://msdn.microsoft.com/library/windows/desktop/ms647575) structure contenant des informations pour le menu.  
  
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
|**MF_BYCOMMAND**|Spécifie que le paramètre indique l’ID de commande de l’élément de menu existant. Ceci est la valeur par défaut si aucune **MF_BYCOMMAND** ni **MF_BYPOSITION** est défini.|  
|**MF_BYPOSITION**|Spécifie que le paramètre indique la position de l’élément de menu existant. Le premier élément est à la position 0.|  
  
 *nIndicateurs*  
 Spécifie comment *nPosition* est interprété.  
  
 *pBmpUnchecked*  
 Spécifie l’image bitmap à utiliser pour les éléments de menu qui ne sont pas vérifiées.  
  
 *pBmpChecked*  
 Spécifie l’image bitmap à utiliser pour les éléments de menu qui sont vérifiées.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur différente de zéro si la fonction réussit ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si l’élément de menu est activée ou désactivée, Windows affiche le bitmap appropriée en regard de l’élément de menu.  
  
 Si le paramètre *pBmpUnchecked* ou *pBmpChecked* est **NULL**, puis Windows n’affiche rien en regard de l’élément de menu pour l’attribut correspondant. Si les deux paramètres sont **NULL**, Windows utilise la case à cocher par défaut lorsque l’élément est activé et supprime la case à cocher lorsque l’élément est désactivé.  
  
 Lorsque le menu est détruit, ces bitmaps ne sont pas détruits ; l’application doit les détruire.  
  
 Les fenêtres **GetMenuCheckMarkDimensions** fonction récupère les dimensions de la case à cocher par défaut utilisé pour les éléments de menu. L’application utilise ces valeurs pour déterminer la taille appropriée pour les bitmaps fournis avec cette fonction. Obtenir la taille, créer vos images bitmap, puis de les définir.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#32](../../mfc/reference/codesnippet/cpp/cmenu-class_12.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#33](../../mfc/reference/codesnippet/cpp/cmenu-class_13.cpp)]  
  
##  <a name="setmenuiteminfo"></a>  CMenu::SetMenuItemInfo  
 Modifie les informations relatives à un élément de menu.  
  
```  
BOOL SetMenuItemInfo(
    UINT uItem,  
    LPMENUITEMINFO lpMenuItemInfo,  
    BOOL fByPos = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 *uItem*  
 Consultez la description de *uItem* dans [SetMenuItemInfo](http://msdn.microsoft.com/library/windows/desktop/ms648001) dans le Kit de développement logiciel Windows.  
  
 *lpMenuItemInfo*  
 Consultez la description de *lpmii* dans **SetMenuItemInfo** dans le Kit de développement logiciel Windows.  
  
 *fByPos*  
 Consultez la description de *fByPosition* dans **SetMenuItemInfo** dans le Kit de développement logiciel Windows.  
  
### <a name="remarks"></a>Notes  
 Cette fonction encapsule [SetMenuItemInfo](http://msdn.microsoft.com/library/windows/desktop/ms648001), comme décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="trackpopupmenu"></a>  CMenu::TrackPopupMenu  
 Affiche un menu contextuel flottant à l’emplacement spécifié et effectue le suivi de la sélection d’éléments dans le menu contextuel.  
  
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
 Spécifie des indicateurs de position de l’écran et la position de la souris. Consultez [TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002) pour obtenir la liste des indicateurs disponibles.  
  
 *x*  
 Spécifie la position horizontale, en coordonnées d’écran du menu contextuel. Selon la valeur de la *nIndicateurs* paramètre, le menu peut être aligné à gauche, aligné à droite ou centré par rapport à cette position.  
  
 *y*  
 Spécifie la position verticale, en coordonnées d’écran du haut du menu à l’écran.  
  
 *pWnd*  
 Identifie la fenêtre propriétaire de la liste déroulante. Ce paramètre ne peut pas être **NULL**, même si le **TPM_NONOTIFY** indicateur est spécifié. Cette fenêtre reçoit tous les **WM_COMMAND** messages à partir du menu. Dans Windows 3.1 et versions ultérieures, la fenêtre ne reçoit pas **WM_COMMAND** jusqu'à ce que les messages `TrackPopupMenu` retourne. Dans Windows 3.0, la fenêtre reçoit **WM_COMMAND** messages avant `TrackPopupMenu` retourne.  
  
 *lpRect*  
 Ignoré.  
  
### <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne le résultat de l’appel de [TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002) dans le Kit de développement logiciel Windows.  
  
### <a name="remarks"></a>Notes  
 Un menu contextuel flottant peut apparaître n’importe où sur l’écran.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#34](../../mfc/reference/codesnippet/cpp/cmenu-class_14.cpp)]  
  
##  <a name="trackpopupmenuex"></a>  CMenu::TrackPopupMenuEx  
 Affiche un menu contextuel flottant à l’emplacement spécifié et effectue le suivi de la sélection d’éléments dans le menu contextuel.  
  
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
 Spécifie les diverses fonctions de menu étendu. Pour obtenir la liste de toutes les valeurs et leur signification, consultez [fonction TrackPopupMenuEx](http://msdn.microsoft.com/library/windows/desktop/ms648003).  
  
 *x*  
 Spécifie la position horizontale, en coordonnées d’écran du menu contextuel.  
  
 *y*  
 Spécifie la position verticale, en coordonnées d’écran du haut du menu à l’écran.  
  
 *pWnd*  
 Pointeur vers la fenêtre propriétaire de la liste déroulante et la réception des messages à partir du menu créé. Cette fenêtre peut être n’importe quelle fenêtre de l’application active, mais ne peut pas être **NULL**. Si vous spécifiez **TPM_NONOTIFY** dans les *fuFlags* paramètre, la fonction n’envoie pas de tous les messages vers *pWnd*. La fonction doit retourner pour la fenêtre vers laquelle pointée *pWnd* pour recevoir le **WM_COMMAND** message.  
  
 *lptpm*  
 Pointeur vers un [TPMPARAMS](http://msdn.microsoft.com/library/windows/desktop/ms647586) structure qui spécifie une zone de l’écran du menu ne doit pas se chevaucher. Ce paramètre peut être **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Si vous spécifiez **TPM_RETURNCMD** dans les *fuFlags* paramètre, la valeur de retour est l’identificateur de l’élément de menu de l’élément sélectionné par l’utilisateur. Si l’utilisateur annule le menu sans effectuer de sélection, ou si une erreur se produit, la valeur de retour est 0.  
  
 Si vous ne spécifiez pas **TPM_RETURNCMD** dans les *fuFlags* paramètre, la valeur de retour est différent de zéro si la fonction réussit et 0 en cas d’échec. Pour obtenir des informations d’erreur plus complètes, appelez [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Notes  
 Un menu contextuel flottant peut apparaître n’importe où sur l’écran. Pour plus d’informations sur la gestion des erreurs lors de la création du menu contextuel, consultez [fonction TrackPopupMenuEx](http://msdn.microsoft.com/library/windows/desktop/ms648003).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC CTRLTEST](../../visual-cpp-samples.md)   
 [Exemple MFC DYNAMENU](../../visual-cpp-samples.md)   
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CObject, classe](../../mfc/reference/cobject-class.md)
