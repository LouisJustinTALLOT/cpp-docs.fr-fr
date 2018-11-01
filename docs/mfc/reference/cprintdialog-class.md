---
title: Cprintdialog, classe
ms.date: 11/04/2016
f1_keywords:
- CPrintDialog
- AFXDLGS/CPrintDialog
- AFXDLGS/CPrintDialog::CPrintDialog
- AFXDLGS/CPrintDialog::CreatePrinterDC
- AFXDLGS/CPrintDialog::DoModal
- AFXDLGS/CPrintDialog::GetCopies
- AFXDLGS/CPrintDialog::GetDefaults
- AFXDLGS/CPrintDialog::GetDeviceName
- AFXDLGS/CPrintDialog::GetDevMode
- AFXDLGS/CPrintDialog::GetDriverName
- AFXDLGS/CPrintDialog::GetFromPage
- AFXDLGS/CPrintDialog::GetPortName
- AFXDLGS/CPrintDialog::GetPrinterDC
- AFXDLGS/CPrintDialog::GetToPage
- AFXDLGS/CPrintDialog::PrintAll
- AFXDLGS/CPrintDialog::PrintCollate
- AFXDLGS/CPrintDialog::PrintRange
- AFXDLGS/CPrintDialog::PrintSelection
- AFXDLGS/CPrintDialog::m_pd
helpviewer_keywords:
- CPrintDialog [MFC], CPrintDialog
- CPrintDialog [MFC], CreatePrinterDC
- CPrintDialog [MFC], DoModal
- CPrintDialog [MFC], GetCopies
- CPrintDialog [MFC], GetDefaults
- CPrintDialog [MFC], GetDeviceName
- CPrintDialog [MFC], GetDevMode
- CPrintDialog [MFC], GetDriverName
- CPrintDialog [MFC], GetFromPage
- CPrintDialog [MFC], GetPortName
- CPrintDialog [MFC], GetPrinterDC
- CPrintDialog [MFC], GetToPage
- CPrintDialog [MFC], PrintAll
- CPrintDialog [MFC], PrintCollate
- CPrintDialog [MFC], PrintRange
- CPrintDialog [MFC], PrintSelection
- CPrintDialog [MFC], m_pd
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
ms.openlocfilehash: 3e86ce3e0179ff7c7a47a7083b6c168fea91ccbc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662434"
---
# <a name="cprintdialog-class"></a>Cprintdialog, classe

Encapsule les services fournis par la boîte de dialogue courante d'impression Windows.

## <a name="syntax"></a>Syntaxe

```
class CPrintDialog : public CCommonDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPrintDialog::CPrintDialog](#cprintdialog)|Construit un objet `CPrintDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Crée un contexte de périphérique d’imprimante sans afficher la boîte de dialogue Imprimer.|
|[CPrintDialog::DoModal](#domodal)|Affiche la boîte de dialogue et permet à l’utilisateur d’effectuer une sélection.|
|[CPrintDialog::GetCopies](#getcopies)|Récupère le nombre de copies demandé.|
|[CPrintDialog::GetDefaults](#getdefaults)|Récupère les valeurs par défaut de l’appareil sans afficher une boîte de dialogue.|
|[CPrintDialog::GetDeviceName](#getdevicename)|Récupère le nom de l’appareil de l’imprimante actuellement sélectionnée.|
|[CPrintDialog::GetDevMode](#getdevmode)|Récupère le `DEVMODE` structure.|
|[CPrintDialog::GetDriverName](#getdrivername)|Récupère le nom du pilote d’imprimante actuellement sélectionnée.|
|[CPrintDialog::GetFromPage](#getfrompage)|Récupère la page de démarrage de l’étendue d’impression.|
|[CPrintDialog::GetPortName](#getportname)|Récupère le nom du port imprimante actuellement sélectionnée.|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Récupère un handle vers le contexte de périphérique d’imprimante.|
|[CPrintDialog::GetToPage](#gettopage)|Récupère la page Fin de l’étendue d’impression.|
|[CPrintDialog::PrintAll](#printall)|Détermine s’il faut imprimer toutes les pages du document.|
|[CPrintDialog::PrintCollate](#printcollate)|Détermine si assemblés copies sont demandées.|
|[CPrintDialog::PrintRange](#printrange)|Détermine s’il faut imprimer uniquement une plage de pages spécifiée.|
|[CPrintDialog::PrintSelection](#printselection)|Détermine s’il faut imprimer uniquement les éléments actuellement sélectionnés.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPrintDialog::m_pd](#m_pd)|Une structure utilisée pour personnaliser un `CPrintDialog` objet.|

## <a name="remarks"></a>Notes

Les boîtes de dialogue d’impression courantes fournissent un moyen simple pour implémenter des boîtes de dialogue d’impression et de configuration de l’impression de manière cohérente avec les normes de Windows.

> [!NOTE]
>  Le `CPrintDialogEx` classe encapsule les services fournis par la feuille de propriétés d’impression de Windows. Pour plus d’informations, consultez le [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) vue d’ensemble.

`CPrintDialog`de fonctionnalités sont remplacée par celle de [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), qui est conçu pour vous fournir une boîte de dialogue commune pour les deux le programme d’installation et de mise en page d’impression.

Vous pouvez compter sur l’infrastructure pour gérer de nombreux aspects du processus d’impression pour votre application. Dans ce cas, l’infrastructure affiche automatiquement la boîte de dialogue commune de Windows pour l’impression. Vous pouvez également avoir le handle de framework d’impression pour votre application mais remplacer la boîte de dialogue commune avec votre propre boîte de dialogue d’impression. Pour plus d’informations sur l’utilisation de l’infrastructure pour gérer des tâches d’impression, consultez l’article [impression](../../mfc/printing.md).

Si vous souhaitez que votre application pour gérer l’impression sans l’intervention de l’infrastructure, vous pouvez utiliser la `CPrintDialog` de classe avec le constructeur fourni « tel quel », ou vous pouvez dériver votre propre classe de boîte de dialogue de `CPrintDialog` et écrire un constructeur pour l’adapter à vos besoins. Dans les deux cas, ces boîtes de dialogue se comportera comme des boîtes de dialogue MFC standards, car ils sont dérivés de la classe `CCommonDialog`.

Pour utiliser un `CPrintDialog` d’objet, commencez par créer l’objet en utilisant le `CPrintDialog` constructeur. Une fois la boîte de dialogue a été construite, vous pouvez définir ou modifier des valeurs dans le [m_pd](#m_pd) structure pour initialiser les valeurs des contrôles de la boîte de dialogue. Le `m_pd` structure est de type [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda). Pour plus d’informations sur cette structure, consultez le Kit de développement Windows.

Si vous ne fournissez pas de vos propres descripteurs dans `m_pd` pour le `hDevMode` et `hDevNames` membres, veillez à appeler la fonction Windows `GlobalFree` pour ces descripteurs lorsque vous avez terminé avec la boîte de dialogue. Lorsque vous utilisez l’implémentation de configuration de l’impression de l’infrastructure fournie par `CWinApp::OnFilePrintSetup`, vous n’êtes pas obligé de libérer ces handles. Les handles sont gérées par `CWinApp` et sont libérés `CWinApp`du destructeur. Il est uniquement nécessaire libérer ces handles lors de l’utilisation `CPrintDialog` autonome.

Après l’initialisation du contrôle de boîte de dialogue, appelez le `DoModal` fonction membre à la boîte de dialogue s’affiche et autorise l’utilisateur à sélectionner les options d’impression. `DoModal` Retourne si l’utilisateur a sélectionné le bouton OK (IDOK) ou Annuler (IDCANCEL).

Si `DoModal` retourne IDOK, vous pouvez utiliser une des `CPrintDialog`de fonctions membres pour récupérer les informations entrées par l’utilisateur.

Le `CPrintDialog::GetDefaults` fonction membre est utile pour extraire les valeurs par défaut d’imprimante en cours sans afficher une boîte de dialogue. Cette fonction membre ne requiert aucune interaction utilisateur.

Vous pouvez utiliser le Windows `CommDlgExtendedError` fonction pour déterminer si une erreur s’est produite lors de l’initialisation de la boîte de dialogue et pour en savoir plus sur l’erreur. Pour plus d’informations sur cette fonction, consultez le Kit de développement Windows.

`CPrintDialog` s’appuie sur le COMMDLG. Fichier DLL qui est livré avec Windows 3.1 et versions ultérieures.

Pour personnaliser la boîte de dialogue, dérivez une classe de `CPrintDialog`, de fournir un modèle de boîte de dialogue personnalisée et ajouter une table des messages pour traiter les messages de notification à partir de contrôles étendus. Tous les messages non traités doivent être transmises à la classe de base. Personnalisation de la fonction de raccordement n’est pas nécessaire.

Pour traiter le message même différemment selon que la boîte de dialogue Imprimer ou la configuration de l’impression, vous devez dériver une classe pour chaque boîte de dialogue. Vous devez également substituer la Windows `AttachOnSetup` (fonction), qui gère la création d’une boîte de dialogue lorsque le bouton de la configuration de l’impression est sélectionné dans une boîte de dialogue Imprimer.

Pour plus d’informations sur l’utilisation de `CPrintDialog`, consultez [des Classes de boîte de dialogue communes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdlgs.h

##  <a name="cprintdialog"></a>  CPrintDialog::CPrintDialog

Construit un objet de boîte de dialogue une impression de Windows ou une configuration de l’impression.

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*bPrintSetupOnly*<br/>
Spécifie si la boîte de dialogue d’impression de Windows standard ou de la boîte de dialogue de configuration de l’impression est affiché. Définissez ce paramètre à True pour afficher la boîte de dialogue de configuration de l’impression Windows standard. Affectez-lui la valeur FALSE pour afficher la boîte de dialogue d’impression de Windows. Si *bPrintSetupOnly* est FALSE, une configuration de l’impression case d’option est toujours affiché dans la boîte de dialogue Imprimer.

*dwFlags*<br/>
Un ou plusieurs indicateurs que vous pouvez utiliser pour personnaliser les paramètres de la boîte de dialogue, combinées à l’aide de l’opérateur OR au niveau du bit. Par exemple, l’indicateur PD_ALLPAGES définit l’étendue d’impression par défaut à toutes les pages du document. Consultez le [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) structure dans le SDK Windows pour plus d’informations sur ces indicateurs.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente ou propriétaire de la boîte de dialogue.

### <a name="remarks"></a>Notes

Cette fonction membre construit uniquement l’objet. Utilisez le `DoModal` fonction membre pour afficher la boîte de dialogue.

Notez que lorsque vous appelez le constructeur avec *bPrintSetupOnly* définie sur FALSE, l’indicateur PD_RETURNDC est automatiquement utilisé. Après avoir appelé `DoModal`, `GetDefaults`, ou `GetPrinterDC`, une contrôleur de domaine de l’imprimante s’affichera dans `m_pd.hDC`. Ce contrôleur de domaine doit être libérée avec un appel à [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) par l’appelant de `CPrintDialog`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPrintDialog::CreatePrinterDC

Crée un contexte de périphérique (DC) à partir de la [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) et [DEVNAMES](../../mfc/reference/devnames-structure.md) structures.

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valeur de retour

Handle de contexte de l’imprimante qui vient d’être créé.

### <a name="remarks"></a>Notes

Ce contrôleur de domaine est censé pour être le périphérique d’impression en cours, et tout autre obtenue précédemment imprimante que contrôleurs de domaine doivent être supprimées par l’utilisateur. Cette fonction peut être appelée et le contrôleur de domaine qui en résulte est utilisé, sans jamais afficher la boîte de dialogue Imprimer.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

##  <a name="domodal"></a>  CPrintDialog::DoModal

Affiche la boîte de dialogue d’impression Windows courantes ainsi que de l’utilisateur de sélectionner différentes options d’impression telles que le nombre de copies, plage de pages, et si les copies doivent être triées.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

IDOK ou IDCANCEL. Si IDCANCEL est retournée, appelez le Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) fonction permettant de déterminer si une erreur s’est produite.

IDOK et IDCANCEL sont des constantes qui indiquent si l’utilisateur a sélectionné le bouton OK ou sur Annuler.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les différentes options de la boîte de dialogue Imprimer en définissant des membres de la `m_pd` structure, vous devez le faire avant d’appeler `DoModal`, mais une fois que l’objet de la boîte de dialogue est construit.

Après avoir appelé `DoModal`, vous pouvez appeler des fonctions pour récupérer les paramètres ou les informations saisies par l’utilisateur dans la boîte de dialogue autres membres.

Notez que lorsque vous appelez le constructeur avec *bPrintSetupOnly* définie sur FALSE, l’indicateur PD_RETURNDC est automatiquement utilisé. Après avoir appelé `DoModal`, `GetDefaults`, ou `GetPrinterDC`, une contrôleur de domaine de l’imprimante s’affichera dans `m_pd.hDC`. Ce contrôleur de domaine doit être libérée avec un appel à [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) par l’appelant de `CPrintDialog`.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPrintDialog::CreatePrinterDC](#createprinterdc).

##  <a name="getcopies"></a>  CPrintDialog::GetCopies

Récupère le nombre de copies demandé.

```
int GetCopies() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de copies demandé.

### <a name="remarks"></a>Notes

Appelez cette fonction après l’appel `DoModal` pour récupérer le nombre de copies demandé.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPrintDialog::PrintCollate](#printcollate).

##  <a name="getdefaults"></a>  CPrintDialog::GetDefaults

Récupère les valeurs par défaut de l’appareil de l’imprimante par défaut sans afficher une boîte de dialogue.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; sinon 0.

### <a name="remarks"></a>Notes

Les valeurs récupérées sont placés dans le `m_pd` structure.

Dans certains cas, un appel à cette fonction appelle le [constructeur](#cprintdialog) pour `CPrintDialog` avec *bPrintSetupOnly* définie sur FALSE. Dans ce cas, un périphérique d’impression et `hDevNames` et `hDevMode` (deux poignées se trouve dans le `m_pd` membre de données) sont alloués automatiquement.

If le constructeur de `CPrintDialog` a été appelé avec *bPrintSetupOnly* définie sur FALSE, cette fonction seulement retourneront `hDevNames` et `hDevMode` situé dans `m_pd.hDevNames` et `m_pd.hDevMode`) à l’appelant, mais retourne également un périphérique d’impression dans `m_pd.hDC`. Il incombe à l’appelant de supprimer le périphérique d’impression et appelez le Windows [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree) fonction sur les poignées lorsque vous avez terminé avec le `CPrintDialog` objet.

### <a name="example"></a>Exemple

Ce fragment de code obtient le contexte de périphérique de l’imprimante par défaut et signale à l’utilisateur de la résolution de l’imprimante en points par pouce. (Cet attribut de fonctionnalités de l’imprimante est souvent appelé PPP.)

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

##  <a name="getdevicename"></a>  CPrintDialog::GetDeviceName

Récupère le nom de l’appareil de l’imprimante actuellement sélectionnée.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom de l’imprimante actuellement sélectionnée.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir appelé [DoModal](#domodal) pour récupérer le nom de l’imprimante actuellement sélectionnée, ou après l’appel [GetDefaults](#getdefaults) pour récupérer les valeurs par défaut de périphérique en cours de l’imprimante par défaut. Utiliser un pointeur vers le `CString` objet retourné par `GetDeviceName` comme valeur de `lpszDeviceName` dans un appel à [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Exemple

Ce fragment de code affiche le nom de l’imprimante par défaut de l’utilisateur et le port qu’il est connecté, ainsi que le nom de spouleur qu'utilise l’imprimante. Le code peut afficher un message indiquant « votre imprimante par défaut est HP LaserJet IIIP sur \\\server\share à l’aide de winspool. », par exemple.

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

##  <a name="getdevmode"></a>  CPrintDialog::GetDevMode

Récupère le `DEVMODE` structure.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valeur de retour

Le [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) structure de données qui contient des informations sur l’environnement d’un pilote d’impression et de l’initialisation des périphériques. Vous devez déverrouiller la mémoire consommée par cette structure avec le Windows [GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock) (fonction), qui est décrit dans le SDK Windows.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer des informations sur le périphérique d’impression.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPrintDialog::PrintCollate](#printcollate).

##  <a name="getdrivername"></a>  CPrintDialog::GetDriverName

Récupère le nom du pilote d’imprimante actuellement sélectionnée.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valeur de retour

Un `CString` en spécifiant le nom du pilote définie par le système.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer le nom du pilote de périphérique d’imprimante définie par le système. Utiliser un pointeur vers le `CString` objet retourné par `GetDriverName` comme valeur de `lpszDriverName` dans un appel à [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPrintDialog::GetDeviceName](#getdevicename).

##  <a name="getfrompage"></a>  CPrintDialog::GetFromPage

Récupère la page de démarrage de l’étendue d’impression.

```
int GetFromPage() const;
```

### <a name="return-value"></a>Valeur de retour

Numéro de page de départ dans la plage de pages à imprimer.

### <a name="remarks"></a>Notes

Appelez cette fonction après l’appel `DoModal` pour récupérer le numéro de page à partir de la plage de pages à imprimer.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPrintDialog::m_pd](#m_pd).

##  <a name="getportname"></a>  CPrintDialog::GetPortName

Récupère le nom du port imprimante actuellement sélectionnée.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom du port imprimante actuellement sélectionnée.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer le nom du port imprimante actuellement sélectionnée.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPrintDialog::GetDeviceName](#getdevicename).

##  <a name="getprinterdc"></a>  CPrintDialog::GetPrinterDC

Récupère un handle vers le contexte de périphérique d’imprimante.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Valeur de retour

Un handle vers le contexte de l’imprimante en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

Si le *bPrintSetupOnly* paramètre de la `CPrintDialog` constructeur était FALSE (indiquant que la boîte de dialogue Imprimer s’affiche), puis `GetPrinterDC` retourne un handle vers le contexte de périphérique d’imprimante. Vous devez appeler la Windows [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) (fonction) pour supprimer le contexte de périphérique lorsque vous avez terminé l’utiliser.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

##  <a name="gettopage"></a>  CPrintDialog::GetToPage

Récupère la page Fin de l’étendue d’impression.

```
int GetToPage() const;
```

### <a name="return-value"></a>Valeur de retour

Numéro de page de fin dans la plage de pages à imprimer.

### <a name="remarks"></a>Notes

Appelez cette fonction après l’appel `DoModal` pour récupérer le numéro de page Fin de la plage de pages à imprimer.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPrintDialog::m_pd](#m_pd).

##  <a name="m_pd"></a>  CPrintDialog::m_pd

Une structure dont les membres stockent les caractéristiques de l’objet de la boîte de dialogue.

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>Notes

Après avoir construit un `CPrintDialog` de l’objet, vous pouvez utiliser `m_pd` pour définir les divers aspects de la boîte de dialogue avant d’appeler le [DoModal](#domodal) fonction membre. Pour plus d’informations sur la `m_pd` structure, consultez [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) dans le SDK Windows.

Si vous modifiez le `m_pd` membre de données directement, vous remplacerez tout comportement par défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

##  <a name="printall"></a>  CPrintDialog::PrintAll

Détermine s’il faut imprimer toutes les pages du document.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si toutes les pages dans le document doivent être affichés ; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction après l’appel `DoModal` pour déterminer s’il faut imprimer toutes les pages dans le document.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPrintDialog::m_pd](#m_pd).

##  <a name="printcollate"></a>  CPrintDialog::PrintCollate

Détermine si assemblés copies sont demandées.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur sélectionne la case à cocher collate dans la boîte de dialogue ; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction après l’appel `DoModal` pour déterminer si l’imprimante doit collate imprimées toutes les copies du document.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

##  <a name="printrange"></a>  CPrintDialog::PrintRange

Détermine s’il faut imprimer uniquement une plage de pages spécifiée.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro uniquement si une plage de pages dans le document sont à imprimer ; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction après l’appel `DoModal` pour déterminer s’il faut N'imprimer qu’une plage de pages dans le document.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPrintDialog::m_pd](#m_pd).

##  <a name="printselection"></a>  CPrintDialog::PrintSelection

Détermine s’il faut imprimer uniquement les éléments actuellement sélectionnés.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si seuls les éléments sélectionnés doivent être affichés ; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction après l’appel `DoModal` pour déterminer s’il faut imprimer uniquement les éléments actuellement sélectionnés.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPrintDialog::m_pd](#m_pd).

## <a name="see-also"></a>Voir aussi

[Exemple MFC DIBLOOK](../../visual-cpp-samples.md)<br/>
[CCommonDialog, classe](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo, structure](../../mfc/reference/cprintinfo-structure.md)
