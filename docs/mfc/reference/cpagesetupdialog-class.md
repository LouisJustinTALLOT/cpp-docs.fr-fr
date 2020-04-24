---
title: Classe CPageSetupDialog
ms.date: 11/04/2016
f1_keywords:
- CPageSetupDialog
- AFXDLGS/CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CreatePrinterDC
- AFXDLGS/CPageSetupDialog::DoModal
- AFXDLGS/CPageSetupDialog::GetDeviceName
- AFXDLGS/CPageSetupDialog::GetDevMode
- AFXDLGS/CPageSetupDialog::GetDriverName
- AFXDLGS/CPageSetupDialog::GetMargins
- AFXDLGS/CPageSetupDialog::GetPaperSize
- AFXDLGS/CPageSetupDialog::GetPortName
- AFXDLGS/CPageSetupDialog::OnDrawPage
- AFXDLGS/CPageSetupDialog::PreDrawPage
- AFXDLGS/CPageSetupDialog::m_psd
helpviewer_keywords:
- CPageSetupDialog [MFC], CPageSetupDialog
- CPageSetupDialog [MFC], CreatePrinterDC
- CPageSetupDialog [MFC], DoModal
- CPageSetupDialog [MFC], GetDeviceName
- CPageSetupDialog [MFC], GetDevMode
- CPageSetupDialog [MFC], GetDriverName
- CPageSetupDialog [MFC], GetMargins
- CPageSetupDialog [MFC], GetPaperSize
- CPageSetupDialog [MFC], GetPortName
- CPageSetupDialog [MFC], OnDrawPage
- CPageSetupDialog [MFC], PreDrawPage
- CPageSetupDialog [MFC], m_psd
ms.assetid: 049c0ac8-f254-4854-9414-7a8271d1447a
ms.openlocfilehash: 3664149ef0d7476b460ef06cddaf2b8145ade701
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753688"
---
# <a name="cpagesetupdialog-class"></a>Classe CPageSetupDialog

Encapsule les services fournis par la boîte de dialogue Mise en page OLE courante Windows avec une prise en charge supplémentaire pour définir et modifier les marges d'impression.

## <a name="syntax"></a>Syntaxe

```
class CPageSetupDialog : public CCommonDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|Construit un objet `CPageSetupDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPageSetupDialog::CréerPrinterDC](#createprinterdc)|Crée un contexte d’appareil pour l’impression.|
|[CPageSetupDialog::DoModal](#domodal)|Affiche la boîte de dialogue et permet à l’utilisateur de faire une sélection.|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|Retourne le nom de l’imprimante.|
|[CPageSetupDialog::GetDevMode](#getdevmode)|Retourne le DEVMODE actuel de l’imprimante.|
|[CPageSetupDialog::GetDriverName](#getdrivername)|Retourne le conducteur utilisé par l’imprimante.|
|[CPageSetupDialog::GetMargins](#getmargins)|Retourne les paramètres de marge actuels de l’imprimante.|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|Retourne la taille du papier de l’imprimante.|
|[CPageSetupDialog::GetPortName](#getportname)|Retourne le nom du port de sortie.|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|Appelé par le cadre pour rendre une image d’écran d’une page imprimée.|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|Appelé par le cadre avant de rendre une image d’écran d’une page imprimée.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|Une structure utilisée pour `CPageSetupDialog` personnaliser un objet.|

## <a name="remarks"></a>Notes

Cette classe est conçue pour prendre la place de la boîte de dialogue Print Setup.

Pour utiliser `CPageSetupDialog` un objet, créez `CPageSetupDialog` d’abord l’objet à l’aide du constructeur. Une fois que la boîte de dialogue a été `m_psd` construite, vous pouvez définir ou modifier toutes les valeurs du membre des données pour initialiser les valeurs des contrôles de la boîte de dialogue. La structure [m_psd](#m_psd) est de type PAGESETUPDLG.

Après avoir paralysé les `DoModal` commandes de la boîte de dialogue, appelez la fonction membre pour afficher la boîte de dialogue et permettre à l’utilisateur de sélectionner les options d’impression. `DoModal`l’utilisateur a choisi le bouton OK (IDOK) ou Annuler (IDCANCEL).

Si `DoModal` vous retournez IDOK, `CPageSetupDialog`vous pouvez utiliser plusieurs `m_psd` fonctions de membre ou accéder au membre des données pour récupérer l’entrée d’informations de l’utilisateur.

> [!NOTE]
> Une fois que la boîte de dialogue commune OLE Page Setup est rejetée, les modifications apportées par l’utilisateur ne seront pas enregistrées par le cadre. Il appartient à l’application elle-même d’enregistrer toutes les valeurs de cette boîte de dialogue à un emplacement permanent, comme le membre du document de l’application ou de la classe de demande.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdlgs.h

## <a name="cpagesetupdialogcpagesetupdialog"></a><a name="cpagesetupdialog"></a>CPageSetupDialog::CPageSetupDialog

Appelez cette fonction `CPageSetupDialog` pour construire un objet.

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Un ou plusieurs drapeaux que vous pouvez utiliser pour personnaliser les paramètres de la boîte de dialogue. Les valeurs peuvent être combinées à l’aide de l’opérateur bitwise-OR. Ces valeurs ont les significations suivantes :

- PSD_DEFAULTMINMARGINS définit les largeurs minimales autorisées pour que les marges de la page soient les mêmes que les minimums de l’imprimante. Ce drapeau est ignoré si les drapeaux PSD_MARGINS et PSD_MINMARGINS sont également spécifiés.

- PSD_INWININIINTLMEASURE non mis en œuvre.

- PSD_MINMARGINS provoque le système d’utiliser les `rtMinMargin` valeurs spécifiées dans le membre comme les largeurs minimales autorisées pour les marges gauche, supérieure, droite et inférieure. Le système empêche l’utilisateur d’entrer une largeur inférieure au minimum spécifié. Si PSD_MINMARGINS n’est pas spécifiée, le système définit les largeurs minimales autorisées à celles autorisées par l’imprimante.

- PSD_MARGINS active la zone de contrôle des marges.

- PSD_INTHOUSANDTHSOFINCHES fait mesurer les unités de la boîte de dialogue en 1/1000 de pouce.

- PSD_INHUNDREDTHSOFMILLIMETERS fait mesurer les unités de la boîte de dialogue en 1/100 de millimètre.

- PSD_DISABLEMARGINS désactive les contrôles de boîte de dialogue de marge.

- PSD_DISABLEPRINTER désactive le bouton Imprimante.

- PSD_NOWARNING empêche le message d’avertissement d’être affiché lorsqu’il n’y a pas d’imprimante par défaut.

- PSD_DISABLEORIENTATION désactive le contrôle du dialogue d’orientation de la page.

- PSD_RETURNDEFAULT Causes de `CPageSetupDialog` retour des structures [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) et [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) qui sont paralysées pour l’imprimante par défaut du système sans afficher une boîte de dialogue. On suppose que `hDevNames` `hDevMode` les deux et sont NULL; autrement, la fonction renvoie une erreur. Si l’imprimante par défaut du système est prise en charge par `hDevNames` un ancien pilote d’imprimante (plus tôt que la version Windows 3.0), seulement est retournée; `hDevMode` est NULL.

- PSD_DISABLEPAPER désactive le contrôle de sélection du papier.

- PSD_SHOWHELP provoque la boîte de dialogue pour afficher le bouton Aide. Le `hwndOwner` membre ne doit pas être NULL si ce drapeau est spécifié.

- PSD_ENABLEPAGESETUPHOOK Permet la fonction de `lpfnSetupHook`crochet spécifiée dans .

- PSD_ENABLEPAGESETUPTEMPLATE provoque le système d’exploitation de créer la boîte de `hInstance` dialogue `lpSetupTemplateName`en utilisant la boîte de modèle de dialogue identifié par et .

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE indique qu’il s’identifie `hInstance` à un bloc de données qui contient un modèle de boîte de dialogue préchargé. Le système `lpSetupTemplateName` ne tient pas compte si ce drapeau est spécifié.

- PSD_ENABLEPAGEPAINTHOOK Permet la fonction de `lpfnPagePaintHook`crochet spécifiée dans .

- PSD_DISABLEPAGEPAINTING désactive la zone de tirage de la boîte de dialogue.

*pParentWnd*<br/>
Pointeur vers le parent ou le propriétaire de la boîte de dialogue.

### <a name="remarks"></a>Notes

Utilisez la fonction [DoModal](../../mfc/reference/cdialog-class.md#domodal) pour afficher la boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

## <a name="cpagesetupdialogcreateprinterdc"></a><a name="createprinterdc"></a>CPageSetupDialog::CréerPrinterDC

Crée un contexte d’imprimante à partir des structures [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) et [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valeur de retour

Gérer le contexte nouvel et nouvellement créé de l’appareil d’imprimante (DC).

## <a name="cpagesetupdialogdomodal"></a><a name="domodal"></a>CPageSetupDialog::DoModal

Appelez cette fonction pour afficher la boîte de dialogue commune OLE Page Setup de Windows et permettre à l’utilisateur de sélectionner diverses options de configuration d’impression telles que les marges d’impression, la taille et l’orientation du papier et l’imprimante de destination.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

IDOK ou IDCANCEL. Si IDCANCEL est retourné, appelez la fonction Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) pour déterminer si une erreur s’est produite.

IDOK et IDCANCEL sont des constantes qui indiquent si l’utilisateur a choisi le bouton OK ou Annuler.

### <a name="remarks"></a>Notes

En outre, l’utilisateur peut accéder aux options d’installation de l’imprimante telles que l’emplacement du réseau et les propriétés spécifiques à l’imprimante sélectionnée.

Si vous souhaitez paralyser les différentes options de `m_psd` dialogue Page Setup en `DoModal`définissant les membres de la structure, vous devez le faire avant d’appeler, et après la construction de l’objet de dialogue. Après `DoModal`avoir appelé, appelez d’autres fonctions de membre pour récupérer les paramètres ou l’entrée d’informations par l’utilisateur dans la boîte de dialogue.

Si vous souhaitez propager les paramètres actuels saisis par l’utilisateur, appelez [CWinApp:SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter). Cette fonction prend les `CPageSetupDialog` informations de l’objet et initialise et sélectionne une nouvelle imprimante DC avec les attributs appropriés.

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

## <a name="cpagesetupdialoggetdevicename"></a><a name="getdevicename"></a>CPageSetupDialog::GetDeviceName

Appelez cette `DoModal` fonction après pour récupérer le nom de l’imprimante actuellement sélectionnée.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom de `CPageSetupDialog` l’appareil utilisé par l’objet.

## <a name="cpagesetupdialoggetdevmode"></a><a name="getdevmode"></a>CPageSetupDialog::GetDevMode

Appelez cette fonction `DoModal` après avoir appelé pour récupérer `CPageSetupDialog` des informations sur le contexte de l’appareil d’imprimante de l’objet.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valeur de retour

La structure de données [DEVMODE,](/windows/win32/api/wingdi/ns-wingdi-devmodea) qui contient des informations sur l’initialisation de l’appareil et l’environnement d’un pilote d’impression. Vous devez déverrouiller la mémoire prise par cette structure avec la fonction Windows [GlobalUnlock,](/windows/win32/api/winbase/nf-winbase-globalunlock) qui est décrite dans le SDK Windows.

## <a name="cpagesetupdialoggetdrivername"></a><a name="getdrivername"></a>CPageSetupDialog::GetDriverName

Appelez cette fonction après avoir appelé [DoModal](../../mfc/reference/cprintdialog-class.md#domodal) pour récupérer le nom du pilote de périphérique d’imprimante défini par le système.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valeur de retour

Un `CString` spécifier le nom du conducteur défini par le système.

### <a name="remarks"></a>Notes

Utilisez un pointeur `CString` à `GetDriverName` l’objet `lpszDriverName` retourné par comme la valeur d’un appel à [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

## <a name="cpagesetupdialoggetmargins"></a><a name="getmargins"></a>CPageSetupDialog::GetMargins

Appelez cette fonction après `DoModal` un appel pour récupérer les marges du pilote de l’appareil d’imprimante.

```cpp
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>Paramètres

*lpRectMargins*<br/>
Pointeur vers une structure [RECT](/windows/win32/api/windef/ns-windef-rect) ou un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui décrit (en 1/1000 pouces ou 1/100 mm) les marges d’impression pour l’imprimante actuellement sélectionnée. Passer NULL pour ce paramètre, si vous n’êtes pas intéressé par ce rectangle.

*lpRectMinMargins*<br/>
Pointeur `RECT` vers `CRect` une structure ou un objet qui décrit (en 1/1000 pouces ou 1/100 mm) les marges d’impression minimales pour l’imprimante actuellement sélectionnée. Passer NULL pour ce paramètre, si vous n’êtes pas intéressé par ce rectangle.

## <a name="cpagesetupdialoggetpapersize"></a><a name="getpapersize"></a>CPageSetupDialog::GetPaperSize

Appelez cette fonction pour récupérer la taille du papier sélectionné pour l’impression.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Valeur de retour

Un objet [CSize](../../atl-mfc-shared/reference/csize-class.md) contenant la taille du papier (en 1/1000 pouces ou 1/100 mm) sélectionné pour l’impression.

## <a name="cpagesetupdialoggetportname"></a><a name="getportname"></a>CPageSetupDialog::GetPortName

Appelez cette fonction `DoModal` après avoir appelé pour récupérer le nom du port d’imprimante actuellement sélectionné.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom du port d’imprimante actuellement sélectionné.

## <a name="cpagesetupdialogm_psd"></a><a name="m_psd"></a>CPageSetupDialog::m_psd

Une structure de type PAGESETUPDLG, dont les membres stockent les caractéristiques de l’objet de dialogue.

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>Notes

Après la `CPageSetupDialog` construction d’un `m_psd` objet, vous pouvez utiliser pour `DoModal` définir divers aspects de la boîte de dialogue avant d’appeler la fonction membre.

Si vous `m_psd` modifiez directement le membre des données, vous remplacerez tout comportement par défaut.

Pour plus d’informations sur la structure [PAGESETUPDLG,](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw) voir le SDK Windows.

Voir l’exemple pour [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

## <a name="cpagesetupdialogondrawpage"></a><a name="ondrawpage"></a>CPageSetupDialog::OnDrawPage

Appelé par le cadre pour dessiner une image d’écran d’une page imprimée.

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur sur le contexte de l’appareil d’imprimante.

*nMessage*<br/>
Spécifie un message indiquant la zone de la page actuellement en cours de tirage. Il peut s'agir d'une des méthodes suivantes :

- WM_PSD_FULLPAGERECT Toute la page.

- WM_PSD_MINMARGINRECT marges minimales actuelles.

- WM_PSD_MARGINRECT marges actuelles.

- WM_PSD_GREEKTEXTRECT Contenu de la page.

- WM_PSD_ENVSTAMPRECT Zone réservée à la représentation d’un timbre-poste.

- WM_PSD_YAFULLPAGERECT zone pour une représentation d’adresse de retour. Cette zone s’étend jusqu’aux bords de la zone de la page de l’échantillon.

*lpRect*<br/>
Pointeur vers un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou [RECT](/windows/win32/api/windef/ns-windef-rect) contenant les coordonnées de la zone de dessin.

### <a name="return-value"></a>Valeur de retour

Valeur non zéro si manipulé; sinon 0.

### <a name="remarks"></a>Notes

Cette image est ensuite affichée dans le cadre de la boîte de dialogue OLE Page Setup commune. L’implémentation par défaut dresse une image d’une page de texte.

Remplacer cette fonction pour personnaliser le dessin d’une zone spécifique de l’image, ou l’image entière. Vous pouvez le faire en utilisant une instruction **de commutation** avec des instructions de **cas** vérifiant la valeur de *nMessage*. Par exemple, pour personnaliser le rendu du contenu de l’image de la page, vous pouvez utiliser l’exemple suivant :

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

Notez que vous n’avez pas besoin de gérer tous les cas de *nMessage*. Vous pouvez choisir de manipuler un composant de l’image, plusieurs composants de l’image, ou toute la zone.

## <a name="cpagesetupdialogpredrawpage"></a><a name="predrawpage"></a>CPageSetupDialog::PreDrawPage

Appelé par le cadre avant de dessiner l’image d’écran d’une page imprimée.

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>Paramètres

*wPaper (en)*<br/>
Spécifie une valeur qui indique la taille du papier. Cette valeur peut être l’une des **valeurs DMPAPER_** énumérées dans la description de la structure [DEVMODE.](/windows/win32/api/wingdi/ns-wingdi-devmodea)

*wFlags (en)*<br/>
Indique l’orientation du papier ou de l’enveloppe, et si l’imprimante est un dispositif de matrice de points ou de HPPCL (Hewlett Packard Printer Control Language). Ce paramètre peut prendre l'une des valeurs suivantes :

- 0x001 Papier en mode paysage (matrice de points)

- 0x003 Papier en mode paysage (HPPCL)

- 0x005 Papier en mode portrait (matrice de points)

- 0x007 Papier en mode portrait (HPPCL)

- Enveloppe 0x00b en mode paysage (HPPCL)

- Enveloppe 0x00d en mode portrait (matrice de points)

- 0x019 Enveloppe en mode paysage (matrice de points)

- Enveloppe 0x01f en mode portrait (matrice de points)

*pPSD (en)*<br/>
Pointeur désignant une structure `PAGESETUPDLG`. Pour plus d’informations sur [PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw), voir le Windows SDK.

### <a name="return-value"></a>Valeur de retour

Valeur non zéro si manipulé; sinon 0.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour personnaliser le dessin de l’image. Si vous remplacez cette fonction et retournez VRAI, vous devez dessiner l’image entière. Si vous remplacez cette fonction et retournez FALSE, l’image par défaut entière est dessinée par le cadre.

## <a name="see-also"></a>Voir aussi

[Échantillon MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[Classe CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
