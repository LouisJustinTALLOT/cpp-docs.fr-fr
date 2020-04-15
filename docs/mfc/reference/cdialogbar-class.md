---
title: CDialogBar, classe
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
ms.openlocfilehash: cf9a2658807959108b3bb0af672d4c1835b58bc5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375672"
---
# <a name="cdialogbar-class"></a>CDialogBar, classe

Fournit les fonctionnalités d'une boîte de dialogue non modale Windows dans une barre de contrôles.

## <a name="syntax"></a>Syntaxe

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDialogBar::CDialogBar](#cdialogbar)|Construit un objet `CDialogBar`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDialogBar::Créer](#create)|Crée une barre de dialogue Windows `CDialogBar` et l’attache à l’objet.|

## <a name="remarks"></a>Notes

Une barre de dialogue ressemble à une boîte de dialogue en ce qu’elle contient des contrôles Windows standard que l’utilisateur peut onglet entre. Une autre similitude est que vous créez un modèle de dialogue pour représenter la barre de dialogue.

La création et l’utilisation d’une `CFormView` barre de dialogue sont similaires à la création et à l’utilisation d’un objet. Tout d’abord, utilisez [l’éditeur de dialogue](../../windows/dialog-editor.md) pour définir un modèle de dialogue avec le style WS_CHILD et pas d’autre style. Le modèle ne doit pas avoir le style WS_VISIBLE. Dans votre code d’application, appelez `CDialogBar` le constructeur `Create` pour construire l’objet, puis appelez `CDialogBar` pour créer la fenêtre de dialogue-bar et attachez-le à l’objet.

Pour plus `CDialogBar`d’informations sur , voir l’article [Dialog Bars](../../mfc/dialog-bars.md) et [Technical Note 31](../../mfc/tn031-control-bars.md), Control Bars.

> [!NOTE]
> Dans la version `CDialogBar` actuelle, un objet ne peut pas héberger les commandes de formulaires Windows. Pour plus d’informations sur les contrôles des formulaires Windows dans Visual C, voir [à l’aide d’un contrôle d’utilisateur de formulaire Windows dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar (en)](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>Spécifications

**En-tête:** afxext.h

## <a name="cdialogbarcdialogbar"></a><a name="cdialogbar"></a>CDialogBar::CDialogBar

Construit un objet `CDialogBar`.

```
CDialogBar();
```

## <a name="cdialogbarcreate"></a><a name="create"></a>CDialogBar::Créer

Charge le modèle de ressource de `lpszTemplateName` `nIDTemplate`boîte de dialogue spécifié par ou, crée la fenêtre `CDialogBar` de dialogue-bar, définit son style, et l’associe à l’objet.

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
Un pointeur `CWnd` à l’objet parent.

*lpszTemplateName*<br/>
Un pointeur sur `CDialogBar` le nom du modèle de ressources de l’objet.

*nStyle*<br/>
Le style barre d’outils. D’autres modèles de barres d’outils pris en charge sont les :

- CBRS_TOP barre de contrôle est en haut de la fenêtre du cadre.

- CBRS_BOTTOM barre de contrôle se trouve au bas de la fenêtre du cadre.

- CBRS_NOALIGN barre de contrôle n’est pas repositionnée lorsque le parent est resized.

- CBRS_TOOLTIPS la barre de contrôle affiche des conseils d’outil.

- CBRS_SIZE_DYNAMIC barre de contrôle est dynamique.

- CBRS_SIZE_FIXED barre de contrôle est fixe.

- CBRS_FLOATING barre de contrôle flotte.

- CBRS_FLYBY barre de statut affiche des informations sur le bouton.

- CBRS_HIDE_INPLACE barre de contrôle n’est pas affichée à l’utilisateur.

*nID*<br/>
L’ID de contrôle de la barre de dialogue.

*nIDTemplate (en)*<br/>
L’ID de `CDialogBar` ressource du modèle de boîte de dialogue de l’objet.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Si vous spécifiez le style d’alignement CBRS_TOP ou CBRS_BOTTOM, la largeur de la barre de dialogue est celle de la fenêtre du cadre et sa hauteur est celle de la ressource spécifiée par *nIDTemplate*. Si vous spécifiez le style d’alignement CBRS_LEFT ou CBRS_RIGHT, la hauteur de la barre de dialogue est celle de la fenêtre du cadre et sa largeur est celle de la ressource spécifiée par *nIDTemplate*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CControlBar, classe](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CFormView](../../mfc/reference/cformview-class.md)<br/>
[CControlBar, classe](../../mfc/reference/ccontrolbar-class.md)
