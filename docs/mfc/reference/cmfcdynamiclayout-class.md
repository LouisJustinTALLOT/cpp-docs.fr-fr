---
title: Cmfcdynamiclayout, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout::AddItem
- AFXLAYOUT/CMFCDynamicLayout::Adjust
- AFXLAYOUT/CMFCDynamicLayout::Create
- AFXLAYOUT/CMFCDynamicLayout::GetHostWnd
- AFXLAYOUT/CMFCDynamicLayout::GetMinSize
- AFXLAYOUT/CMFCDynamicLayout::GetWindowRect
- AFXLAYOUT/CMFCDynamicLayout::HasItem
- AFXLAYOUT/CMFCDynamicLayout::IsEmpty
- AFXLAYOUT/CMFCDynamicLayout::LoadResource
- AFXLAYOUT/CMFCDynamicLayout::SetMinSize
dev_langs:
- C++
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1313c50682a2d2baad124db512e7e0ad4b441284
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082307"
---
# <a name="cmfcdynamiclayout-class"></a>CMFCDynamicLayout Class

Spécifie comment les contrôles dans une fenêtre sont déplacés et redimensionnés à mesure que l'utilisateur redimensionne la fenêtre.

## <a name="syntax"></a>Syntaxe

```
class CMFCDynamicLayout : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMFCDynamicLayout::CMFCDynamicLayout`|Construit un objet `CMFCDynamicLayout`.|
|`CMFCDynamicLayout::~CMFCDynamicLayout`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCDynamicLayout::AddItem](#additem)|Ajoute une fenêtre enfant, généralement un contrôle, à la liste des fenêtres contrôlées par le gestionnaire de disposition dynamique.|
|[CMFCDynamicLayout::Adjust](#adjust)|Ajoute une fenêtre enfant, généralement un contrôle, à la liste des fenêtres contrôlées par le gestionnaire de disposition dynamique.|
|[CMFCDynamicLayout::Create](#create)|Stocke et valide la fenêtre hôte.|
|[CMFCDynamicLayout::GetHostWnd](#gethostwnd)|Retourne un pointeur vers une fenêtre hôte.|
|[CMFCDynamicLayout::GetMinSize](#getminsize)|Retourne la taille de fenêtre en dessous de laquelle la disposition n'est pas ajustée.|
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|Récupère le rectangle pour la zone cliente active de la fenêtre.|
|[CMFCDynamicLayout::HasItem](#hasitem)|Vérifie si un contrôle enfant a été ajouté à la disposition dynamique.|
|[CMFCDynamicLayout::IsEmpty](#isempty)|Vérifie qu'aucune fenêtre enfant n'a été ajoutée à une disposition dynamique.|
|[CMFCDynamicLayout::LoadResource](#loadresource)|Lit la disposition dynamique de la ressource AFX_DIALOG_LAYOUT, puis applique la disposition à la fenêtre hôte.|
|statique [CMFCDynamicLayout::MoveHorizontal](#movehorizontal)|Obtient un [MoveSettings](#movesettings_structure) valeur qui définit le degré de contrôle enfant est déplacé horizontalement quand l’utilisateur redimensionne sa fenêtre hôte.|
|statique [CMFCDynamicLayout::MoveHorizontalAndVertical](#movehorizontalandvertical)|Obtient un [MoveSettings](#movesettings_structure) valeur qui définit le degré de contrôle enfant est déplacé horizontalement quand l’utilisateur redimensionne sa fenêtre hôte.|
|statique [CMFCDynamicLayout::MoveNone](#movenone)|Obtient un [MoveSettings](#movesettings_structure) valeur qui ne représente aucun mouvement, verticale ou horizontale, pour un contrôle enfant.|
|statique [CMFCDynamicLayout::MoveVertical](#movevertical)|Obtient un [MoveSettings](#movesettings_structure) valeur qui définit le degré de contrôle enfant est déplacé verticalement quand l’utilisateur redimensionne sa fenêtre hôte.|
|[CMFCDynamicLayout::SetMinSize](#setminsize)|Définit la taille de fenêtre en dessous de laquelle la disposition n'est pas ajustée.|
|statique [CMFCDynamicLayout::SizeHorizontal](#sizehorizontal)|Obtient un [SizeSettings](#sizesettings_structure) valeur qui définit le degré de contrôle enfant est redimensionné horizontalement quand l’utilisateur redimensionne sa fenêtre hôte.|
|statique [CMFCDynamicLayout::SizeHorizontalAndVertical](#sizehorizontalandvertical)|Obtient un [SizeSettings](#sizesettings_structure) valeur qui définit le degré de contrôle enfant est redimensionné horizontalement quand l’utilisateur redimensionne sa fenêtre hôte.|
|statique [CMFCDynamicLayout::SizeNone](#sizenone)|Obtient un [SizeSettings](#sizesettings_structure) valeur qui ne représente aucun changement de taille pour un contrôle enfant.|
|statique [CMFCDynamicLayout::SizeVertical](#sizevertical)|Obtient un [SizeSettings](#sizesettings_structure) valeur qui définit le degré de contrôle enfant est redimensionné verticalement quand l’utilisateur redimensionne sa fenêtre hôte.|

## <a name="nested-types"></a>Types imbriqués

|Name|Description|
|----------|-----------------|
|[Cmfcdynamiclayout::movesettings, Structure](#movesettings_structure)|Encapsule les données de déplacement des contrôles dans une disposition dynamique.|
|[Cmfcdynamiclayout::sizesettings, Structure](#sizesettings_structure)|Encapsule les données de changement de taille des contrôles dans une disposition dynamique.|

## <a name="remarks"></a>Notes

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxlayout.h

##  <a name="additem"></a>  CMFCDynamicLayout::AddItem

Ajoute une fenêtre enfant, généralement un contrôle, à la liste des fenêtres contrôlées par le gestionnaire de disposition dynamique.

```
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```

### <a name="parameters"></a>Paramètres

*HWND*<br/>
Handle de la fenêtre à ajouter.

*nID*<br/>
ID du contrôle enfant à ajouter.

*moveSettings*<br/>
Structure qui décrit la façon dont le contrôle doit être déplacé quand la taille de fenêtre change.

*sizeSettings*<br/>
Structure qui décrit la façon dont le contrôle doit être redimensionné quand la taille de fenêtre change.

### <a name="return-value"></a>Valeur de retour

TRUE si l'élément a bien été ajouté ; sinon, FALSE.

### <a name="remarks"></a>Notes

La position et la taille d'un contrôle enfant change de façon dynamique quand une fenêtre hôte est redimensionnée.

##  <a name="adjust"></a>  CMFCDynamicLayout::Adjust

Ajoute une fenêtre enfant, généralement un contrôle, à la liste des fenêtres contrôlées par le gestionnaire de disposition dynamique.

```
void Adjust();
```

### <a name="remarks"></a>Notes

La position et la taille d'un contrôle enfant change de façon dynamique quand une fenêtre hôte est redimensionnée.

##  <a name="create"></a>  CMFCDynamicLayout::Create

Stocke et valide la fenêtre hôte.

```
BOOL Create(CWnd* pHostWnd);
```

### <a name="parameters"></a>Paramètres

*pHostWnd*<br/>
Pointeur vers la fenêtre hôte.

### <a name="return-value"></a>Valeur de retour

TRUE si la création a abouti ; sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="gethostwnd"></a>  CMFCDynamicLayout::GetHostWnd

Retourne un pointeur vers une fenêtre hôte.

```
CWnd* GetHostWnd();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre hôte.

### <a name="remarks"></a>Notes

Par défaut, la position de tous les contrôles enfants est recalculée par rapport à cette fenêtre.

##  <a name="getminsize"></a>  CMFCDynamicLayout::GetMinSize

Retourne la taille de fenêtre en dessous de laquelle la disposition n'est pas ajustée.

```
CSize GetMinSize();
```

### <a name="return-value"></a>Valeur de retour

Taille de fenêtre en dessous de laquelle la disposition n'est pas ajustée.

### <a name="remarks"></a>Notes

La position et la taille d'un contrôle enfant sont modifiées de façon dynamique du moment où une fenêtre hôte est redimensionnée, mais il y a une taille minimale en dessous de laquelle la disposition n'est pas ajustée. L'utilisateur peut réduire la taille de la fenêtre, mais certaines parties de la fenêtre sont alors masquées.

##  <a name="getwindowrect"></a>  CMFCDynamicLayout::GetWindowRect

Récupère le rectangle pour la zone cliente active de la fenêtre.

```
void GetHostWndRect(CRect& rect,);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Une fois que la fonction a retourné une valeur, ce paramètre contient le rectangle englobant de la zone de présentation. Il s'agit d'un paramètre de sortie ; la valeur d'entrée est remplacée.

### <a name="remarks"></a>Notes

##  <a name="hasitem"></a>  CMFCDynamicLayout::HasItem

Vérifie si un contrôle enfant a été ajouté à la disposition dynamique.

```
BOOL HasItem(HWND hwnd);
```

### <a name="parameters"></a>Paramètres

*HWND*<br/>
Handle de fenêtre pour le contrôle.

### <a name="return-value"></a>Valeur de retour

TRUE si la disposition contient déjà cet élément ; sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="isempty"></a>  CMFCDynamicLayout::IsEmpty

Vérifie qu'aucune fenêtre enfant n'a été ajoutée à une disposition dynamique.

```
BOOL IsEmpty();
```

### <a name="return-value"></a>Valeur de retour

TRUE si la disposition n'a pas d'éléments ; sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="loadresource"></a>  CMFCDynamicLayout::LoadResource

Lit la disposition dynamique de la ressource AFX_DIALOG_LAYOUT, puis applique la disposition à la fenêtre hôte.

```
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);
```

### <a name="parameters"></a>Paramètres

*pHostWnd*<br/>
Pointeur vers la fenêtre hôte.

*lpResource*<br/>
Pointeur vers la mémoire tampon qui contient la ressource AFX_DIALOG_LAYOUT.

*dwSize*<br/>
Taille de la mémoire tampon en octets.

### <a name="return-value"></a>Valeur de retour

TRUE si la ressource est chargée et appliquée à la fenêtre hôte ; sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="movehorizontal"></a>  CMFCDynamicLayout::MoveHorizontal

Obtient un [MoveSettings](#movesettings_structure) valeur qui définit le degré de contrôle enfant est déplacé horizontalement quand l’utilisateur redimensionne sa fenêtre hôte.

```
static MoveSettings MoveHorizontal(int nRatio);
```

### <a name="parameters"></a>Paramètres

*nRatio*<br/>
Définit sous forme de pourcentage l'amplitude du déplacement d'un contrôle enfant sur le plan horizontal quand l'utilisateur redimensionne la fenêtre hôte.

### <a name="return-value"></a>Valeur de retour

Un [MoveSettings](#movesettings_structure) rapport de déplacement de valeur qui encapsule les informations demandées.

### <a name="remarks"></a>Notes

##  <a name="movehorizontalandvertical"></a>  CMFCDynamicLayout::MoveHorizontalAndVertical

Obtient un [MoveSettings](#movesettings_structure) valeur qui définit le degré de contrôle enfant est déplacé horizontalement quand l’utilisateur redimensionne sa fenêtre hôte.

```
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Paramètres

*nXRatio*<br/>
Définit sous forme de pourcentage l'amplitude du déplacement d'un contrôle enfant sur le plan horizontal quand l'utilisateur redimensionne la fenêtre hôte.

*nYRatio*<br/>
Définit sous forme de pourcentage l'amplitude du déplacement d'un contrôle enfant sur le plan vertical quand l'utilisateur redimensionne la fenêtre hôte.

### <a name="return-value"></a>Valeur de retour

Un [MoveSettings](#movesettings_structure) rapport de déplacement de valeur qui encapsule les informations demandées.

### <a name="remarks"></a>Notes

##  <a name="movenone"></a>  CMFCDynamicLayout::MoveNone

Obtient un [MoveSettings](#movesettings_structure) valeur qui ne représente aucun mouvement, verticale ou horizontale, pour un contrôle enfant.

```
static MoveSettings MoveNone();
```

### <a name="return-value"></a>Valeur de retour

Un [MoveSettings](#movesettings_structure) valeur permettant de résoudre le contrôle en place, afin qu’il ne déplace pas quand l’utilisateur redimensionne la fenêtre hôte.

### <a name="remarks"></a>Notes

##  <a name="movesettings_structure"></a>  Cmfcdynamiclayout::movesettings, Structure

Encapsule les données de déplacement des contrôles dans une disposition dynamique.

```
struct CMFCDynamicLayout::MoveSettings;
```

### <a name="remarks"></a>Notes

Il s'agit d'une classe imbriquée dans `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout::MoveSettings::IsHorizontal

Vérifie si les données de déplacement spécifient un déplacement horizontal différent de zéro.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Valeur de retour

TRUE si l'objet `MoveSettings` spécifie un déplacement horizontal différent de zéro.

## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout::MoveSettings::IsNone

Vérifie si les données de déplacement ne spécifient aucun déplacement.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Valeur de retour

TRUE si l'objet `MoveSettings` ne spécifie aucun déplacement.

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout::MoveSettings::IsVertical

  Vérifie si les données de déplacement spécifient un déplacement vertical différent de zéro.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Valeur de retour

TRUE si l'objet `MoveSettings` spécifie un déplacement vertical différent de zéro.

##  <a name="movevertical"></a>  CMFCDynamicLayout::MoveVertical

Obtient un [MoveSettings](#movesettings_structure) valeur qui définit le degré de contrôle enfant est déplacé verticalement quand l’utilisateur redimensionne sa fenêtre hôte.

```
static MoveSettings MoveVertical(int nRatio);
```

### <a name="parameters"></a>Paramètres

*nRatio*<br/>
Définit sous forme de pourcentage l'amplitude du déplacement d'un contrôle enfant sur le plan vertical quand l'utilisateur redimensionne la fenêtre hôte.

### <a name="return-value"></a>Valeur de retour

Un [MoveSettings](#movesettings_structure) rapport de déplacement de valeur qui encapsule les informations demandées.

### <a name="remarks"></a>Notes

##  <a name="setminsize"></a>  CMFCDynamicLayout::SetMinSize

Définit la taille de fenêtre en dessous de laquelle la disposition n'est pas ajustée.

```
void SetMinSize(const CSize& size);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Taille souhaitée en dessous de laquelle la disposition n'est pas ajustée.

### <a name="remarks"></a>Notes

La position et la taille d'un contrôle enfant sont modifiées de façon dynamique du moment où une fenêtre hôte est redimensionnée, mais il y a une taille minimale en dessous de laquelle la disposition n'est pas ajustée. L'utilisateur peut réduire la taille de la fenêtre, mais certaines parties de la fenêtre sont alors masquées.

##  <a name="sizehorizontal"></a>  CMFCDynamicLayout::SizeHorizontal

Obtient un [SizeSettings](#sizesettings_structure) valeur qui définit le degré de contrôle enfant est redimensionné horizontalement quand l’utilisateur redimensionne sa fenêtre hôte.

```
static SizeSettings SizeHorizontal(int nRatio);
```

### <a name="parameters"></a>Paramètres

*nRatio*<br/>
Définit sous forme de pourcentage l'amplitude du redimensionnement d'un contrôle enfant sur le plan horizontal quand l'utilisateur redimensionne la fenêtre hôte.

### <a name="return-value"></a>Valeur de retour

Un [SizeSettings](#sizesettings_structure) valeur qui encapsule le ratio de la taille demandée.

### <a name="remarks"></a>Notes

##  <a name="sizehorizontalandvertical"></a>  CMFCDynamicLayout::SizeHorizontalAndVertical

Obtient un [SizeSettings](#sizesettings_structure) valeur qui définit le degré de contrôle enfant est redimensionné horizontalement quand l’utilisateur redimensionne sa fenêtre hôte.

```
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Paramètres

*nXRatio*<br/>
Définit sous forme de pourcentage l'amplitude du redimensionnement d'un contrôle enfant sur le plan horizontal quand l'utilisateur redimensionne la fenêtre hôte.

*nYRatio*<br/>
Définit sous forme de pourcentage l'amplitude du redimensionnement d'un contrôle enfant sur le plan vertical quand l'utilisateur redimensionne la fenêtre hôte.

### <a name="return-value"></a>Valeur de retour

Un [SizeSettings](#sizesettings_structure) valeur qui encapsule le ratio de la taille demandée.

### <a name="remarks"></a>Notes

##  <a name="sizenone"></a>  CMFCDynamicLayout::SizeNone

Obtient un [SizeSettings](#sizesettings_structure) valeur qui ne représente aucun changement de taille pour un contrôle enfant.

```
static SizeSettings SizeNone();
```

### <a name="return-value"></a>Valeur de retour

Un [SizeSettings](#sizesettings_structure) valeur permettant de résoudre le contrôle à une certaine taille, afin qu’il ne modifie pas la taille quand l’utilisateur redimensionne la fenêtre hôte.

### <a name="remarks"></a>Notes

##  <a name="sizesettings_structure"></a>  Cmfcdynamiclayout::sizesettings, Structure

Encapsule les données de changement de taille des contrôles dans une disposition dynamique.

```
struct CMFCDynamicLayout::SizeSettings;
```

### <a name="remarks"></a>Notes

Il s'agit d'une classe imbriquée dans `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout::SizeSettings::IsHorizontal

Vérifie si les données de redimensionnement spécifient un redimensionnement horizontal différent de zéro.

```
BOOL IsHorizontal() const
```

## <a name="return-value"></a>Valeur de retour

TRUE si l'objet `SizeSettings` spécifie un redimensionnement horizontal différent de zéro.

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout::SizeSettings::IsNone

Vérifie si les données de redimensionnement ne spécifient aucun redimensionnement.

```
BOOL IsNone() const
```

## <a name="return-value"></a>Valeur de retour

TRUE si l'objet `SizeSettings` ne spécifie aucun redimensionnement.

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout::SizeSettings::IsVertical

Vérifie si les données de redimensionnement spécifient un redimensionnement vertical différent de zéro.

```
BOOL IsVertical() const
```

## <a name="return-value"></a>Valeur de retour

TRUE si l'objet `SizeSettings` spécifie un redimensionnement vertical différent de zéro.

##  <a name="sizevertical"></a>  CMFCDynamicLayout::SizeVertical

Obtient un [SizeSettings](#sizesettings_structure) valeur qui définit le degré de contrôle enfant est redimensionné verticalement quand l’utilisateur redimensionne sa fenêtre hôte.

```
static SizeSettings SizeVertical(int nRatio);
```

### <a name="parameters"></a>Paramètres

*nRatio*<br/>
Définit sous forme de pourcentage l'amplitude du redimensionnement d'un contrôle enfant sur le plan vertical quand l'utilisateur redimensionne la fenêtre hôte.

### <a name="return-value"></a>Valeur de retour

Un [SizeSettings](#sizesettings_structure) valeur qui encapsule le ratio de la taille demandée.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
