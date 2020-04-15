---
title: Classe CPrintDialogEx
ms.date: 11/04/2016
f1_keywords:
- CPrintDialogEx
- AFXDLGS/CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CreatePrinterDC
- AFXDLGS/CPrintDialogEx::DoModal
- AFXDLGS/CPrintDialogEx::GetCopies
- AFXDLGS/CPrintDialogEx::GetDefaults
- AFXDLGS/CPrintDialogEx::GetDeviceName
- AFXDLGS/CPrintDialogEx::GetDevMode
- AFXDLGS/CPrintDialogEx::GetDriverName
- AFXDLGS/CPrintDialogEx::GetPortName
- AFXDLGS/CPrintDialogEx::GetPrinterDC
- AFXDLGS/CPrintDialogEx::PrintAll
- AFXDLGS/CPrintDialogEx::PrintCollate
- AFXDLGS/CPrintDialogEx::PrintCurrentPage
- AFXDLGS/CPrintDialogEx::PrintRange
- AFXDLGS/CPrintDialogEx::PrintSelection
- AFXDLGS/CPrintDialogEx::m_pdex
helpviewer_keywords:
- CPrintDialogEx [MFC], CPrintDialogEx
- CPrintDialogEx [MFC], CreatePrinterDC
- CPrintDialogEx [MFC], DoModal
- CPrintDialogEx [MFC], GetCopies
- CPrintDialogEx [MFC], GetDefaults
- CPrintDialogEx [MFC], GetDeviceName
- CPrintDialogEx [MFC], GetDevMode
- CPrintDialogEx [MFC], GetDriverName
- CPrintDialogEx [MFC], GetPortName
- CPrintDialogEx [MFC], GetPrinterDC
- CPrintDialogEx [MFC], PrintAll
- CPrintDialogEx [MFC], PrintCollate
- CPrintDialogEx [MFC], PrintCurrentPage
- CPrintDialogEx [MFC], PrintRange
- CPrintDialogEx [MFC], PrintSelection
- CPrintDialogEx [MFC], m_pdex
ms.assetid: 1d506703-ee1c-44cc-b4ce-4e778fec26b8
ms.openlocfilehash: 52e992cf021a592198daeddf0a4321fcea487f72
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364039"
---
# <a name="cprintdialogex-class"></a>Classe CPrintDialogEx

Encapsule les services fournis par la feuille de propriété Windows Print.

## <a name="syntax"></a>Syntaxe

```
class CPrintDialogEx : public CCommonDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPrintDialogEx::CPrintDialogEx](#cprintdialogex)|Construit un objet `CPrintDialogEx`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPrintDialogEx::CréerPrinterDC](#createprinterdc)|Crée un contexte d’appareil d’imprimante sans afficher la boîte de dialogue d’impression.|
|[CPrintDialogEx::DoModal](#domodal)|Affiche la boîte de dialogue et permet à l’utilisateur de faire des sélections.|
|[CPrintDialogEx::GetCopies](#getcopies)|Récupère le nombre d’exemplaires demandés.|
|[CPrintDialogEx::GetDefaults](#getdefaults)|Récupère les défauts de l’appareil sans afficher une boîte de dialogue.|
|[CPrintDialogEx:GetDeviceName](#getdevicename)|Récupère le nom de l’appareil d’imprimante actuellement sélectionné.|
|[CPrintDialogEx::GetDevMode](#getdevmode)|Récupère la `DEVMODE` structure.|
|[CPrintDialogEx::GetDriverName](#getdrivername)|Récupère le nom du pilote de périphérique d’imprimante défini par le système.|
|[CPrintDialogEx::GetPortName](#getportname)|Récupère le nom du port d’imprimantes actuellement sélectionné.|
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|Récupère une poignée dans le contexte de l’appareil d’imprimante.|
|[CPrintDialogEx::PrintAll](#printall)|Détermine s’il y a toutes les pages du document.|
|[CPrintDialogEx::PrintCollate](#printcollate)|Détermine si des copies rassemblées sont demandées.|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|Détermine s’il convient d’imprimer la page actuelle du document.|
|[CPrintDialogEx::PrintRange](#printrange)|Détermine s’il ne faut imprimer qu’une gamme spécifiée de pages.|
|[CPrintDialogEx::PrintSelection](#printselection)|Détermine s’il ne faut imprimer que les articles actuellement sélectionnés.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPrintDialogEx:m_pdex](#m_pdex)|Une structure utilisée pour `CPrintDialogEx` personnaliser un objet.|

## <a name="remarks"></a>Notes

Vous pouvez compter sur le cadre pour gérer de nombreux aspects du processus d’impression pour votre application. Pour plus d’informations sur l’utilisation du cadre pour gérer les tâches d’impression, voir l’article [Impression](../../mfc/printing.md).

Si vous voulez que votre application gère l’impression sans `CPrintDialogEx` la participation du cadre, vous pouvez utiliser la classe « `CPrintDialogEx` telle qu’elle est » avec le constructeur fourni, ou vous pouvez tirer votre propre classe de dialogue et écrire un constructeur en fonction de vos besoins. Dans les deux cas, ces boîtes de dialogue se comporteront comme `CCommonDialog`des boîtes de dialogue MFC standard parce qu’elles sont dérivées de la classe.

Pour utiliser `CPrintDialogEx` un objet, créez `CPrintDialogEx` d’abord l’objet à l’aide du constructeur. Une fois que la boîte de dialogue a été construite, vous pouvez définir ou modifier toutes les valeurs de la structure [m_pdex](#m_pdex) pour initialiser les valeurs des commandes de la boîte de dialogue. La `m_pdex` structure est de type [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw). Pour plus d’informations sur cette structure, voir le SDK Windows.

Si vous ne fournissez pas `m_pdex` vos `hDevMode` `hDevNames` propres poignées pour les `GlobalFree` membres et les membres, assurez-vous d’appeler la fonction Windows pour ces poignées lorsque vous avez terminé avec la boîte de dialogue.

Après avoir paralysé les `DoModal` commandes de la boîte de dialogue, appelez la fonction membre pour afficher la boîte de dialogue et permettre à l’utilisateur de sélectionner les options d’impression. Lors `DoModal` de votre retour, vous pouvez déterminer si l’utilisateur a sélectionné le bouton OK, Apply ou Annuler.

Si l’utilisateur a appuyé `CPrintDialogEx`sur OK, vous pouvez utiliser les fonctions des membres pour récupérer l’entrée d’informations par l’utilisateur.

La `CPrintDialogEx::GetDefaults` fonction membre est utile pour récupérer les défauts d’imprimante actuels sans afficher une boîte de dialogue. Cette méthode ne nécessite aucune interaction utilisateur.

Vous pouvez utiliser `CommDlgExtendedError` la fonction Windows pour déterminer si une erreur s’est produite lors de l’initialisation de la boîte de dialogue et pour en savoir plus sur l’erreur. Pour plus d’informations sur cette fonction, voir le SDK Windows.

Pour plus d’informations sur l’utilisation `CPrintDialogEx`, voir Classes de dialogue [commun](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`IObjectWithSite`

`IPrintDialogCallback`

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialogEx`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdlgs.h

## <a name="cprintdialogexcprintdialogex"></a><a name="cprintdialogex"></a>CPrintDialogEx::CPrintDialogEx

Construit une feuille de propriété Windows Print.

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Un ou plusieurs drapeaux que vous pouvez utiliser pour personnaliser les paramètres de la boîte de dialogue, combinés à l’aide de l’opérateur BITwise OU. Par exemple, le drapeau PD_ALLPAGES définit la plage d’impression par défaut à toutes les pages du document. Consultez la structure [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) dans le Windows SDK pour plus d’informations sur ces drapeaux.

*pParentWnd*<br/>
Un pointeur à la fenêtre parent ou propriétaire de la boîte de dialogue.

### <a name="remarks"></a>Notes

Cette fonction de membre ne construit que l’objet. Utilisez `DoModal` la fonction du membre pour afficher la boîte de dialogue.

## <a name="cprintdialogexcreateprinterdc"></a><a name="createprinterdc"></a>CPrintDialogEx::CréerPrinterDC

Crée un contexte d’imprimante (DC) à partir des structures [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) et [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valeur de retour

Gérer le contexte nouvel et nouvellement créé de l’appareil d’imprimante.

### <a name="remarks"></a>Notes

Le DC retourné est `hDC` également stocké dans le membre de [m_pdex](#m_pdex).

Ce DC est supposé être l’imprimante actuelle DC, et tout autre DC imprimante précédemment obtenu doit être supprimé. Cette fonction peut être appelée, et le DC résultant utilisé, sans jamais afficher la boîte de dialogue d’impression.

## <a name="cprintdialogexdomodal"></a><a name="domodal"></a>CPrintDialogEx::DoModal

Appelez cette fonction pour afficher la feuille de propriété Windows Print et permettre à l’utilisateur de sélectionner diverses options d’impression telles que le nombre d’exemplaires, la plage de pages et la collecte de copies.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

La valeur de rendement INT_PTR est en fait un HRESULT. Consultez la section Valeurs de retour dans [PrintDlgEx](/previous-versions/windows/desktop/legacy/ms646942\(v=vs.85\)) dans windows SDK.

### <a name="remarks"></a>Notes

Si vous souhaitez paralyser les différentes options `m_pdex` de dialogue d’impression `DoModal`en définissant les membres de la structure, vous devriez le faire avant d’appeler, mais après la construction de l’objet de dialogue.

Après `DoModal`avoir appelé, vous pouvez appeler d’autres fonctions de membre pour récupérer les paramètres ou l’entrée d’informations par l’utilisateur dans la boîte de dialogue.

Si le drapeau PD_RETURNDC est `DoModal`utilisé lors de l’appel `hDC` , une imprimante DC sera retourné dans le membre de [m_pdex](#m_pdex). Ce DC doit être libéré avec un appel `CPrintDialogEx`à [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) par l’appelant de .

## <a name="cprintdialogexgetcopies"></a><a name="getcopies"></a>CPrintDialogEx::GetCopies

Appelez cette fonction `DoModal` après avoir appelé pour récupérer le nombre de copies demandées.

```
int GetCopies() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’exemplaires demandés.

## <a name="cprintdialogexgetdefaults"></a><a name="getdefaults"></a>CPrintDialogEx::GetDefaults

Appelez cette fonction pour récupérer les défauts de l’imprimante par défaut sans afficher une boîte de dialogue.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Valeur de retour

VRAI en cas de succès, sinon FALSE.

### <a name="remarks"></a>Notes

Crée un contexte d’imprimante (DC) à partir des structures [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) et [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

`GetDefaults`n’affiche pas la feuille de propriété Imprimer. Au lieu de `hDevNames` `hDevMode` cela, il définit les membres et les membres de [m_pdex](#m_pdex) pour les poignées aux structures [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) et [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) qui sont parasélisées pour l’imprimante par défaut du système. Les `hDevNames` `hDevMode` deux et doivent `GetDefaults` être NULL, ou échoue.

Si le drapeau PD_RETURNDC est défini, cette `hDevNames` fonction `hDevMode` non `m_pdex.hDevNames` seulement `m_pdex.hDevMode`retournera et (situé dans et ) `m_pdex.hDC`à l’appelant, mais retournera également une imprimante DC dans . Il est de la responsabilité de l’appelant de supprimer l’imprimante DC et d’appeler `CPrintDialogEx` la fonction Windows [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) sur les poignées lorsque vous avez terminé avec l’objet.

## <a name="cprintdialogexgetdevicename"></a><a name="getdevicename"></a>CPrintDialogEx:GetDeviceName

Appelez cette fonction après avoir appelé [DoModal](#domodal) pour récupérer le nom de l’imprimante actuellement sélectionnée, ou après avoir appelé [GetDefaults](#getdefaults) pour récupérer le nom de l’imprimante par défaut.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom de l’imprimante actuellement sélectionnée.

### <a name="remarks"></a>Notes

Utilisez un pointeur `CString` à `GetDeviceName` l’objet `lpszDeviceName` retourné par comme la valeur d’un appel à [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

## <a name="cprintdialogexgetdevmode"></a><a name="getdevmode"></a>CPrintDialogEx::GetDevMode

Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer des informations sur l’appareil d’impression.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valeur de retour

La structure de données [DEVMODE,](/windows/win32/api/wingdi/ns-wingdi-devmodea) qui contient des informations sur l’initialisation de l’appareil et l’environnement d’un pilote d’impression. Vous devez déverrouiller la mémoire prise par cette structure avec la fonction Windows [GlobalUnlock,](/windows/win32/api/winbase/nf-winbase-globalunlock) qui est décrite dans le SDK Windows.

## <a name="cprintdialogexgetdrivername"></a><a name="getdrivername"></a>CPrintDialogEx::GetDriverName

Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer le nom du pilote de périphérique d’imprimante défini par le système.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valeur de retour

Un `CString` spécifier le nom du conducteur défini par le système.

### <a name="remarks"></a>Notes

Utilisez un pointeur `CString` à `GetDriverName` l’objet retourné par comme la valeur de *lpszDriverName* dans un appel à [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

## <a name="cprintdialogexgetportname"></a><a name="getportname"></a>CPrintDialogEx::GetPortName

Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer le nom du port d’imprimante actuellement sélectionné.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom du port d’imprimante actuellement sélectionné.

## <a name="cprintdialogexgetprinterdc"></a><a name="getprinterdc"></a>CPrintDialogEx::GetPrinterDC

Retourne une poignée dans le contexte de l’appareil d’imprimante.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Valeur de retour

Une poignée au contexte de l’appareil d’imprimante.

### <a name="remarks"></a>Notes

Vous devez appeler la fonction [Windows DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) pour supprimer le contexte de l’appareil lorsque vous avez terminé de l’utiliser.

## <a name="cprintdialogexm_pdex"></a><a name="m_pdex"></a>CPrintDialogEx:m_pdex

Une structure PRINTDLGEX dont les membres stockent les caractéristiques de l’objet de dialogue.

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>Notes

Après la `CPrintDialogEx` construction d’un `m_pdex` objet, vous pouvez utiliser pour définir divers aspects de la boîte de dialogue avant d’appeler la fonction membre [DoModal.](#domodal) Pour plus d’informations sur la `m_pdex` structure, voir [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) dans le SDK Windows.

Si vous `m_pdex` modifiez directement le membre des données, vous remplacerez tout comportement par défaut.

## <a name="cprintdialogexprintall"></a><a name="printall"></a>CPrintDialogEx::PrintAll

Appelez cette fonction `DoModal` après avoir appelé pour déterminer s’il y a eu pour imprimer toutes les pages du document.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si toutes les pages du document doivent être imprimées; autrement FALSE.

## <a name="cprintdialogexprintcollate"></a><a name="printcollate"></a>CPrintDialogEx::PrintCollate

Appelez cette fonction `DoModal` après avoir appelé pour déterminer si l’imprimante doit rassembler toutes les copies imprimées du document.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si l’utilisateur sélectionne la case à cocher collate dans la boîte de dialogue; autrement FALSE.

## <a name="cprintdialogexprintcurrentpage"></a><a name="printcurrentpage"></a>CPrintDialogEx::PrintCurrentPage

Appelez cette fonction `DoModal` après avoir appelé pour déterminer s’il y a à imprimer la page actuelle dans le document.

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si **la page d’impression actuelle** est sélectionnée dans le dialogue d’impression ; autrement FALSE.

## <a name="cprintdialogexprintrange"></a><a name="printrange"></a>CPrintDialogEx::PrintRange

Appelez cette fonction `DoModal` après avoir appelé pour déterminer s’il ne faut imprimer qu’une gamme de pages dans le document.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si seulement une gamme de pages dans le document doivent être imprimées; autrement FALSE.

### <a name="remarks"></a>Notes

Les plages de pages spécifiées peuvent être `nMaxPageRanges`déterminées `lpPageRanges` à partir de [m_pdex](#m_pdex) (voir `nPageRanges`, et dans la structure [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) dans le SDK Windows).

## <a name="cprintdialogexprintselection"></a><a name="printselection"></a>CPrintDialogEx::PrintSelection

Appelez cette fonction `DoModal` après avoir appelé pour déterminer s’il ne faut imprimer que les éléments actuellement sélectionnés.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si seulement les articles sélectionnés doivent être imprimés; autrement FALSE.

## <a name="see-also"></a>Voir aussi

[Classe CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo, structure](../../mfc/reference/cprintinfo-structure.md)
