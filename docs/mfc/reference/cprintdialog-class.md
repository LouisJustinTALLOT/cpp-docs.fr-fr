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
ms.openlocfilehash: 1f4a4dbec9a1c79ac1e0cec925156ae7db4c293e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502898"
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
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Crée un contexte de périphérique d’impression sans afficher la boîte de dialogue Imprimer.|
|[CPrintDialog::DoModal](#domodal)|Affiche la boîte de dialogue et permet à l’utilisateur d’effectuer une sélection.|
|[CPrintDialog::GetCopies](#getcopies)|Récupère le nombre de copies demandées.|
|[CPrintDialog::GetDefaults](#getdefaults)|Récupère les valeurs par défaut des appareils sans afficher de boîte de dialogue.|
|[CPrintDialog::GetDeviceName](#getdevicename)|Récupère le nom du périphérique d’impression actuellement sélectionné.|
|[CPrintDialog::GetDevMode](#getdevmode)|Récupère la `DEVMODE` structure.|
|[CPrintDialog::GetDriverName](#getdrivername)|Récupère le nom du pilote d’imprimante actuellement sélectionné.|
|[CPrintDialog::GetFromPage](#getfrompage)|Récupère la page de démarrage de la plage d’impression.|
|[CPrintDialog::GetPortName](#getportname)|Récupère le nom du port d’imprimante actuellement sélectionné.|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Récupère un handle vers le contexte de périphérique d’impression.|
|[CPrintDialog::GetToPage](#gettopage)|Récupère la page de fin de la plage d’impression.|
|[CPrintDialog::PrintAll](#printall)|Détermine si toutes les pages du document doivent être imprimées.|
|[CPrintDialog::PrintCollate](#printcollate)|Détermine si les copies assemblées sont demandées.|
|[CPrintDialog::PrintRange](#printrange)|Détermine s’il faut imprimer uniquement une plage de pages spécifiée.|
|[CPrintDialog::PrintSelection](#printselection)|Détermine s’il faut imprimer uniquement les éléments actuellement sélectionnés.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPrintDialog::m_pd](#m_pd)|Structure utilisée pour personnaliser un `CPrintDialog` objet.|

## <a name="remarks"></a>Notes

Les boîtes de dialogue d’impression courantes offrent un moyen simple d’implémenter des boîtes de dialogue d’impression et d’impression de manière cohérente avec les normes Windows.

> [!NOTE]
>  La `CPrintDialogEx` classe encapsule les services fournis par la feuille de propriétés d’impression Windows. Pour plus d’informations, consultez la vue d’ensemble de [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) .

`CPrintDialog`la fonctionnalité de est remplacée par celle de [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), qui est conçue pour fournir une boîte de dialogue commune pour la configuration de l’impression et la mise en page.

Vous pouvez vous appuyer sur l’infrastructure pour gérer de nombreux aspects du processus d’impression pour votre application. Dans ce cas, l’infrastructure affiche automatiquement la boîte de dialogue commune Windows pour l’impression. Vous pouvez également faire en sorte que le handle de l’infrastructure soit imprimé pour votre application, tout en remplaçant la boîte de dialogue d’impression courante par votre propre boîte de dialogue Imprimer. Pour plus d’informations sur l’utilisation de l’infrastructure pour gérer les tâches d’impression, consultez l’article [impression](../../mfc/printing.md).

Si vous souhaitez que votre application gère l’impression sans l’implication de l’infrastructure, vous pouvez `CPrintDialog` utiliser la classe «telle quelle» avec le constructeur fourni, ou vous pouvez dériver votre propre `CPrintDialog` classe de boîte de dialogue à partir de et écrire un constructeur pour répondre à vos besoins. Dans les deux cas, ces boîtes de dialogue se comportent comme des boîtes de dialogue MFC standard `CCommonDialog`, car elles sont dérivées de la classe.

Pour utiliser un `CPrintDialog` objet, commencez par créer l’objet à `CPrintDialog` l’aide du constructeur. Une fois la boîte de dialogue construite, vous pouvez définir ou modifier les valeurs de la structure [m_pd](#m_pd) pour initialiser les valeurs des contrôles de la boîte de dialogue. La `m_pd` structure est de type [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-pdw). Pour plus d’informations sur cette structure, consultez la SDK Windows.

Si vous `m_pd` ne fournissez pas vos propres handles dans pour `hDevNames` les `hDevMode` membres et, veillez à appeler la `GlobalFree` fonction Windows pour ces handles lorsque vous avez fini d’utiliser la boîte de dialogue. Lors de l’utilisation de l’implémentation d’impression de `CWinApp::OnFilePrintSetup`l’infrastructure fournie par, vous n’avez pas à libérer ces handles. Les handles sont gérés `CWinApp` par et sont libérés `CWinApp`dans le destructeur de. Il est uniquement nécessaire de libérer ces handles quand `CPrintDialog` vous utilisez le autonome.

Après l’initialisation des contrôles de boîte de dialogue, `DoModal` appelez la fonction membre pour afficher la boîte de dialogue et permettre à l’utilisateur de sélectionner des options d’impression. `DoModal`retourne une valeur indiquant si l’utilisateur a sélectionné le bouton OK (IDOK) ou CANCEL (IDCANCEL).

Si `DoModal` retourne IDOK, vous pouvez utiliser l’une `CPrintDialog`des fonctions membres de pour récupérer les informations entrées par l’utilisateur.

La `CPrintDialog::GetDefaults` fonction membre est utile pour récupérer les valeurs par défaut de l’imprimante actuelle sans afficher de boîte de dialogue. Cette fonction membre ne requiert aucune intervention de l’utilisateur.

Vous pouvez utiliser la fonction `CommDlgExtendedError` Windows pour déterminer si une erreur s’est produite lors de l’initialisation de la boîte de dialogue et pour en savoir plus sur l’erreur. Pour plus d’informations sur cette fonction, consultez la SDK Windows.

`CPrintDialog`s’appuie sur le COMMDLG. Fichier DLL fourni avec Windows versions 3,1 et ultérieures.

Pour personnaliser la boîte de dialogue, dérivez `CPrintDialog`une classe de, fournissez un modèle de boîte de dialogue personnalisé et ajoutez une table des messages pour traiter les messages de notification des contrôles étendus. Tous les messages non traités doivent être transmis à la classe de base. La personnalisation de la fonction de raccordement n’est pas obligatoire.

Pour traiter le même message différemment selon qu’il s’agit d’une boîte de dialogue d’impression ou d’impression, vous devez dériver une classe pour chaque boîte de dialogue. Vous devez également remplacer la fonction Windows `AttachOnSetup` , qui gère la création d’une nouvelle boîte de dialogue lorsque le bouton de configuration de l’impression est sélectionné dans une boîte de dialogue Imprimer.

Pour plus d’informations sur `CPrintDialog`l’utilisation de, consultez [classes de boîtes de dialogue communes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>Configuration requise

**En-tête:** afxdlgs. h

##  <a name="cprintdialog"></a>  CPrintDialog::CPrintDialog

Construit un objet de boîte de dialogue d’impression ou d’impression Windows.

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*bPrintSetupOnly*<br/>
Spécifie si la boîte de dialogue d’impression Windows standard ou la boîte de dialogue de configuration de l’impression s’affiche. Affectez la valeur TRUE à ce paramètre pour afficher la boîte de dialogue Configuration de l’impression Windows standard. Affectez-lui la valeur FALSe pour afficher la boîte de dialogue Imprimer de Windows. Si *bPrintSetupOnly* a la valeur false, une case d’option de configuration de l’impression s’affiche toujours dans la boîte de dialogue Imprimer.

*dwFlags*<br/>
Un ou plusieurs indicateurs que vous pouvez utiliser pour personnaliser les paramètres de la boîte de dialogue, combinés à l’aide de l’opérateur de bits or. Par exemple, l’indicateur PD_ALLPAGES définit la plage d’impression par défaut sur toutes les pages du document. Pour plus d’informations sur ces indicateurs, consultez la structure [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-pdw) dans le SDK Windows.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente ou propriétaire de la boîte de dialogue.

### <a name="remarks"></a>Notes

Cette fonction membre construit uniquement l’objet. Utilisez la `DoModal` fonction membre pour afficher la boîte de dialogue.

Notez que lorsque vous appelez le constructeur avec *bPrintSetupOnly* défini sur false, l’indicateur PD_RETURNDC est utilisé automatiquement. Après l' `DoModal`appel `GetDefaults`de, `GetPrinterDC`ou, un contrôleur de périphérique d’imprimante `m_pd.hDC`est retourné dans. Ce contrôleur de périphérique doit être libéré à l’aide d’un appel à [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) par l’appelant de `CPrintDialog`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPrintDialog::CreatePrinterDC

Crée un contexte de périphérique (DC) d’imprimante à partir des structures [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) et [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) .

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valeur de retour

Handle vers le contexte de périphérique d’impression nouvellement créé.

### <a name="remarks"></a>Notes

Ce contrôleur de périphérique est supposé être le contrôleur de l’imprimante en cours et tous les autres contrôleurs d’imprimante obtenus précédemment doivent être supprimés par l’utilisateur. Cette fonction peut être appelée, et le contrôleur de périphérique obtenu utilisé, sans jamais afficher la boîte de dialogue Imprimer.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

##  <a name="domodal"></a>  CPrintDialog::DoModal

Affiche la boîte de dialogue d’impression commune de Windows et permet à l’utilisateur de sélectionner différentes options d’impression, telles que le nombre de copies, la plage de pages, et si les copies doivent être assemblées.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

IDOK ou IDCANCEL. Si IDCANCEL est retourné, appelez la fonction [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows pour déterminer si une erreur s’est produite.

IDOK et IDCANCEL sont des constantes qui indiquent si l’utilisateur a sélectionné le bouton OK ou annuler.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les différentes options de la boîte de dialogue d’impression en `m_pd` définissant les membres de la structure, `DoModal`vous devez effectuer cette opération avant d’appeler, mais après la construction de l’objet de boîte de dialogue.

Après avoir `DoModal`appelé, vous pouvez appeler d’autres fonctions membres pour récupérer les paramètres ou les informations entrées par l’utilisateur dans la boîte de dialogue.

Notez que lorsque vous appelez le constructeur avec *bPrintSetupOnly* défini sur false, l’indicateur PD_RETURNDC est utilisé automatiquement. Après l' `DoModal`appel `GetDefaults`de, `GetPrinterDC`ou, un contrôleur de périphérique d’imprimante `m_pd.hDC`est retourné dans. Ce contrôleur de périphérique doit être libéré à l’aide d’un appel à [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) par l’appelant de `CPrintDialog`.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPrintDialog:: CreatePrinterDC](#createprinterdc).

##  <a name="getcopies"></a>  CPrintDialog::GetCopies

Récupère le nombre de copies demandées.

```
int GetCopies() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de copies demandées.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir `DoModal` appelé pour récupérer le nombre de copies demandées.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CPrintDialog::P rintcollate](#printcollate).

##  <a name="getdefaults"></a>  CPrintDialog::GetDefaults

Récupère les valeurs par défaut de l’imprimante par défaut sans afficher de boîte de dialogue.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi; Sinon, 0.

### <a name="remarks"></a>Notes

Les valeurs récupérées sont placées `m_pd` dans la structure.

Dans certains cas, un appel à cette fonction appellera le [constructeur](#cprintdialog) pour `CPrintDialog` avec *bPrintSetupOnly* défini sur false. Dans ce cas, un DC d’imprimante `hDevNames` et `hDevMode` et (deux Handles situés `m_pd` dans le membre de données) sont alloués automatiquement.

Si le constructeur pour `CPrintDialog` a été appelé avec *bPrintSetupOnly* ayant la valeur false, cette fonction ne `hDevNames` retourne `hDevMode` pas et `m_pd.hDevNames` ne `m_pd.hDevMode`se trouve pas dans et) à l’appelant, mais elle retourne également un contrôleur de périphérique d’imprimante dans `m_pd.hDC`. Il incombe à l’appelant de supprimer le contrôleur de l’imprimante et d’appeler la fonction [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) de Windows sur les handles lorsque vous `CPrintDialog` avez terminé avec l’objet.

### <a name="example"></a>Exemple

Ce fragment de code obtient le contexte de périphérique de l’imprimante par défaut et signale à l’utilisateur la résolution en points par pouce. (Cet attribut des fonctionnalités de l’imprimante est souvent appelé PPP.)

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

##  <a name="getdevicename"></a>  CPrintDialog::GetDeviceName

Récupère le nom du périphérique d’impression actuellement sélectionné.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valeur de retour

Nom de l’imprimante actuellement sélectionnée.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir appelé [DoModal](#domodal) pour récupérer le nom de l’imprimante actuellement sélectionnée, ou après l’appel de [GetDefaults](#getdefaults) pour récupérer les valeurs par défaut de l’imprimante par défaut. Utilisez un pointeur vers l' `CString` objet retourné par `GetDeviceName` comme valeur de `lpszDeviceName` dans un appel à [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Exemple

Ce fragment de code montre le nom de l’imprimante par défaut de l’utilisateur et le port auquel il est connecté, ainsi que le nom du spouleur utilisé par l’imprimante. Le code peut afficher une boîte de message indiquant «votre imprimante par défaut est HP LaserJet IIIP sur \\\server\share à l’aide de winspool.», par exemple.

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

##  <a name="getdevmode"></a>  CPrintDialog::GetDevMode

Récupère la `DEVMODE` structure.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valeur de retour

Structure de données [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) , qui contient des informations sur l’initialisation de l’appareil et l’environnement d’un pilote d’impression. Vous devez déverrouiller la mémoire prise par cette structure à l’aide de la fonction [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock) de Windows, qui est décrite dans la SDK Windows.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer des informations sur le périphérique d’impression.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CPrintDialog::P rintcollate](#printcollate).

##  <a name="getdrivername"></a>  CPrintDialog::GetDriverName

Récupère le nom du pilote d’imprimante actuellement sélectionné.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valeur de retour

`CString` Spécifiant le nom du pilote défini par le système.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer le nom du pilote de périphérique d’imprimante défini par le système. Utilisez un pointeur vers l' `CString` objet retourné par `GetDriverName` comme valeur de `lpszDriverName` dans un appel à [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPrintDialog:: GetDeviceName](#getdevicename).

##  <a name="getfrompage"></a>  CPrintDialog::GetFromPage

Récupère la page de démarrage de la plage d’impression.

```
int GetFromPage() const;
```

### <a name="return-value"></a>Valeur de retour

Numéro de la page de début dans la plage de pages à imprimer.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir `DoModal` appelé pour récupérer le numéro de la page de début dans la plage de pages à imprimer.

### <a name="example"></a>Exemples

  Consultez l’exemple de [CPrintDialog:: m_pd](#m_pd).

##  <a name="getportname"></a>  CPrintDialog::GetPortName

Récupère le nom du port d’imprimante actuellement sélectionné.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valeur de retour

Nom du port d’imprimante actuellement sélectionné.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer le nom du port d’imprimante actuellement sélectionné.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPrintDialog:: GetDeviceName](#getdevicename).

##  <a name="getprinterdc"></a>  CPrintDialog::GetPrinterDC

Récupère un handle vers le contexte de périphérique d’impression.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Valeur de retour

Handle vers le contexte de périphérique d’impression en cas de réussite; Sinon, NULL.

### <a name="remarks"></a>Notes

Si le paramètre *bPrintSetupOnly* du `CPrintDialog` constructeur était false (ce qui indique que la boîte de dialogue Imprimer est `GetPrinterDC` affichée), retourne un handle vers le contexte de périphérique d’impression. Vous devez appeler la fonction [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) de Windows pour supprimer le contexte de périphérique une fois que vous avez fini de l’utiliser.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

##  <a name="gettopage"></a>  CPrintDialog::GetToPage

Récupère la page de fin de la plage d’impression.

```
int GetToPage() const;
```

### <a name="return-value"></a>Valeur de retour

Numéro de la page de fin dans la plage de pages à imprimer.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir `DoModal` appelé pour extraire le numéro de la page de fin dans la plage de pages à imprimer.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPrintDialog:: m_pd](#m_pd).

##  <a name="m_pd"></a>  CPrintDialog::m_pd

Structure dont les membres stockent les caractéristiques de l’objet Dialog.

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>Notes

Après avoir construit un `CPrintDialog` objet, vous pouvez utiliser `m_pd` pour définir différents aspects de la boîte de dialogue avant d’appeler la fonction membre [DoModal](#domodal) . Pour plus d’informations sur `m_pd` la structure, consultez [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-pdw) dans le SDK Windows.

Si vous modifiez directement `m_pd` le membre de données, vous remplacerez tout comportement par défaut.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

##  <a name="printall"></a>  CPrintDialog::PrintAll

Détermine si toutes les pages du document doivent être imprimées.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si toutes les pages du document doivent être imprimées; Sinon, 0.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir `DoModal` appelé pour déterminer si toutes les pages du document doivent être imprimées.

### <a name="example"></a>Exemples

  Consultez l’exemple de [CPrintDialog:: m_pd](#m_pd).

##  <a name="printcollate"></a>  CPrintDialog::PrintCollate

Détermine si les copies assemblées sont demandées.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur sélectionne la case à cocher assembler dans la boîte de dialogue; Sinon, 0.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir `DoModal` appelé pour déterminer si l’imprimante doit reclasser toutes les copies imprimées du document.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

##  <a name="printrange"></a>  CPrintDialog::PrintRange

Détermine s’il faut imprimer uniquement une plage de pages spécifiée.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si seule une plage de pages dans le document doit être imprimée. Sinon, 0.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir `DoModal` appelé pour déterminer s’il faut imprimer uniquement une plage de pages dans le document.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPrintDialog:: m_pd](#m_pd).

##  <a name="printselection"></a>  CPrintDialog::PrintSelection

Détermine s’il faut imprimer uniquement les éléments actuellement sélectionnés.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si seuls les éléments sélectionnés doivent être imprimés. Sinon, 0.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir `DoModal` appelé pour déterminer s’il faut imprimer uniquement les éléments actuellement sélectionnés.

### <a name="example"></a>Exemples

  Consultez l’exemple de [CPrintDialog:: m_pd](#m_pd).

## <a name="see-also"></a>Voir aussi

[Exemple MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog, classe](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo, structure](../../mfc/reference/cprintinfo-structure.md)
