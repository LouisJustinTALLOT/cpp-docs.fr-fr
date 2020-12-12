---
description: 'En savoir plus sur : CDialogBar, classe'
title: CDialogBar (classe)
ms.date: 11/04/2016
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
ms.openlocfilehash: 7feb31cd8152309557a398f5c8d0edb8d91c340e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185217"
---
# <a name="cdialogbar-class"></a>CDialogBar (classe)

Fournit les fonctionnalités d'une boîte de dialogue non modale Windows dans une barre de contrôles.

## <a name="syntax"></a>Syntaxe

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDialogBar :: CDialogBar](#cdialogbar)|Construit un objet `CDialogBar`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDialogBar :: Create](#create)|Crée une barre de boîte de dialogue Windows et l’attache à l' `CDialogBar` objet.|

## <a name="remarks"></a>Notes

Une barre de boîte de dialogue ressemble à une boîte de dialogue dans la mesure où elle contient des contrôles Windows standard que l’utilisateur peut passer d’un onglet à l’autre. Une autre similarité est que vous créez un modèle de boîte de dialogue pour représenter la barre de boîte de dialogue.

La création et l’utilisation d’une barre de boîte de dialogue sont similaires à la création et à l’utilisation d’un `CFormView` objet. Tout d’abord, utilisez l' [éditeur de boîtes](../../windows/dialog-editor.md) de dialogue pour définir un modèle de boîte de dialogue avec le style WS_CHILD et aucun autre style. Le modèle ne doit pas avoir le style WS_VISIBLE. Dans votre code d’application, appelez le constructeur pour construire l' `CDialogBar` objet, puis appelez `Create` pour créer la fenêtre de la barre de dialogue et l’attacher à l' `CDialogBar` objet.

Pour plus d’informations sur `CDialogBar` , consultez les [barres de boîte de dialogue](../../mfc/dialog-bars.md) d’article et la [note technique 31](../../mfc/tn031-control-bars.md), barres de contrôles.

> [!NOTE]
> Dans la version actuelle, un `CDialogBar` objet ne peut pas héberger des contrôles Windows Forms. Pour plus d’informations sur les contrôles Windows Forms dans Visual C++, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>Spécifications

**En-tête :** afxext. h

## <a name="cdialogbarcdialogbar"></a><a name="cdialogbar"></a> CDialogBar :: CDialogBar

Construit un objet `CDialogBar`.

```
CDialogBar();
```

## <a name="cdialogbarcreate"></a><a name="create"></a> CDialogBar :: Create

Charge le modèle de ressource de boîte de dialogue spécifié par `lpszTemplateName` ou `nIDTemplate` , crée la fenêtre de la barre de dialogue, définit son style et l’associe à l' `CDialogBar` objet.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

virtual BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers l’objet parent `CWnd` .

*lpszTemplateName*<br/>
Pointeur vers le nom du modèle de `CDialogBar` ressource de boîte de dialogue de l’objet.

*nStyle*<br/>
Style de la barre d’outils. Les autres styles de barres d’outils pris en charge sont les suivants :

- CBRS_TOP barre de contrôle est en haut de la fenêtre frame.

- CBRS_BOTTOM barre de contrôle est en bas de la fenêtre frame.

- CBRS_NOALIGN barre de contrôle n’est pas repositionnée lorsque le parent est redimensionné.

- CBRS_TOOLTIPS barre de contrôle affiche des info-bulles.

- CBRS_SIZE_DYNAMIC barre de contrôle est dynamique.

- CBRS_SIZE_FIXED barre de contrôle est fixe.

- CBRS_FLOATING barre de contrôle est flottante.

- CBRS_FLYBY barre d’état affiche des informations sur le bouton.

- CBRS_HIDE_INPLACE barre de contrôle n’est pas affichée à l’utilisateur.

*nID*<br/>
ID de contrôle de la barre de boîte de dialogue.

*nIDTemplate*<br/>
ID de ressource du modèle de boîte de dialogue de l' `CDialogBar` objet.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Si vous spécifiez le style d’alignement CBRS_TOP ou CBRS_BOTTOM, la largeur de la barre de boîte de dialogue est celle de la fenêtre frame et sa hauteur est celle de la ressource spécifiée par *nIDTemplate*. Si vous spécifiez le style d’alignement CBRS_LEFT ou CBRS_RIGHT, la hauteur de la barre de boîte de dialogue est celle de la fenêtre frame et sa largeur est celle de la ressource spécifiée par *nIDTemplate*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CControlBar (classe)](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFormView, classe](../../mfc/reference/cformview-class.md)<br/>
[CControlBar (classe)](../../mfc/reference/ccontrolbar-class.md)
