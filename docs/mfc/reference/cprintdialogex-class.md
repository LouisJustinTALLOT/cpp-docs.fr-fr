---
title: CPrintDialogEx, classe
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
ms.openlocfilehash: ebef892e174525c0b907818c02b7d34b1b41f850
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916896"
---
# <a name="cprintdialogex-class"></a>CPrintDialogEx, classe

Encapsule les services fournis par la feuille de propriétés d’impression Windows.

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
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|Crée un contexte de périphérique d’impression sans afficher la boîte de dialogue Imprimer.|
|[CPrintDialogEx::DoModal](#domodal)|Affiche la boîte de dialogue et permet à l’utilisateur d’effectuer des sélections.|
|[CPrintDialogEx::GetCopies](#getcopies)|Récupère le nombre de copies demandées.|
|[CPrintDialogEx::GetDefaults](#getdefaults)|Récupère les valeurs par défaut des appareils sans afficher de boîte de dialogue.|
|[CPrintDialogEx::GetDeviceName](#getdevicename)|Récupère le nom du périphérique d’impression actuellement sélectionné.|
|[CPrintDialogEx::GetDevMode](#getdevmode)|Récupère la `DEVMODE` structure.|
|[CPrintDialogEx::GetDriverName](#getdrivername)|Récupère le nom du pilote de périphérique d’imprimante défini par le système.|
|[CPrintDialogEx::GetPortName](#getportname)|Récupère le nom du port d’imprimante actuellement sélectionné.|
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|Récupère un handle vers le contexte de périphérique d’impression.|
|[CPrintDialogEx::PrintAll](#printall)|Détermine si toutes les pages du document doivent être imprimées.|
|[CPrintDialogEx::PrintCollate](#printcollate)|Détermine si les copies assemblées sont demandées.|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|Détermine s’il faut imprimer la page active du document.|
|[CPrintDialogEx::PrintRange](#printrange)|Détermine s’il faut imprimer uniquement une plage de pages spécifiée.|
|[CPrintDialogEx::PrintSelection](#printselection)|Détermine s’il faut imprimer uniquement les éléments actuellement sélectionnés.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPrintDialogEx::m_pdex](#m_pdex)|Structure utilisée pour personnaliser un `CPrintDialogEx` objet.|

## <a name="remarks"></a>Notes

Vous pouvez vous appuyer sur l’infrastructure pour gérer de nombreux aspects du processus d’impression pour votre application. Pour plus d’informations sur l’utilisation de l’infrastructure pour gérer les tâches d’impression, consultez l’article [impression](../../mfc/printing.md).

Si vous souhaitez que votre application gère l’impression sans l’implication de l’infrastructure, vous pouvez `CPrintDialogEx` utiliser la classe «telle quelle» avec le constructeur fourni, ou vous pouvez dériver votre propre `CPrintDialogEx` classe de boîte de dialogue à partir de et écrire un constructeur pour répondre à vos besoins. Dans les deux cas, ces boîtes de dialogue se comportent comme des boîtes de dialogue MFC standard `CCommonDialog`, car elles sont dérivées de la classe.

Pour utiliser un `CPrintDialogEx` objet, commencez par créer l’objet à `CPrintDialogEx` l’aide du constructeur. Une fois la boîte de dialogue construite, vous pouvez définir ou modifier les valeurs de la structure [m_pdex](#m_pdex) pour initialiser les valeurs des contrôles de la boîte de dialogue. La `m_pdex` structure est de type [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa). Pour plus d’informations sur cette structure, consultez la SDK Windows.

Si vous `m_pdex` ne fournissez pas vos propres handles dans pour `hDevNames` les `hDevMode` membres et, veillez à appeler la `GlobalFree` fonction Windows pour ces handles lorsque vous avez fini d’utiliser la boîte de dialogue.

Après l’initialisation des contrôles de boîte de dialogue, `DoModal` appelez la fonction membre pour afficher la boîte de dialogue et permettre à l’utilisateur de sélectionner des options d’impression. Lorsque `DoModal` retourne, vous pouvez déterminer si l’utilisateur a sélectionné le bouton OK, appliquer ou annuler.

Si l’utilisateur a cliqué sur OK, vous `CPrintDialogEx`pouvez utiliser les fonctions membres de pour récupérer les informations entrées par l’utilisateur.

La `CPrintDialogEx::GetDefaults` fonction membre est utile pour récupérer les valeurs par défaut de l’imprimante actuelle sans afficher de boîte de dialogue. Cette méthode ne nécessite aucune intervention de l’utilisateur.

Vous pouvez utiliser la fonction `CommDlgExtendedError` Windows pour déterminer si une erreur s’est produite lors de l’initialisation de la boîte de dialogue et pour en savoir plus sur l’erreur. Pour plus d’informations sur cette fonction, consultez la SDK Windows.

Pour plus d’informations sur `CPrintDialogEx`l’utilisation de, consultez [classes de boîtes de dialogue communes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`IObjectWithSite`

`IPrintDialogCallback`

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialogEx`

## <a name="requirements"></a>Configuration requise

**En-tête:** afxdlgs. h

##  <a name="cprintdialogex"></a>  CPrintDialogEx::CPrintDialogEx

Construit une feuille de propriétés d’impression Windows.

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Un ou plusieurs indicateurs que vous pouvez utiliser pour personnaliser les paramètres de la boîte de dialogue, combinés à l’aide de l’opérateur de bits or. Par exemple, l’indicateur PD_ALLPAGES définit la plage d’impression par défaut sur toutes les pages du document. Pour plus d’informations sur ces indicateurs, consultez la structure [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) dans le SDK Windows.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente ou propriétaire de la boîte de dialogue.

### <a name="remarks"></a>Notes

Cette fonction membre construit uniquement l’objet. Utilisez la `DoModal` fonction membre pour afficher la boîte de dialogue.

##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC

Crée un contexte de périphérique (DC) d’imprimante à partir des structures [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) et [DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames) .

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valeur de retour

Handle vers le contexte de périphérique d’impression nouvellement créé.

### <a name="remarks"></a>Notes

Le contrôleur de périphérique retourné est également stocké dans le `hDC` membre de [m_pdex](#m_pdex).

Ce contrôleur de périphérique est supposé être le contrôleur de l’imprimante en cours et tous les autres contrôleurs d’imprimante précédemment obtenus doivent être supprimés. Cette fonction peut être appelée, et le contrôleur de périphérique obtenu utilisé, sans jamais afficher la boîte de dialogue Imprimer.

##  <a name="domodal"></a>  CPrintDialogEx::DoModal

Appelez cette fonction pour afficher la feuille de propriétés d’impression Windows et permettre à l’utilisateur de sélectionner différentes options d’impression, telles que le nombre de copies, la plage de pages et si les copies doivent être assemblées.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

La valeur de retour INT_PTR est en fait un HRESULT. Consultez la section valeurs de retour dans [PrintDlgEx](/previous-versions/windows/desktop/legacy/ms646942\(v=vs.85\)) dans le SDK Windows.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les différentes options de la boîte de dialogue d’impression en `m_pdex` définissant les membres de la structure, `DoModal`vous devez effectuer cette opération avant d’appeler, mais après la construction de l’objet de boîte de dialogue.

Après avoir `DoModal`appelé, vous pouvez appeler d’autres fonctions membres pour récupérer les paramètres ou les informations entrées par l’utilisateur dans la boîte de dialogue.

Si l’indicateur PD_RETURNDC est utilisé lors de `DoModal`l’appel de, un DC d’imprimante est `hDC` retourné dans le membre de [m_pdex](#m_pdex). Ce contrôleur de périphérique doit être libéré à l’aide d’un appel à [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) par l’appelant de `CPrintDialogEx`.

##  <a name="getcopies"></a>  CPrintDialogEx::GetCopies

Appelez cette fonction après avoir `DoModal` appelé pour récupérer le nombre de copies demandées.

```
int GetCopies() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de copies demandées.

##  <a name="getdefaults"></a>  CPrintDialogEx::GetDefaults

Appelez cette fonction pour récupérer les valeurs par défaut de l’imprimante par défaut sans afficher de boîte de dialogue.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite; sinon, FALSe.

### <a name="remarks"></a>Notes

Crée un contexte de périphérique (DC) d’imprimante à partir des structures [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) et [DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames) .

`GetDefaults`n’affiche pas la feuille de propriétés d’impression. Au lieu de cela, `hDevNames` il `hDevMode` définit les membres et de [m_pdex](#m_pdex) sur les descripteurs des structures [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) et [DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames) initialisées pour l’imprimante par défaut du système. Et doivent avoir la valeur null, `GetDefaults` ou échouer. `hDevMode` `hDevNames`

Si l’indicateur PD_RETURNDC est défini, `hDevNames` cette fonction ne retourne pas et `hDevMode` (située dans `m_pdex.hDevNames` et `m_pdex.hDevMode`) à l’appelant, mais elle retourne également un DC d’imprimante dans `m_pdex.hDC`. Il incombe à l’appelant de supprimer le contrôleur de l’imprimante et d’appeler la fonction [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree) de Windows sur les handles lorsque vous `CPrintDialogEx` avez terminé avec l’objet.

##  <a name="getdevicename"></a>  CPrintDialogEx::GetDeviceName

Appelez cette fonction après avoir appelé [DoModal](#domodal) pour récupérer le nom de l’imprimante actuellement sélectionnée, ou après l’appel de [GetDefaults](#getdefaults) pour récupérer le nom de l’imprimante par défaut.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valeur de retour

Nom de l’imprimante actuellement sélectionnée.

### <a name="remarks"></a>Notes

Utilisez un pointeur vers l' `CString` objet retourné par `GetDeviceName` comme valeur de `lpszDeviceName` dans un appel à [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getdevmode"></a>  CPrintDialogEx::GetDevMode

Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer des informations sur le périphérique d’impression.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valeur de retour

Structure de données [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) , qui contient des informations sur l’initialisation de l’appareil et l’environnement d’un pilote d’impression. Vous devez déverrouiller la mémoire prise par cette structure à l’aide de la fonction [GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock) de Windows, qui est décrite dans la SDK Windows.

##  <a name="getdrivername"></a>  CPrintDialogEx::GetDriverName

Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer le nom du pilote de périphérique d’imprimante défini par le système.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valeur de retour

`CString` Spécifiant le nom du pilote défini par le système.

### <a name="remarks"></a>Notes

Utilisez un pointeur vers l' `CString` objet retourné par `GetDriverName` comme valeur de *lpszDriverName* dans un appel à [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getportname"></a>  CPrintDialogEx::GetPortName

Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer le nom du port d’imprimante actuellement sélectionné.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valeur de retour

Nom du port d’imprimante actuellement sélectionné.

##  <a name="getprinterdc"></a>  CPrintDialogEx::GetPrinterDC

Retourne un handle vers le contexte de périphérique d’impression.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Valeur de retour

Handle vers le contexte de périphérique d’impression.

### <a name="remarks"></a>Notes

Vous devez appeler la fonction [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) de Windows pour supprimer le contexte de périphérique une fois que vous avez fini de l’utiliser.

##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex

Structure PRINTDLGEX dont les membres stockent les caractéristiques de l’objet Dialog.

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>Notes

Après avoir construit un `CPrintDialogEx` objet, vous pouvez utiliser `m_pdex` pour définir différents aspects de la boîte de dialogue avant d’appeler la fonction membre [DoModal](#domodal) . Pour plus d’informations sur `m_pdex` la structure, consultez [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) dans le SDK Windows.

Si vous modifiez directement `m_pdex` le membre de données, vous remplacerez tout comportement par défaut.

##  <a name="printall"></a>  CPrintDialogEx::PrintAll

Appelez cette fonction après avoir `DoModal` appelé pour déterminer si toutes les pages du document doivent être imprimées.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si toutes les pages du document doivent être imprimées; Sinon, FALSe.

##  <a name="printcollate"></a>  CPrintDialogEx::PrintCollate

Appelez cette fonction après avoir `DoModal` appelé pour déterminer si l’imprimante doit reclasser toutes les copies imprimées du document.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si l’utilisateur active la case à cocher assembler dans la boîte de dialogue; Sinon, FALSe.

##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage

Appelez cette fonction après avoir `DoModal` appelé pour déterminer s’il faut imprimer la page actuelle dans le document.

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si l’option **imprimer la page active** est sélectionnée dans la boîte de dialogue Imprimer; Sinon, FALSe.

##  <a name="printrange"></a>  CPrintDialogEx::PrintRange

Appelez cette fonction après avoir `DoModal` appelé pour déterminer s’il faut imprimer uniquement une plage de pages dans le document.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si seule une plage de pages dans le document doit être imprimée; Sinon, FALSe.

### <a name="remarks"></a>Notes

Les plages de pages spécifiées peuvent être déterminées `nPageRanges`à `nMaxPageRanges`partir de `lpPageRanges` [m_pdex](#m_pdex) (consultez, et dans la structure [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) du SDK Windows).

##  <a name="printselection"></a>  CPrintDialogEx::PrintSelection

Appelez cette fonction après avoir `DoModal` appelé pour déterminer s’il faut imprimer uniquement les éléments actuellement sélectionnés.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si seuls les éléments sélectionnés doivent être imprimés; Sinon, FALSe.

## <a name="see-also"></a>Voir aussi

[CCommonDialog, classe](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo, structure](../../mfc/reference/cprintinfo-structure.md)
