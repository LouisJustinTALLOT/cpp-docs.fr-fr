---
title: Cpagesetupdialog, classe
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
ms.openlocfilehash: 01a320fbcd9760bab484f3c75553613852ca9aed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62373165"
---
# <a name="cpagesetupdialog-class"></a>Cpagesetupdialog, classe

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
|[CPageSetupDialog::DoModal](#domodal)|Affiche la boîte de dialogue et permet une sélection à la marque de l’utilisateur.|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|Retourne le nom de l’appareil de l’imprimante.|
|[CPageSetupDialog::GetDevMode](#getdevmode)|Retourne la structure DEVMODE actuelle de l’imprimante.|
|[CPageSetupDialog::GetDriverName](#getdrivername)|Retourne le pilote utilisé par l’imprimante.|
|[CPageSetupDialog::GetMargins](#getmargins)|Retourne les paramètres actuels de la marge de l’imprimante.|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|Retourne la taille du papier de l’imprimante.|
|[CPageSetupDialog::GetPortName](#getportname)|Retourne le nom de port de sortie.|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|Appelé par l’infrastructure pour afficher l’image d’une page imprimée.|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|Appelé par l’infrastructure avant le rendu de l’image d’une page imprimée.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|Une structure utilisée pour personnaliser un `CPageSetupDialog` objet.|

## <a name="remarks"></a>Notes

Cette classe est conçue pour prendre la place de la boîte de dialogue de configuration de l’impression.

Pour utiliser un `CPageSetupDialog` d’objet, commencez par créer l’objet en utilisant le `CPageSetupDialog` constructeur. Une fois la boîte de dialogue a été construite, vous pouvez définir ou modifier des valeurs dans le `m_psd` membre de données pour initialiser les valeurs des contrôles de la boîte de dialogue. Le [m_psd](#m_psd) structure est de type PAGESETUPDLG.

Après l’initialisation du contrôle de boîte de dialogue, appelez le `DoModal` fonction membre à la boîte de dialogue s’affiche et autorise l’utilisateur à sélectionner les options d’impression. `DoModal` Retourne si l’utilisateur a sélectionné le bouton OK (IDOK) ou Annuler (IDCANCEL).

Si `DoModal` retourne IDOK, vous pouvez utiliser plusieurs `CPageSetupDialog`de fonctions membres, ou accès le `m_psd` membre de données, pour récupérer les informations saisies par l’utilisateur.

> [!NOTE]
>  Une fois que la boîte de dialogue Mise en Page OLE est fermée, toutes les modifications apportées par l’utilisateur ne seront pas enregistrées par l’infrastructure. C’est à l’application elle-même pour enregistrer toutes les valeurs à partir de cette boîte de dialogue vers un emplacement permanent, comme membre du document de l’application ou de la classe d’application.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdlgs.h

##  <a name="cpagesetupdialog"></a>  CPageSetupDialog::CPageSetupDialog

Appelez cette fonction pour construire un `CPageSetupDialog` objet.

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Un ou plusieurs indicateurs que vous pouvez utiliser pour personnaliser les paramètres de la boîte de dialogue. Les valeurs peuvent être combinées à l’aide de l’opérateur OR au niveau du bit. Ces valeurs ont les significations suivantes :

- PSD_DEFAULTMINMARGINS définit les largeurs minimale autorisées pour les marges de page être le même que les valeurs minimales de l’imprimante. Cet indicateur est ignoré si les indicateurs PSD_MARGINS et PSD_MINMARGINS sont également spécifiés.

- PSD_INWININIINTLMEASURE pas implémentée.

- PSD_MINMARGINS provoque le système à utiliser les valeurs spécifiées dans le `rtMinMargin` membre en tant que les largeurs minimale autorisées pour la gauche, haut, droite et marges. Le système empêche l’utilisateur d’entrer la largeur est inférieure à la valeur minimale spécifiée. Si PSD_MINMARGINS n’est pas spécifié, le système définit les largeurs minimales autorisées à celles autorisées par l’imprimante.

- PSD_MARGINS Active la zone de contrôle de marge.

- PSD_INTHOUSANDTHSOFINCHES entraîne les unités de la boîte de dialogue à mesurer 1/1000 de pouce.

- PSD_INHUNDREDTHSOFMILLIMETERS entraîne les unités de la boîte de dialogue doit être mesurée dans 1/100 de millimètre.

- PSD_DISABLEMARGINS désactive les contrôles de boîte de dialogue de marge.

- PSD_DISABLEPRINTER désactive le bouton imprimante.

- PSD_NOWARNING empêche le message d’avertissement s’affiche lorsque aucune imprimante par défaut.

- PSD_DISABLEORIENTATION désactive le contrôle de boîte de dialogue de l’orientation de page.

- PSD_RETURNDEFAULT provoque `CPageSetupDialog` pour retourner [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) et [DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames) structures qui sont initialisés pour l’imprimante par défaut sans afficher une boîte de dialogue. Il est supposé que les deux `hDevNames` et `hDevMode` ont la valeur NULL ; sinon, la fonction retourne une erreur. Si l’imprimante par défaut du système est prise en charge par un ancien pilote d’imprimante (antérieure à Windows version 3.0), uniquement `hDevNames` est retournée ; `hDevMode` a la valeur NULL.

- PSD_DISABLEPAPER désactive le contrôle de sélection de papier.

- PSD_SHOWHELP provoque la boîte de dialogue Afficher le bouton aide. Le `hwndOwner` membre ne doit pas être NULL si cet indicateur est spécifié.

- PSD_ENABLEPAGESETUPHOOK permet la fonction de raccordement spécifiée dans `lpfnSetupHook`.

- PSD_ENABLEPAGESETUPTEMPLATE provoque le système d’exploitation créer la boîte de dialogue à l’aide de la boîte de dialogue modèle identifiée par `hInstance` et `lpSetupTemplateName`.

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE indique que `hInstance` identifie un bloc de données qui contient un modèle de boîte de dialogue préchargées. Le système ignore `lpSetupTemplateName` si cet indicateur est spécifié.

- PSD_ENABLEPAGEPAINTHOOK permet la fonction de raccordement spécifiée dans `lpfnPagePaintHook`.

- PSD_DISABLEPAGEPAINTING désactive la zone de dessin de la boîte de dialogue.

*pParentWnd*<br/>
Pointeur vers le parent ou le propriétaire de la boîte de dialogue.

### <a name="remarks"></a>Notes

Utilisez le [DoModal](../../mfc/reference/cdialog-class.md#domodal) (fonction) pour afficher la boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPageSetupDialog::CreatePrinterDC

Crée un contexte de périphérique à partir de la [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) et [DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames) structures.

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valeur de retour

Handle de contexte de l’imprimante qui vient d’être créé (DC).

##  <a name="domodal"></a>  CPageSetupDialog::DoModal

Appelez cette fonction pour afficher la boîte de dialogue Mise en Page OLE Windows courants et permettre à l’utilisateur de sélectionner différentes options d’impression telles que les marges d’impression, la taille et l’orientation du papier et imprimante de destination.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

IDOK ou IDCANCEL. Si IDCANCEL est retournée, appelez le Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) fonction permettant de déterminer si une erreur s’est produite.

IDOK et IDCANCEL sont des constantes qui indiquent si l’utilisateur a sélectionné le bouton OK ou sur Annuler.

### <a name="remarks"></a>Notes

En outre, l’utilisateur peut accéder les options de configuration d’imprimante tels que l’emplacement réseau et des propriétés spécifiques à l’imprimante sélectionnée.

Si vous souhaitez initialiser les différentes options de la boîte de dialogue Mise en Page en définissant des membres de la `m_psd` structure, vous devez le faire avant d’appeler `DoModal`, et après la construction de l’objet de la boîte de dialogue. Après avoir appelé `DoModal`, appeler des fonctions pour récupérer les paramètres ou les informations saisies par l’utilisateur dans la boîte de dialogue autres membres.

Si vous souhaitez propager les paramètres actuels entrés par l’utilisateur, effectuez un appel à [CWinApp::SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter). Cette fonction accepte les informations à partir de la `CPageSetupDialog` de l’objet et initialise et sélectionne une nouvelle imprimante de contrôleur de domaine avec les attributs corrects.

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

##  <a name="getdevicename"></a>  CPageSetupDialog::GetDeviceName

Appelez cette fonction après `DoModal` pour récupérer le nom de l’imprimante actuellement sélectionnée.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom de l’appareil utilisé par le `CPageSetupDialog` objet.

##  <a name="getdevmode"></a>  CPageSetupDialog::GetDevMode

Appelez cette fonction après avoir appelé `DoModal` pour récupérer des informations sur le contexte de périphérique d’imprimante de la `CPageSetupDialog` objet.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valeur de retour

Le [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) structure de données qui contient des informations sur l’environnement d’un pilote d’impression et de l’initialisation des périphériques. Vous devez déverrouiller la mémoire consommée par cette structure avec le Windows [GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock) (fonction), qui est décrit dans le SDK Windows.

##  <a name="getdrivername"></a>  CPageSetupDialog::GetDriverName

Appelez cette fonction après avoir appelé [DoModal](../../mfc/reference/cprintdialog-class.md#domodal) pour récupérer le nom du pilote de périphérique d’imprimante définie par le système.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valeur de retour

Un `CString` en spécifiant le nom du pilote définie par le système.

### <a name="remarks"></a>Notes

Utiliser un pointeur vers le `CString` objet retourné par `GetDriverName` comme valeur de `lpszDriverName` dans un appel à [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getmargins"></a>  CPageSetupDialog::GetMargins

Appelez cette fonction après un appel à `DoModal` pour récupérer les marges du pilote de périphérique d’imprimante.

```
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>Paramètres

*lpRectMargins*<br/>
Pointeur vers un [RECT](/windows/desktop/api/windef/ns-windef-tagrect) structure ou [CRect](../../atl-mfc-shared/reference/crect-class.md) objet qui décrit les marges d’impression pour l’imprimante actuellement sélectionnée (en pouces de 1/1000 ou 1/100 mm). Passez la valeur NULL pour ce paramètre, si vous n’êtes pas intéressé par ce rectangle.

*lpRectMinMargins*<br/>
Pointeur vers un `RECT` structure ou `CRect` objet qui décrit les marges d’impression minimale pour l’imprimante actuellement sélectionnée (en pouces de 1/1000 ou 1/100 mm). Passez la valeur NULL pour ce paramètre, si vous n’êtes pas intéressé par ce rectangle.

##  <a name="getpapersize"></a>  CPageSetupDialog::GetPaperSize

Appelez cette fonction pour extraire la taille du papier sélectionné pour l’impression.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Valeur de retour

Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objet qui contient la taille du papier (en pouces de 1/1000 ou 1/100 mm) sélectionné pour l’impression.

##  <a name="getportname"></a>  CPageSetupDialog::GetPortName

Appelez cette fonction après l’appel `DoModal` pour récupérer le nom du port imprimante actuellement sélectionnée.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom du port imprimante actuellement sélectionnée.

##  <a name="m_psd"></a>  CPageSetupDialog::m_psd

Une structure de type PAGESETUPDLG, dont les membres stockent les caractéristiques de l’objet de la boîte de dialogue.

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>Notes

Après avoir construit un `CPageSetupDialog` de l’objet, vous pouvez utiliser `m_psd` pour définir les divers aspects de la boîte de dialogue avant d’appeler le `DoModal` fonction membre.

Si vous modifiez le `m_psd` membre de données directement, vous remplacerez tout comportement par défaut.

Pour plus d’informations sur la [PAGESETUPDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpsda) structure, consultez le kit SDK Windows.

Consultez l’exemple de [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

##  <a name="ondrawpage"></a>  CPageSetupDialog::OnDrawPage

Appelé par l’infrastructure pour dessiner l’image d’une page imprimée.

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers le contexte de périphérique d’imprimante.

*nMessage*<br/>
Spécifie un message indiquant la zone de la page en cours de saisie. Il peut s'agir d'une des valeurs suivantes :

- WM_PSD_FULLPAGERECT la zone de page entière.

- Marges minimales WM_PSD_MINMARGINRECT actuel.

- Marges WM_PSD_MARGINRECT actuel.

- WM_PSD_GREEKTEXTRECT le contenu de la page.

- Zone WM_PSD_ENVSTAMPRECT réservé pour une représentation sous forme de timbre.

- Zone WM_PSD_YAFULLPAGERECT pour obtenir une représentation de l’adresse de retour. Cette zone s’étend sur les bords de la zone de page d’exemple.

*lpRect*<br/>
Pointeur vers un [CRect](../../atl-mfc-shared/reference/crect-class.md) ou [RECT](/windows/desktop/api/windef/ns-windef-tagrect) objet contenant les coordonnées de la zone de dessin.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si géré ; sinon 0.

### <a name="remarks"></a>Notes

Cette image est ensuite affichée dans le cadre de la boîte de dialogue Mise en Page OLE courante. L’implémentation par défaut Dessine une image d’une page de texte.

Remplacez cette fonction pour personnaliser le dessin d’une zone spécifique de l’image ou l’image entière. Vous pouvez le faire à l’aide un **basculer** instruction avec **cas** instructions vérifiant la valeur de *nMessage*. Par exemple, pour personnaliser le rendu du contenu de l’image de page, vous pouvez utiliser l’exemple de code suivant :

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

Notez que vous n’avez pas besoin de gérer tous les cas de *nMessage*. Vous pouvez choisir de gérer un composant de l’image, plusieurs composants de l’image ou la zone entière.

##  <a name="predrawpage"></a>  CPageSetupDialog::PreDrawPage

Appelé par l’infrastructure avant de dessiner l’image d’écran d’une page imprimée.

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>Paramètres

*wPaper*<br/>
Spécifie une valeur qui indique le format du papier. Cette valeur peut s’agir de la **DMPAPER_** valeurs répertoriées dans la description de la [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) structure.

*wFlags*<br/>
Indique l’orientation du papier ou d’enveloppe, et que l’imprimante est une matrice de points ou d’un appareil HPPCL (Hewlett Packard Printer Control Language). Ce paramètre peut prendre l'une des valeurs suivantes :

- 0 x 001 papier en mode paysage (matriciel)

- 0 x 003 papier en mode paysage (HPPCL)

- 0x005 papier en mode portrait (matriciel)

- 0x007 papier en mode portrait (HPPCL)

- 0x00b enveloppe en mode paysage (HPPCL)

- 0x00d enveloppe en mode portrait (matriciel)

- 0x019 enveloppe en mode paysage (matriciel)

- 0x01f enveloppe en mode portrait (matriciel)

*pPSD*<br/>
Pointeur désignant une structure `PAGESETUPDLG`. Pour plus d’informations sur [PAGESETUPDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpsda), consultez le kit SDK Windows.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si géré ; sinon 0.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour personnaliser le dessin de l’image. Si vous substituez cette fonction renvoie la valeur TRUE, vous devez dessiner l’image entière. Si vous substituez cette fonction renvoie la valeur FALSE, l’image entière par défaut est dessiné par le framework.

## <a name="see-also"></a>Voir aussi

[Exemple MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog, classe](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
