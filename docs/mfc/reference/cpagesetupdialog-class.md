---
title: CPageSetupDialog, classe
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
ms.openlocfilehash: b81e2a65d09bf5dadbc0860d692caee7a4bd386f
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739763"
---
# <a name="cpagesetupdialog-class"></a>CPageSetupDialog, classe

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
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|Crée un contexte de périphérique pour l’impression.|
|[CPageSetupDialog::DoModal](#domodal)|Affiche la boîte de dialogue et permet à l’utilisateur d’effectuer une sélection.|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|Retourne le nom de l’appareil de l’imprimante.|
|[CPageSetupDialog::GetDevMode](#getdevmode)|Retourne le DEVMODE actuel de l’imprimante.|
|[CPageSetupDialog::GetDriverName](#getdrivername)|Retourne le pilote utilisé par l’imprimante.|
|[CPageSetupDialog::GetMargins](#getmargins)|Retourne les paramètres de marge actuelle de l’imprimante.|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|Retourne le format de papier de l’imprimante.|
|[CPageSetupDialog::GetPortName](#getportname)|Retourne le nom du port de sortie.|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|Appelé par l’infrastructure pour restituer une image d’écran d’une page imprimée.|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|Appelée par l’infrastructure avant de restituer une image d’écran d’une page imprimée.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|Structure utilisée pour personnaliser un `CPageSetupDialog` objet.|

## <a name="remarks"></a>Notes

Cette classe est conçue pour remplacer la boîte de dialogue Configuration de l’impression.

Pour utiliser un `CPageSetupDialog` objet, commencez par créer l’objet à `CPageSetupDialog` l’aide du constructeur. Une fois la boîte de dialogue construite, vous pouvez définir ou modifier les valeurs `m_psd` du membre de données pour initialiser les valeurs des contrôles de la boîte de dialogue. La structure [m_psd](#m_psd) est de type PAGESETUPDLG.

Après l’initialisation des contrôles de boîte de dialogue, `DoModal` appelez la fonction membre pour afficher la boîte de dialogue et permettre à l’utilisateur de sélectionner des options d’impression. `DoModal`retourne une valeur indiquant si l’utilisateur a sélectionné le bouton OK (IDOK) ou CANCEL (IDCANCEL).

Si `DoModal` retourne IDOK, vous pouvez utiliser plusieurs fonctions `CPageSetupDialog`membres de ou accéder au `m_psd` membre de données pour récupérer les informations entrées par l’utilisateur.

> [!NOTE]
>  Une fois la boîte de dialogue mise en page OLE courante fermée, les modifications apportées par l’utilisateur ne sont pas enregistrées par l’infrastructure. Il appartient à l’application elle-même d’enregistrer toutes les valeurs de cette boîte de dialogue dans un emplacement permanent, comme le membre de la classe document ou application de l’application.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdlgs. h

##  <a name="cpagesetupdialog"></a>  CPageSetupDialog::CPageSetupDialog

Appelez cette fonction pour construire un `CPageSetupDialog` objet.

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Un ou plusieurs indicateurs que vous pouvez utiliser pour personnaliser les paramètres de la boîte de dialogue. Les valeurs peuvent être combinées à l’aide de l’opérateur or au niveau du bit. Ces valeurs ont les significations suivantes :

- PSD_DEFAULTMINMARGINS définit la largeur minimale autorisée pour les marges de la page afin qu’elles soient identiques aux valeurs minimales de l’imprimante. Cet indicateur est ignoré si les indicateurs PSD_MARGINS et PSD_MINMARGINS sont également spécifiés.

- PSD_INWININIINTLMEASURE non implémenté.

- PSD_MINMARGINS fait en sorte que le système utilise les valeurs spécifiées dans le `rtMinMargin` membre en tant que largeur minimale autorisée pour les marges gauche, haut, droite et inférieure. Le système empêche l’utilisateur d’entrer une largeur inférieure à la valeur minimale spécifiée. Si PSD_MINMARGINS n’est pas spécifié, le système définit les largeurs minimales autorisées sur celles autorisées par l’imprimante.

- PSD_MARGINS active la zone de contrôle des marges.

- PSD_INTHOUSANDTHSOFINCHES entraîne la mesure des unités de la boîte de dialogue en 1/1000 de pouce.

- PSD_INHUNDREDTHSOFMILLIMETERS entraîne la mesure des unités de la boîte de dialogue en 1/100 d’un millimètre.

- PSD_DISABLEMARGINS désactive les contrôles de boîte de dialogue marge.

- PSD_DISABLEPRINTER désactive le bouton imprimante.

- PSD_NOWARNING empêche l’affichage du message d’avertissement lorsqu’il n’y a pas d’imprimante par défaut.

- PSD_DISABLEORIENTATION désactive le contrôle de boîte de dialogue d’orientation de page.

- PSD_RETURNDEFAULT oblige `CPageSetupDialog` à retourner des structures [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) et [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) initialisées pour l’imprimante système par défaut sans afficher de boîte de dialogue. Il est supposé que et `hDevNames` `hDevMode` ont tous deux la valeur null ; dans le cas contraire, la fonction retourne une erreur. Si l’imprimante par défaut du système est prise en charge par un ancien pilote d’imprimante (antérieur à la `hDevNames` version 3,0 de Windows), seul est retourné ; `hDevMode` a la valeur null.

- PSD_DISABLEPAPER désactive le contrôle de sélection de papier.

- PSD_SHOWHELP fait en sorte que la boîte de dialogue affiche le bouton aide. Le `hwndOwner` membre ne doit pas avoir la valeur null si cet indicateur est spécifié.

- PSD_ENABLEPAGESETUPHOOK active la fonction de raccordement spécifiée `lpfnSetupHook`dans.

- PSD_ENABLEPAGESETUPTEMPLATE fait en sorte que le système d’exploitation crée la boîte de dialogue à l’aide de `hInstance` la `lpSetupTemplateName`boîte de dialogue modèle identifiée par et.

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE indique que `hInstance` identifie un bloc de données qui contient un modèle de boîte de dialogue préchargé. Le système ignore `lpSetupTemplateName` si cet indicateur est spécifié.

- PSD_ENABLEPAGEPAINTHOOK active la fonction de raccordement spécifiée `lpfnPagePaintHook`dans.

- PSD_DISABLEPAGEPAINTING désactive la zone de dessin de la boîte de dialogue.

*pParentWnd*<br/>
Pointeur vers le parent ou le propriétaire de la boîte de dialogue.

### <a name="remarks"></a>Notes

Utilisez la fonction [DoModal](../../mfc/reference/cdialog-class.md#domodal) pour afficher la boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPageSetupDialog::CreatePrinterDC

Crée un contexte de périphérique d’impression à partir des structures [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) et [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) .

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valeur de retour

Handle vers le contexte de périphérique (DC) d’imprimante nouvellement créé.

##  <a name="domodal"></a>  CPageSetupDialog::DoModal

Appelez cette fonction pour afficher la boîte de dialogue mise en page OLE courante de Windows et autoriser l’utilisateur à sélectionner diverses options d’impression, telles que les marges d’impression, la taille et l’orientation du papier et l’imprimante de destination.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

IDOK ou IDCANCEL. Si IDCANCEL est retourné, appelez la fonction [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows pour déterminer si une erreur s’est produite.

IDOK et IDCANCEL sont des constantes qui indiquent si l’utilisateur a sélectionné le bouton OK ou annuler.

### <a name="remarks"></a>Notes

En outre, l’utilisateur peut accéder aux options de configuration de l’imprimante, telles que l’emplacement réseau et les propriétés spécifiques à l’imprimante sélectionnée.

Si vous souhaitez initialiser les différentes options de la boîte de dialogue de mise en page `m_psd` en définissant les membres de la structure `DoModal`, vous devez le faire avant d’appeler, et après la construction de l’objet de boîte de dialogue. Après l' `DoModal`appel de, appelez d’autres fonctions membres pour récupérer les paramètres ou les informations entrées par l’utilisateur dans la boîte de dialogue.

Si vous souhaitez propager les paramètres actuels entrés par l’utilisateur, effectuez un appel à [CWinApp :: SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter). Cette fonction prend les informations de l' `CPageSetupDialog` objet et initialise et sélectionne un nouveau contrôleur de contexte d’imprimante avec les attributs appropriés.

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPageSetupDialog :: CPageSetupDialog](#cpagesetupdialog).

##  <a name="getdevicename"></a>  CPageSetupDialog::GetDeviceName

Appelez cette fonction après `DoModal` pour récupérer le nom de l’imprimante actuellement sélectionnée.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valeur de retour

Nom de l’appareil utilisé par `CPageSetupDialog` l’objet.

##  <a name="getdevmode"></a>  CPageSetupDialog::GetDevMode

Appelez cette fonction après avoir `DoModal` appelé pour extraire des informations sur le contexte de périphérique `CPageSetupDialog` d’impression de l’objet.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valeur de retour

Structure de données [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) , qui contient des informations sur l’initialisation de l’appareil et l’environnement d’un pilote d’impression. Vous devez déverrouiller la mémoire prise par cette structure à l’aide de la fonction [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock) de Windows, qui est décrite dans la SDK Windows.

##  <a name="getdrivername"></a>  CPageSetupDialog::GetDriverName

Appelez cette fonction après avoir appelé [DoModal](../../mfc/reference/cprintdialog-class.md#domodal) pour récupérer le nom du pilote de périphérique d’imprimante défini par le système.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valeur de retour

`CString` Spécifiant le nom du pilote défini par le système.

### <a name="remarks"></a>Notes

Utilisez un pointeur vers l' `CString` objet retourné par `GetDriverName` comme valeur de `lpszDriverName` dans un appel à [CDC :: CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getmargins"></a>  CPageSetupDialog::GetMargins

Appelez cette fonction après un appel à `DoModal` pour récupérer les marges du pilote de périphérique d’impression.

```
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>Paramètres

*lpRectMargins*<br/>
Pointeur vers une structure [Rect](/windows/win32/api/windef/ns-windef-rect) ou un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui décrit (dans 1/1000 pouces ou 1/100 mm) les marges d’impression pour l’imprimante actuellement sélectionnée. Transmettez la valeur NULL pour ce paramètre, si vous n’êtes pas intéressé par ce rectangle.

*lpRectMinMargins*<br/>
Pointeur vers une `RECT` structure ou `CRect` un objet qui décrit (en 1/1000 pouces ou 1/100 mm) les marges d’impression minimales pour l’imprimante actuellement sélectionnée. Transmettez la valeur NULL pour ce paramètre, si vous n’êtes pas intéressé par ce rectangle.

##  <a name="getpapersize"></a>  CPageSetupDialog::GetPaperSize

Appelez cette fonction pour récupérer la taille du papier sélectionné pour l’impression.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Valeur de retour

Objet [CSize](../../atl-mfc-shared/reference/csize-class.md) contenant la taille du papier (en 1/1000 pouces ou 1/100 mm) sélectionné pour l’impression.

##  <a name="getportname"></a>  CPageSetupDialog::GetPortName

Appelez cette fonction après avoir `DoModal` appelé pour récupérer le nom du port d’imprimante actuellement sélectionné.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valeur de retour

Nom du port d’imprimante actuellement sélectionné.

##  <a name="m_psd"></a>  CPageSetupDialog::m_psd

Structure de type PAGESETUPDLG, dont les membres stockent les caractéristiques de l’objet Dialog.

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>Notes

Après avoir construit un `CPageSetupDialog` objet, vous pouvez utiliser `m_psd` pour définir différents aspects de la boîte de dialogue avant d' `DoModal` appeler la fonction membre.

Si vous modifiez directement `m_psd` le membre de données, vous remplacerez tout comportement par défaut.

Pour plus d’informations sur la structure [PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw) , reportez-vous à la SDK Windows.

Consultez l’exemple de [CPageSetupDialog :: CPageSetupDialog](#cpagesetupdialog).

##  <a name="ondrawpage"></a>  CPageSetupDialog::OnDrawPage

Appelé par l’infrastructure pour dessiner une image d’écran d’une page imprimée.

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers le contexte de périphérique d’impression.

*nMessage*<br/>
Spécifie un message indiquant la zone de la page en cours de dessin. Il peut s'agir d'une des valeurs suivantes :

- WM_PSD_FULLPAGERECT la totalité de la zone de page.

- WM_PSD_MINMARGINRECT marges minimales actuelles.

- WM_PSD_MARGINRECT marges actuelles.

- WM_PSD_GREEKTEXTRECT contenu de la page.

- Zone WM_PSD_ENVSTAMPRECT réservée pour une représentation d’horodatage de la publication.

- Zone WM_PSD_YAFULLPAGERECT pour une représentation d’adresse de retour. Cette zone s’étend jusqu’aux bords de l’exemple de zone de page.

*lpRect*<br/>
Pointeur vers un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou [Rect](/windows/win32/api/windef/ns-windef-rect) contenant les coordonnées de la zone de dessin.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si elle est gérée ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette image s’affiche alors dans la boîte de dialogue mise en page OLE courante. L’implémentation par défaut dessine une image d’une page de texte.

Substituez cette fonction pour personnaliser le dessin d’une zone spécifique de l’image ou de la totalité de l’image. Pour ce faire, vous pouvez utiliser une instruction **switch** avec des instructions **case** vérifiant la valeur de *nsuivant*. Par exemple, pour personnaliser le rendu du contenu de l’image de page, vous pouvez utiliser l’exemple de code suivant :

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

Notez que vous n’avez pas besoin de gérer tous les cas de *nsuivant*. Vous pouvez choisir de gérer un composant de l’image, plusieurs composants de l’image ou la zone entière.

##  <a name="predrawpage"></a>  CPageSetupDialog::PreDrawPage

Appelée par l’infrastructure avant de dessiner l’image d’écran d’une page imprimée.

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>Paramètres

*wPaper*<br/>
Spécifie une valeur qui indique le format du papier. Cette valeur peut être l’une des valeurs **DMPAPER_** indiquées dans la description de la structure [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) .

*wFlags*<br/>
Indique l’orientation du papier ou de l’enveloppe, et si l’imprimante est un appareil à matrice matricielle ou en HPPCL (Hewlett Packard Printer Control Language). Ce paramètre peut prendre l'une des valeurs suivantes :

- Papier 0x001 en mode paysage (matricielle)

- Papier 0x003 en mode paysage (en HPPCL)

- Papier 0x005 en mode Portrait (matricielle)

- Papier 0x007 en mode Portrait (en HPPCL)

- Enveloppe 0x00b en mode paysage (en HPPCL)

- Enveloppe 0x00d en mode Portrait (matricielle)

- Enveloppe 0x019 en mode paysage (matricielle)

- Enveloppe 0x01f en mode Portrait (matricielle)

*pPSD*<br/>
Pointeur désignant une structure `PAGESETUPDLG`. Pour plus d’informations sur [PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw), consultez la SDK Windows.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si elle est gérée ; Sinon, 0.

### <a name="remarks"></a>Notes

Substituez cette fonction pour personnaliser le dessin de l’image. Si vous remplacez cette fonction et que vous retournez la valeur TRUE, vous devez dessiner l’intégralité de l’image. Si vous substituez cette fonction et que vous retournez FALSe, l’ensemble de l’image par défaut est dessiné par l’infrastructure.

## <a name="see-also"></a>Voir aussi

[Exemple MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog, classe](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
