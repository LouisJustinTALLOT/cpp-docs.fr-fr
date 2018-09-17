---
title: La classe CListCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CListCtrl
- AFXCMN/CListCtrl
- AFXCMN/CListCtrl::CListCtrl
- AFXCMN/CListCtrl::ApproximateViewRect
- AFXCMN/CListCtrl::Arrange
- AFXCMN/CListCtrl::CancelEditLabel
- AFXCMN/CListCtrl::Create
- AFXCMN/CListCtrl::CreateDragImage
- AFXCMN/CListCtrl::CreateEx
- AFXCMN/CListCtrl::DeleteAllItems
- AFXCMN/CListCtrl::DeleteColumn
- AFXCMN/CListCtrl::DeleteItem
- AFXCMN/CListCtrl::DrawItem
- AFXCMN/CListCtrl::EditLabel
- AFXCMN/CListCtrl::EnableGroupView
- AFXCMN/CListCtrl::EnsureVisible
- AFXCMN/CListCtrl::FindItem
- AFXCMN/CListCtrl::GetBkColor
- AFXCMN/CListCtrl::GetBkImage
- AFXCMN/CListCtrl::GetCallbackMask
- AFXCMN/CListCtrl::GetCheck
- AFXCMN/CListCtrl::GetColumn
- AFXCMN/CListCtrl::GetColumnOrderArray
- AFXCMN/CListCtrl::GetColumnWidth
- AFXCMN/CListCtrl::GetCountPerPage
- AFXCMN/CListCtrl::GetEditControl
- AFXCMN/CListCtrl::GetEmptyText
- AFXCMN/CListCtrl::GetExtendedStyle
- AFXCMN/CListCtrl::GetFirstSelectedItemPosition
- AFXCMN/CListCtrl::GetFocusedGroup
- AFXCMN/CListCtrl::GetGroupCount
- AFXCMN/CListCtrl::GetGroupInfo
- AFXCMN/CListCtrl::GetGroupInfoByIndex
- AFXCMN/CListCtrl::GetGroupMetrics
- AFXCMN/CListCtrl::GetGroupRect
- AFXCMN/CListCtrl::GetGroupState
- AFXCMN/CListCtrl::GetHeaderCtrl
- AFXCMN/CListCtrl::GetHotCursor
- AFXCMN/CListCtrl::GetHotItem
- AFXCMN/CListCtrl::GetHoverTime
- AFXCMN/CListCtrl::GetImageList
- AFXCMN/CListCtrl::GetInsertMark
- AFXCMN/CListCtrl::GetInsertMarkColor
- AFXCMN/CListCtrl::GetInsertMarkRect
- AFXCMN/CListCtrl::GetItem
- AFXCMN/CListCtrl::GetItemCount
- AFXCMN/CListCtrl::GetItemData
- AFXCMN/CListCtrl::GetItemIndexRect
- AFXCMN/CListCtrl::GetItemPosition
- AFXCMN/CListCtrl::GetItemRect
- AFXCMN/CListCtrl::GetItemSpacing
- AFXCMN/CListCtrl::GetItemState
- AFXCMN/CListCtrl::GetItemText
- AFXCMN/CListCtrl::GetNextItem
- AFXCMN/CListCtrl::GetNextItemIndex
- AFXCMN/CListCtrl::GetNextSelectedItem
- AFXCMN/CListCtrl::GetNumberOfWorkAreas
- AFXCMN/CListCtrl::GetOrigin
- AFXCMN/CListCtrl::GetOutlineColor
- AFXCMN/CListCtrl::GetSelectedColumn
- AFXCMN/CListCtrl::GetSelectedCount
- AFXCMN/CListCtrl::GetSelectionMark
- AFXCMN/CListCtrl::GetStringWidth
- AFXCMN/CListCtrl::GetSubItemRect
- AFXCMN/CListCtrl::GetTextBkColor
- AFXCMN/CListCtrl::GetTextColor
- AFXCMN/CListCtrl::GetTileInfo
- AFXCMN/CListCtrl::GetTileViewInfo
- AFXCMN/CListCtrl::GetToolTips
- AFXCMN/CListCtrl::GetTopIndex
- AFXCMN/CListCtrl::GetView
- AFXCMN/CListCtrl::GetViewRect
- AFXCMN/CListCtrl::GetWorkAreas
- AFXCMN/CListCtrl::HasGroup
- AFXCMN/CListCtrl::HitTest
- AFXCMN/CListCtrl::InsertColumn
- AFXCMN/CListCtrl::InsertGroup
- AFXCMN/CListCtrl::InsertGroupSorted
- AFXCMN/CListCtrl::InsertItem
- AFXCMN/CListCtrl::InsertMarkHitTest
- AFXCMN/CListCtrl::IsGroupViewEnabled
- AFXCMN/CListCtrl::IsItemVisible
- AFXCMN/CListCtrl::MapIDToIndex
- AFXCMN/CListCtrl::MapIndexToID
- AFXCMN/CListCtrl::MoveGroup
- AFXCMN/CListCtrl::MoveItemToGroup
- AFXCMN/CListCtrl::RedrawItems
- AFXCMN/CListCtrl::RemoveAllGroups
- AFXCMN/CListCtrl::RemoveGroup
- AFXCMN/CListCtrl::Scroll
- AFXCMN/CListCtrl::SetBkColor
- AFXCMN/CListCtrl::SetBkImage
- AFXCMN/CListCtrl::SetCallbackMask
- AFXCMN/CListCtrl::SetCheck
- AFXCMN/CListCtrl::SetColumn
- AFXCMN/CListCtrl::SetColumnOrderArray
- AFXCMN/CListCtrl::SetColumnWidth
- AFXCMN/CListCtrl::SetExtendedStyle
- AFXCMN/CListCtrl::SetGroupInfo
- AFXCMN/CListCtrl::SetGroupMetrics
- AFXCMN/CListCtrl::SetHotCursor
- AFXCMN/CListCtrl::SetHotItem
- AFXCMN/CListCtrl::SetHoverTime
- AFXCMN/CListCtrl::SetIconSpacing
- AFXCMN/CListCtrl::SetImageList
- AFXCMN/CListCtrl::SetInfoTip
- AFXCMN/CListCtrl::SetInsertMark
- AFXCMN/CListCtrl::SetInsertMarkColor
- AFXCMN/CListCtrl::SetItem
- AFXCMN/CListCtrl::SetItemCount
- AFXCMN/CListCtrl::SetItemCountEx
- AFXCMN/CListCtrl::SetItemData
- AFXCMN/CListCtrl::SetItemIndexState
- AFXCMN/CListCtrl::SetItemPosition
- AFXCMN/CListCtrl::SetItemState
- AFXCMN/CListCtrl::SetItemText
- AFXCMN/CListCtrl::SetOutlineColor
- AFXCMN/CListCtrl::SetSelectedColumn
- AFXCMN/CListCtrl::SetSelectionMark
- AFXCMN/CListCtrl::SetTextBkColor
- AFXCMN/CListCtrl::SetTextColor
- AFXCMN/CListCtrl::SetTileInfo
- AFXCMN/CListCtrl::SetTileViewInfo
- AFXCMN/CListCtrl::SetToolTips
- AFXCMN/CListCtrl::SetView
- AFXCMN/CListCtrl::SetWorkAreas
- AFXCMN/CListCtrl::SortGroups
- AFXCMN/CListCtrl::SortItems
- AFXCMN/CListCtrl::SortItemsEx
- AFXCMN/CListCtrl::SubItemHitTest
- AFXCMN/CListCtrl::Update
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl [MFC], CListCtrl
- CListCtrl [MFC], ApproximateViewRect
- CListCtrl [MFC], Arrange
- CListCtrl [MFC], CancelEditLabel
- CListCtrl [MFC], Create
- CListCtrl [MFC], CreateDragImage
- CListCtrl [MFC], CreateEx
- CListCtrl [MFC], DeleteAllItems
- CListCtrl [MFC], DeleteColumn
- CListCtrl [MFC], DeleteItem
- CListCtrl [MFC], DrawItem
- CListCtrl [MFC], EditLabel
- CListCtrl [MFC], EnableGroupView
- CListCtrl [MFC], EnsureVisible
- CListCtrl [MFC], FindItem
- CListCtrl [MFC], GetBkColor
- CListCtrl [MFC], GetBkImage
- CListCtrl [MFC], GetCallbackMask
- CListCtrl [MFC], GetCheck
- CListCtrl [MFC], GetColumn
- CListCtrl [MFC], GetColumnOrderArray
- CListCtrl [MFC], GetColumnWidth
- CListCtrl [MFC], GetCountPerPage
- CListCtrl [MFC], GetEditControl
- CListCtrl [MFC], GetEmptyText
- CListCtrl [MFC], GetExtendedStyle
- CListCtrl [MFC], GetFirstSelectedItemPosition
- CListCtrl [MFC], GetFocusedGroup
- CListCtrl [MFC], GetGroupCount
- CListCtrl [MFC], GetGroupInfo
- CListCtrl [MFC], GetGroupInfoByIndex
- CListCtrl [MFC], GetGroupMetrics
- CListCtrl [MFC], GetGroupRect
- CListCtrl [MFC], GetGroupState
- CListCtrl [MFC], GetHeaderCtrl
- CListCtrl [MFC], GetHotCursor
- CListCtrl [MFC], GetHotItem
- CListCtrl [MFC], GetHoverTime
- CListCtrl [MFC], GetImageList
- CListCtrl [MFC], GetInsertMark
- CListCtrl [MFC], GetInsertMarkColor
- CListCtrl [MFC], GetInsertMarkRect
- CListCtrl [MFC], GetItem
- CListCtrl [MFC], GetItemCount
- CListCtrl [MFC], GetItemData
- CListCtrl [MFC], GetItemIndexRect
- CListCtrl [MFC], GetItemPosition
- CListCtrl [MFC], GetItemRect
- CListCtrl [MFC], GetItemSpacing
- CListCtrl [MFC], GetItemState
- CListCtrl [MFC], GetItemText
- CListCtrl [MFC], GetNextItem
- CListCtrl [MFC], GetNextItemIndex
- CListCtrl [MFC], GetNextSelectedItem
- CListCtrl [MFC], GetNumberOfWorkAreas
- CListCtrl [MFC], GetOrigin
- CListCtrl [MFC], GetOutlineColor
- CListCtrl [MFC], GetSelectedColumn
- CListCtrl [MFC], GetSelectedCount
- CListCtrl [MFC], GetSelectionMark
- CListCtrl [MFC], GetStringWidth
- CListCtrl [MFC], GetSubItemRect
- CListCtrl [MFC], GetTextBkColor
- CListCtrl [MFC], GetTextColor
- CListCtrl [MFC], GetTileInfo
- CListCtrl [MFC], GetTileViewInfo
- CListCtrl [MFC], GetToolTips
- CListCtrl [MFC], GetTopIndex
- CListCtrl [MFC], GetView
- CListCtrl [MFC], GetViewRect
- CListCtrl [MFC], GetWorkAreas
- CListCtrl [MFC], HasGroup
- CListCtrl [MFC], HitTest
- CListCtrl [MFC], InsertColumn
- CListCtrl [MFC], InsertGroup
- CListCtrl [MFC], InsertGroupSorted
- CListCtrl [MFC], InsertItem
- CListCtrl [MFC], InsertMarkHitTest
- CListCtrl [MFC], IsGroupViewEnabled
- CListCtrl [MFC], IsItemVisible
- CListCtrl [MFC], MapIDToIndex
- CListCtrl [MFC], MapIndexToID
- CListCtrl [MFC], MoveGroup
- CListCtrl [MFC], MoveItemToGroup
- CListCtrl [MFC], RedrawItems
- CListCtrl [MFC], RemoveAllGroups
- CListCtrl [MFC], RemoveGroup
- CListCtrl [MFC], Scroll
- CListCtrl [MFC], SetBkColor
- CListCtrl [MFC], SetBkImage
- CListCtrl [MFC], SetCallbackMask
- CListCtrl [MFC], SetCheck
- CListCtrl [MFC], SetColumn
- CListCtrl [MFC], SetColumnOrderArray
- CListCtrl [MFC], SetColumnWidth
- CListCtrl [MFC], SetExtendedStyle
- CListCtrl [MFC], SetGroupInfo
- CListCtrl [MFC], SetGroupMetrics
- CListCtrl [MFC], SetHotCursor
- CListCtrl [MFC], SetHotItem
- CListCtrl [MFC], SetHoverTime
- CListCtrl [MFC], SetIconSpacing
- CListCtrl [MFC], SetImageList
- CListCtrl [MFC], SetInfoTip
- CListCtrl [MFC], SetInsertMark
- CListCtrl [MFC], SetInsertMarkColor
- CListCtrl [MFC], SetItem
- CListCtrl [MFC], SetItemCount
- CListCtrl [MFC], SetItemCountEx
- CListCtrl [MFC], SetItemData
- CListCtrl [MFC], SetItemIndexState
- CListCtrl [MFC], SetItemPosition
- CListCtrl [MFC], SetItemState
- CListCtrl [MFC], SetItemText
- CListCtrl [MFC], SetOutlineColor
- CListCtrl [MFC], SetSelectedColumn
- CListCtrl [MFC], SetSelectionMark
- CListCtrl [MFC], SetTextBkColor
- CListCtrl [MFC], SetTextColor
- CListCtrl [MFC], SetTileInfo
- CListCtrl [MFC], SetTileViewInfo
- CListCtrl [MFC], SetToolTips
- CListCtrl [MFC], SetView
- CListCtrl [MFC], SetWorkAreas
- CListCtrl [MFC], SortGroups
- CListCtrl [MFC], SortItems
- CListCtrl [MFC], SortItemsEx
- CListCtrl [MFC], SubItemHitTest
- CListCtrl [MFC], Update
ms.assetid: fe08a1ca-4b05-4ff7-a12a-ee4c765a2197
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1e869fd70fb8f2d0b52d69dedb555c600fd390b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726815"
---
# <a name="clistctrl-class"></a>CListCtrl (classe)
Encapsule les fonctionnalités d’un contrôle d’affichage de liste, qui affiche une collection d’éléments constitués chacun d’une icône (de liste d’images) et d’une étiquette.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CListCtrl : public CWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CListCtrl::CListCtrl](#clistctrl)|Construit un objet `CListCtrl`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CListCtrl::ApproximateViewRect](#approximateviewrect)|Détermine la largeur et la hauteur requise pour afficher les éléments d’un contrôle list view.|  
|[CListCtrl::Arrange](#arrange)|Aligne les éléments sur une grille.|  
|[CListCtrl::CancelEditLabel](#canceleditlabel)|Annule l’opération d’édition de texte élément.|  
|[CListCtrl::Create](#create)|Crée un contrôle de liste et l’attache à un `CListCtrl` objet.|  
|[CListCtrl::CreateDragImage](#createdragimage)|Crée une liste d’images pour un élément spécifié.|  
|[CListCtrl::CreateEx](#createex)|Crée un contrôle de liste avec les styles étendus Windows spécifiés et l’attache à un `CListCtrl` objet.|  
|[CListCtrl::DeleteAllItems](#deleteallitems)|Supprime tous les éléments du contrôle.|  
|[CListCtrl::DeleteColumn](#deletecolumn)|Supprime une colonne du contrôle list view.|  
|[CListCtrl::DeleteItem](#deleteitem)|Supprime un élément à partir du contrôle.|  
|[CListCtrl::DrawItem](#drawitem)|Appelé lorsqu’un aspect visuel d’un contrôle en mode owner-draw change.|  
|[CListCtrl::EditLabel](#editlabel)|Commence la modification sur place du texte de l’élément.|  
|[CListCtrl::EnableGroupView](#enablegroupview)|Active ou désactive la possibilité pour les éléments dans un contrôle list view s’affichent en tant que groupe.|  
|[CListCtrl::EnsureVisible](#ensurevisible)|Garantit qu’un élément est visible.|  
|[CListCtrl::FindItem](#finditem)|Recherche un élément de liste ayant les caractéristiques spécifiées.|  
|[CListCtrl::GetBkColor](#getbkcolor)|Récupère la couleur d’arrière-plan d’un contrôle list view.|  
|[CListCtrl::GetBkImage](#getbkimage)|Récupère l’image d’arrière-plan actuelle d’un contrôle list view.|  
|[CListCtrl::GetCallbackMask](#getcallbackmask)|Récupère le masque de rappel pour un contrôle list view.|  
|[CListCtrl::GetCheck](#getcheck)|Récupère l’état d’affichage actuel de l’image d’état associé à un élément.|  
|[CListCtrl::GetColumn](#getcolumn)|Récupère les attributs de colonne d’un contrôle.|  
|[CListCtrl::GetColumnOrderArray](#getcolumnorderarray)|Récupère l’ordre des colonnes (de gauche à droite) d’un contrôle list view.|  
|[CListCtrl::GetColumnWidth](#getcolumnwidth)|Récupère la largeur d’une colonne dans la liste ou un affichage de rapport.|  
|[CListCtrl::GetCountPerPage](#getcountperpage)|Calcule le nombre d’éléments qui peuvent s’ajuster verticalement dans un contrôle list view.|  
|[CListCtrl::GetEditControl](#geteditcontrol)|Récupère le handle du contrôle d’édition permet de modifier le texte de l’élément.|  
|[CListCtrl::GetEmptyText](#getemptytext)|Récupère la chaîne à afficher si le contrôle de liste actuel est vide.|  
|[CListCtrl::GetExtendedStyle](#getextendedstyle)|Récupère les styles étendus en cours d’un contrôle list view.|  
|[CListCtrl::GetFirstSelectedItemPosition](#getfirstselecteditemposition)|Récupère la position du premier élément d’affichage de liste sélectionné dans un contrôle list view.|  
|[CListCtrl::GetFocusedGroup](#getfocusedgroup)|Récupère le groupe qui a le focus clavier dans le contrôle de liste actuel.|  
|[CListCtrl::GetGroupCount](#getgroupcount)|Récupère le nombre de groupes dans le contrôle de liste actuel.|  
|[CListCtrl::GetGroupInfo](#getgroupinfo)|Obtient les informations pour un groupe spécifié de contrôle list view.|  
|[CListCtrl::GetGroupInfoByIndex](#getgroupinfobyindex)|Récupère des informations sur un groupe spécifié dans le contrôle de liste actuel.|  
|[CListCtrl::GetGroupMetrics](#getgroupmetrics)|Récupère les mesures d’un groupe.|  
|[CListCtrl::GetGroupRect](#getgrouprect)|Récupère le rectangle englobant pour un groupe spécifié dans le contrôle de liste actuel.|  
|[CListCtrl::GetGroupState](#getgroupstate)|Récupère l’état pour un groupe spécifié dans le contrôle de liste actuel.|  
|[CListCtrl::GetHeaderCtrl](#getheaderctrl)|Récupère le contrôle d’en-tête d’un contrôle list view.|  
|[CListCtrl::GetHotCursor](#gethotcursor)|Récupère le curseur utilisé lorsque la sélection réactive est activée pour un contrôle list view.|  
|[CListCtrl::GetHotItem](#gethotitem)|Récupère l’élément du ListView sous le curseur.|  
|[CListCtrl::GetHoverTime](#gethovertime)|Récupère le délai de pointage actuel d’un contrôle list view.|  
|[CListCtrl::GetImageList](#getimagelist)|Récupère le handle d’une liste d’images utilisée pour afficher les éléments de liste dessin.|  
|[CListCtrl::GetInsertMark](#getinsertmark)|Récupère la position actuelle de la marque d’insertion.|  
|[CListCtrl::GetInsertMarkColor](#getinsertmarkcolor)|Récupère la couleur actuelle de la marque d’insertion.|  
|[CListCtrl::GetInsertMarkRect](#getinsertmarkrect)|Récupère le rectangle qui délimite le point d’insertion.|  
|[CListCtrl::GetItem](#getitem)|Récupère les attributs d’un élément de vue de liste.|  
|[CListCtrl::GetItemCount](#getitemcount)|Récupère le nombre d’éléments dans un contrôle list view.|  
|[CListCtrl::GetItemData](#getitemdata)|Récupère la valeur spécifique à l’application associée à un élément.|  
|[CListCtrl::GetItemIndexRect](#getitemindexrect)|Récupère le rectangle englobant pour tout ou partie d’un sous-élément dans le contrôle de liste actuel.|  
|[CListCtrl::GetItemPosition](#getitemposition)|Récupère la position d’un élément de liste.|  
|[CListCtrl::GetItemRect](#getitemrect)|Récupère le rectangle englobant d’un élément.|  
|[CListCtrl::GetItemSpacing](#getitemspacing)|Calcule l’espacement entre les éléments dans le contrôle de liste actuel.|  
|[CListCtrl::GetItemState](#getitemstate)|Récupère l’état d’un élément de liste.|  
|[CListCtrl::GetItemText](#getitemtext)|Récupère le texte d’un élément de vue de liste ou d’un sous-élément.|  
|[CListCtrl::GetNextItem](#getnextitem)|Recherche un élément de liste avec les propriétés spécifiées et avec la relation spécifiée à un élément donné.|  
|[CListCtrl::GetNextItemIndex](#getnextitemindex)|Récupère l’index de l’élément dans le contrôle d’affichage de liste actuel qui a un ensemble de propriétés spécifié.|  
|[CListCtrl::GetNextSelectedItem](#getnextselecteditem)|Récupère l’index de la position d’un élément de vue de liste et la position de l’élément de vue de liste sélectionné suivant pour une itération.|  
|[CListCtrl::GetNumberOfWorkAreas](#getnumberofworkareas)|Récupère le nombre actuel de zones de travail pour un contrôle list view.|  
|[CListCtrl::GetOrigin](#getorigin)|Récupère l’origine de la vue actuelle pour un contrôle list view.|  
|[CListCtrl::GetOutlineColor](#getoutlinecolor)|Récupère la couleur de la bordure d’un contrôle list view.|  
|[CListCtrl::GetSelectedColumn](#getselectedcolumn)|Récupère l’index de la colonne actuellement sélectionnée dans le contrôle de liste.|  
|[CListCtrl::GetSelectedCount](#getselectedcount)|Récupère le nombre d’éléments sélectionnés dans le contrôle list view.|  
|[CListCtrl::GetSelectionMark](#getselectionmark)|Récupère la marque de sélection d’un contrôle list view.|  
|[CListCtrl::GetStringWidth](#getstringwidth)|Détermine la largeur de colonne minimale nécessaire pour afficher toutes les une chaîne donnée.|  
|[CListCtrl::GetSubItemRect](#getsubitemrect)|Récupère le rectangle englobant d’un élément dans un contrôle list view.|  
|[CListCtrl::GetTextBkColor](#gettextbkcolor)|Récupère la couleur d’arrière-plan du texte d’un contrôle list view.|  
|[CListCtrl::GetTextColor](#gettextcolor)|Récupère la couleur du texte d’un contrôle list view.|  
|[CListCtrl::GetTileInfo](#gettileinfo)|Récupère des informations sur une vignette dans un contrôle list view.|  
|[CListCtrl::GetTileViewInfo](#gettileviewinfo)|Récupère des informations sur un contrôle list view dans l’affichage en mosaïque.|  
|[CListCtrl::GetToolTips](#gettooltips)|Récupère le contrôle d’info-bulle du contrôle list view utilise pour afficher des info-bulles.|  
|[CListCtrl::GetTopIndex](#gettopindex)|Récupère l’index du premier élément visible.|  
|[CListCtrl::GetView](#getview)|Obtient la vue du contrôle list view.|  
|[CListCtrl::GetViewRect](#getviewrect)|Récupère le rectangle englobant de tous les éléments dans le contrôle list view.|  
|[CListCtrl::GetWorkAreas](#getworkareas)|Récupère les zones de travail en cours d’un contrôle list view.|  
|[CListCtrl::HasGroup](#hasgroup)|Détermine si le contrôle list view a le groupe spécifié.|  
|[CListCtrl::HitTest](#hittest)|Détermine quelle liste est d’afficher l’élément à une position spécifiée.|  
|[CListCtrl::InsertColumn](#insertcolumn)|Insère une nouvelle colonne dans un contrôle list view.|  
|[CListCtrl::InsertGroup](#insertgroup)|Insère un groupe dans le contrôle list view.|  
|[CListCtrl::InsertGroupSorted](#insertgroupsorted)|Insère le groupe spécifié dans une liste triée des groupes.|  
|[CListCtrl::InsertItem](#insertitem)|Insère un nouvel élément dans un contrôle list view.|  
|[CListCtrl::InsertMarkHitTest](#insertmarkhittest)|Récupère le point d’insertion le plus proche à un point spécifié.|  
|[CListCtrl::IsGroupViewEnabled](#isgroupviewenabled)|Détermine si l’affichage du groupe est activé pour un contrôle list view.|  
|[CListCtrl::IsItemVisible](#isitemvisible)|Indique si un élément spécifié dans le contrôle de liste actuel est visible.|  
|[CListCtrl::MapIDToIndex](#mapidtoindex)|Mappe l’ID unique d’un élément dans le contrôle de liste actuel à un index.|  
|[CListCtrl::MapIndexToID](#mapindextoid)|Mappe l’index d’un élément dans le contrôle de liste actuel à un ID unique.|  
|[CListCtrl::MoveGroup](#movegroup)|Déplace le groupe spécifié.|  
|[CListCtrl::MoveItemToGroup](#moveitemtogroup)|Déplace le que groupe spécifié spécifiée à l’index de base zéro du contrôle list view.|  
|[CListCtrl::RedrawItems](#redrawitems)|Force un contrôle list view à repeindre une plage d’éléments.|  
|[CListCtrl::RemoveAllGroups](#removeallgroups)|Supprime tous les groupes à partir d’un contrôle list view.|  
|[CListCtrl::RemoveGroup](#removegroup)|Supprime le groupe spécifié à partir du contrôle list view.|  
|[CListCtrl::Scroll](#scroll)|Fait défiler le contenu d’un contrôle list view.|  
|[CListCtrl::SetBkColor](#setbkcolor)|Définit la couleur d’arrière-plan du contrôle list view.|  
|[CListCtrl::SetBkImage](#setbkimage)|Définit l’image d’arrière-plan actuelle d’un contrôle list view.|  
|[CListCtrl::SetCallbackMask](#setcallbackmask)|Définit le masque de rappel pour un contrôle list view.|  
|[CListCtrl::SetCheck](#setcheck)|Jeux actuel afficher l’état de l’image d’état associé à un élément.|  
|[CListCtrl::SetColumn](#setcolumn)|Définit les attributs d’une colonne de vue de liste.|  
|[CListCtrl::SetColumnOrderArray](#setcolumnorderarray)|Définit l’ordre des colonnes (de gauche à droite) d’un contrôle list view.|  
|[CListCtrl::SetColumnWidth](#setcolumnwidth)|Modifie la largeur d’une colonne dans la liste ou un affichage de rapport.|  
|[CListCtrl::SetExtendedStyle](#setextendedstyle)|Définit les styles étendus en cours d’un contrôle list view.|  
|[CListCtrl::SetGroupInfo](#setgroupinfo)|Définit les informations pour le groupe spécifié d’un contrôle list view.|  
|[CListCtrl::SetGroupMetrics](#setgroupmetrics)|Définit les mesures de groupe d’un contrôle list view.|  
|[CListCtrl::SetHotCursor](#sethotcursor)|Définit le curseur utilisé lors de la sélection réactive est activée pour un contrôle list view.|  
|[CListCtrl::SetHotItem](#sethotitem)|Définit l’élément actif actuel d’un contrôle list view.|  
|[CListCtrl::SetHoverTime](#sethovertime)|Définit le délai de pointage actuel d’un contrôle list view.|  
|[CListCtrl::SetIconSpacing](#seticonspacing)|Définit l’espacement entre les icônes dans un contrôle list view.|  
|[CListCtrl::SetImageList](#setimagelist)|Affecte une liste d’images à un contrôle list view.|  
|[CListCtrl::SetInfoTip](#setinfotip)|Définit le texte d’info-bulle.|  
|[CListCtrl::SetInsertMark](#setinsertmark)|Définit le point d’insertion à la position définie.|  
|[CListCtrl::SetInsertMarkColor](#setinsertmarkcolor)|Définit la couleur du point d’insertion.|  
|[CListCtrl::SetItem](#setitem)|Définit les attributs de l’élément de tout ou partie d’une vue liste.|  
|[CListCtrl::SetItemCount](#setitemcount)|Prépare un contrôle list view pour l’ajout d’un grand nombre d’éléments.|  
|[CListCtrl::SetItemCountEx](#setitemcountex)|Définit le nombre d’éléments pour un contrôle d’affichage de liste virtuelle.|  
|[CListCtrl::SetItemData](#setitemdata)|Définit la valeur de l’élément spécifique à l’application.|  
|[CListCtrl::SetItemIndexState](#setitemindexstate)|Définit l’état d’un élément dans le contrôle de liste actuel.|  
|[CListCtrl::SetItemPosition](#setitemposition)|Déplace un élément à une position spécifiée dans un contrôle list view.|  
|[CListCtrl::SetItemState](#setitemstate)|Modifie l’état d’un élément dans un contrôle list view.|  
|[CListCtrl::SetItemText](#setitemtext)|Modifie le texte d’un élément de vue de liste ou d’un sous-élément.|  
|[CListCtrl::SetOutlineColor](#setoutlinecolor)|Définit la couleur de la bordure d’un contrôle list view.|  
|[CListCtrl::SetSelectedColumn](#setselectedcolumn)|Définit la colonne sélectionnée du contrôle list view.|  
|[CListCtrl::SetSelectionMark](#setselectionmark)|Définit la marque de sélection d’un contrôle list view.|  
|[CListCtrl::SetTextBkColor](#settextbkcolor)|Définit la couleur d’arrière-plan du texte dans un contrôle list view.|  
|[CListCtrl::SetTextColor](#settextcolor)|Définit la couleur du texte d’un contrôle list view.|  
|[CListCtrl::SetTileInfo](#settileinfo)|Définit les informations pour une vignette de l’affichage de liste.|  
|[CListCtrl::SetTileViewInfo](#settileviewinfo)|Définit les informations qui utilise un contrôle list view dans l’affichage en mosaïque.|  
|[CListCtrl::SetToolTips](#settooltips)|Définit le contrôle d’info-bulle du contrôle list view utilisera pour afficher des info-bulles.|  
|[CListCtrl::SetView](#setview)|Définit l’affichage de contrôle list view.|  
|[CListCtrl::SetWorkAreas](#setworkareas)|Définit la zone où les icônes peuvent être affichés dans un contrôle list view.|  
|[CListCtrl::SortGroups](#sortgroups)|Trie les groupes d’une liste permet d’afficher le contrôle avec une fonction définie par l’utilisateur.|  
|[CListCtrl::SortItems](#sortitems)|Trie les éléments d’affichage de liste à l’aide d’une fonction définie par l’application de comparaison.|  
|[CListCtrl::SortItemsEx](#sortitemsex)|Trie les éléments d’affichage de liste à l’aide d’une fonction définie par l’application de comparaison.|  
|[CListCtrl::SubItemHitTest](#subitemhittest)|Détermine quel élément d’affichage de liste, si une, est à une position donnée.|  
|[CListCtrl::Update](#update)|Force le contrôle à repeindre un élément spécifié.|  
  
## <a name="remarks"></a>Notes  
 Outre une icône et une étiquette, chaque élément peut avoir des informations affichées dans les colonnes à droite de l’icône et une étiquette. Ce contrôle (et par conséquent la `CListCtrl` classe) est disponible uniquement pour les programmes s’exécutant sous Windows 95/98 et Windows NT version 3.51 et ultérieures.  
  
 Voici un bref aperçu de la `CListCtrl` classe. Pour une explication détaillée, conceptuelle, consultez [utilisation de CListCtrl](../../mfc/using-clistctrl.md) et [contrôles](../../mfc/controls-mfc.md).  
  
## <a name="views"></a>Affichages  
 Contrôles d’affichage de liste peuvent afficher leur contenu de quatre manières différentes, appelés « vues ».  
  
-   Affichage de l’icône  
  
     Chaque élément apparaît comme une icône de taille normale (32 x 32 pixels) avec une étiquette placée au-dessous. L’utilisateur peut faire glisser les éléments à n’importe quel emplacement dans la fenêtre d’affichage de liste.  
  
-   Affichage de la petite icône  
  
     Chaque élément apparaît comme une petite icône (pixels de 16 x 16) avec l’étiquette à droite de celui-ci. L’utilisateur peut faire glisser les éléments à n’importe quel emplacement dans la fenêtre d’affichage de liste.  
  
-   Liste (vue)  
  
     Chaque élément apparaît comme une petite icône avec une étiquette à droite de celui-ci. Les éléments sont organisés en colonnes et ne peut pas être déplacées à n’importe quel emplacement dans la fenêtre d’affichage de liste.  
  
-   Vue rapport  
  
     Chaque élément apparaît sur sa propre ligne, avec des informations supplémentaires sont disposées en colonnes à droite. La colonne de gauche contient la petite icône et une étiquette et les colonnes suivantes contiennent des sous-éléments, comme spécifié par l’application. Un contrôle header incorporé (classe [CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)) implémente ces colonnes. Pour plus d’informations sur le contrôle d’en-tête et les colonnes dans une vue de rapport, consultez [utilisation de CListCtrl : ajout de colonnes au contrôle (vue rapport)](../../mfc/adding-columns-to-the-control-report-view.md).  
  
 Voir aussi :  
  
-   Article de la Base de connaissances Q250614 : Comment : trier les éléments dans un objet CListCtrl dans la vue rapport  
  
-   Article de la Base de connaissances Q200054 : PRB : OnTimer() n’est pas appelée à plusieurs reprises pour un contrôle de liste  
  
 Le style d’affichage de liste actuel du contrôle détermine l’affichage actuel. Pour plus d’informations sur ces styles et leur utilisation, consultez [utilisation de CListCtrl : modification des Styles de contrôle liste](../../mfc/changing-list-control-styles.md).  
  
## <a name="extended-styles"></a>Styles étendus  
 Outre les styles de liste standard, classe `CListCtrl` prend en charge un large éventail de styles étendus, fournissant des fonctionnalités enrichies. Voici quelques exemples de cette fonctionnalité :  
  
-   Sélection de pointage  
  
     Lorsque l’option est activée, permet la sélection automatique d’un élément lorsque le curseur reste sur l’élément pendant un certain laps de temps.  
  
-   Vues de liste virtuelle  
  
     Lorsque l’option est activée, permet au contrôle prendre en charge les éléments DWORD au maximum. Cela est possible en plaçant la surcharge de la gestion des données de l’élément sur l’application. À l’exception de la sélection d’éléments et les informations de focus, toutes les informations de l’élément doivent être gérées par l’application. Pour plus d’informations, consultez [utilisation de CListCtrl : contrôles de liste virtuels](../../mfc/virtual-list-controls.md).  
  
-   Activation et deux-clic  
  
     Lorsque activé, permet la sélection réactive (mise en surbrillance automatique du texte de l’élément) et l’activation d’un ou deux clic de l’élément en surbrillance.  
  
-   Faites glisser et déposez l’ordre des colonnes  
  
     Lorsque l’option est activée, permet de glisser-déplacer la réorganisation des colonnes dans un contrôle list view. Disponible uniquement dans la vue rapport.  
  
 Pour plus d’informations sur l’utilisation des nouveaux des styles étendus, consultez [utilisation de CListCtrl : modification des Styles de contrôle liste](../../mfc/changing-list-control-styles.md).  
  
## <a name="items-and-subitems"></a>Éléments et sous-éléments  
 Chaque élément dans un contrôle list view se compose d’une icône (à partir d’une liste d’images), une étiquette, un état actuel et une valeur définie par l’application (également appelé « élément de données »). Un ou plusieurs sous-éléments peuvent également être associées à chaque élément. Un sous-élément « » est une chaîne qui, dans la vue de rapport, peut être affichée dans une colonne à droite de l’icône et l’étiquette d’un élément. Tous les éléments dans un contrôle list view doivent avoir le même nombre de sous-éléments.  
  
 Classe `CListCtrl` fournit plusieurs fonctions pour l’insertion, la suppression, la recherche et la modification de ces éléments. Pour plus d’informations, consultez [CListCtrl::GetItem](#getitem), [CListCtrl::InsertItem](#insertitem), et [CListCtrl::FindItem](#finditem), [Ajout d’éléments au contrôle](../adding-items-to-the-control.md), et [défilement, organisation, tri et recherche dans les contrôles de liste](../scrolling-arranging-sorting-and-finding-in-list-controls.md).  
  
 Par défaut, le contrôle list view est responsable du stockage des attributs d’icône et le texte d’un élément. Toutefois, en plus de ces types d’éléments, la classe `CListCtrl` prend en charge les « éléments de rappel ». Un élément de « rappel » est un élément de liste pour lequel l’application, plutôt que le contrôle, stocke le texte, icône ou les deux. Un masque de rappel est utilisé pour spécifier les attributs de l’élément (texte et/ou l’icône) sont fournies par l’application. Si une application utilise des éléments de rappel, il doit être en mesure de fournir les attributs de texte et/ou l’icône à la demande. Éléments de rappel sont utiles lorsque votre application a déjà gère certaines de ces informations. Pour plus d’informations, consultez [utilisation de CListCtrl : éléments de rappel et masque de rappel](../callback-items-and-the-callback-mask.md).  
  
## <a name="image-lists"></a>Listes d’images  
 Les icônes, images d’élément en-tête et application - défini des États pour afficher les éléments de liste sont contenus dans plusieurs listes d’images (implémentée par la classe [CImageList](cimagelist-class.md)), que vous pouvez créer et affecter à un contrôle list view. Chaque contrôle list view peut avoir jusqu'à quatre différents types de listes d’images :  
  
-   Grande icône  
  
     Utilisé dans la vue de l’icône pour les icônes en taille réelle.  
  
-   Petite icône  
  
     Utilisée dans la petite icône, liste et les vues de rapport pour des versions plus petites des icônes utilisées dans la vue de l’icône.  
  
-   État défini par l’application  
  
     Contient des images d’état sont affichées en regard de l’icône d’un élément pour indiquer un état défini par l’application.  
  
-   Élément d’en-tête  
  
     Utilisé dans la vue de rapport pour les petites images qui apparaissent dans chaque élément de contrôle d’en-tête.  
  
 Par défaut, un contrôle list view détruit les listes d’images qui lui est assignées lorsqu’il est détruit ; Toutefois, le développeur peut personnaliser ce comportement en détruisant chaque liste d’images lorsqu’il n’est plus utilisé, tel que déterminé par l’application. Pour plus d’informations, consultez [utilisation de CListCtrl : éléments de liste et listes d’images](../list-items-and-image-lists.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 `CListCtrl`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcmn.h  
  
##  <a name="approximateviewrect"></a>  CListCtrl::ApproximateViewRect  
 Détermine la largeur et la hauteur requise pour afficher les éléments d’un contrôle list view.  
  
```  
CSize ApproximateViewRect(
    CSize sz = CSize(-1,  
 -1),  
    int iCount = -1) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *sz*  
 Les dimensions proposées du contrôle, en pixels. Si les dimensions ne sont pas spécifiées, l’infrastructure utilise les valeurs actuelles de la largeur ou hauteur du contrôle.  
  
 *iCount*  
 Nombre d’éléments à afficher dans le contrôle. Si ce paramètre est -1, le framework utilise le nombre total d’éléments actuellement dans le contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Un `CSize` objet qui contient la largeur approximative et la hauteur nécessaire pour afficher les éléments, en pixels.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_ApproximateViewRect](/windows/desktop/api/commctrl/nf-commctrl-listview_approximateviewrect), comme décrit dans le SDK Windows.  
  
##  <a name="arrange"></a>  CListCtrl::Arrange  
 Repositionne les éléments dans un affichage de l’icône afin qu’ils s’alignent sur une grille.  
  
```  
BOOL Arrange(UINT nCode);
```  
  
### <a name="parameters"></a>Paramètres  
 *nCode*  
 Spécifie le style d’alignement pour les éléments. Il peut prendre l’une des valeurs suivantes :  
  
- LVA_ALIGNLEFT aligne les éléments le long du bord gauche de la fenêtre.  
  
- LVA_ALIGNTOP aligne les éléments le long du bord supérieur de la fenêtre.  
  
- LVA_DEFAULT aligne les éléments en fonction des styles d’alignement actuel de la vue liste (la valeur par défaut).  
  
- LVA_SNAPTOGRID s’aligne toutes les icônes sur la position de grille le plus proche.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Le *nCode* paramètre spécifie le style d’alignement.  
  
### <a name="example"></a>Exemple    
```cpp  
    // Align all of the list view control items along the top
    // of the window (the list view control must be in icon or
    // small icon mode).
    m_myListCtrl.Arrange(LVA_ALIGNTOP);
```

  
##  <a name="canceleditlabel"></a>  CListCtrl::CancelEditLabel  
 Annule l’opération d’édition de texte élément.  
  
```  
void CancelEditLabel();
```  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_CANCELEDITLABEL](/windows/desktop/Controls/lvm-canceleditlabel) du message, comme décrit dans le SDK Windows.  
  
##  <a name="clistctrl"></a>  CListCtrl::CListCtrl  
 Construit un objet `CListCtrl`.  
  
```  
CListCtrl();
```  
  
##  <a name="create"></a>  CListCtrl::Create  
 Crée un contrôle de liste et l’attache à un `CListCtrl` objet.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwStyle*  
 Spécifie le style du contrôle de liste. Appliquer n’importe quelle combinaison de styles de contrôle de liste au contrôle. Consultez [styles de fenêtre d’affichage liste](/windows/desktop/Controls/list-view-window-styles) dans le SDK Windows pour obtenir la liste complète de ces styles. Ensemble spécifique d’un contrôle en utilisant des styles étendus [SetExtendedStyle](#setextendedstyle).  
  
 *Rect*  
 Spécifie la taille et la position du contrôle de liste. Il peut s’agir un `CRect` objet ou un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure.  
  
 *pParentWnd*  
 Spécifie la liste fenêtre du contrôle parent, généralement un `CDialog`. Il ne doit pas être NULL.  
  
 *nID*  
 Spécifie l’ID. du contrôle de liste  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Vous construisez un `CListCtrl` en deux étapes. Tout d’abord, appelez le constructeur, puis `Create`, ce qui crée le contrôle list view et l’attache à la `CListCtrl` objet.  
  
 Pour appliquer des styles étendus Windows à l’objet de contrôle de liste, appelez [CreateEx](#createex) au lieu de `Create`.  
  
### <a name="example"></a>Exemple  

```cpp  
    m_myListCtrl.Create(
        WS_CHILD|WS_VISIBLE|WS_BORDER|LVS_REPORT|LVS_EDITLABELS,
        CRect(10,10,400,200), pParentWnd, IDD_MYLISTCTRL);   
```

  
##  <a name="createex"></a>  CListCtrl::CreateEx  
 Crée un contrôle (une fenêtre enfant) et l’associe le `CListCtrl` objet.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwExStyle*  
 Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles étendus de Windows, consultez le *dwExStyle* paramètre pour [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) dans le SDK Windows.  
  
 *dwStyle*  
 Spécifie le style du contrôle de liste. Appliquer n’importe quelle combinaison de styles de contrôle de liste au contrôle. Pour obtenir une liste complète de ces styles, consultez [styles de fenêtre d’affichage liste](/windows/desktop/Controls/list-view-window-styles) dans le SDK Windows.  
  
 *Rect*  
 Une référence à un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure décrivant la taille et la position de la fenêtre doit être créée, dans les coordonnées clientes de *pParentWnd*.  
  
 *pParentWnd*  
 Pointeur vers la fenêtre qui est le parent du contrôle.  
  
 *nID*  
 ID de fenêtre enfant. du contrôle  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles étendus de Windows, spécifiés par la préface de style étendu Windows **WS_EX_**.  
  
 `CreateEx` crée le contrôle avec les styles étendus de Windows spécifiés par *dwExStyle*. Pour définir des styles étendus spécifique à un contrôle, appelez [SetExtendedStyle](#setextendedstyle). Par exemple, utilisez `CreateEx` pour définir des styles de ce type en tant que WS_EX_CONTEXTHELP, mais utiliser `SetExtendedStyle` pour définir des styles de ce type comme LVS_EX_FULLROWSELECT. Pour plus d’informations, consultez les styles décrites dans la rubrique [Styles étendus de la vue liste](/windows/desktop/Controls/extended-list-view-styles) dans le SDK Windows.  
  
##  <a name="createdragimage"></a>  CListCtrl::CreateDragImage  
 Crée une liste d’images pour l’élément spécifié par *nItem*.  
  
```  
CImageList* CreateDragImage(
    int nItem,  
    LPPOINT lpPoint);
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 Index de l’élément dont la liste d’image glisser doit être créé.  
  
 *lpPoint*  
 Adresse d’un [POINT](https://msdn.microsoft.com/library/windows/desktop/dd162805) coordonne la structure qui reçoit l’emplacement initial de l’angle supérieur gauche de l’image, dans la vue.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la liste d’images glisser en cas de réussite ; Sinon, NULL.  
  
### <a name="remarks"></a>Notes  
 Le `CImageList` objet est définitive et vous devez le supprimer une fois. Exemple :  
  

```cpp  
        CImageList* pImageList = m_myListCtrl.CreateDragImage(nItem, &point);

        // do something

        delete pImageList;
```

  
##  <a name="deleteallitems"></a>  CListCtrl::DeleteAllItems  
 Supprime tous les éléments du contrôle list view.  
  
```  
BOOL DeleteAllItems();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="example"></a>Exemple  

```cpp  
    // Delete all of the items from the list view control.
    m_myListCtrl.DeleteAllItems();
    ASSERT(m_myListCtrl.GetItemCount() == 0);
```

  
##  <a name="deletecolumn"></a>  CListCtrl::DeleteColumn  
 Supprime une colonne du contrôle list view.  
  
```  
BOOL DeleteColumn(int nCol);
```  
  
### <a name="parameters"></a>Paramètres  
 *nCol*  
 Index de la colonne à supprimer.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="example"></a>Exemple  

```cpp  
        int nColumnCount = m_myListCtrl.GetHeaderCtrl()->GetItemCount();

        // Delete all of the columns.
        for (int i=0; i < nColumnCount; i++)
        {
            m_myListCtrl.DeleteColumn(0);
        }
```

  
##  <a name="deleteitem"></a>  CListCtrl::DeleteItem  
 Supprime un élément d’un contrôle list view.  
  
```  
BOOL DeleteItem(int nItem);
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 Spécifie l’index de l’élément à supprimer.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="example"></a>Exemple  
```cpp  
        int nCount = m_myListCtrl.GetItemCount();

        // Delete all of the items from the list view control.
        for (int i=0; i < nCount; i++)
        {
            m_myListCtrl.DeleteItem(0);
        }
```

  
##  <a name="drawitem"></a>  CListCtrl::DrawItem  
 Appelé par l’infrastructure lorsqu’un aspect visuel d’un mode owner-draw liste Affichage contrôle change.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpDrawItemStruct*  
 Un pointeur long désignant un `DRAWITEMSTRUCT` structure qui contient des informations sur le type de dessin requis.  
  
### <a name="remarks"></a>Notes  
 Le `itemAction` membre de la [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) structure définit l’action de dessin qui doit être effectuée.  
  
 Par défaut, cette fonction membre ne fait rien. Remplacez cette fonction membre pour implémenter le dessin pour un mode owner-draw `CListCtrl` objet.  
  
 L’application doit restaurer tous les objets interface (GDI) périphérique graphique sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant ce membre de fonction se termine.  
  
##  <a name="editlabel"></a>  CListCtrl::EditLabel  
 Commence la modification sur place du texte de l’élément.  
  
```  
CEdit* EditLabel(int nItem);
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 Index de l’élément d’affichage de liste qui doit être modifié.  
  
### <a name="return-value"></a>Valeur de retour  
 Si l’opération réussit, un pointeur vers le `CEdit` objet qui est utilisé pour modifier le texte de l’élément ; sinon, NULL.  
  
### <a name="remarks"></a>Notes  
 Un contrôle list view qui a le style de fenêtre LVS_EDITLABELS permet à un utilisateur modifier les étiquettes des éléments en place. L’utilisateur commence à modifier en cliquant sur l’étiquette d’un élément qui a le focus.  
  
 Utilisez cette fonction pour commencer la modification sur place du texte de l’élément de vue de liste spécifiée.  
  
### <a name="example"></a>Exemple  
```cpp  
        // Make sure the focus is set to the list view control.
        m_myListCtrl.SetFocus();

        // Show the edit control on the label of the first
        // item in the list view control.
        CEdit* pmyEdit = m_myListCtrl.EditLabel(1);
        ASSERT(pmyEdit != NULL);
```

  
##  <a name="enablegroupview"></a>  CListCtrl::EnableGroupView  
 Active ou désactive la possibilité pour les éléments dans un contrôle list view s’affichent en tant que groupe.  
  
```  
LRESULT EnableGroupView(BOOL fEnable);
```  
  
### <a name="parameters"></a>Paramètres  
 *fEnable*  
 Indique si, pour activer un contrôle listview au groupe éléments affiché. TRUE pour activer le regroupement ; FALSE pour la désactiver.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
- **0** la possibilité d’afficher la liste des éléments comme un groupe est déjà activé ou désactivé.  
  
- **1** l’état du contrôle a été modifié avec succès.  
  
- **-1** l’opération a échoué.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_ENABLEGROUPVIEW](/windows/desktop/Controls/lvm-enablegroupview) du message, comme décrit dans le SDK Windows.  
  
##  <a name="ensurevisible"></a>  CListCtrl::EnsureVisible  
 Garantit qu’un élément de liste est au moins partiellement visible.  
  
```  
BOOL EnsureVisible(
    int nItem,  
    BOOL bPartialOK);
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 Index de l’élément d’affichage de liste qui doit être visible.  
  
 *bPartialOK*  
 Spécifie si la visibilité partielle est acceptable.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Le contrôle list view défile si nécessaire. Si le *bPartialOK* paramètre est différent de zéro, aucun défilement se produit si l’élément est partiellement visible.  
  
### <a name="example"></a>Exemple  
```cpp  
        // Ensure that the last item is visible.
        int nCount = m_myListCtrl.GetItemCount();
        if (nCount > 0)
            m_myListCtrl.EnsureVisible(nCount-1, FALSE);
```

  
##  <a name="finditem"></a>  CListCtrl::FindItem  
 Recherche un élément de liste ayant les caractéristiques spécifiées.  
  
```  
int FindItem(
    LVFINDINFO* pFindInfo,  
    int nStart = -1) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pFindInfo*  
 Un pointeur vers un [LVFINDINFO](/windows/desktop/api/commctrl/ns-commctrl-taglvfindinfoa) structure contenant des informations sur l’élément à rechercher.  
  
 *Début*  
 Index de l’élément pour commencer la recherche, ou -1 pour démarrer à partir du début. L’élément à *début* est exclu de la recherche si *début* n’est pas égal à -1.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de l’élément en cas de réussite ou sinon -1.  
  
### <a name="remarks"></a>Notes  
 Le *pFindInfo* paramètre pointe vers une `LVFINDINFO` structure qui contient les informations utilisées pour rechercher pour un élément de liste.  
  
### <a name="example"></a>Exemple  

```cpp  
        LVFINDINFO info;
        int nIndex;

        info.flags = LVFI_PARTIAL|LVFI_STRING;
        info.psz = _T("item");

        // Delete all of the items that begin with the string.
        while ((nIndex = m_myListCtrl.FindItem(&info)) != -1)
        {
            m_myListCtrl.DeleteItem(nIndex);
        }
```

  
##  <a name="getbkcolor"></a>  CListCtrl::GetBkColor  
 Récupère la couleur d’arrière-plan d’un contrôle list view.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur 32 bits utilisée pour spécifier une couleur RVB.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::SetBkColor](#setbkcolor).  
  
##  <a name="getbkimage"></a>  CListCtrl::GetBkImage  
 Récupère l’image d’arrière-plan actuelle d’un contrôle list view.  
  
```  
BOOL GetBkImage(LVBKIMAGE* plvbkImage) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *plvbkImage*  
 Un pointeur vers un `LVBKIMAGE` structure contenant l’image d’arrière-plan actuelle de la vue liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne zéro en cas de réussite, ou zéro sinon.  
  
### <a name="remarks"></a>Notes  
 Cette méthode implémente le comportement de la macro Win32, [ListView_GetBkImage](/windows/desktop/api/commctrl/nf-commctrl-listview_getbkimage), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  

```cpp  
        LVBKIMAGE bki;

        // If no background image is set for the list view control use
        // the Microsoft homepage image as the background image.
        if (m_myListCtrl.GetBkImage(&bki) && (bki.ulFlags == LVBKIF_SOURCE_NONE))
        {
            m_myListCtrl.SetBkImage(
                _T("http://www.microsoft.com/library/images/gifs/homepage/microsoft.gif"),
                TRUE);
        }
```

  
##  <a name="getcallbackmask"></a>  CListCtrl::GetCallbackMask  
 Récupère le masque de rappel pour un contrôle list view.  
  
```  
UINT GetCallbackMask() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Masque de rappel du contrôle list view.  
  
### <a name="remarks"></a>Notes  
 Un élément de « rappel » est un élément de liste pour lequel l’application, plutôt que le contrôle, stocke le texte, icône ou les deux. Bien qu’un contrôle list view peut stocker ces attributs pour vous, vous souhaiterez utiliser les éléments de rappel si votre application a déjà gère certaines de ces informations. Le masque de rappel spécifie les bits d’état élément sont gérés par l’application, et elle s’applique à l’ensemble du contrôle plutôt qu’à un élément spécifique. Le masque de rappel est zéro par défaut, ce qui signifie que le contrôle effectue le suivi de tous les États d’élément. Si une application utilise des éléments de rappel ou spécifie un masque de rappel différent de zéro, il doit être en mesure de fournir des attributs d’élément de vue liste à la demande.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::SetCallbackMask](#setcallbackmask).  
  
##  <a name="getcheck"></a>  CListCtrl::GetCheck  
 Récupère l’état d’affichage actuel de l’image d’état associé à un élément.  
  
```  
BOOL GetCheck(int nItem) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 Index de base zéro d’un élément de contrôle de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément est sélectionné, sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_GetCheckState](/windows/desktop/api/commctrl/nf-commctrl-listview_getcheckstate), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::SetCheck](#setcheck).  
  
##  <a name="getcolumn"></a>  CListCtrl::GetColumn  
 Récupère les attributs de colonne d’un contrôle list view.  
  
```  
BOOL GetColumn(
    int nCol,  
    LVCOLUMN* pColumn) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nCol*  
 Index de la colonne dont les attributs doivent être récupérés.  
  
 *pColumn*  
 Adresse d’un [LVCOLUMN](/windows/desktop/api/commctrl/ns-commctrl-taglvcolumna) structure qui spécifie les informations à récupérer et reçoit des informations sur la colonne. Le `mask` membre spécifie quelle colonne d’attributs à récupérer. Si le `mask` membre spécifie la valeur LVCF_TEXT, le `pszText` membre doit contenir l’adresse de la mémoire tampon qui reçoit le texte de l’élément et le `cchTextMax` membre doit spécifier la taille de la mémoire tampon.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Le `LVCOLUMN` structure contient des informations sur une colonne dans la vue rapport.  
  
### <a name="example"></a>Exemple  

```cpp  
        LVCOLUMN col;

        col.mask = LVCF_WIDTH;

        // Double the column width of the first column.
        if (m_myListCtrl.GetColumn(0, &col))
        {
            col.cx *= 2;
            m_myListCtrl.SetColumn(0, &col);
        }
```

  
##  <a name="getcolumnorderarray"></a>  CListCtrl::GetColumnOrderArray  
 Récupère l’ordre des colonnes (de gauche à droite) d’un contrôle list view.  
  
```  
BOOL GetColumnOrderArray(
    LPINT piArray,  
    int iCount = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 *piArray*  
 Pointeur vers une mémoire tampon qui contient les valeurs d’index des colonnes dans le contrôle list view. La mémoire tampon doit être assez grande pour contenir le nombre total de colonnes dans le contrôle list view.  
  
 *iCount*  
 Nombre de colonnes dans le contrôle list view. Si ce paramètre est -1, le nombre de colonnes est automatiquement récupéré par l’infrastructure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_GetColumnOrderArray](/windows/desktop/api/commctrl/nf-commctrl-listview_getcolumnorderarray), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  

```cpp  
        // Reverse the order of the columns in the list view control
        // (i.e. make the first column the last, the last column
        // the first, and so on...).
        CHeaderCtrl* pHeaderCtrl = m_myListCtrl.GetHeaderCtrl();

        if (pHeaderCtrl != NULL)
        {
            int  nColumnCount = pHeaderCtrl->GetItemCount();
            LPINT pnOrder = (LPINT) malloc(nColumnCount*sizeof(int));
            ASSERT(pnOrder != NULL);
m_myListCtrl.GetColumnOrderArray(pnOrder, nColumnCount);

            int i, j, nTemp;
            for (i = 0, j = nColumnCount-1; i < j; i++, j--)
            {
                nTemp = pnOrder[i];
                pnOrder[i] = pnOrder[j];
                pnOrder[j] = nTemp;
            }

            m_myListCtrl.SetColumnOrderArray(nColumnCount, pnOrder);
            free(pnOrder);
        }
```

  
##  <a name="getcolumnwidth"></a>  CListCtrl::GetColumnWidth  
 Récupère la largeur d’une colonne dans la liste ou un affichage de rapport.  
  
```  
int GetColumnWidth(int nCol) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nCol*  
 Spécifie l’index de la colonne dont la largeur doit être récupéré.  
  
### <a name="return-value"></a>Valeur de retour  
 La largeur, en pixels, de la colonne spécifiée par *nCol*.  
  
### <a name="example"></a>Exemple  

```cpp  
        // Increase the column width of the second column by 20.
        int nWidth = m_myListCtrl.GetColumnWidth(1);
        m_myListCtrl.SetColumnWidth(1, 20 + nWidth);
```

  
##  <a name="getcountperpage"></a>  CListCtrl::GetCountPerPage  
 Calcule le nombre d’éléments qui peuvent s’ajuster verticalement dans la zone visible d’un contrôle list view en mode liste ou rapport.  
  
```  
int GetCountPerPage() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments qui peuvent s’ajuster verticalement dans la zone visible d’un contrôle list view en mode liste ou rapport.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::GetTopIndex](#gettopindex).  
  
##  <a name="geteditcontrol"></a>  CListCtrl::GetEditControl  
 Récupère le handle du contrôle d’édition utilisé pour modifier texte d’un élément de liste.  
  
```  
CEdit* GetEditControl() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si l’opération réussit, un pointeur vers le [CEdit](cedit-class.md) objet qui est utilisé pour modifier le texte de l’élément ; sinon, NULL.  
  
### <a name="example"></a>Exemple  

```cpp  
        // The string replacing the text in the edit control.
        LPCTSTR lpszmyString = _T("custom label!");

        // If possible, replace the text in the label edit control.
        CEdit* pEdit = m_myListCtrl.GetEditControl();

        if (pEdit != NULL)
        {
            pEdit->SetWindowText(lpszmyString);
        }
```

  
##  <a name="getemptytext"></a>  CListCtrl::GetEmptyText  
 Récupère la chaîne à afficher si le contrôle de liste actuel est vide.  
  
```  
CString GetEmptyText() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui contient le texte à afficher si le contrôle est vide.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [LVM_GETEMPTYTEXT](/windows/desktop/Controls/lvm-getemptytext) message, qui est décrite dans le SDK Windows.  
  
##  <a name="getextendedstyle"></a>  CListCtrl::GetExtendedStyle  
 Récupère les styles étendus en cours d’un contrôle list view.  
  
```  
DWORD GetExtendedStyle();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une combinaison des styles étendus en cours d’utilisation par la liste de contrôle view. Pour obtenir une liste descriptive des ces styles étendus, consultez la [Styles étendus de la vue liste](/windows/desktop/Controls/extended-list-view-styles) rubrique dans le SDK Windows.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_GetExtendedListViewStyle](/windows/desktop/api/commctrl/nf-commctrl-listview_getextendedlistviewstyle), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::SetExtendedStyle](#setextendedstyle).  
  
##  <a name="getfirstselecteditemposition"></a>  CListCtrl::GetFirstSelectedItemPosition  
 Obtient la position du premier élément sélectionné dans le contrôle list view.  
  
```  
POSITION GetFirstSelectedItemPosition() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur POSITION qui peut être utilisée pour l’itération ou l’extraction de pointeur d’objet ; NULL si aucun élément n’est sélectionnées.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant illustre l’utilisation de cette fonction.  
  

```cpp  
        POSITION pos = m_myListCtrl.GetFirstSelectedItemPosition();
        if (pos == NULL)
        {
            TRACE(_T("No items were selected!\n"));
        }
        else
        {
            while (pos)
            {
                int nItem = m_myListCtrl.GetNextSelectedItem(pos);
                TRACE(_T("Item %d was selected!\n"), nItem);
                // you could do your own processing on nItem here
            }
        }
```

  
##  <a name="getfocusedgroup"></a>  CListCtrl::GetFocusedGroup  
 Récupère le groupe qui a le focus clavier dans le contrôle de liste actuel.  
  
```  
int GetFocusedGroup() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’index du groupe dont l’état est LVGS_FOCUSED, s’il existe un tel groupe ; Sinon, -1.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [LVM_GETFOCUSEDGROUP](/windows/desktop/Controls/lvm-getfocusedgroup) message, qui est décrite dans le SDK Windows. Pour plus d’informations, consultez la valeur LVGS_FOCUSED de la `state` membre de la [LVGROUP](/windows/desktop/api/commctrl/ns-commctrl-taglvgroup) structure.  
  
##  <a name="getgroupcount"></a>  CListCtrl::GetGroupCount  
 Récupère le nombre de groupes dans le contrôle de liste actuel.  
  
```  
int GetGroupCount()const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de groupes dans le contrôle de liste.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [LVM_GETGROUPCOUNT](/windows/desktop/Controls/lvm-getgroupcount) message, qui est décrite dans le SDK Windows-->.  
  
##  <a name="getgroupinfo"></a>  CListCtrl::GetGroupInfo  
 Obtient les informations pour un groupe spécifié de contrôle list view.  
  
```  
int GetGroupInfo(
    int iGroupId,  
    PLVGROUP pgrp) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *iGroupId*  
 L’identificateur du groupe dont les informations sont à récupérer.  
  
 *PGRP*  
 Un pointeur vers le [LVGROUP](/windows/desktop/api/commctrl/ns-commctrl-taglvgroup) contenant des informations sur le groupe spécifié.  
  
### <a name="return-value"></a>Valeur de retour  
 Sinon, retourne l’ID du groupe en cas de réussite, ou -1.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_GETGROUPINFO](/windows/desktop/Controls/lvm-getgroupinfo) du message, comme décrit dans le SDK Windows.  
  
##  <a name="getgroupinfobyindex"></a>  CListCtrl::GetGroupInfoByIndex  
 Récupère des informations sur un groupe spécifié dans le contrôle de liste actuel.  
  
```  
BOOL GetGroupInfoByIndex(
    int iIndex,   
    PLVGROUP pGroup) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*iIndex*|[in] Index de base zéro d’un groupe.|  
|*pGroup*|[out] Pointeur vers un [LVGROUP](/windows/desktop/api/commctrl/ns-commctrl-taglvgroup) structure qui reçoit des informations sur le groupe spécifié par le *iIndex* paramètre.<br /><br /> L’appelant est chargé d’initialiser les membres de la [LVGROUP](/windows/desktop/api/commctrl/ns-commctrl-taglvgroup) structure. Définir le `cbSize` membre à la taille de la structure et les indicateurs de le `mask` membre pour spécifier les informations à récupérer.|  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si cette méthode a réussi ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [LVM_GETGROUPINFOBYINDEX](https://msdn.microsoft.com/library/windows/desktop/bb774933) message, qui est décrite dans le SDK Windows-->.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit une variable, `m_listCtrl`, qui est utilisé pour accéder au contrôle d’affichage de liste actuel. Cette variable est utilisée dans l'exemple suivant.  

```cpp  
public:
    // Variable used to access the list control.
    CListCtrl m_listCtrl; 
```

  
### <a name="example"></a>Exemple  
 L’exemple de code suivant montre le `GetGroupInfoByIndex` (méthode). Dans la section précédente de ce code exemple nous avons créé un contrôle de liste qui affiche deux colonnes intitulées « ClientID » et « Grade » dans une vue de rapport. L’exemple de code suivant récupère des informations sur le groupe dont l’index est 0, si un tel groupe existe.    
```cpp  
    // GetGroupInfoByIndex
    const int GROUP_HEADER_BUFFER_SIZE = 40;

// Initialize the structure 
    LVGROUP gInfo = {0};
    gInfo.cbSize = sizeof(LVGROUP);
    wchar_t wstrHeadGet[GROUP_HEADER_BUFFER_SIZE] = {0};
    gInfo.cchHeader = GROUP_HEADER_BUFFER_SIZE;
    gInfo.pszHeader = wstrHeadGet;
    gInfo.mask = (LVGF_ALIGN | LVGF_STATE | LVGF_HEADER | LVGF_GROUPID);
    gInfo.state = LVGS_NORMAL;
    gInfo.uAlign  = LVGA_HEADER_LEFT;

    BOOL bRet = m_listCtrl.GetGroupInfoByIndex( 0, &gInfo );
    if (bRet == TRUE) {
        CString strHeader = CString( gInfo.pszHeader );
        CString str;
        str.Format(_T("Header: '%s'"), strHeader);
        AfxMessageBox(str, MB_ICONINFORMATION);
    }
    else
    {
        AfxMessageBox(_T("No group information was retrieved."));
    }
```

  
##  <a name="getgroupmetrics"></a>  CListCtrl::GetGroupMetrics  
 Récupère les mesures d’un groupe.  
  
```  
void GetGroupMetrics(PLVGROUPMETRICS pGroupMetrics) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pGroupMetrics*  
 Un pointeur vers un [LVGROUPMETRICS](/windows/desktop/api/commctrl/ns-commctrl-taglvgroupmetrics) contenant les informations de métriques de groupe.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_GETGROUPMETRICS](/windows/desktop/Controls/lvm-getgroupmetrics) du message, comme décrit dans le SDK Windows.  
  
##  <a name="getgrouprect"></a>  CListCtrl::GetGroupRect  
 Récupère le rectangle englobant pour un groupe spécifié dans le contrôle de liste actuel.  
  
```  
BOOL GetGroupRect(
    int iGroupId,   
    LPRECT lpRect,   
    int iCoords = LVGGR_GROUP) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*iGroupId*|[in] Spécifie un groupe.|  
|*lpRect*|[in, out] Pointeur vers un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure. Si cette méthode réussite, la structure reçoit les coordonnées du rectangle du groupe spécifié par *iGroupId*.|  
|*iCoords*|[in] Spécifie les coordonnées du rectangle à récupérer. Utilisez une des valeurs suivantes :<br /><br /> -LVGGR_GROUP - (valeur par défaut) des coordonnées de l’ensemble du groupe développé.<br />-LVGGR_HEADER - coordonnées d’uniquement l’en-tête (groupe réduit).<br />-LVGGR_SUBSETLINK - coordonnées du uniquement le lien de sous-ensemble (sous-ensemble de balisage).|  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si cette méthode a réussi ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 L’appelant est chargé d’allouer le [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure vers laquelle pointe le *pRect* paramètre.  
  
 Cette méthode envoie le [LVM_GETGROUPRECT](/windows/desktop/Controls/lvm-getgrouprect) message, qui est décrite dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit une variable, `m_listCtrl`, qui est utilisé pour accéder au contrôle d’affichage de liste actuel. Cette variable est utilisée dans l'exemple suivant.    
```cpp  
public:
    // Variable used to access the list control.
    CListCtrl m_listCtrl; 
```

  
### <a name="example"></a>Exemple  
 L’exemple de code suivant montre le `GetGroupRect` (méthode). Dans la section précédente de cet exemple de code, nous avons créé un contrôle d’affichage de liste qui affiche deux colonnes intitulées « ClientID » et « Grade » dans une vue de rapport. L’exemple de code suivant dessine un rectangle 3D autour du groupe dont l’index est 0, si un tel groupe existe.    
  
```cpp  
    // GetGroupRect

    // Get the graphics rectangle that surrounds group 0.
    CRect rect;
    BOOL bRet = m_listCtrl.GetGroupRect( 0, &rect, LVGGR_GROUP); 
    // Draw a blue rectangle around group 0.
    if (bRet == TRUE) {
        m_listCtrl.GetDC()->Draw3dRect( &rect, RGB(0, 0, 255), RGB(0, 0, 255));
    }
    else {
        AfxMessageBox(_T("No group information was retrieved."), MB_ICONINFORMATION);
    }
```

  
##  <a name="getgroupstate"></a>  CListCtrl::GetGroupState  
 Récupère l’état pour un groupe spécifié dans le contrôle de liste actuel.  
  
```  
UINT GetGroupState(
    int iGroupId,   
    DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*iGroupId*|[in] Index de base zéro d’un groupe.|  
|*dwMask*|[in] Masque qui spécifie la valeur d’état à récupérer pour le groupe spécifié. Pour plus d’informations, consultez le `mask` membre de la [LVGROUP](/windows/desktop/api/commctrl/ns-commctrl-taglvgroup) structure.|  
  
### <a name="return-value"></a>Valeur de retour  
 L’état requis pour le groupe spécifié, ou 0 si le groupe est introuvable.  
  
### <a name="remarks"></a>Notes  
 La valeur de retour est le résultat d’une opération AND au niveau du bit sur le *dwMask* et la valeur de la `state` membre d’un [LVGROUP](/windows/desktop/api/commctrl/ns-commctrl-taglvgroup) structure qui représente le contrôle de liste actuel.  
  
 Cette méthode envoie le [LVM_GETGROUPSTATE](/windows/desktop/Controls/lvm-getgroupstate) message, qui est décrite dans le SDK Windows. Pour plus d’informations, consultez le [ListView_GetGroupState](/windows/desktop/api/commctrl/nf-commctrl-listview_getgroupstate) (macro).  
  
##  <a name="getheaderctrl"></a>  CListCtrl::GetHeaderCtrl  
 Récupère le contrôle d’en-tête d’un contrôle list view.  
  
```  
CHeaderCtrl* GetHeaderCtrl();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le contrôle header, utilisé par le contrôle list view.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_GetHeader](/windows/desktop/api/commctrl/nf-commctrl-listview_getheader), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::GetColumnOrderArray](#getcolumnorderarray).  
  
##  <a name="gethotcursor"></a>  CListCtrl::GetHotCursor  
 Récupère le curseur utilisé lorsque la sélection réactive est activée pour un contrôle list view.  
  
```  
HCURSOR GetHotCursor();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle vers la ressource curseur actif actuel utilisé par le contrôle list view.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_GetHotCursor](/windows/desktop/api/commctrl/nf-commctrl-listview_gethotcursor), comme décrit dans le SDK Windows. Le curseur à chaud, visible uniquement lorsque la sélection de pointage est activée, s’affiche lorsque le curseur passe sur n’importe quel élément du ListView. Sélection de pointage est activée en définissant le LVS_EX_TRACKSELECT style étendu.  
  
### <a name="example"></a>Exemple    
  
```cpp  
        // Set the hot cursor to be the system app starting cursor.
        HCURSOR hCursor = ::LoadCursor(NULL, IDC_APPSTARTING);
        m_myListCtrl.SetHotCursor(hCursor);
        ASSERT(m_myListCtrl.GetHotCursor() == hCursor);
```

  
##  <a name="gethotitem"></a>  CListCtrl::GetHotItem  
 Récupère l’élément du ListView sous le curseur.  
  
```  
int GetHotItem();
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de l’élément actif actuel du contrôle list view.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_GetHotItem](/windows/desktop/api/commctrl/nf-commctrl-listview_gethotitem), comme décrit dans le SDK Windows. L’élément actif est défini comme l’élément actuellement sélectionné lorsqu’à chaud de suivi (et placez le curseur sélection) est activée.  
  
 Si la sélection réactive est activée, lorsqu’un utilisateur est maintenu sur un élément de liste, l’étiquette de l’élément est automatiquement mis en surbrillance sans l’utilisation d’un bouton de la souris.  
  
### <a name="example"></a>Exemple    
  
```cpp  
    // Set the hot item to the first item only if no other item is 
    // highlighted.
    if (m_myListCtrl.GetHotItem() == -1)
        m_myListCtrl.SetHotItem(0);
```

  
##  <a name="gethovertime"></a>  CListCtrl::GetHoverTime  
 Récupère le délai de pointage actuel d’un contrôle list view.  
  
```  
DWORD GetHoverTime() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le délai, en millisecondes, pendant lequel le curseur de la souris doit pointer sur un élément avant qu’il est sélectionné. Si la valeur de retour est -1, le délai de pointage est le délai de pointage par défaut.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_GetHoverTime](/windows/desktop/api/commctrl/nf-commctrl-listview_gethovertime), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple    
  
```cpp  
        // If the hover time is the default set to 1 sec.
        DWORD dwTime = m_myListCtrl.GetHoverTime();
        if (dwTime == -1)
            m_myListCtrl.SetHoverTime(1000);
```

  
##  <a name="getimagelist"></a>  CListCtrl::GetImageList  
 Récupère le handle d’une liste d’images utilisée pour afficher les éléments de liste dessin.  
  
```  
CImageList* GetImageList(int nImageList) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nImageList*  
 Valeur qui spécifie quelle liste d’images à récupérer. Il peut être une des valeurs suivantes :  
  
- Liste d’images de LVSIL_NORMAL avec grandes icônes.  
  
- Liste d’images de LVSIL_SMALL avec petites icônes.  
  
- Liste d’images de LVSIL_STATE avec des images d’état.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la liste d’images utilisée pour afficher les éléments de liste de dessin.  
  
### <a name="example"></a>Exemple    
  
```cpp  
        ASSERT(m_myListCtrl.GetImageList(LVSIL_NORMAL) == NULL);
m_myListCtrl.SetImageList(&m_lcImageList, LVSIL_NORMAL);
        ASSERT(m_myListCtrl.GetImageList(LVSIL_NORMAL) == &m_lcImageList);
```

  
##  <a name="getinsertmark"></a>  CListCtrl::GetInsertMark  
 Récupère la position actuelle de la marque d’insertion.  
  
```  
BOOL GetInsertMark(LPLVINSERTMARK lvim) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *lvim*  
 Un pointeur vers un [LVINSERTMARK](/windows/desktop/api/commctrl/ns-commctrl-lvinsertmark) structure contenant les informations de la marque d’insertion.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne TRUE en cas de réussite, ou FALSE dans le cas contraire. Valeur FALSE est retournée si la taille de la `cbSize` membre de la `LVINSERTMARK` structure n’est pas égale la taille réelle de la structure.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_GETINSERTMARK](/windows/desktop/Controls/lvm-getinsertmark) du message, comme décrit dans le SDK Windows.  
  
##  <a name="getinsertmarkcolor"></a>  CListCtrl::GetInsertMarkColor  
 Récupère la couleur actuelle de la marque d’insertion.  
  
```  
COLORREF GetInsertMarkColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un [COLORREF](/windows/desktop/gdi/colorref) structure qui contient la couleur du point d’insertion.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_GETINSERTMARKCOLOR](/windows/desktop/Controls/lvm-getinsertmarkcolor) du message, comme décrit dans le SDK Windows.  
  
##  <a name="getinsertmarkrect"></a>  CListCtrl::GetInsertMarkRect  
 Récupère le rectangle qui délimite le point d’insertion.  
  
```  
int GetInsertMarkRect(LPRECT pRect) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pRect*  
 Pointeur vers un `RECT` structure qui contient les coordonnées d’un rectangle qui délimite le point d’insertion.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
- **0** aucun point d’insertion trouvé.  
  
- **1** point d’insertion trouvé.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_GETINSERTMARKRECT](/windows/desktop/Controls/lvm-getinsertmarkrect) du message, comme décrit dans le SDK Windows.  
  
##  <a name="getitem"></a>  CListCtrl::GetItem  
 Récupère tout ou partie des attributs d’un élément Affichage de liste.  
  
```  
BOOL GetItem(LVITEM* pItem) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pItem*  
 Pointeur vers un [LVITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) structure qui reçoit les attributs de l’élément.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Le `LVITEM` structure spécifie ou reçoit les attributs d’un élément de liste.  
  
##  <a name="getitemcount"></a>  CListCtrl::GetItemCount  
 Récupère le nombre d’éléments dans un contrôle list view.  
  
```  
int GetItemCount() const; 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans le contrôle list view.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::DeleteItem](#deleteitem).  
  
##  <a name="getitemdata"></a>  CListCtrl::GetItemData  
 Récupère la valeur de spécifique à l’application 32 bits associée à l’élément spécifié par `nItem`.  
  
```  
DWORD_PTR GetItemData(int nItem) const; 
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 Index de l’élément de liste dont les données doit être récupéré.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur spécifique à l’application 32 bits associée à l’élément spécifié.  
  
### <a name="remarks"></a>Notes  
 Cette valeur est la `lParam` membre de la [LVITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) structure, comme décrit dans le Kit de développement Windows  
  
### <a name="example"></a>Exemple  

```cpp  
    // If any item's data is equal to zero then reset it to -1.
    for (int i=0; i < m_myListCtrl.GetItemCount(); i++)
    {
        if (m_myListCtrl.GetItemData(i) == 0)
        {
            m_myListCtrl.SetItemData(i, (DWORD) -1);
        }
    }
```

  
##  <a name="getitemindexrect"></a>  CListCtrl::GetItemIndexRect  
 Récupère le rectangle englobant pour tout ou partie d’un sous-élément dans le contrôle de liste actuel.  
  
```  
BOOL GetItemIndexRect(
    PLVITEMINDEX pItemIndex,   
    int iColumn,   
    int rectType,   
    LPRECT pRect) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*pItemIndex*|[in] Pointeur vers un [LVITEMINDEX](https://msdn.microsoft.com/library/windows/desktop/bb774762) structure pour l’élément parent du sous-élément.<br /><br /> L’appelant est chargé d’allouer et définissant les membres de la [LVITEMINDEX](https://msdn.microsoft.com/library/windows/desktop/bb774762) structure. Ce paramètre ne peut pas être NULL.|  
|*iColumn*|[in] Index de base zéro d’une colonne dans le contrôle.|  
|*rectType*|[in] Partie du sous-élément d’affichage de liste pour laquelle le rectangle englobant est récupéré. Spécifiez l'une des valeurs suivantes :<br /><br /> LVIR_BOUNDS - retourne le rectangle englobant du sous-élément entière, y compris l’icône et une étiquette.<br /><br /> LVIR_ICON - retourne le rectangle englobant de l’icône ou d’une petite icône du sous-élément.<br /><br /> LVIR_LABEL - retourne le rectangle englobant du texte du sous-élément.|  
|*pRect*|[out] Pointeur vers un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui reçoit des informations sur le rectangle englobant du sous-élément.<br /><br /> L’appelant est chargé d’allouer le [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure. Ce paramètre ne peut pas être NULL.|  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si cette méthode a réussi ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [LVM_GETITEMINDEXRECT](/windows/desktop/Controls/lvm-getitemindexrect) message, qui est décrite dans le SDK Windows. Pour plus d’informations, consultez [ListView_GetItemIndexRect Macro](/windows/desktop/api/commctrl/nf-commctrl-listview_getitemindexrect).  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit une variable, `m_listCtrl`, qui est utilisé pour accéder au contrôle d’affichage de liste actuel. Cette variable est utilisée dans l'exemple suivant.    
  
```cpp  
public:
    // Variable used to access the list control.
    CListCtrl m_listCtrl; 
```

  
### <a name="example"></a>Exemple  
 L’exemple de code suivant montre le `GetGroupRect` (méthode). Avant d’entrer ce code exemple nous avons créé un contrôle de liste qui affiche deux colonnes intitulées « ClientID » et « Grade » dans une vue de rapport. L’exemple de code suivant dessine un rectangle 3D autour du deuxième sous-élément dans les deux colonnes.    
  
```cpp  
    // GetItemIndexRect
    // Get the rectangle that bounds the second item in the first group.
    LVITEMINDEX lvItemIndex;
    lvItemIndex.iGroup = 0;
    lvItemIndex.iItem = 1;
    CRect rect;
    BOOL bRet = m_listCtrl.GetItemIndexRect(
        &lvItemIndex, 0, LVIR_BOUNDS, &rect);

    // Draw a red rectangle around the item.
    m_listCtrl.GetDC()->Draw3dRect( &rect, RGB(255, 0, 0), RGB(255, 0, 0) );
```

  
##  <a name="getitemposition"></a>  CListCtrl::GetItemPosition  
 Récupère la position d’un élément de liste.  
  
```  
BOOL GetItemPosition(
    int nItem,  
    LPPOINT lpPoint) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 L’index de l’élément dont la position doit être récupéré.  
  
 *lpPoint*  
 Adresse d’un [POINT](https://msdn.microsoft.com/library/windows/desktop/dd162805) coordonne la structure qui reçoit la position du coin supérieur gauche de l’élément, dans la vue.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="example"></a>Exemple    
  
```cpp  
        POINT pt;

        // Move all items in the list control 100 pixels to the right.
        UINT i, nCount = m_myListCtrl.GetItemCount();

        for (i=0; i < nCount; i++)
        {
            m_myListCtrl.GetItemPosition(i, &pt);
            pt.x += 100;
            m_myListCtrl.SetItemPosition(i, pt);
        }   
```

  
##  <a name="getitemrect"></a>  CListCtrl::GetItemRect  
 Récupère le rectangle englobant pour tout ou partie d’un élément dans la vue actuelle.  
  
```  
BOOL GetItemRect(
    int nItem,  
    LPRECT lpRect,  
    UINT nCode) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 L’index de l’élément dont la position doit être récupéré.  
  
 *lpRect*  
 Adresse d’un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui reçoit le rectangle englobant.  
  
 *nCode*  
 Partie de l’élément d’affichage de liste pour lequel récupérer le rectangle englobant. Il peut être une des valeurs suivantes :  
  
- LVIR_BOUNDS retourne le rectangle englobant de l’élément entier, y compris l’icône et une étiquette.  
  
- LVIR_ICON retourne le rectangle englobant de l’icône ou d’une petite icône.  
  
- LVIR_LABEL retourne le rectangle englobant de l’élément.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="example"></a>Exemple    
  
```cpp  
// OnClick is the handler for the NM_CLICK notification
void CListCtrlDlg::OnClick(NMHDR* pNMHDR, LRESULT* pResult)
{
    UNREFERENCED_PARAMETER(pResult);
LPNMITEMACTIVATE pia = (LPNMITEMACTIVATE)pNMHDR;

    // Get the current mouse location and convert it to client
    // coordinates.
    CPoint pos( ::GetMessagePos() ); 
    ScreenToClient(&pos);

    // Get indexes of the first and last visible items in 
    // the listview control.
    int index = m_myListCtrl.GetTopIndex();
    int last_visible_index = index + m_myListCtrl.GetCountPerPage();
    if (last_visible_index > m_myListCtrl.GetItemCount())
        last_visible_index = m_myListCtrl.GetItemCount();

    // Loop until number visible items has been reached.
    while (index <= last_visible_index)
    {
        // Get the bounding rectangle of an item. If the mouse
        // location is within the bounding rectangle of the item,
        // you know you have found the item that was being clicked.
        CRect r;
        m_myListCtrl.GetItemRect(index, &r, LVIR_BOUNDS);
        if (r.PtInRect(pia->ptAction))
        {
            UINT flag = LVIS_SELECTED | LVIS_FOCUSED;
            m_myListCtrl.SetItemState(index, flag, flag);
            break;
        }

        // Get the next item in listview control.
        index++;
    }
}
```

  
##  <a name="getitemspacing"></a>  CListCtrl::GetItemSpacing  
 Calcule l’espacement entre les éléments dans le contrôle de liste actuel.  
  
```  
BOOL GetItemSpacing(
    BOOL fSmall,   
    int* pnHorzSpacing,   
    int* pnVertSpacing) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*fSmall*|[in] Vue pour lequel récupérer l’espacement de l’élément. Spécifiez TRUE pour l’affichage de la petite icône, ou FALSE pour l’affichage de l’icône.|  
|*pnHorzSpacing*|[out] Contient l’espacement horizontal entre les éléments.|  
|*pnVertSpacing*|[out] Contient l’espacement vertical entre les éléments.|  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si cette méthode a réussi ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [LVM_GETITEMSPACING](/windows/desktop/Controls/lvm-getitemspacing) message, qui est décrite dans le SDK Windows.  
  
##  <a name="getitemstate"></a>  CListCtrl::GetItemState  
 Récupère l’état d’un élément de liste.  
  
```  
UINT GetItemState(
    int nItem,  
    UINT nMask) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 L’index de l’élément dont l’état doit être récupéré.  
  
 *nMask*  
 Masque spécifiant les de l’état de l’élément indicateurs à retourner.  
  
### <a name="return-value"></a>Valeur de retour  
 Les indicateurs d’état pour la liste spécifiée afficher l’élément.  
  
### <a name="remarks"></a>Notes  
 État d’un élément est spécifié par le `state` membre de la [LVITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) structure, comme décrit dans le SDK Windows. Lorsque vous définissez ou modifiez l’état d’un élément, le `stateMask` membre spécifie les bits d’état que vous souhaitez modifier.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::GetTopIndex](#gettopindex).  
  
##  <a name="getitemtext"></a>  CListCtrl::GetItemText  
 Récupère le texte d’un élément de vue de liste ou d’un sous-élément.  
  
```  
int GetItemText(
    int nItem,  
    int nSubItem,  
    LPTSTR lpszText,  
    int nLen) const; 
 
CString GetItemText(
    int nItem,  
    int nSubItem) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 L’index de l’élément dont le texte doit être récupéré.  
  
 *nSubItem*  
 Spécifie le sous-élément dont le texte doit être récupéré.  
  
 *lpszText*  
 Pointeur vers une chaîne qui doit recevoir le texte de l’élément.  
  
 *nLen*  
 Longueur de la mémoire tampon vers laquelle pointe *lpszText*.  
  
### <a name="return-value"></a>Valeur de retour  
 La version retournant **int** retourne la longueur de la chaîne récupérée.  
  
 La version retournant un `CString` retourne le texte de l’élément.  
  
### <a name="remarks"></a>Notes  
 Si *nSubItem* est égal à zéro, cette fonction récupère l’étiquette d’élément ; si *nSubItem* est différent de zéro, il récupère le texte du sous-élément. Pour plus d’informations sur l’argument de sous-élément, consultez la rubrique sur la [LVITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) structure dans le SDK Windows.  
  
##  <a name="getnextitem"></a>  CListCtrl::GetNextItem  
 Recherches pour obtenir la liste Afficher l’élément qui possède les propriétés spécifiées et qui présente la relation spécifiée à un élément donné.  
  
```  
int GetNextItem(
    int nItem,  
    int nFlags) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 Index de l’élément pour commencer la recherche à l’aide, ou -1 pour rechercher le premier élément qui correspond aux indicateurs spécifiés. L’élément spécifié lui-même est exclu de la recherche.  
  
 *nIndicateurs*  
 Relation géométrique de l’élément demandé à l’élément spécifié et l’état de l’élément demandé. La relation géométrique peut être une des valeurs suivantes :  
  
- LVNI_ABOVE recherche un élément qui se trouve au-dessus de l’élément spécifié.  
  
- LVNI_ALL recherche un élément par index (la valeur par défaut) suivant.  
  
- LVNI_BELOW recherche un élément qui se trouve sous l’élément spécifié.  
  
- LVNI_TOLEFT recherche un élément à gauche de l’élément spécifié.  
  
- LVNI_TORIGHT recherche un élément à droite de l’élément spécifié.  
  
 L’état peut être égal à zéro, ou il peut être une ou plusieurs des valeurs suivantes :  
  
- LVNI_DROPHILITED l’élément a l’indicateur d’état LVIS_DROPHILITED définie.  
  
- LVNI_FOCUSED l’élément a l’indicateur d’état LVIS_FOCUSED définie.  
  
- LVNI_SELECTED l’élément a l’indicateur d’état LVIS_SELECTED définie.  
  
 Si un élément n’a pas toutes les indicateurs de cet état spécifié, la recherche se poursuit avec l’élément suivant.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de l’élément suivant en cas de réussite, ou sinon -1.  
  
##  <a name="getnextitemindex"></a>  CListCtrl::GetNextItemIndex  
 Récupère l’index de l’élément dans le contrôle d’affichage de liste actuel qui a un ensemble de propriétés spécifié.  
  
```  
BOOL GetNextItemIndex(
    PLVITEMINDEX pItemIndex,   
    int nFlags) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*pItemIndex*|[in, out] Pointeur vers le [LVITEMINDEX](https://msdn.microsoft.com/library/windows/desktop/bb774762) structure qui décrit l’élément où la recherche commence, ou -1 pour rechercher le premier élément qui correspond aux indicateurs dans le *nIndicateurs* paramètre.<br /><br /> Si cette méthode réussite, le `LVITEMINDEX` structure décrit l’élément trouvé par la recherche.|  
|*nIndicateurs*|[in] Une combinaison (OR) au niveau du bit des indicateurs qui spécifient comment effectuer la recherche.<br /><br /> La recherche peut dépendre de l’index, l’état ou l’apparence de l’élément cible, ou emplacement physique de l’élément cible par rapport à l’élément spécifié par le *pItemIndex* paramètre. Pour plus d’informations, consultez le *indicateurs* paramètre dans le [LVM_GETNEXTITEMINDEX](https://msdn.microsoft.com/library/windows/desktop/bb761059) message.|  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si cette méthode a réussi ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 L’appelant est chargé d’allouer et définissant les membres de la `LVITEMINDEX` structure vers laquelle pointe le *pItemIndex* paramètre.  
  
 Cette méthode envoie le [LVM_GETNEXTITEMINDEX](https://msdn.microsoft.com/library/windows/desktop/bb761059) message, qui est décrite dans le SDK Windows.  
  
##  <a name="getnextselecteditem"></a>  CListCtrl::GetNextSelectedItem  
 Obtient l’index de l’élément de liste identifié par *pos*, puis définit *pos* à la valeur POSITION.  
  
```  
int GetNextSelectedItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *points de vente*  
 Une référence à une valeur POSITION retournée par un appel précédent à `GetNextSelectedItem` ou `GetFirstSelectedItemPosition`. La valeur est mise à jour à la position suivante par cet appel.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de l’élément identifié par *pos*.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser `GetNextSelectedItem` dans une boucle d’itération en avant si vous établissez la position initiale avec un appel à `GetFirstSelectedItemPosition`.  
  
 Vous devez vous assurer que votre valeur POSITION est valide. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant illustre l’utilisation de cette fonction.    
  
```cpp  
        POSITION pos = m_myListCtrl.GetFirstSelectedItemPosition();
        if (pos == NULL)
        {
            TRACE(_T("No items were selected!\n"));
        }
        else
        {
            while (pos)
            {
                int nItem = m_myListCtrl.GetNextSelectedItem(pos);
                TRACE(_T("Item %d was selected!\n"), nItem);
                // you could do your own processing on nItem here
            }
        }
```

  
##  <a name="getnumberofworkareas"></a>  CListCtrl::GetNumberOfWorkAreas  
 Récupère le nombre actuel de zones de travail pour un contrôle list view.  
  
```  
UINT GetNumberOfWorkAreas() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pas utilisé pour l’instant.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_GetNumberOfWorkAreas](/windows/desktop/api/commctrl/nf-commctrl-listview_getnumberofworkareas), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple    
  
```cpp  
        UINT i, uCount = m_myListCtrl.GetNumberOfWorkAreas();
        LPRECT lpRects = (LPRECT) malloc(uCount*sizeof(RECT));

        if (lpRects != NULL)
        {
            // Dump all of the work area dimensions.
            m_myListCtrl.GetWorkAreas(uCount, lpRects);

            for (i=0; i < uCount; i++)
            {
                TRACE(_T("Work area %d; left = %d, top = %d, right = %d, ")
                    _T("bottom = %d\r\n"),
                    i, lpRects[i].left, lpRects[i].top, lpRects[i].right, 
                    lpRects[i].bottom);
            }

            free(lpRects);
        }
        else
        {
            TRACE(_T("Couldn't allocate enough memory!"));   
        }

```

  
##  <a name="getoutlinecolor"></a>  CListCtrl::GetOutlineColor  
 Récupère la couleur de la bordure d’un contrôle list view.  
  
```  
COLORREF GetOutlineColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un [COLORREF](/windows/desktop/gdi/colorref) structure contenant la couleur de contour.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_GETOUTLINECOLOR](/windows/desktop/Controls/lvm-getoutlinecolor) du message, comme décrit dans le SDK Windows.  
  
##  <a name="getorigin"></a>  CListCtrl::GetOrigin  
 Récupère l’origine de la vue actuelle pour un contrôle list view.  
  
```  
BOOL GetOrigin(LPPOINT lpPoint) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *lpPoint*  
 Adresse d’un [POINT](https://msdn.microsoft.com/library/windows/desktop/dd162805) structure qui reçoit l’origine de la vue.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro. Toutefois, si le contrôle est en mode rapport, la valeur de retour est toujours zéro.  
  
##  <a name="getselectedcolumn"></a>  CListCtrl::GetSelectedColumn  
 Récupère l’index de la colonne actuellement sélectionnée dans le contrôle de liste.  
  
```  
UINT GetSelectedColumn() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Index de la colonne sélectionnée.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_GETSELECTEDCOLUMN](/windows/desktop/Controls/lvm-getselectedcolumn) du message, comme décrit dans le SDK Windows.  
  
##  <a name="getselectedcount"></a>  CListCtrl::GetSelectedCount  
 Récupère le nombre d’éléments sélectionnés dans le contrôle list view.  
  
```  
UINT GetSelectedCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments sélectionnés dans le contrôle list view.  
  
### <a name="example"></a>Exemple    
  
```cpp  
        UINT i, uSelectedCount = m_myListCtrl.GetSelectedCount();
        int  nItem = -1;

        // Update all of the selected items.
        if (uSelectedCount > 0)
        {
            for (i=0; i < uSelectedCount; i++)
            {
                nItem = m_myListCtrl.GetNextItem(nItem, LVNI_SELECTED);
                ASSERT(nItem != -1);
                m_myListCtrl.Update(nItem); 
            }
        }
```

  
##  <a name="getselectionmark"></a>  CListCtrl::GetSelectionMark  
 Récupère la marque de sélection d’un contrôle list view.  
  
```  
int GetSelectionMark();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La marque de sélection de base zéro, ou -1 s’il n’existe aucune marque de sélection.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_GetSelectionMark](/windows/desktop/api/commctrl/nf-commctrl-listview_getselectionmark), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  

```cpp  
    // Set the selection mark to the first item only if no other item is 
    // selected.
    if (m_myListCtrl.GetSelectionMark() == -1)
        m_myListCtrl.SetSelectionMark(0);
```

  
##  <a name="getstringwidth"></a>  CListCtrl::GetStringWidth  
 Détermine la largeur de colonne minimale nécessaire pour afficher toutes les une chaîne donnée.  
  
```  
int GetStringWidth(LPCTSTR lpsz) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *lpsz*  
 Adresse d’une chaîne se terminant par null dont la largeur doit être déterminée.  
  
### <a name="return-value"></a>Valeur de retour  
 La largeur, en pixels, de la chaîne vers laquelle pointé *lpsz*.  
  
### <a name="remarks"></a>Notes  
 La largeur retournée prend en compte la police du contrôle actuel et les marges de la colonne, mais pas la largeur d’une petite icône.  
  
### <a name="example"></a>Exemple  

```cpp  
        CString strColumn;
        int nWidth;

        // Insert six columns in the list view control. Make the width of
        // the column be the width of the column header plus 50%.
        for (int i = 0; i < 6; i++)
        {
            strColumn.Format(_T("column %d"), i);
            nWidth = 3*m_myListCtrl.GetStringWidth(strColumn)/2;
            m_myListCtrl.InsertColumn(i, strColumn, LVCFMT_LEFT, nWidth);
        }
```

  
##  <a name="getsubitemrect"></a>  CListCtrl::GetSubItemRect  
 Récupère le rectangle englobant d’un élément dans un contrôle list view.  
  
```  
BOOL GetSubItemRect(
    int iItem,  
    int iSubItem,  
    int nArea,  
    CRect& ref);
```  
  
### <a name="parameters"></a>Paramètres  
 *iItem*  
 Index de l’élément du parent du sous-élément.  
  
 *iSubItem*  
 L’index de base 1 du sous-élément.  
  
 *nArea*  
 Détermine la partie du rectangle englobant (du sous-élément de la vue de liste) à récupérer. La partie (icône, étiquette ou les deux) du rectangle englobant est spécifiée en appliquant l’opérateur OR au niveau du bit à une ou plusieurs des valeurs suivantes :  
  
- LVIR_BOUNDS retourne le rectangle englobant de l’élément entier, y compris l’icône et une étiquette.  
  
- LVIR_ICON retourne le rectangle englobant de l’icône ou d’une petite icône.  
  
- LVIR_LABEL retourne le rectangle englobant de l’élément entier, y compris l’icône et une étiquette. Cela est identique à LVIR_BOUNDS.  
  
 *ref*  
 Référence à un [CRect](../../atl-mfc-shared/reference/crect-class.md) rectangle englobant de l’objet qui contient les coordonnées du sous-élément.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_GetSubItemRect](/windows/desktop/api/commctrl/nf-commctrl-listview_getsubitemrect), comme décrit dans le SDK Windows.  
  
##  <a name="gettextbkcolor"></a>  CListCtrl::GetTextBkColor  
 Récupère la couleur d’arrière-plan du texte d’un contrôle list view.  
  
```  
COLORREF GetTextBkColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur 32 bits utilisée pour spécifier une couleur RVB.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::SetTextBkColor](#settextbkcolor).  
  
##  <a name="gettextcolor"></a>  CListCtrl::GetTextColor  
 Récupère la couleur du texte d’un contrôle list view.  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur 32 bits utilisée pour spécifier une couleur RVB.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::SetTextColor](#settextcolor).  
  
##  <a name="gettileinfo"></a>  CListCtrl::GetTileInfo  
 Récupère des informations sur une vignette dans un contrôle list view.  
  
```  
BOOL GetTileInfo(PLVTILEINFO pti) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pti*  
 Un pointeur vers un [LVTILEINFO](/windows/desktop/api/commctrl/ns-commctrl-taglvtileinfo) structure qui reçoit les informations de la vignette.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur de retour n’est pas utilisée.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_GETTILEINFO](/windows/desktop/Controls/lvm-gettileinfo) du message, comme décrit dans le SDK Windows.  
  
##  <a name="gettileviewinfo"></a>  CListCtrl::GetTileViewInfo  
 Récupère des informations sur un contrôle list view dans l’affichage en mosaïque.  
  
```  
BOOL GetTileViewInfo(PLVTILEVIEWINFO ptvi) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *ptvi*  
 Un pointeur vers un [LVTILEVIEWINFO](/windows/desktop/api/commctrl/ns-commctrl-taglvtileviewinfo) structure qui reçoit les informations récupérées.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur de retour n’est pas utilisée.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_GETTILEVIEWINFO](/windows/desktop/Controls/lvm-gettileviewinfo) du message, comme décrit dans le SDK Windows.  
  
##  <a name="gettooltips"></a>  CListCtrl::GetToolTips  
 Récupère le contrôle d’info-bulle du contrôle list view utilise pour afficher des info-bulles.  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un [CToolTipCtrl](ctooltipctrl-class.md) objet utilisable par le contrôle de liste. Si le [créer](#create) fonction membre utilise le style LVS_NOTOOLTIPS, aucune info-bulles ne sont utilisées, et la valeur NULL est retournée.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [LVM_GETTOOLTIPS](/windows/desktop/Controls/lvm-gettooltips), comme décrit dans le SDK Windows. L’implémentation MFC de `GetToolTips` retourne un `CToolTipCtrl` objet, qui est utilisé par le contrôle de liste, plutôt qu’un handle à un contrôle d’info-bulle.  
  
### <a name="example"></a>Exemple  

```cpp  
        CToolTipCtrl* pTip = m_myListCtrl.GetToolTips();
        if (NULL != pTip)
        {
            pTip->UpdateTipText(_T("I'm a list view!"), &m_myListCtrl,
                IDD_MYLISTCTRL);
        }
```

  
##  <a name="gettopindex"></a>  CListCtrl::GetTopIndex  
 Récupère l’index du premier élément visible en mode liste ou rapport.  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’index du premier élément visible.  
  
### <a name="example"></a>Exemple  

 
```cpp  
        // Make sure the focus is set to the list view control.
        m_myListCtrl.SetFocus();

        // Select all of the items that are completely visible.
        int n = m_myListCtrl.GetTopIndex();
        int nLast = n + m_myListCtrl.GetCountPerPage();

        for (; n < nLast; n++)
        {
            m_myListCtrl.SetItemState(n, LVIS_SELECTED, LVIS_SELECTED);
            ASSERT(m_myListCtrl.GetItemState(n, LVIS_SELECTED) == LVIS_SELECTED); 
        }
```

  
##  <a name="getview"></a>  CListCtrl::GetView  
 Obtient la vue du contrôle list view.  
  
```  
DWORD GetView() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’affichage actuel du contrôle list view.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_GETVIEW](/windows/desktop/Controls/lvm-getview) du message, comme décrit dans le SDK Windows.  
  
##  <a name="getviewrect"></a>  CListCtrl::GetViewRect  
 Récupère le rectangle englobant de tous les éléments dans le contrôle list view.  
  
```  
BOOL GetViewRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *lpRect*  
 Adresse d’un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 L’affichage de liste doit être en mode icône ou petite icône.  
  
##  <a name="getworkareas"></a>  CListCtrl::GetWorkAreas  
 Récupère les zones de travail en cours d’un contrôle list view.  
  
```  
void GetWorkAreas(
    int nWorkAreas,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *nWorkAreas*  
 Le nombre de `RECT` structures contenues dans le *prc* tableau.  
  
 *République populaire de Chine*  
 Un pointeur vers un tableau de `RECT` structures (ou [CRect](../../atl-mfc-shared/reference/crect-class.md) objets) qui reçoivent les zones de travail de contrôle list view. Les valeurs dans ces structures sont dans les coordonnées clientes.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_GetWorkAreas](/windows/desktop/api/commctrl/nf-commctrl-listview_getworkareas), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::GetNumberOfWorkAreas](#getnumberofworkareas).  
  
##  <a name="hasgroup"></a>  CListCtrl::HasGroup  
 Détermine si le contrôle list view a le groupe spécifié.  
  
```  
BOOL HasGroup(int iGroupId) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *iGroupId*  
 L’identificateur du groupe demandé.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_HASGROUP](/windows/desktop/Controls/lvm-hasgroup) du message, comme décrit dans le SDK Windows.  
  
##  <a name="hittest"></a>  CListCtrl::HitTest  
 Détermine quel élément d’affichage de liste, si une, est à la position spécifiée.  
  
```  
int HitTest(LVHITTESTINFO* pHitTestInfo) const;  
  
int HitTest(
    CPoint pt,  
    UINT* pFlags = NULL) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pHitTestInfo*  
 Adresse d’un `LVHITTESTINFO` structure qui contient la position pour atteindre le test et qui reçoit des informations sur les résultats du test d’atteinte.  
  
 *pt*  
 Point à tester.  
  
 *pFlags*  
 Pointeur vers un entier qui reçoit des informations sur les résultats du test. Consultez l’explication de la `flags` membre de la [LVHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-taglvhittestinfo) structure dans le SDK Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de l’élément à la position spécifiée par *pHitTestInfo*, le cas échéant, ou sinon -1.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser les valeurs LVHT_ABOVE, LVHT_BELOW, LVHT_TOLEFT et LVHT_TORIGHT de la structure `flag` membre pour déterminer s’il faut faire défiler le contenu d’un contrôle list view. Deux de ces indicateurs peuvent être combinés, par exemple, si la position est au-dessus et à gauche de la zone cliente.  
  
 Vous pouvez tester la valeur LVHT_ONITEM de la structure `flag` membre pour déterminer si une position donnée se trouve sur un élément de liste. Cette valeur est une opération de bits OR sur les valeurs LVHT_ONITEMICON, LVHT_ONITEMLABEL et LVHT_ONITEMSTATEICON de la structure `flag` membre.  
  
### <a name="example"></a>Exemple  

```cpp  
void CListCtrlDlg::OnRClick(NMHDR* pNMHDR, LRESULT* pResult)
{
    LPNMITEMACTIVATE pia = (LPNMITEMACTIVATE)pNMHDR;
    CPoint point(pia->ptAction);

    // Select the item the user clicked on.
    UINT uFlags;
    int nItem = m_myListCtrl.HitTest(point, &uFlags);

    if (uFlags & LVHT_ONITEMLABEL)
    {
        m_myListCtrl.SetItem(nItem, 0, LVIF_STATE, NULL, 0, LVIS_SELECTED, 
            LVIS_SELECTED, 0);
    }

    *pResult = 0;
}
```

  
##  <a name="insertcolumn"></a>  CListCtrl::InsertColumn  
 Insère une nouvelle colonne dans un contrôle list view.  
  
```  
int InsertColumn(
    int nCol,  
    const LVCOLUMN* pColumn);

 
int InsertColumn(
    int nCol,  
    LPCTSTR lpszColumnHeading,  
    int nFormat = LVCFMT_LEFT,  
    int nWidth = -1,  
    int nSubItem = -1);
```  
  
### <a name="parameters"></a>Paramètres  
 *nCol*  
 L’index de la nouvelle colonne.  
  
 *pColumn*  
 Adresse d’un `LVCOLUMN` structure qui contient les attributs de la nouvelle colonne.  
  
 *lpszColumnHeading*  
 Adresse d’une chaîne contenant le titre de la colonne.  
  
 *nFormat*  
 Entier spécifiant l’alignement de la colonne. Il peut être une des valeurs suivantes : LVCFMT_LEFT, LVCFMT_RIGHT ou LVCFMT_CENTER.  
  
 *nWidth*  
 Largeur de la colonne, en pixels. Si ce paramètre est -1, la largeur de colonne n’est pas définie.  
  
 *nSubItem*  
 Index du sous-élément associé à la colonne. Si ce paramètre est -1, aucun sous-élément n’est associé à la colonne.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de la nouvelle colonne en cas de réussite ou sinon -1.  
  
### <a name="remarks"></a>Notes  
 La colonne la plus à gauche dans un contrôle list view doit être aligné à gauche.  
  
 Le [LVCOLUMN](/windows/desktop/api/commctrl/ns-commctrl-taglvcolumna) structure contient les attributs d’une colonne dans la vue rapport. Il est également utilisé pour recevoir des informations sur une colonne. Cette structure est décrite dans le SDK Windows.  
  
##  <a name="insertgroup"></a>  CListCtrl::InsertGroup  
 Insère un groupe dans le contrôle list view.  
  
```  
LRESULT InsertGroup(
    int index,  
    PLVGROUP pgrp);
```  
  
### <a name="parameters"></a>Paramètres  
 *index*  
 L’index de l’élément dans lequel le groupe doit être inséré.  
  
 *PGRP*  
 Un pointeur vers un [LVGROUP](/windows/desktop/api/commctrl/ns-commctrl-taglvgroup) structure qui contient le groupe à ajouter.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’index de l’élément qui a été ajouté au groupe, ou -1 si l’opération a échoué.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_INSERTGROUP](/windows/desktop/Controls/lvm-insertgroup) du message, comme décrit dans le SDK Windows.  
  
##  <a name="insertgroupsorted"></a>  CListCtrl::InsertGroupSorted  
 Insère le groupe spécifié dans une liste triée des groupes.  
  
```  
LRESULT InsertGroupSorted(PLVINSERTGROUPSORTED pStructInsert);
```  
  
### <a name="parameters"></a>Paramètres  
 *pStructInsert*  
 Un pointeur vers un [LVINSERTGROUPSORTED](/windows/desktop/api/commctrl/ns-commctrl-taglvinsertgroupsorted) structure qui contient le groupe à insérer.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur de retour n’est pas utilisée.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_INSERTGROUPSORTED](/windows/desktop/Controls/lvm-insertgroupsorted) du message, comme décrit dans le SDK Windows.  
  
##  <a name="insertitem"></a>  CListCtrl::InsertItem  
 Insère un élément dans le contrôle list view.  
  
```  
int InsertItem(const LVITEM* pItem);

 
int InsertItem(
    int nItem,  
    LPCTSTR lpszItem);

 
int InsertItem(
    int nItem,  
    LPCTSTR lpszItem,  
    int nImage);

 
int InsertItem(
    UINT nMask,  
    int nItem,  
    LPCTSTR lpszItem,  
    UINT nState,  
    UINT nStateMask,  
    int nImage,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Paramètres  
 *pItem*  
 Pointeur vers un [LVITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) structure qui spécifie les attributs de l’élément, comme décrit dans le SDK Windows.  
  
 *nItem*  
 Index de l’élément à insérer.  
  
 *lpszItem*  
 Adresse d’une chaîne contenant l’étiquette de l’élément, ou LPSTR_TEXTCALLBACK si l’élément est un élément de rappel. Pour plus d’informations sur les éléments de rappel, consultez [CListCtrl::GetCallbackMask](#getcallbackmask).  
  
 *nImage*  
 Index de l’élément image ou I_IMAGECALLBACK si l’élément est un élément de rappel. Pour plus d’informations sur les éléments de rappel, consultez [CListCtrl::GetCallbackMask](#getcallbackmask).  
  
 *nMask*  
 Le *nMask* paramètre spécifie quel élément passés comme paramètres des attributs sont valides. Il peut prendre l’une ou plusieurs des valeurs de masque décrit dans [LVITEM Structure](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) dans le SDK Windows. Les valeurs valides peuvent être combinés avec l’opérateur OR au niveau du bit.  
  
 *nState*  
 Indique l’état de l’élément, l’image de l’état et image de superposition. Consultez les rubriques du Kit de développement logiciel Windows [LVITEM Structure](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) pour plus d’informations et [États d’affichage de liste élément](/windows/desktop/Controls/list-view-item-states) pour obtenir la liste d’indicateurs valides.  
  
 *nStateMask*  
 Indique les bits du membre état seront récupérées ou modifiées. Consultez [LVITEM Structure](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) dans le SDK Windows pour plus d’informations.  
  
 *lParam*  
 Valeur 32 bits spécifique à l’application associée à l’élément. Si ce paramètre est spécifié, vous devez définir le *nMask* LVIF_PARAM d’attribut.  
  
### <a name="return-value"></a>Valeur de retour  
 Index du nouvel élément en cas de réussite ou sinon -1.  
  
### <a name="remarks"></a>Notes  
 Appel de cette méthode peut entraîner le message LVM_INSERTITEM à envoyer à votre fenêtre de contrôle. Le Gestionnaire de messages associé pour le contrôle peut ne pas définir le texte de l’élément sous certaines conditions (par exemple, à l’aide de styles de fenêtre telles que LVS_OWNERDRAW). Pour plus d’informations sur ces conditions, consultez [LVM_INSERTITEM](/windows/desktop/Controls/lvm-insertitem) dans le SDK Windows.  
  
### <a name="example"></a>Exemple  

```cpp  
        CString strText;
        int nColumnCount = m_myListCtrl.GetHeaderCtrl()->GetItemCount();

        // Insert 10 items in the list view control.
        for (int i = 0; i < 10; i++)
        {
            strText.Format(TEXT("item %d"), i);

            // Insert the item, select every other item.
            m_myListCtrl.InsertItem(LVIF_TEXT | LVIF_STATE, i, strText, 
                (i % 2) == 0 ? LVIS_SELECTED : 0, LVIS_SELECTED, 0, 0);

            // Initialize the text of the subitems.
            for (int j = 1; j < nColumnCount; j++)
            {
                strText.Format(TEXT("sub-item %d %d"), i, j);
                m_myListCtrl.SetItemText(i, j, strText);
            }
        }
```

  
##  <a name="insertmarkhittest"></a>  CListCtrl::InsertMarkHitTest  
 Récupère le point d’insertion le plus proche à un point spécifié.  
  
```  
int InsertMarkHitTest(
    LPPOINT pPoint,  
    LPLVINSERTMARK lvim) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPoint*  
 Un pointeur vers un [POINT](https://msdn.microsoft.com/library/windows/desktop/dd162805) coordonne la structure qui contient le test de positionnement, par rapport à la zone cliente du contrôle de liste.  
  
 *lvim*  
 Un pointeur vers un [LVINSERTMARK](/windows/desktop/api/commctrl/ns-commctrl-lvinsertmark) structure qui spécifie le point d’insertion le plus proche pour les coordonnées définies par le paramètre de point.  
  
### <a name="return-value"></a>Valeur de retour  
 Le point d’insertion le plus proche spécifié point.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_INSERTMARKHITTEST](/windows/desktop/Controls/lvm-insertmarkhittest) du message, comme décrit dans le SDK Windows.  
  
##  <a name="isgroupviewenabled"></a>  CListCtrl::IsGroupViewEnabled  
 Détermine si l’affichage du groupe est activé pour un contrôle list view.  
  
```  
BOOL IsGroupViewEnabled() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE si l’affichage du groupe est activé, ou FALSE dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_ISGROUPVIEWENABLED](/windows/desktop/Controls/lvm-isgroupviewenabled) du message, comme décrit dans le SDK Windows.  
  
##  <a name="isitemvisible"></a>  CListCtrl::IsItemVisible  
 Indique si un élément spécifié dans le contrôle de liste actuel est visible.  
  
```  
BOOL IsItemVisible(int index) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*index*|[in] Index de base zéro d’un élément dans le contrôle de liste actuel.|  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si l’élément spécifié est visible ; sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [LVM_ISITEMVISIBLE](/windows/desktop/Controls/lvm-isitemvisible) message, qui est décrite dans le SDK Windows.  
  
##  <a name="mapidtoindex"></a>  CListCtrl::MapIDToIndex  
 Mappe l’ID unique d’un élément dans le contrôle de liste actuel à un index.  
  
```  
UINT MapIDToIndex(UINT id) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*ID*|[in] ID unique d’un élément.|  
  
### <a name="return-value"></a>Valeur de retour  
 L’index actuel pour l’ID spécifié.  
  
### <a name="remarks"></a>Notes  
 Un contrôle de liste effectue le suivi en interne des éléments par index. Cela peut présenter des problèmes, car l’index peuvent changer pendant la durée de vie du contrôle. Le contrôle de liste pouvez marquer un élément avec un ID lorsque l’élément est créé et vous pouvez utiliser cet ID pour garantir l’unicité pendant la durée de vie de l’affichage de liste.  
  
 Notez que, dans un environnement multithread, l’index est garantie uniquement sur le thread qui héberge le contrôle list view, pas sur les threads d’arrière-plan.  
  
 Cette méthode envoie le [LVM_MAPIDTOINDEX](https://msdn.microsoft.com/library/windows/desktop/bb761137) message, qui est décrite dans le SDK Windows.  
  
##  <a name="mapindextoid"></a>  CListCtrl::MapIndexToID  
 Mappe l’index d’un élément dans le contrôle de liste actuel à un ID unique.  
  
```  
UINT MapIndexToID(UINT index) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*index*|[in] Index de base zéro d’un élément.|  
  
### <a name="return-value"></a>Valeur de retour  
 Un ID unique pour l’élément spécifié.  
  
### <a name="remarks"></a>Notes  
 Un contrôle de liste effectue le suivi en interne des éléments par index. Cela peut présenter des problèmes, car l’index peuvent changer pendant la durée de vie du contrôle. Le contrôle de liste pouvez marquer un élément avec un ID lorsque l’élément est créé. Vous pouvez utiliser cet ID pour accéder à un élément spécifique de la durée de vie de l’affichage de liste.  
  
 Notez que, dans un environnement multithread, l’index est garantie uniquement sur le thread qui héberge le contrôle list view, pas sur les threads d’arrière-plan.  
  
 Cette méthode envoie le [LVM_MAPINDEXTOID](/windows/desktop/Controls/lvm-mapindextoid) message, qui est décrite dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit une variable, `m_listCtrl`, qui est utilisé pour accéder au contrôle d’affichage de liste actuel. Cette variable est utilisée dans l'exemple suivant.    
  
```cpp  
public:
    // Variable used to access the list control.
    CListCtrl m_listCtrl; 
```

  
### <a name="example"></a>Exemple  
 L’exemple de code suivant montre le `MapIndexToID` (méthode). Dans la section précédente de cet exemple de code, nous avons créé un contrôle d’affichage de liste qui affiche deux colonnes intitulées « ClientID » et « Grade » dans une vue de rapport. L’exemple suivant mappe l’index de chaque élément d’affichage de liste à un numéro d’identification, puis récupère l’index pour chaque numéro d’identification. Enfin, l’exemple signale si les index d’origine ont été récupérés.    
  
```cpp  
    // MapIndexToID
    int iCount = m_listCtrl.GetItemCount();
    UINT nId = 0;
    UINT nIndex = 0;
    for (int iIndexOriginal = 0; iIndexOriginal < iCount; iIndexOriginal++)
    {
        // Map index to ID.
        nId = m_listCtrl.MapIndexToID((UINT)iIndexOriginal);

        // Map ID to index.
        nIndex = m_listCtrl.MapIDToIndex(nId);

        if (nIndex != (UINT)(iIndexOriginal))
        {
            CString str;
            str.Format(_T("Mapped index (%d) is not equal to original index (%d)"),
                nIndex, (UINT)(iIndexOriginal));
            AfxMessageBox(str);
            return;
        }
    }
    AfxMessageBox(_T("The mapped indexes and original indexes are equal."), 
        MB_ICONINFORMATION);
```

  
##  <a name="movegroup"></a>  CListCtrl::MoveGroup  
 Déplace le que groupe spécifié spécifiée à l’index de base zéro du contrôle list view.  
  
```  
LRESULT MoveGroup(
    int iGroupId,  
    int toIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 *iGroupId*  
 L’identificateur du groupe à déplacer.  
  
 *toIndex*  
 Index de base zéro où le groupe doit être déplacé.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur de retour n’est pas utilisée.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_MOVEGROUP](/windows/desktop/Controls/lvm-movegroup) du message, comme décrit dans le SDK Windows.  
  
##  <a name="moveitemtogroup"></a>  CListCtrl::MoveItemToGroup  
 Déplace l’élément spécifié dans le groupe spécifié.  
  
```  
void MoveItemToGroup(
    int idItemFrom,  
    int idGroupTo);
```  
  
### <a name="parameters"></a>Paramètres  
*idItemFrom*<br/>
[in] L’index de l’élément à déplacer.  
  
*idGroupTo*<br/>
[in] L’identificateur du groupe de l’élément sera déplacé vers.  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette méthode n’est actuellement pas implémentée.  
  
 Cette méthode émule la fonctionnalité de la [LVM_MOVEITEMTOGROUP](/windows/desktop/Controls/lvm-moveitemtogroup) du message, comme décrit dans le SDK Windows.  
  
##  <a name="redrawitems"></a>  CListCtrl::RedrawItems  
 Force un contrôle list view à repeindre une plage d’éléments.  
  
```  
BOOL RedrawItems(
    int nFirst,  
    int nLast);
```  
  
### <a name="parameters"></a>Paramètres  
 *Npremier*  
 Index du premier élément à être redessinée.  
  
 *Ndernier*  
 Index du dernier élément à être redessinée.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Les éléments spécifiés ne sont pas réellement repeinte jusqu'à ce que la fenêtre d’affichage de liste reçoit un message WM_PAINT. Pour redessiner immédiatement, appelez le Windows [UpdateWindow](/windows/desktop/api/winuser/nf-winuser-updatewindow) fonction après l’utilisation de cette fonction.  
  
##  <a name="removeallgroups"></a>  CListCtrl::RemoveAllGroups  
 Supprime tous les groupes à partir d’un contrôle list view.  
  
```  
void RemoveAllGroups();
```  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_REMOVEALLGROUPS](/windows/desktop/Controls/lvm-removeallgroups) du message, comme décrit dans le SDK Windows.  
  
##  <a name="removegroup"></a>  CListCtrl::RemoveGroup  
 Supprime le groupe spécifié à partir du contrôle list view.  
  
```  
LRESULT RemoveGroup(int iGroupId);
```  
  
### <a name="parameters"></a>Paramètres  
 *iGroupId*  
 L’identificateur du groupe à supprimer.  
  
### <a name="return-value"></a>Valeur de retour  
 Sinon, retourne l’index du groupe en cas de réussite, ou -1.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_REMOVEGROUP](/windows/desktop/Controls/lvm-removegroup) du message, comme décrit dans le SDK Windows.  
  
##  <a name="scroll"></a>  CListCtrl::Scroll  
 Fait défiler le contenu d’un contrôle list view.  
  
```  
BOOL Scroll(CSize size);
```  
  
### <a name="parameters"></a>Paramètres  
 *size*  
 Un `CSize` objet spécifiant la quantité de défilement horizontale et verticale, en pixels. Le `y` membre *taille* est divisée par la hauteur, en pixels, de la ligne du contrôle list view, et le contrôle défile par le nombre de lignes obtenu.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
##  <a name="setbkcolor"></a>  CListCtrl::SetBkColor  
 Définit la couleur d’arrière-plan du contrôle list view.  
  
```  
BOOL SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>Paramètres  
 *CR*  
 Couleur d’arrière-plan pour définir, ou la valeur vous définissez CLR_NONE comme aucune couleur d’arrière-plan. Contrôles d’affichage de liste avec les couleurs d’arrière-plan redessiner considérablement plus rapides que celles sans les couleurs d’arrière-plan. Pour plus d’informations, consultez [COLORREF](/windows/desktop/gdi/colorref) dans le SDK Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="example"></a>Exemple  

 
```cpp  
        // Use the 3D button face color for the background.
        COLORREF crBkColor = ::GetSysColor(COLOR_3DFACE);
        m_myListCtrl.SetBkColor(crBkColor);
        ASSERT(m_myListCtrl.GetBkColor() == crBkColor);
```

  
##  <a name="setbkimage"></a>  CListCtrl::SetBkImage  
 Définit l’image d’arrière-plan d’un contrôle list view.  
  
```  
BOOL SetBkImage(LVBKIMAGE* plvbkImage);
 
BOOL SetBkImage(
    HBITMAP hbm,  
    BOOL fTile = TRUE,  
    int xOffsetPercent = 0,  
    int yOffsetPercent = 0);
 
BOOL SetBkImage(
    LPTSTR pszUrl,  
    BOOL fTile = TRUE,  
    int xOffsetPercent = 0,  
    int yOffsetPercent = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 *plvbkImage*  
 Adresse d’un `LVBKIMAGE` structure, qui contient les nouvelles informations d’image d’arrière-plan.  
  
 *hbm*  
 Handle vers une image bitmap.  
  
 *pszUrl*  
 Chaîne se terminant par NULL qui contient l’URL de l’image d’arrière-plan.  
  
 *fTile*  
 Différent de zéro si l’image doit être affichée en mosaïque dans l’arrière-plan du contrôle de la vue de liste ; sinon 0.  
  
 *xOffsetPercent*  
 Offset, en pixels, du bord gauche de l’image, à partir de l’origine du contrôle list view.  
  
 *yOffsetPercent*  
 Offset, en pixels, du bord supérieur de l’image, à partir de l’origine du contrôle list view.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne zéro en cas de réussite, ou zéro sinon.  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Étant donné que `CListCtrl::SetBkImage` utilise des fonctionnalités OLE COM, les bibliothèques OLE doivent être initialisés avant d’utiliser `SetBkImage`. Il est préférable d’initialiser les bibliothèques COM lorsque l’application est initialisée et annuler l’initialisation les bibliothèques lors de l’application se termine. Cette opération est automatiquement effectuée dans MFC, applications qui utilisent des ActiveX technologies, OLE Automation, OLE liaison/incorporation ou les opérations ODBC/DAO.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::GetBkImage](#getbkimage).  
  
##  <a name="setcallbackmask"></a>  CListCtrl::SetCallbackMask  
 Définit le masque de rappel pour un contrôle list view.  
  
```  
BOOL SetCallbackMask(UINT nMask);
```  
  
### <a name="parameters"></a>Paramètres  
 *nMask*  
 Nouvelle valeur de masque de rappel.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="example"></a>Exemple  

 
```cpp  
    // Set the callback mask so that only the selected and focused states
    // are stored for each item.
    m_myListCtrl.SetCallbackMask(LVIS_SELECTED|LVIS_FOCUSED);
    ASSERT(m_myListCtrl.GetCallbackMask() == 
        (LVIS_SELECTED|LVIS_FOCUSED));
```


##  <a name="setcheck"></a>  CListCtrl::SetCheck  
 Détermine si l’image d’état d’un élément de contrôle de liste est visible.  
  
```  
BOOL SetCheck(
    int nItem,  
    BOOL fCheck = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 Index de base zéro d’un élément de contrôle de liste.  
  
 *Consultez*  
 Spécifie si l’image d’état de l’élément doit être visible ou non. Par défaut, *consultez* a la valeur TRUE et l’image d’état est visible. Si *consultez* est FALSE, il n’est pas visible.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément est activé, sinon, 0.  
  
### <a name="example"></a>Exemple  

 
```cpp  
        int nCount = m_myListCtrl.GetItemCount();
        BOOL fCheck = FALSE;

        // Set the check state of every other item to TRUE and 
        // all others to FALSE.
        for (int i = 0; i < nCount; i++)
        {
            m_myListCtrl.SetCheck(i, fCheck);
            ASSERT((m_myListCtrl.GetCheck(i) && fCheck) || 
                (!m_myListCtrl.GetCheck(i) && !fCheck));
            fCheck = !fCheck;
        }
```

  
##  <a name="setcolumn"></a>  CListCtrl::SetColumn  
 Définit les attributs d’une colonne de vue de liste.  
  
```  
BOOL SetColumn(
    int nCol,  
    const LVCOLUMN* pColumn);
```  
  
### <a name="parameters"></a>Paramètres  
 *nCol*  
 Index de la colonne dont les attributs doivent être définis.  
  
 *pColumn*  
 Adresse d’un [LVCOLUMN](/windows/desktop/api/commctrl/ns-commctrl-taglvcolumna) attributs de structure qui contient la nouvelle colonne, comme décrit dans le SDK Windows. La structure `mask` membre spécifie quelle colonne attributs à définir. Si le `mask` membre spécifie LVCF_TEXT, la structure de valeur `pszText` membre est l’adresse d’une chaîne se terminant par null et de la structure `cchTextMax` membre est ignoré.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::GetColumn](#getcolumn).  
  
##  <a name="setcolumnorderarray"></a>  CListCtrl::SetColumnOrderArray  
 Définit l’ordre des colonnes (de gauche à droite) d’un contrôle list view.  
  
```  
BOOL SetColumnOrderArray(
    int iCount,  
    LPINT piArray);
```  
  
### <a name="parameters"></a>Paramètres  
 *piArray*  
 Pointeur vers une mémoire tampon contenant les valeurs d’index des colonnes dans le contrôle list view (de gauche à droite). La mémoire tampon doit être assez grande pour contenir le nombre total de colonnes dans le contrôle list view.  
  
 *iCount*  
 Nombre de colonnes dans le contrôle list view.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_SetColumnOrderArray](/windows/desktop/api/commctrl/nf-commctrl-listview_setcolumnorderarray), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::GetColumnOrderArray](#getcolumnorderarray).  
  
##  <a name="setcolumnwidth"></a>  CListCtrl::SetColumnWidth  
 Modifie la largeur d’une colonne dans la liste ou un affichage de rapport.  
  
```  
BOOL SetColumnWidth(
    int nCol,  
    int cx);
```  
  
### <a name="parameters"></a>Paramètres  
 *nCol*  
 Index de la colonne pour laquelle la largeur doit être définie. Dans la vue de liste, ce paramètre doit être 0.  
  
 *CX*  
 La nouvelle largeur de la colonne. Peut être LVSCW_AUTOSIZE ou LVSCW_AUTOSIZE_USEHEADER, comme décrit dans [LVM_SETCOLUMNWIDTH](/windows/desktop/Controls/lvm-setcolumnwidth) dans le SDK Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
##  <a name="setextendedstyle"></a>  CListCtrl::SetExtendedStyle  
 Définit les styles étendus en cours d’un contrôle list view.  
  
```  
DWORD SetExtendedStyle(DWORD dwNewStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwNewStyle*  
 Une combinaison des styles étendus pour être utilisé par le contrôle list view. Pour obtenir une liste descriptive de ces styles, consultez le [Styles étendus de la vue liste](/windows/desktop/Controls/extended-list-view-styles) rubrique dans le SDK Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Une combinaison des styles étendus précédentes utilisée par le contrôle list view.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_SetExtendedListViewStyle](/windows/desktop/api/commctrl/nf-commctrl-listview_setextendedlistviewstyle), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  

 
```cpp  
    // Allow the header controls item to be movable by the user.
    m_myListCtrl.SetExtendedStyle
        (m_myListCtrl.GetExtendedStyle()|LVS_EX_HEADERDRAGDROP);
```

  
##  <a name="setgroupinfo"></a>  CListCtrl::SetGroupInfo  
 Définit les informations qui décrivent le groupe spécifié de contrôle d’affichage de liste actuel.  
  
```  
int SetGroupInfo(
    int iGroupId,  
    PLVGROUP pgrp);
```  
  
### <a name="parameters"></a>Paramètres  
 *iGroupId*  
 L’identificateur du groupe dont les informations sont définies.  
  
 *PGRP*  
 Pointeur vers un [LVGROUP](/windows/desktop/api/commctrl/ns-commctrl-taglvgroup) structure qui contient les informations à définir. L’appelant est chargé d’allouer cette structure et de définition de ses membres.  
  
### <a name="return-value"></a>Valeur de retour  
 L’ID du groupe si la méthode a réussi ; Sinon, -1.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [LVM_SETGROUPINFO](/windows/desktop/Controls/lvm-setgroupinfo) message, qui est décrite dans le SDK Windows.  
  
##  <a name="setgroupmetrics"></a>  CListCtrl::SetGroupMetrics  
 Définit les mesures de groupe d’un contrôle list view.  
  
```  
void SetGroupMetrics(PLVGROUPMETRICS pGroupMetrics);
```  
  
### <a name="parameters"></a>Paramètres  
 *pGroupMetrics*  
 Un pointeur vers un [LVGROUPMETRICS](/windows/desktop/api/commctrl/ns-commctrl-taglvgroupmetrics) structure contenant les informations de métriques de groupe à définir.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_SETGROUPMETRICS](/windows/desktop/Controls/lvm-setgroupmetrics) du message, comme décrit dans le SDK Windows.  
  
##  <a name="sethotcursor"></a>  CListCtrl::SetHotCursor  
 Définit le curseur utilisé lors de la sélection réactive est activée pour un contrôle list view.  
  
```  
HCURSOR SetHotCursor(HCURSOR hc);
```  
  
### <a name="parameters"></a>Paramètres  
 *connexion hybride*  
 Handle vers une ressource de curseur, utilisé pour représenter le curseur à chaud.  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle vers la ressource curseur à chaud précédente utilisée par le contrôle list view.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_SetHotCursor](/windows/desktop/api/commctrl/nf-commctrl-listview_sethotcursor), comme décrit dans le SDK Windows.  
  
 Le curseur à chaud, visible uniquement lorsque la sélection de pointage est activée, s’affiche lorsque le curseur passe sur n’importe quel élément du ListView. Sélection de pointage est activée en définissant le LVS_EX_TRACKSELECT style étendu.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::GetHotCursor](#gethotcursor).  
  
##  <a name="sethotitem"></a>  CListCtrl::SetHotItem  
 Définit l’élément actif actuel d’un contrôle list view.  
  
```  
int SetHotItem(int iIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 *iIndex*  
 Index de base zéro de l’élément à définir comme l’élément actif.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro de l’élément précédemment actif.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_SetHotItem](/windows/desktop/api/commctrl/nf-commctrl-listview_sethotitem), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::GetHotItem](#gethotitem).  
  
##  <a name="sethovertime"></a>  CListCtrl::SetHoverTime  
 Définit le délai de pointage actuel d’un contrôle list view.  
  
```  
DWORD SetHoverTime(DWORD dwHoverTime = (DWORD)-1);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwHoverTime*  
 Le nouveau délai, en millisecondes, pendant lequel le curseur de la souris doit pointer sur un élément avant qu’il est sélectionné. Si la valeur par défaut est passée, l’heure est définie pour le délai de pointage par défaut.  
  
### <a name="return-value"></a>Valeur de retour  
 Le délai précédente de pointage, en millisecondes.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_SetHoverTime](/windows/desktop/api/commctrl/nf-commctrl-listview_sethovertime), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::GetHoverTime](#gethovertime).  
  
##  <a name="seticonspacing"></a>  CListCtrl::SetIconSpacing  
 Définit l’espacement entre les icônes dans un contrôle list view.  
  
```  
CSize SetIconSpacing(
    int cx,  
    int cy);  
  
CSize SetIconSpacing(CSize size);
```  
  
### <a name="parameters"></a>Paramètres  
 *CX*  
 La distance (en pixels) entre les icônes sur l’axe x.  
  
 *CY*  
 La distance (en pixels) entre les icônes sur l’axe y.  
  
 *size*  
 Un `CSize` objet qui spécifie la distance (en pixels) entre les icônes sur le x - et y.  
  
### <a name="return-value"></a>Valeur de retour  
 Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objet contenant les valeurs précédentes pour l’espacement d’icône.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_SetIconSpacing](/windows/desktop/api/commctrl/nf-commctrl-listview_seticonspacing), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  

 
```cpp  
    // Leave lots of space between icons.
    m_myListCtrl.SetIconSpacing(CSize(100, 100));
```

  
##  <a name="setimagelist"></a>  CListCtrl::SetImageList  
 Affecte une liste d’images à un contrôle list view.  
  
```  
CImageList* SetImageList(
    CImageList* pImageList,  
    int nImageListType);
```  
  
### <a name="parameters"></a>Paramètres  
 *pImageList*  
 Pointeur vers la liste d’images à affecter.  
  
 *nImageListType*  
 Type de liste d’images. Il peut être une des valeurs suivantes :  
  
- Liste d’images de LVSIL_NORMAL avec grandes icônes.  
  
- Liste d’images de LVSIL_SMALL avec petites icônes.  
  
- Liste d’images de LVSIL_STATE avec des images d’état.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la précédente liste d’images.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::GetImageList](#getimagelist).  
  
##  <a name="setinfotip"></a>  CListCtrl::SetInfoTip  
 Définit le texte d’info-bulle.  
  
```  
BOOL SetInfoTip(PLVSETINFOTIP plvInfoTip);
```  
  
### <a name="parameters"></a>Paramètres  
 *plvInfoTip*  
 Un pointeur vers un [LVFSETINFOTIP](/windows/desktop/api/commctrl/ns-commctrl-taglvsetinfotip) structure contenant les informations à définir.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_SETINFOTIP](/windows/desktop/Controls/lvm-setinfotip) du message, comme décrit dans le SDK Windows.  
  
##  <a name="setinsertmark"></a>  CListCtrl::SetInsertMark  
 Définit le point d’insertion à la position définie.  
  
```  
BOOL SetInsertMark(LPLVINSERTMARK lvim);
```  
  
### <a name="parameters"></a>Paramètres  
 *lvim*  
 Un pointeur vers un [LVINSERTMARK](/windows/desktop/api/commctrl/ns-commctrl-lvinsertmark) structure spécifiant où définir le point d’insertion.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne TRUE en cas de réussite, ou FALSE dans le cas contraire. Valeur FALSE est retournée si la taille dans le `cbSize` membre de la `LVINSERTMARK` structure n’est pas égale la taille réelle de la structure, ou lorsqu’une insertion point ne s’applique pas dans l’affichage actuel.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_SETINSERTMARK](/windows/desktop/Controls/lvm-setinsertmark) du message, comme décrit dans le SDK Windows.  
  
##  <a name="setinsertmarkcolor"></a>  CListCtrl::SetInsertMarkColor  
 Définit la couleur du point d’insertion.  
  
```  
COLORREF SetInsertMarkColor(COLORREF color);
```  
  
### <a name="parameters"></a>Paramètres  
 *Couleur*  
 Un [COLORREF](/windows/desktop/gdi/colorref) structure qui spécifie la couleur pour définir le point d’insertion.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un `COLORREF` structure contenant la couleur précédente.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_SETINSERTMARKCOLOR](/windows/desktop/Controls/lvm-setinsertmarkcolor) du message, comme décrit dans le SDK Windows.  
  
##  <a name="setitem"></a>  CListCtrl::SetItem  
 Définit les attributs de l’élément de tout ou partie d’une vue liste.  
  
```  
BOOL SetItem(const LVITEM* pItem);

 
BOOL SetItem(
    int nItem,  
    int nSubItem,  
    UINT nMask,  
    LPCTSTR lpszItem,  
    int nImage,  
    UINT nState,  
    UINT nStateMask,  
    LPARAM lParam);

 
BOOL SetItem(
    int nItem,  
    int nSubItem,  
    UINT nMask,  
    LPCTSTR lpszItem,  
    int nImage,  
    UINT nState,  
    UINT nStateMask,  
    LPARAM lParam,  
    int nIndent);
```  
  
### <a name="parameters"></a>Paramètres  
 *pItem*  
 Adresse d’un [LVITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) attributs de structure qui contient le nouvel élément, comme décrit dans le SDK Windows. La structure `iItem` et `iSubItem` membres identifient l’élément ou sous-élément et de la structure `mask` membre spécifie les attributs à définir. Pour plus d’informations sur la `mask` membre, consultez le **notes**.  
  
 *nItem*  
 Index de l’élément dont les attributs doivent être définis.  
  
 *nSubItem*  
 Index du sous-élément dont les attributs doivent être définis.  
  
 *nMask*  
 Spécifie quels attributs doivent être définis (voir la section Notes).  
  
 *lpszItem*  
 Adresse d’une chaîne se terminant par null spécifiant l’étiquette de l’élément.  
  
 *nImage*  
 Index de l’image l’élément dans la liste d’images.  
  
 *nState*  
 Spécifie des valeurs pour les États d’être modifié (voir la section Notes).  
  
 *nStateMask*  
 Spécifie les États doivent être modifiés (voir la section Notes).  
  
 *lParam*  
 Une valeur spécifique à l’application 32 bits à associer à l’élément.  
  
 *nIndent*  
 Largeur, en pixels, de la mise en retrait. Si *nIndent* est inférieure à la largeur minimale définie par le système, la nouvelle largeur est définie à la valeur minimale définie par le système  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Le `iItem` et `iSubItem` membres de la `LVITEM` structure et le *nItem* et *nSubItem* paramètres identifient les sous-élément dont les attributs doivent être définis.  
  
 Le `mask` membre de la `LVITEM` structure et le *nMask* paramètre spécifier quel élément attributs doivent être définis :  
  
- LVIF_TEXT le `pszText` membre ou le *lpszItem* paramètre est l’adresse d’une chaîne se terminant par null ; la `cchTextMax` membre est ignoré.  
  
- LVIF_STATE le `stateMask` membre ou *nStateMask* paramètre spécifie quel élément États à modifier et le `state` membre ou *nState* paramètre contient les valeurs pour ces États.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::HitTest](#hittest).  
  
##  <a name="setitemcount"></a>  CListCtrl::SetItemCount  
 Prépare un contrôle list view pour l’ajout d’un grand nombre d’éléments.  
  
```  
void SetItemCount(int nItems);
```  
  
### <a name="parameters"></a>Paramètres  
 *nItems*  
 Nombre d’éléments qui le contrôle doit contenir.  
  
### <a name="remarks"></a>Notes  
 Pour définir le nombre d’éléments pour un contrôle virtual list view, consultez [CListCtrl::SetItemCountEx](#setitemcountex).  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_SetItemCount](/windows/desktop/api/commctrl/nf-commctrl-listview_setitemcount), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  

 
```cpp  
        CString str;

        // Add 1024 items to the list view control.
        m_myListCtrl.SetItemCount(1024);

        for (int i = 0; i < 1024; i++)
        {
            str.Format(TEXT("item %d"), i);
            m_myListCtrl.InsertItem(i, str);
        }
```

  
##  <a name="setitemcountex"></a>  CListCtrl::SetItemCountEx  
 Définit le nombre d’éléments pour un contrôle d’affichage de liste virtuelle.  
  
```  
BOOL SetItemCountEx(
    int iCount,  
    DWORD dwFlags = LVSICF_NOINVALIDATEALL);
```  
  
### <a name="parameters"></a>Paramètres  
 *iCount*  
 Nombre d’éléments qui le contrôle doit contenir.  
  
 *dwFlags*  
 Spécifie le comportement du contrôle list view après la réinitialisation du nombre d’éléments. Cette valeur peut être une combinaison des éléments suivants :  
  
- LVSICF_NOINVALIDATEALL le contrôle list view ne se repeint pas, sauf si les éléments affectés sont en cours d’affichage. Valeur par défaut.  
  
- LVSICF_NOSCROLL le contrôle list view ne changera pas la position de défilement lorsque l’élément de nombre de modifications.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_SetItemCountEx](/windows/desktop/api/commctrl/nf-commctrl-listview_setitemcountex), comme décrit dans la SDKand Windows doit être appelée uniquement pour les vues de liste virtuelle.  
  
### <a name="example"></a>Exemple  

 
```cpp  
        CString str;

        // Add 1024 items to the list view control.

        // Force my virtual list view control to allocate 
        // enough memory for my 1024 items.
        m_myVirtualListCtrl.SetItemCountEx(1024, LVSICF_NOSCROLL|
            LVSICF_NOINVALIDATEALL);

        for (int i = 0; i < 1024; i++)
        {
            str.Format(TEXT("item %d"), i);
            m_myVirtualListCtrl.InsertItem(i, str);
        }
```

  
##  <a name="setitemdata"></a>  CListCtrl::SetItemData  
 Définit la valeur de spécifique à l’application 32 bits associée à l’élément spécifié par *nItem*.  
  
```  
BOOL SetItemData(int nItem, DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 Index de l’élément de liste dont les données sont à définir.  
  
 *dwData*  
 Une valeur 32 bits à associer à l’élément.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette valeur est la `lParam` membre de la [LVITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) structure, comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  

 
```cpp  
    // Set the data of each item to be equal to its index.
    for (int i = 0; i < m_myListCtrl.GetItemCount(); i++)
    {
        m_myListCtrl.SetItemData(i, i);
    }
```

  
##  <a name="setitemindexstate"></a>  CListCtrl::SetItemIndexState  
 Définit l’état d’un élément dans le contrôle de liste actuel.  
  
```  
BOOL SetItemIndexState(
    PLVITEMINDEX pItemIndex,   
    DWORD dwState,   
    DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*pItemIndex*|[in] Pointeur vers un [LVITEMINDEX](https://msdn.microsoft.com/library/windows/desktop/bb774762) structure qui décrit un élément. L’appelant est chargé d’allouer cette structure et de définition de ses membres.|  
|*dwState*|[in] L’état à définir l’élément, qui est une combinaison au niveau du bit de [liste des États d’élément de vue](/windows/desktop/Controls/list-view-item-states). Spécifiez zéro à la réinitialisation ou une définition, un état.|  
|*dwMask*|[in] Un masque de bits valides de l’état spécifié par le *dwState* paramètre. Spécifiez une combinaison au niveau du bit (OR) de [liste des États d’élément de vue](/windows/desktop/Controls/list-view-item-states).|  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si cette méthode a réussi ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur la *dwState* paramètre, consultez [États d’élément de liste affichage](/windows/desktop/Controls/list-view-item-states).  
  
 Pour plus d’informations sur la *dwMask* paramètre, consultez le *stateMask* membre de la [LVITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) structure.  
  
 Cette méthode envoie le [LVM_SETITEMINDEXSTATE](/windows/desktop/Controls/lvm-setitemindexstate) message, qui est décrite dans le SDK Windows.  
  
##  <a name="setitemposition"></a>  CListCtrl::SetItemPosition  
 Déplace un élément à une position spécifiée dans un contrôle list view.  
  
```  
BOOL SetItemPosition(
    int nItem,  
    POINT pt);
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 Index de l’élément dont la position est à définir.  
  
 *pt*  
 Un [POINT](https://msdn.microsoft.com/library/windows/desktop/dd162805) coordonne la structure qui spécifie la nouvelle position, dans la vue, du coin supérieur gauche de l’élément.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Le contrôle doit être en icône ou petite icône.  
  
 Si le contrôle list view a le style LVS_AUTOARRANGE, l’affichage de liste est réorganisé après que la position de l’élément est définie.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::GetItemPosition](#getitemposition).  
  
##  <a name="setitemstate"></a>  CListCtrl::SetItemState  
 Modifie l’état d’un élément dans un contrôle list view.  
  
```  
BOOL SetItemState(
    int nItem,  
    LVITEM* pItem);

 
BOOL SetItemState(
    int nItem,  
    UINT nState,  
    UINT nMask);
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 Index de l’élément dont l’état doit être défini.  
  
 *pItem*  
 Adresse d’un [LVITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) structure, comme décrit dans le SDK Windows. La structure `stateMask` membre spécifie quel état les bits pour la modification et de la structure `state` membre contient les nouvelles valeurs pour ces bits. Les autres membres sont ignorés.  
  
 *nState*  
 Nouvelles valeurs pour les bits d’état. Pour obtenir la liste des valeurs possibles, consultez [CListCtrl::GetNextItem](#getnextitem) et [LVITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) membre de l’état.  
  
 *nMask*  
 Masque spécifiant quel état les bits à modifier. Cette valeur correspond au membre stateMask de la [LVITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 « État » d’un élément est une valeur qui indique la disponibilité de l’article, indique les actions de l’utilisateur ou sinon reflète l’état de facturation. Un contrôle list view modifie certains bits d’état, telles que lorsque l’utilisateur sélectionne un élément. Une application peut modifier les autres bits d’état pour désactiver ou masquer l’élément, ou pour spécifier une image de superposition ou d’une image d’état.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::GetTopIndex](#gettopindex).  
  
##  <a name="setitemtext"></a>  CListCtrl::SetItemText  
 Modifie le texte d’un élément de vue de liste ou d’un sous-élément.  
  
```  
BOOL SetItemText(
    int nItem,  
    int nSubItem,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 Index de l’élément dont le texte doit être défini.  
  
 *nSubItem*  
 Index de sous-élément, ou zéro pour définir l’étiquette de l’élément.  
  
 *lpszText*  
 Pointeur vers une chaîne qui contient le texte d’élément.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Cette méthode n’est pas destinée à utiliser avec les contrôles contenant le style de fenêtre est LVS_OWNERDATA (en fait, que cela entraîne une assertion dans les versions Debug). Pour plus d’informations sur ce style de contrôle de liste, consultez [vue d’ensemble des contrôles List View](/windows/desktop/Controls/list-view-controls-overview).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::InsertItem](#insertitem).  
  
##  <a name="setoutlinecolor"></a>  CListCtrl::SetOutlineColor  
 Définit la couleur de la bordure d’un contrôle de liste si le [LVS_EX_BORDERSELECT](/windows/desktop/Controls/list-view-window-styles) style de fenêtre étendus est défini.  
  
```  
COLORREF SetOutlineColor(COLORREF color);
```  
  
### <a name="parameters"></a>Paramètres  
 *Couleur*  
 La nouvelle [COLORREF](/windows/desktop/gdi/colorref) structure contenant la couleur de contour.  
  
### <a name="return-value"></a>Valeur de retour  
 Le précédent `COLORREF` structure contenant la couleur de contour  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_SETOUTLINECOLOR](/windows/desktop/Controls/lvm-setoutlinecolor) du message, comme décrit dans le SDK Windows.  
  
##  <a name="setselectedcolumn"></a>  CListCtrl::SetSelectedColumn  
 Définit la colonne sélectionnée du contrôle list view.  
  
```  
LRESULT SetSelectedColumn(int iCol);
```  
  
### <a name="parameters"></a>Paramètres  
 *iCol*  
 L’index de la colonne à sélectionner.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur de retour n’est pas utilisée.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_SETSELECTEDCOLUMN](/windows/desktop/Controls/lvm-setselectedcolumn) du message, comme décrit dans le SDK Windows.  
  
##  <a name="setselectionmark"></a>  CListCtrl::SetSelectionMark  
 Définit la marque de sélection d’un contrôle list view.  
  
```  
int SetSelectionMark(int iIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 *iIndex*  
 Index de base zéro du premier élément dans une sélection multiple.  
  
### <a name="return-value"></a>Valeur de retour  
 La marque de sélection précédente, ou -1 s’il n’y avait aucune marque de sélection.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_SetSelectionMark](/windows/desktop/api/commctrl/nf-commctrl-listview_setselectionmark), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::GetSelectionMark](#getselectionmark).  
  
##  <a name="settextbkcolor"></a>  CListCtrl::SetTextBkColor  
 Définit la couleur d’arrière-plan du texte dans un contrôle list view.  
  
```  
BOOL SetTextBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>Paramètres  
 *CR*  
 COLORREF spécifiant la nouvelle couleur d’arrière-plan de texte. Pour plus d’informations, consultez [COLORREF](/windows/desktop/gdi/colorref) dans le SDK Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="example"></a>Exemple  

 
```cpp  
        // Use the 3D button face color for the background.
        COLORREF crBkColor = ::GetSysColor(COLOR_3DFACE);
        m_myListCtrl.SetTextBkColor(crBkColor);
        ASSERT(m_myListCtrl.GetTextBkColor() == crBkColor);
```

  
##  <a name="settextcolor"></a>  CListCtrl::SetTextColor  
 Définit la couleur du texte d’un contrôle list view.  
  
```  
BOOL SetTextColor(COLORREF cr);
```  
  
### <a name="parameters"></a>Paramètres  
 *CR*  
 COLORREF spécifiant la nouvelle couleur de texte. Pour plus d’informations, consultez [COLORREF](/windows/desktop/gdi/colorref) dans le SDK Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="example"></a>Exemple  

 
```cpp  
    // Use the window text color for
    // the item text of the list view control.
    COLORREF crTextColor = ::GetSysColor(COLOR_WINDOWTEXT);
    m_myListCtrl.SetTextColor(crTextColor);
    ASSERT(m_myListCtrl.GetTextColor() == crTextColor);
```

  
##  <a name="settileinfo"></a>  CListCtrl::SetTileInfo  
 Définit les informations pour une vignette de l’affichage de liste.  
  
```  
BOOL SetTileInfo(PLVTILEINFO pti);
```  
  
### <a name="parameters"></a>Paramètres  
 *pti*  
 Un pointeur vers un [LVTILEINFO](/windows/desktop/api/commctrl/ns-commctrl-taglvtileinfo) structure contenant les informations à définir.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_SETTILEINFO](/windows/desktop/Controls/lvm-settileinfo) du message, comme décrit dans le SDK Windows.  
  
##  <a name="settileviewinfo"></a>  CListCtrl::SetTileViewInfo  
 Définit les informations qui utilise un contrôle list view dans l’affichage en mosaïque.  
  
```  
BOOL SetTileViewInfo(PLVTILEVIEWINFO ptvi);
```  
  
### <a name="parameters"></a>Paramètres  
 *ptvi*  
 Un pointeur vers un [LVTILEVIEWINFO](/windows/desktop/api/commctrl/ns-commctrl-taglvtileviewinfo) structure contenant les informations à définir.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_SETTILEVIEWINFO](/windows/desktop/Controls/lvm-settileviewinfo) du message, comme décrit dans le SDK Windows.  
  
##  <a name="settooltips"></a>  CListCtrl::SetToolTips  
 Définit le contrôle d’info-bulle du contrôle list view utilisera pour afficher des info-bulles.  
  
```  
CToolTipCtrl* SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWndTip*  
 Un pointeur vers un `CToolTipCtrl` objet qui utilise le contrôle de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un [CToolTipCtrl](ctooltipctrl-class.md) objet contenant l’info-bulle précédemment utilisé par le contrôle, ou NULL si aucune info-bulles ont été précédemment utilisés.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [LVM_SETTOOLTIPS](/windows/desktop/Controls/lvm-settooltips), comme décrit dans le SDK Windows.  
  
 Pour ne pas utiliser des info-bulles, indiquent le style LVS_NOTOOLTIPS lorsque vous créez le `CListCtrl` objet.  
  
##  <a name="setview"></a>  CListCtrl::SetView  
 Définit l’affichage de contrôle list view.  
  
```  
DWORD SetView(int iView);
```  
  
### <a name="parameters"></a>Paramètres  
 *iView*  
 La vue à sélectionner.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne 1 si l’opération réussit, ou sinon -1. Par exemple, -1 est retourné si la vue n’est pas valide.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_SETVIEW](/windows/desktop/Controls/lvm-setview) du message, comme décrit dans le SDK Windows.  
  
##  <a name="setworkareas"></a>  CListCtrl::SetWorkAreas  
 Définit la zone où les icônes peuvent être affichés dans un contrôle list view.  
  
```  
void SetWorkAreas(
    int nWorkAreas,  
    LPRECT lpRect);
```  
  
### <a name="parameters"></a>Paramètres  
 *nWorkAreas*  
 Le nombre de `RECT` structures (ou [CRect](../../atl-mfc-shared/reference/crect-class.md) objets) dans le tableau vers lequel pointé *lpRect*.  
  
 *lpRect*  
 L’adresse d’un tableau de `RECT` structures (ou `CRect` objets) qui spécifient les nouveaux espaces de travail de contrôle list view. Ces zones doivent être spécifiés dans les coordonnées clientes. Si ce paramètre est NULL, l’espace de travail est fixé à la zone cliente du contrôle.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_SetWorkAreas](/windows/desktop/api/commctrl/nf-commctrl-listview_setworkareas), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  

 
```cpp  
    // Remove all working areas.
    m_myListCtrl.SetWorkAreas(0, NULL);
```

  
##  <a name="sortgroups"></a>  CListCtrl::SortGroups  
 Utilise une fonction définie par l’application de comparaison pour trier les groupes par ID dans un contrôle list view.  
  
```  
BOOL SortGroups(
    PFNLVGROUPCOMPARE _pfnGroupCompare,  
    LPVOID _plv);
```  
  
### <a name="parameters"></a>Paramètres  
 *_pfnGroupCompare*  
 Pointeur vers la fonction de comparaison de groupe.  
  
 *_plv*  
 Un pointeur void.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [LVM_SORTGROUPS](/windows/desktop/Controls/lvm-sortgroups) du message, comme décrit dans le SDK Windows.  
  
##  <a name="sortitems"></a>  CListCtrl::SortItems  
 Trie les éléments d’affichage de liste à l’aide d’une fonction de comparaison définies par l’application.  
  
```  
BOOL SortItems(
    PFNLVCOMPARE pfnCompare,  
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Paramètres  
*pfnCompare*<br/>
[in] Adresse de la fonction de comparaison définies par l’application.  
  
 L’opération de tri appelle la fonction de comparaison chaque fois que l’ordre relatif de deux éléments de liste doit être déterminée. La fonction de comparaison doit être un membre statique d’une classe ou une fonction autonome qui n’est pas un membre de n’importe quelle classe.  
  
*dwData*<br/>
[in] Valeur définie par l’application qui est passée à la fonction de comparaison.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la méthode réussite ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Cette méthode modifie l’index de chaque élément afin de refléter la nouvelle séquence.  
  
 La fonction de comparaison, *pfnCompare*, a la forme suivante :  
  
```  
int CALLBACK CompareFunc(LPARAM lParam1,
    LPARAM lParam2,
    LPARAM lParamSort);
```  
La fonction de comparaison doit retourner une valeur négative si le premier élément doit précéder la seconde, une valeur positive si le premier élément doit suivre le second, ou zéro si les deux éléments sont égaux.  
  
 Le *lParam1* paramètre est la valeur de 32 bits associée le premier élément qui est comparé, et le *lParam2* paramètre est la valeur associée au deuxième élément. Ce sont les valeurs qui ont été spécifiées dans le *lParam* membre d’éléments [LVITEM](/windows/desktop/api/commctrl/ns-commctrl-taglvitema) structure lorsqu’ils ont été insérés dans la liste. Le *lParamSort* paramètre est le même que le *dwData* valeur.  
  
 Cette méthode envoie le [LVM_SORTITEMS](/windows/desktop/Controls/lvm-sortitems) message, qui est décrite dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
 Voici une fonction de comparaison simple qui aboutit à des éléments en cours de tri par leurs *lParam* valeurs.  
  
```cpp  
// Sort items by associated lParam
int CALLBACK CListCtrlDlg::MyCompareProc(LPARAM lParam1, LPARAM lParam2, 
    LPARAM lParamSort)
{
    UNREFERENCED_PARAMETER(lParamSort);
return (int)(lParam1 - lParam2);
}
```
  
```cpp  
// Sort the items by passing in the comparison function.
void CListCtrlDlg::Sort()
{
    m_myListCtrl.SortItems(&CListCtrlDlg::MyCompareProc, 0);
}
```
  
##  <a name="sortitemsex"></a>  CListCtrl::SortItemsEx  
 Trie les éléments du contrôle d’affichage de liste actuel à l’aide d’une fonction de comparaison définies par l’application.  
  
```  
BOOL SortItemsEx(
    PFNLVCOMPARE pfnCompare,   
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*pfnCompare*|[in] Adresse de la fonction de comparaison définies par l’application.<br /><br /> L’opération de tri appelle la fonction de comparaison chaque fois que l’ordre relatif de deux éléments de liste doit être déterminée. La fonction de comparaison doit être un membre statique d’une classe ou une fonction autonome qui n’est pas un membre de n’importe quelle classe.|  
|*dwData*|[in] Défini par l’application la valeur passée à la fonction de comparaison.|  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si cette méthode a réussi ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Cette méthode modifie l’index de chaque élément afin de refléter la nouvelle séquence.  
  
 La fonction de comparaison, *pfnCompare*, a la forme suivante :  
  
```  
int CALLBACK CompareFunc(LPARAM lParam1,
    LPARAM lParam2,
    LPARAM lParamSort);
```  
Ce message est comme [LVM_SORTITEMS](/windows/desktop/Controls/lvm-sortitems), sauf le type d’informations passées à la fonction de comparaison. Dans [LVM_SORTITEMS](/windows/desktop/Controls/lvm-sortitems), *lParam1* et *lParam2* sont les valeurs des éléments à comparer. Dans [LVM_SORTITEMSEX](/windows/desktop/Controls/lvm-sortitemsex), *lParam1* est l’index actuel du premier élément à comparer et *lParam2* est l’index actuel du deuxième élément. Vous pouvez envoyer un [LVM_GETITEMTEXT](/windows/desktop/Controls/lvm-getitemtext) message pour récupérer des informations sur un élément.  
  
 La fonction de comparaison doit retourner une valeur négative si le premier élément doit précéder la seconde, une valeur positive si le premier élément doit suivre le second, ou zéro si les deux éléments sont égaux.  
  
> [!NOTE]
>  Pendant le processus de tri, le contenu de l’affichage de liste est instable. Si la fonction de rappel envoie tous les messages pour le contrôle de liste autre que [LVM_GETITEM](/windows/desktop/Controls/lvm-getitem), les résultats sont imprévisibles.  
  
 Cette méthode envoie le [LVM_SORTITEMSEX](/windows/desktop/Controls/lvm-sortitemsex) message, qui est décrite dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant définit une variable, `m_listCtrl`, qui est utilisé pour accéder au contrôle d’affichage de liste actuel. Cette variable est utilisée dans l'exemple suivant.  
  
```cpp  
public:
    // Variable used to access the list control.
    CListCtrl m_listCtrl; 
```

  
### <a name="example"></a>Exemple  
 L’exemple de code suivant montre le `SortItemEx` (méthode). Dans la section précédente de cet exemple de code, nous avons créé un contrôle d’affichage de liste qui affiche deux colonnes intitulées « ClientID » et « Grade » dans une vue de rapport. L’exemple de code suivant trie la table en utilisant les valeurs dans la colonne « Grade ».  
  

```cpp  
// The ListCompareFunc() method is a global function used by SortItemEx().
int CALLBACK ListCompareFunc(
                             LPARAM lParam1, 
                             LPARAM lParam2, 
                             LPARAM lParamSort)
{
    CListCtrl* pListCtrl = (CListCtrl*) lParamSort;
    CString    strItem1 = pListCtrl->GetItemText(static_cast<int>(lParam1), 1);
    CString    strItem2 = pListCtrl->GetItemText(static_cast<int>(lParam2), 1)
    int x1 = _tstoi(strItem1.GetBuffer());
    int x2 = _tstoi(strItem2.GetBuffer());
    int result = 0;
    if ((x1 - x2) < 0)
        result = -1;
    else if ((x1 - x2) == 0)
        result = 0;
    else
        result = 1;

    return result;
}

void CCListCtrl_s2Dlg::OnBnClickedButton1()
{
    // SortItemsEx
    m_listCtrl.SortItemsEx( ListCompareFunc, (LPARAM)&m_listCtrl );
}
```

  
##  <a name="subitemhittest"></a>  CListCtrl::SubItemHitTest  
 Détermine quel élément d’affichage de liste, si une, est à une position donnée.  
  
```  
int SubItemHitTest(LPLVHITTESTINFO pInfo);
```  
  
### <a name="parameters"></a>Paramètres  
 *pInfo*  
 Un pointeur vers le [LVHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-taglvhittestinfo) structure.  
  
### <a name="return-value"></a>Valeur de retour  
 L’index de base un de l’élément, ou sous-élément, qui est testée (le cas échéant) ou sinon -1.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement de la macro Win32, [ListView_SubItemHitTest](/windows/desktop/api/commctrl/nf-commctrl-listview_subitemhittest), comme décrit dans le SDK Windows.  
  
### <a name="example"></a>Exemple  

```cpp  
void CListCtrlDlg::OnDblClk(NMHDR* pNMHDR, LRESULT* pResult)
{
    UNREFERENCED_PARAMETER(pResult);
LPNMITEMACTIVATE pia = (LPNMITEMACTIVATE)pNMHDR;
    LVHITTESTINFO lvhti;

    // Clear the subitem text the user clicked on.
    lvhti.pt = pia->ptAction;
    m_myListCtrl.SubItemHitTest(&lvhti);

    if (lvhti.flags & LVHT_ONITEMLABEL)
    {
        m_myListCtrl.SetItemText(lvhti.iItem, lvhti.iSubItem, NULL);
    }
}
```

  
##  <a name="update"></a>  CListCtrl::Update  
 Force le contrôle list view pour redessiner l’élément spécifié par *nItem*.  
  
```  
BOOL Update(int nItem);
```  
  
### <a name="parameters"></a>Paramètres  
 *nItem*  
 Index de l’élément à mettre à jour.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro en cas de réussite ; sinon, zéro.  
  
### <a name="remarks"></a>Notes  
 Cette fonction permet également d’organiser le contrôle list view s’il a le style LVS_AUTOARRANGE.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CListCtrl::GetSelectedCount](#getselectedcount).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC ROWLIST](../../visual-cpp-samples.md)   
 [CWnd, classe](cwnd-class.md)   
 [Graphique hiérarchique](../hierarchy-chart.md)   
 [CImageList, classe](cimagelist-class.md)

