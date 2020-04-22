---
title: CMFCRibbonApplicationButton, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::SetImage
helpviewer_keywords:
- CMFCRibbonApplicationButton [MFC], CMFCRibbonApplicationButton
- CMFCRibbonApplicationButton [MFC], SetImage
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
ms.openlocfilehash: b28d075c5fcc4313e1a62ae731b3fad8ef4d8a12
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749929"
---
# <a name="cmfcribbonapplicationbutton-class"></a>CMFCRibbonApplicationButton, classe

Implémente un bouton spécial situé dans l'angle supérieur gauche de la fenêtre d'application. Une fois activé, le bouton ouvre un menu qui contient généralement des commandes **Fichier** courantes telles que **Ouvrir**, **Enregistrer**et **Quitter**.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonApplicationButton : public CMFCRibbonButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|Construit et initialise un objet `CMFCRibbonApplicationButton`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCRibbonApplicationButton::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCRibbonApplicationButton::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCRibbonApplicationButton::SetImage](#setimage)|Assigne une image sur le bouton d’application du ruban.|

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCRibbonApplicationButton` . L’exemple montre comment attribuer une image au bouton d’application, et comment définir son tooltip. Cet extrait de code fait partie de l’ [exemple Draw Client](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxRibbonBar.h

## <a name="cmfcribbonapplicationbuttoncmfcribbonapplicationbutton"></a><a name="cmfcribbonapplicationbutton"></a>CMFCRibbonApplicationButton::CMFCRibbonApplicationButton

Construit et initialise un objet [CMFCRibbonApplicationButton.](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

```
CMFCRibbonApplicationButton();
CMFCRibbonApplicationButton(UINT uiBmpResID);
CMFCRibbonApplicationButton(HBITMAP hBmp);
```

### <a name="parameters"></a>Paramètres

*uiBmpResID*<br/>
L’ID de ressource de l’image pour afficher sur le bouton d’application.

*hBmp (en)*<br/>
Une poignée à un bitmap pour afficher sur le bouton d’application.

### <a name="remarks"></a>Notes

Le bouton d’application ruban est un bouton spécial qui est situé dans le coin supérieur gauche de la fenêtre d’application. Lorsqu’un utilisateur clique sur ce bouton, l’application ouvre un menu qui contient habituellement des commandes **de fichiers** courantes, telles que **Open**, **Save**, et **Exit**.

## <a name="cmfcribbonapplicationbuttonsetimage"></a><a name="setimage"></a>CMFCRibbonApplicationButton::SetImage

Assigne une image sur le bouton d’application.

```cpp
void SetImage(UINT uiBmpResID);
void SetImage(HBITMAP hBmp);
```

### <a name="parameters"></a>Paramètres

*uiBmpResID*<br/>
[dans] L’ID de ressource de l’image pour afficher sur le bouton d’application.

*hBmp (en)*<br/>
[dans] Une poignée à un bitmap pour afficher sur le bouton d’application.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour attribuer une nouvelle image au bouton d’application du ruban après avoir créé le bouton. Le bouton d’application est situé dans le coin supérieur gauche de la fenêtre d’application.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)
