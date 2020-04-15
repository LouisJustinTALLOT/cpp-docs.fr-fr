---
title: CPrintDialog, classe
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
ms.openlocfilehash: 6490e5488c5ab3b808a02e3608b75541e4063d8f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364068"
---
# <a name="cprintdialog-class"></a>CPrintDialog, classe

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
|[CPrintDialog::CréerPrinterDC](#createprinterdc)|Crée un contexte d’appareil d’imprimante sans afficher la boîte de dialogue d’impression.|
|[CPrintDialog::DoModal](#domodal)|Affiche la boîte de dialogue et permet à l’utilisateur de faire une sélection.|
|[CPrintDialog::GetCopies](#getcopies)|Récupère le nombre d’exemplaires demandés.|
|[CPrintDialog::GetDefaults](#getdefaults)|Récupère les défauts de l’appareil sans afficher une boîte de dialogue.|
|[CPrintDialog::GetDeviceName](#getdevicename)|Récupère le nom de l’appareil d’imprimante actuellement sélectionné.|
|[CPrintDialog::GetDevMode](#getdevmode)|Récupère la `DEVMODE` structure.|
|[CPrintDialog::GetDriverName](#getdrivername)|Récupère le nom du pilote d’imprimante actuellement sélectionné.|
|[CPrintDialog::GetDePage](#getfrompage)|Récupère la page de départ de la plage d’impression.|
|[CPrintDialog::GetPortName](#getportname)|Récupère le nom du port d’imprimantes actuellement sélectionné.|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Récupère une poignée dans le contexte de l’appareil d’imprimante.|
|[CPrintDialog::GetToPage](#gettopage)|Récupère la page de fin de la plage d’impression.|
|[CPrintDialog::PrintAll](#printall)|Détermine s’il y a toutes les pages du document.|
|[CPrintDialog::PrintCollate](#printcollate)|Détermine si des copies rassemblées sont demandées.|
|[CPrintDialog::PrintRange](#printrange)|Détermine s’il ne faut imprimer qu’une gamme spécifiée de pages.|
|[CPrintDialog::PrintSelection](#printselection)|Détermine s’il ne faut imprimer que les articles actuellement sélectionnés.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPrintDialog::m_pd](#m_pd)|Une structure utilisée pour `CPrintDialog` personnaliser un objet.|

## <a name="remarks"></a>Notes

Les boîtes de dialogue imprimées communes offrent un moyen facile d’implémenter des boîtes de dialogue imprimées et imprimées d’une manière conforme aux normes Windows.

> [!NOTE]
> La `CPrintDialogEx` classe résume les services fournis par la feuille de propriété Windows Print. Pour plus d’informations, consultez la vue d’ensemble [de CPrintDialogEx.](../../mfc/reference/cprintdialogex-class.md)

`CPrintDialog`la fonctionnalité de [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), qui est conçue pour vous fournir une boîte de dialogue commune pour la configuration d’impression et la configuration de la page.

Vous pouvez compter sur le cadre pour gérer de nombreux aspects du processus d’impression pour votre application. Dans ce cas, le cadre affiche automatiquement la boîte de dialogue commune Windows pour l’impression. Vous pouvez également avoir l’impression de poignée de cadre pour votre application, mais remplacer la boîte commune de dialogue d’impression avec votre propre boîte de dialogue d’impression. Pour plus d’informations sur l’utilisation du cadre pour gérer les tâches d’impression, voir l’article [Impression](../../mfc/printing.md).

Si vous voulez que votre application gère l’impression sans `CPrintDialog` la participation du cadre, vous pouvez utiliser la classe « `CPrintDialog` telle qu’elle est » avec le constructeur fourni, ou vous pouvez tirer votre propre classe de dialogue et écrire un constructeur en fonction de vos besoins. Dans les deux cas, ces boîtes de dialogue se comporteront comme `CCommonDialog`des boîtes de dialogue MFC standard parce qu’elles sont dérivées de la classe.

Pour utiliser `CPrintDialog` un objet, créez `CPrintDialog` d’abord l’objet à l’aide du constructeur. Une fois que la boîte de dialogue a été construite, vous pouvez définir ou modifier toutes les valeurs de la structure [m_pd](#m_pd) pour initialiser les valeurs des commandes de la boîte de dialogue. La `m_pd` structure est de type [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga). Pour plus d’informations sur cette structure, voir le SDK Windows.

Si vous ne fournissez pas `m_pd` vos `hDevMode` `hDevNames` propres poignées pour les `GlobalFree` membres et les membres, assurez-vous d’appeler la fonction Windows pour ces poignées lorsque vous avez terminé avec la boîte de dialogue. Lorsque vous utilisez la mise en `CWinApp::OnFilePrintSetup`œuvre de configuration d’impression du cadre fournie par , vous n’avez pas à libérer ces poignées. Les poignées sont `CWinApp` maintenues par `CWinApp`et sont libérées dans le destructeur de 's. Il est seulement nécessaire de libérer `CPrintDialog` ces poignées lors de l’utilisation autonome.

Après avoir paralysé les `DoModal` commandes de la boîte de dialogue, appelez la fonction membre pour afficher la boîte de dialogue et permettre à l’utilisateur de sélectionner les options d’impression. `DoModal`l’utilisateur a choisi le bouton OK (IDOK) ou Annuler (IDCANCEL).

Si `DoModal` vous retournez IDOK, `CPrintDialog`vous pouvez utiliser l’une des fonctions des membres pour récupérer l’entrée d’informations par l’utilisateur.

La `CPrintDialog::GetDefaults` fonction membre est utile pour récupérer les défauts d’imprimante actuels sans afficher une boîte de dialogue. Cette fonction de membre ne nécessite aucune interaction utilisateur.

Vous pouvez utiliser `CommDlgExtendedError` la fonction Windows pour déterminer si une erreur s’est produite lors de l’initialisation de la boîte de dialogue et pour en savoir plus sur l’erreur. Pour plus d’informations sur cette fonction, voir le SDK Windows.

`CPrintDialog`s’appuie sur le COMMDLG. Fichier DLL qui expédie avec les versions Windows 3.1 et plus tard.

Pour personnaliser la boîte de dialogue, `CPrintDialog`dérivez une classe, fournissez un modèle de dialogue personnalisé et ajoutez une carte de message pour traiter les messages de notification à partir des contrôles étendus. Tous les messages non traités doivent être transmis à la classe de base. Personnaliser la fonction de crochet n’est pas nécessaire.

Pour traiter le même message différemment selon que la boîte de dialogue est imprimée ou imprime configuration, vous devez tirer une classe pour chaque boîte de dialogue. Vous devez également remplacer `AttachOnSetup` la fonction Windows, qui gère la création d’une nouvelle boîte de dialogue lorsque le bouton Print Setup est sélectionné dans une boîte de dialogue d’impression.

Pour plus d’informations sur l’utilisation `CPrintDialog`, voir Classes de dialogue [commun](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdlgs.h

## <a name="cprintdialogcprintdialog"></a><a name="cprintdialog"></a>CPrintDialog::CPrintDialog

Construit soit un objet de dialogue Windows Print ou Print Setup.

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*bPrintSetupOnly*<br/>
Précise si la boîte de dialogue Windows Print standard ou la boîte de dialogue Print Setup est affichée. Définissez ce paramètre à TRUE pour afficher la boîte de dialogue standard de Configuration d’impression De Windows. Réglez-le à FALSE pour afficher la boîte de dialogue Windows Print. Si *bPrintSetupOnly* est FALSE, un bouton d’option d’impression est toujours affiché dans la boîte de dialogue d’impression.

*dwFlags*<br/>
Un ou plusieurs drapeaux que vous pouvez utiliser pour personnaliser les paramètres de la boîte de dialogue, combinés à l’aide de l’opérateur BITwise OU. Par exemple, le drapeau PD_ALLPAGES définit la plage d’impression par défaut à toutes les pages du document. Consultez la structure [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) dans le Windows SDK pour plus d’informations sur ces drapeaux.

*pParentWnd*<br/>
Un pointeur à la fenêtre parent ou propriétaire de la boîte de dialogue.

### <a name="remarks"></a>Notes

Cette fonction de membre ne construit que l’objet. Utilisez `DoModal` la fonction du membre pour afficher la boîte de dialogue.

Notez que lorsque vous appelez le constructeur avec *bPrintSetupOnly* réglé sur FALSE, le drapeau PD_RETURNDC est automatiquement utilisé. Après `DoModal` `GetDefaults`l’appel `GetPrinterDC`, , ou , `m_pd.hDC`une imprimante DC sera retourné dans . Ce DC doit être libéré avec un appel `CPrintDialog`à [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) par l’appelant de .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

## <a name="cprintdialogcreateprinterdc"></a><a name="createprinterdc"></a>CPrintDialog::CréerPrinterDC

Crée un contexte d’imprimante (DC) à partir des structures [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) et [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valeur de retour

Gérer le contexte nouvel et nouvellement créé de l’appareil d’imprimante.

### <a name="remarks"></a>Notes

Ce DC est supposé être l’imprimante actuelle DC, et tout autre DC imprimante précédemment obtenu doit être supprimé par l’utilisateur. Cette fonction peut être appelée, et le DC résultant utilisé, sans jamais afficher la boîte de dialogue d’impression.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

## <a name="cprintdialogdomodal"></a><a name="domodal"></a>CPrintDialog::DoModal

Affiche la boîte de dialogue d’impression commune de Windows et permet à l’utilisateur de sélectionner diverses options d’impression telles que le nombre d’exemplaires, la plage de pages et la collecte de copies.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

IDOK ou IDCANCEL. Si IDCANCEL est retourné, appelez la fonction Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) pour déterminer si une erreur s’est produite.

IDOK et IDCANCEL sont des constantes qui indiquent si l’utilisateur a choisi le bouton OK ou Annuler.

### <a name="remarks"></a>Notes

Si vous souhaitez paralyser les différentes options `m_pd` de dialogue d’impression `DoModal`en définissant les membres de la structure, vous devriez le faire avant d’appeler, mais après la construction de l’objet de dialogue.

Après `DoModal`avoir appelé, vous pouvez appeler d’autres fonctions de membre pour récupérer les paramètres ou l’entrée d’informations par l’utilisateur dans la boîte de dialogue.

Notez que lorsque vous appelez le constructeur avec *bPrintSetupOnly* réglé sur FALSE, le drapeau PD_RETURNDC est automatiquement utilisé. Après `DoModal` `GetDefaults`l’appel `GetPrinterDC`, , ou , `m_pd.hDC`une imprimante DC sera retourné dans . Ce DC doit être libéré avec un appel `CPrintDialog`à [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) par l’appelant de .

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPrintDialog:CreatePrinterDC](#createprinterdc).

## <a name="cprintdialoggetcopies"></a><a name="getcopies"></a>CPrintDialog::GetCopies

Récupère le nombre d’exemplaires demandés.

```
int GetCopies() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’exemplaires demandés.

### <a name="remarks"></a>Notes

Appelez cette fonction `DoModal` après avoir appelé pour récupérer le nombre de copies demandées.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPrintDialog::PrintCollate](#printcollate).

## <a name="cprintdialoggetdefaults"></a><a name="getdefaults"></a>CPrintDialog::GetDefaults

Récupère les défauts de l’imprimante par défaut sans afficher de boîte de dialogue.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction a été réussie; sinon 0.

### <a name="remarks"></a>Notes

Les valeurs récupérées sont `m_pd` placées dans la structure.

Dans certains cas, un appel à [constructor](#cprintdialog) cette `CPrintDialog` fonction appellera le constructeur pour avec *bPrintSetupOnly* réglé à FALSE. Dans ces cas, une `hDevNames` `hDevMode` imprimante DC et (deux poignées situées dans le membre de `m_pd` données) sont automatiquement attribuées.

Si le constructeur `CPrintDialog` pour a été appelé avec *bPrintSetupOnly* réglé `hDevNames` `hDevMode` à `m_pd.hDevNames` FALSE, cette fonction non seulement retournera et situé dans et `m_pd.hDevMode`) à l’appelant, mais retournera également une imprimante DC dans `m_pd.hDC`. Il est de la responsabilité de l’appelant de supprimer l’imprimante DC et d’appeler `CPrintDialog` la fonction Windows [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) sur les poignées lorsque vous avez terminé avec l’objet.

### <a name="example"></a>Exemple

Ce fragment de code permet à l’utilisateur de trouver un contexte d’appareil et de rapporter à l’utilisateur la résolution de l’imprimante en points par pouce. (Cet attribut des capacités de l’imprimante est souvent appelé DPI.)

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

## <a name="cprintdialoggetdevicename"></a><a name="getdevicename"></a>CPrintDialog::GetDeviceName

Récupère le nom de l’appareil d’imprimante actuellement sélectionné.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom de l’imprimante actuellement sélectionnée.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir appelé [DoModal](#domodal) pour récupérer le nom de l’imprimante actuellement sélectionnée, ou après avoir appelé [GetDefaults](#getdefaults) pour récupérer les défauts actuels de l’imprimante par défaut. Utilisez un pointeur `CString` à `GetDeviceName` l’objet `lpszDeviceName` retourné par comme la valeur d’un appel à [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Exemple

Ce fragment de code affiche le nom de l’imprimante par défaut de l’utilisateur et le port à qui il est connecté, ainsi que le nom de bobine que l’imprimante utilise. Le code peut afficher une boîte de messages qui dit: \\«Votre imprimante par défaut est HP LaserJet IIIP sur 'server’share en utilisant winspool.", par exemple.

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

## <a name="cprintdialoggetdevmode"></a><a name="getdevmode"></a>CPrintDialog::GetDevMode

Récupère la `DEVMODE` structure.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valeur de retour

La structure de données [DEVMODE,](/windows/win32/api/wingdi/ns-wingdi-devmodea) qui contient des informations sur l’initialisation de l’appareil et l’environnement d’un pilote d’impression. Vous devez déverrouiller la mémoire prise par cette structure avec la fonction Windows [GlobalUnlock,](/windows/win32/api/winbase/nf-winbase-globalunlock) qui est décrite dans le SDK Windows.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer des informations sur l’appareil d’impression.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPrintDialog::PrintCollate](#printcollate).

## <a name="cprintdialoggetdrivername"></a><a name="getdrivername"></a>CPrintDialog::GetDriverName

Récupère le nom du pilote d’imprimante actuellement sélectionné.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valeur de retour

Un `CString` spécifier le nom du conducteur défini par le système.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer le nom du pilote de périphérique d’imprimante défini par le système. Utilisez un pointeur `CString` à `GetDriverName` l’objet `lpszDriverName` retourné par comme la valeur d’un appel à [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPrintDialog:GetDeviceName](#getdevicename).

## <a name="cprintdialoggetfrompage"></a><a name="getfrompage"></a>CPrintDialog::GetDePage

Récupère la page de départ de la plage d’impression.

```
int GetFromPage() const;
```

### <a name="return-value"></a>Valeur de retour

Le numéro de la page de départ dans la gamme de pages à imprimer.

### <a name="remarks"></a>Notes

Appelez cette fonction `DoModal` après avoir appelé pour récupérer le numéro de page de départ dans la gamme de pages à imprimer.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPrintDialog:m_pd](#m_pd).

## <a name="cprintdialoggetportname"></a><a name="getportname"></a>CPrintDialog::GetPortName

Récupère le nom du port d’imprimantes actuellement sélectionné.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom du port d’imprimante actuellement sélectionné.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer le nom du port d’imprimante actuellement sélectionné.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPrintDialog:GetDeviceName](#getdevicename).

## <a name="cprintdialoggetprinterdc"></a><a name="getprinterdc"></a>CPrintDialog::GetPrinterDC

Récupère une poignée dans le contexte de l’appareil d’imprimante.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Valeur de retour

Une poignée au contexte de l’appareil d’imprimante en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Si le paramètre *bPrintSetupOnly* du `CPrintDialog` constructeur était FALSE (indiquant que `GetPrinterDC` la boîte de dialogue d’impression est affichée), puis renvoie une poignée au contexte de l’appareil d’imprimante. Vous devez appeler la fonction [Windows DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) pour supprimer le contexte de l’appareil lorsque vous avez terminé de l’utiliser.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

## <a name="cprintdialoggettopage"></a><a name="gettopage"></a>CPrintDialog::GetToPage

Récupère la page de fin de la plage d’impression.

```
int GetToPage() const;
```

### <a name="return-value"></a>Valeur de retour

Le numéro de la page de fin dans la gamme de pages à imprimer.

### <a name="remarks"></a>Notes

Appelez cette fonction `DoModal` après avoir appelé pour récupérer le numéro de la page de fin dans la gamme de pages à imprimer.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPrintDialog:m_pd](#m_pd).

## <a name="cprintdialogm_pd"></a><a name="m_pd"></a>CPrintDialog::m_pd

Une structure dont les membres stockent les caractéristiques de l’objet de dialogue.

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>Notes

Après la `CPrintDialog` construction d’un `m_pd` objet, vous pouvez utiliser pour définir divers aspects de la boîte de dialogue avant d’appeler la fonction membre [DoModal.](#domodal) Pour plus d’informations sur la `m_pd` structure, voir [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) dans le SDK Windows.

Si vous `m_pd` modifiez directement le membre des données, vous remplacerez tout comportement par défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

## <a name="cprintdialogprintall"></a><a name="printall"></a>CPrintDialog::PrintAll

Détermine s’il y a toutes les pages du document.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si toutes les pages du document doivent être imprimées; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction `DoModal` après avoir appelé pour déterminer s’il y a eu pour imprimer toutes les pages du document.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPrintDialog:m_pd](#m_pd).

## <a name="cprintdialogprintcollate"></a><a name="printcollate"></a>CPrintDialog::PrintCollate

Détermine si des copies rassemblées sont demandées.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’utilisateur sélectionne la case à cocher collate dans la boîte de dialogue; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction `DoModal` après avoir appelé pour déterminer si l’imprimante doit rassembler toutes les copies imprimées du document.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

## <a name="cprintdialogprintrange"></a><a name="printrange"></a>CPrintDialog::PrintRange

Détermine s’il ne faut imprimer qu’une gamme spécifiée de pages.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si seulement une gamme de pages dans le document doivent être imprimées; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction `DoModal` après avoir appelé pour déterminer s’il ne faut imprimer qu’une gamme de pages dans le document.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPrintDialog:m_pd](#m_pd).

## <a name="cprintdialogprintselection"></a><a name="printselection"></a>CPrintDialog::PrintSelection

Détermine s’il ne faut imprimer que les articles actuellement sélectionnés.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si seulement les articles sélectionnés doivent être imprimés; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction `DoModal` après avoir appelé pour déterminer s’il ne faut imprimer que les éléments actuellement sélectionnés.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPrintDialog:m_pd](#m_pd).

## <a name="see-also"></a>Voir aussi

[MFC Échantillon DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[Classe CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo, structure](../../mfc/reference/cprintinfo-structure.md)
