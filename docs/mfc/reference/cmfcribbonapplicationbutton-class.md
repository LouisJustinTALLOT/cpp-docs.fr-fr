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
ms.openlocfilehash: d1dc8ef6e801623aa96cb4b47936413cd17f24f0
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821240"
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
|`CMFCRibbonApplicationButton::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCRibbonApplicationButton::SetImage](#setimage)|Assigne une image au bouton d’application ruban.|

## <a name="example"></a>Exemples

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCRibbonApplicationButton` . L’exemple montre comment assigner une image au bouton application et comment définir son info-bulle. Cet extrait de code fait partie de l’ [exemple Draw Client](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête:** afxRibbonBar. h

##  <a name="cmfcribbonapplicationbutton"></a>  CMFCRibbonApplicationButton::CMFCRibbonApplicationButton

Construit et initialise un objet [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md) .

```
CMFCRibbonApplicationButton();
CMFCRibbonApplicationButton(UINT uiBmpResID);
CMFCRibbonApplicationButton(HBITMAP hBmp);
```

### <a name="parameters"></a>Paramètres

*uiBmpResID*<br/>
ID de ressource de l’image à afficher sur le bouton d’application.

*hBmp*<br/>
Handle d’une bitmap à afficher sur le bouton d’application.

### <a name="remarks"></a>Notes

Le bouton application ruban est un bouton spécial situé dans l’angle supérieur gauche de la fenêtre d’application. Quand un utilisateur clique sur ce bouton, l’application ouvre un menu qui contient généralement des commandes de **fichiers** courantes, telles que **ouvrir**, **Enregistrer**et **quitter**.

##  <a name="setimage"></a>  CMFCRibbonApplicationButton::SetImage

Assigne une image au bouton de l’application.

```
void SetImage(UINT uiBmpResID);
void SetImage(HBITMAP hBmp);
```

### <a name="parameters"></a>Paramètres

*uiBmpResID*<br/>
dans ID de ressource de l’image à afficher sur le bouton d’application.

*hBmp*<br/>
dans Handle d’une bitmap à afficher sur le bouton d’application.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour assigner une nouvelle image au bouton d’application ruban après avoir créé le bouton. Le bouton application se trouve dans le coin supérieur gauche de la fenêtre d’application.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)
