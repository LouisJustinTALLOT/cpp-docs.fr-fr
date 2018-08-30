---
title: CPrintDialogEx, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d1e8ae445da8c69901c319665704e06895103d1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199507"
---
# <a name="cprintdialogex-class"></a>CPrintDialogEx, classe
Encapsule les services fournis par la feuille de propriétés d’impression de Windows.  
  
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
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|Crée un contexte de périphérique d’imprimante sans afficher la boîte de dialogue Imprimer.|  
|[CPrintDialogEx::DoModal](#domodal)|Affiche la boîte de dialogue et permet à l’utilisateur d’effectuer des sélections.|  
|[CPrintDialogEx::GetCopies](#getcopies)|Récupère le nombre de copies demandé.|  
|[CPrintDialogEx::GetDefaults](#getdefaults)|Récupère les valeurs par défaut de l’appareil sans afficher une boîte de dialogue.|  
|[CPrintDialogEx::GetDeviceName](#getdevicename)|Récupère le nom de l’appareil de l’imprimante actuellement sélectionnée.|  
|[CPrintDialogEx::GetDevMode](#getdevmode)|Récupère le `DEVMODE` structure.|  
|[CPrintDialogEx::GetDriverName](#getdrivername)|Récupère le nom du pilote de périphérique d’imprimante définie par le système.|  
|[CPrintDialogEx::GetPortName](#getportname)|Récupère le nom du port imprimante actuellement sélectionnée.|  
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|Récupère un handle vers le contexte de périphérique d’imprimante.|  
|[CPrintDialogEx::PrintAll](#printall)|Détermine s’il faut imprimer toutes les pages du document.|  
|[CPrintDialogEx::PrintCollate](#printcollate)|Détermine si assemblés copies sont demandées.|  
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|Détermine s’il faut imprimer la page active du document.|  
|[CPrintDialogEx::PrintRange](#printrange)|Détermine s’il faut imprimer uniquement une plage de pages spécifiée.|  
|[CPrintDialogEx::PrintSelection](#printselection)|Détermine s’il faut imprimer uniquement les éléments actuellement sélectionnés.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CPrintDialogEx::m_pdex](#m_pdex)|Une structure utilisée pour personnaliser un `CPrintDialogEx` objet.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez compter sur l’infrastructure pour gérer de nombreux aspects du processus d’impression pour votre application. Pour plus d’informations sur l’utilisation de l’infrastructure pour gérer des tâches d’impression, consultez l’article [impression](../../mfc/printing.md).  
  
 Si vous souhaitez que votre application pour gérer l’impression sans l’intervention de l’infrastructure, vous pouvez utiliser la `CPrintDialogEx` de classe avec le constructeur fourni « tel quel », ou vous pouvez dériver votre propre classe de boîte de dialogue de `CPrintDialogEx` et écrire un constructeur pour l’adapter à vos besoins. Dans les deux cas, ces boîtes de dialogue se comportera comme des boîtes de dialogue MFC standards, car ils sont dérivés de la classe `CCommonDialog`.  
  
 Pour utiliser un `CPrintDialogEx` d’objet, commencez par créer l’objet en utilisant le `CPrintDialogEx` constructeur. Une fois la boîte de dialogue a été construite, vous pouvez définir ou modifier des valeurs dans le [m_pdex](#m_pdex) structure pour initialiser les valeurs des contrôles de la boîte de dialogue. Le `m_pdex` structure est de type [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa). Pour plus d’informations sur cette structure, consultez le Kit de développement Windows.  
  
 Si vous ne fournissez pas de vos propres descripteurs dans `m_pdex` pour le `hDevMode` et `hDevNames` membres, veillez à appeler la fonction Windows `GlobalFree` pour ces descripteurs lorsque vous avez terminé avec la boîte de dialogue.  
  
 Après l’initialisation du contrôle de boîte de dialogue, appelez le `DoModal` fonction membre à la boîte de dialogue s’affiche et autorise l’utilisateur à sélectionner les options d’impression. Lorsque `DoModal` est retournée, vous pouvez déterminer si l’utilisateur a sélectionné le bouton OK, appliquer ou sur Annuler.  
  
 Si l’utilisateur a appuyé sur OK, vous pouvez utiliser `CPrintDialogEx`de fonctions membres pour récupérer les informations entrées par l’utilisateur.  
  
 Le `CPrintDialogEx::GetDefaults` fonction membre est utile pour extraire les valeurs par défaut d’imprimante en cours sans afficher une boîte de dialogue. Cette méthode ne requiert aucune interaction utilisateur.  
  
 Vous pouvez utiliser le Windows `CommDlgExtendedError` fonction pour déterminer si une erreur s’est produite lors de l’initialisation de la boîte de dialogue et pour en savoir plus sur l’erreur. Pour plus d’informations sur cette fonction, consultez le Kit de développement Windows.  
  
 Pour plus d’informations sur l’utilisation de `CPrintDialogEx`, consultez [des Classes de boîte de dialogue communes](../../mfc/common-dialog-classes.md).  
  
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
 **En-tête :** afxdlgs.h  
  
##  <a name="cprintdialogex"></a>  CPrintDialogEx::CPrintDialogEx  
 Construit une feuille de propriétés d’impression de Windows.  
  
```  
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwFlags*  
 Un ou plusieurs indicateurs que vous pouvez utiliser pour personnaliser les paramètres de la boîte de dialogue, combinées à l’aide de l’opérateur OR au niveau du bit. Par exemple, l’indicateur PD_ALLPAGES définit l’étendue d’impression par défaut à toutes les pages du document. Consultez le [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) structure dans le SDK Windows pour plus d’informations sur ces indicateurs.  
  
 *pParentWnd*  
 Pointeur vers la fenêtre parente ou propriétaire de la boîte de dialogue.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre construit uniquement l’objet. Utilisez le `DoModal` fonction membre pour afficher la boîte de dialogue.  
  
##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC  
 Crée un contexte de périphérique (DC) à partir de la [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) et [DEVNAMES](../../mfc/reference/devnames-structure.md) structures.  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Handle de contexte de l’imprimante qui vient d’être créé.  
  
### <a name="remarks"></a>Notes  
 Le contrôleur de domaine retourné est également stocké dans le `hDC` membre [m_pdex](#m_pdex).  
  
 Ce contrôleur de domaine est censé pour être le périphérique d’impression en cours, et tout autre obtenue précédemment imprimante que contrôleurs de domaine doivent être supprimées. Cette fonction peut être appelée et le contrôleur de domaine qui en résulte est utilisé, sans jamais afficher la boîte de dialogue Imprimer.  
  
##  <a name="domodal"></a>  CPrintDialogEx::DoModal  
 Appelez cette fonction pour afficher la feuille de propriétés d’impression de Windows et autoriser l’utilisateur à sélectionner plusieurs options d’impression telles que le nombre de copies, plage de pages, et si les copies doivent être triées.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le INT_PTR valeur de retour est en fait un HRESULT. Consultez la section de valeurs de retour dans [PrintDlgEx](https://msdn.microsoft.com/library/windows/desktop/ms646942) dans le SDK Windows.  
  
### <a name="remarks"></a>Notes  
 Si vous souhaitez initialiser les différentes options de la boîte de dialogue Imprimer en définissant des membres de la `m_pdex` structure, vous devez le faire avant d’appeler `DoModal`, mais une fois que l’objet de la boîte de dialogue est construit.  
  
 Après avoir appelé `DoModal`, vous pouvez appeler des fonctions pour récupérer les paramètres ou les informations saisies par l’utilisateur dans la boîte de dialogue autres membres.  
  
 Si l’indicateur PD_RETURNDC est utilisé lors de l’appel `DoModal`, une contrôleur de domaine de l’imprimante s’affichera dans le `hDC` membre [m_pdex](#m_pdex). Ce contrôleur de domaine doit être libérée avec un appel à [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) par l’appelant de `CPrintDialogEx`.  
  
##  <a name="getcopies"></a>  CPrintDialogEx::GetCopies  
 Appelez cette fonction après l’appel `DoModal` pour récupérer le nombre de copies demandé.  
  
```  
int GetCopies() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de copies demandé.  
  
##  <a name="getdefaults"></a>  CPrintDialogEx::GetDefaults  
 Appelez cette fonction pour récupérer les valeurs par défaut de l’appareil de l’imprimante par défaut sans afficher une boîte de dialogue.  
  
```  
BOOL GetDefaults();
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE en cas de réussite, sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Crée un contexte de périphérique (DC) à partir de la [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) et [DEVNAMES](../../mfc/reference/devnames-structure.md) structures.  
  
 `GetDefaults` n’affiche pas la feuille de propriétés d’impression. Au lieu de cela, il définit le `hDevNames` et `hDevMode` membres de [m_pdex](#m_pdex) pour les poignées pour le [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) et [DEVNAMES](../../mfc/reference/devnames-structure.md) structures qui sont initialisées pour le imprimante par défaut du système. Les deux `hDevNames` et `hDevMode` doit être NULL, ou `GetDefaults` échoue.  
  
 Si l’indicateur PD_RETURNDC est défini, cette fonction seulement retourneront `hDevNames` et `hDevMode` (situé dans `m_pdex.hDevNames` et `m_pdex.hDevMode`) à l’appelant, mais retourne également un périphérique d’impression dans `m_pdex.hDC`. Il incombe à l’appelant de supprimer le périphérique d’impression et appelez le Windows [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree) fonction sur les poignées lorsque vous avez terminé avec le `CPrintDialogEx` objet.  
  
##  <a name="getdevicename"></a>  CPrintDialogEx::GetDeviceName  
 Appelez cette fonction après avoir appelé [DoModal](#domodal) pour récupérer le nom de l’imprimante actuellement sélectionnée, ou après l’appel [GetDefaults](#getdefaults) pour récupérer le nom de l’imprimante par défaut.  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nom de l’imprimante actuellement sélectionnée.  
  
### <a name="remarks"></a>Notes  
 Utiliser un pointeur vers le `CString` objet retourné par `GetDeviceName` comme valeur de `lpszDeviceName` dans un appel à [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
##  <a name="getdevmode"></a>  CPrintDialogEx::GetDevMode  
 Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer des informations sur le périphérique d’impression.  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) structure de données qui contient des informations sur l’environnement d’un pilote d’impression et de l’initialisation des périphériques. Vous devez déverrouiller la mémoire consommée par cette structure avec le Windows [GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock) (fonction), qui est décrit dans le SDK Windows.  
  
##  <a name="getdrivername"></a>  CPrintDialogEx::GetDriverName  
 Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer le nom du pilote de périphérique d’imprimante définie par le système.  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un `CString` en spécifiant le nom du pilote définie par le système.  
  
### <a name="remarks"></a>Notes  
 Utiliser un pointeur vers le `CString` objet retourné par `GetDriverName` comme valeur de *lpszDriverName* dans un appel à [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
##  <a name="getportname"></a>  CPrintDialogEx::GetPortName  
 Appelez cette fonction après avoir appelé [DoModal](#domodal) ou [GetDefaults](#getdefaults) pour récupérer le nom du port imprimante actuellement sélectionnée.  
  
```  
CString GetPortName() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nom du port imprimante actuellement sélectionnée.  
  
##  <a name="getprinterdc"></a>  CPrintDialogEx::GetPrinterDC  
 Retourne un handle vers le contexte de périphérique d’imprimante.  
  
```  
HDC GetPrinterDC() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Handle vers le contexte de périphérique d’imprimante.  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler la Windows [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) (fonction) pour supprimer le contexte de périphérique lorsque vous avez terminé l’utiliser.  
  
##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex  
 Une structure PRINTDLGEX dont les membres stockent les caractéristiques de l’objet de la boîte de dialogue.  
  
```  
PRINTDLGEX m_pdex;  
```  
  
### <a name="remarks"></a>Notes  
 Après avoir construit un `CPrintDialogEx` de l’objet, vous pouvez utiliser `m_pdex` pour définir les divers aspects de la boîte de dialogue avant d’appeler le [DoModal](#domodal) fonction membre. Pour plus d’informations sur la `m_pdex` structure, consultez [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) dans le SDK Windows.  
  
 Si vous modifiez le `m_pdex` membre de données directement, vous remplacerez tout comportement par défaut.  
  
##  <a name="printall"></a>  CPrintDialogEx::PrintAll  
 Appelez cette fonction après l’appel `DoModal` pour déterminer s’il faut imprimer toutes les pages dans le document.  
  
```  
BOOL PrintAll() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si toutes les pages dans le document doivent être affichés ; Sinon, FALSE.  
  
##  <a name="printcollate"></a>  CPrintDialogEx::PrintCollate  
 Appelez cette fonction après l’appel `DoModal` pour déterminer si l’imprimante doit collate imprimées toutes les copies du document.  
  
```  
BOOL PrintCollate() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si l’utilisateur sélectionne la case à cocher collate dans la boîte de dialogue ; Sinon, FALSE.  
  
##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage  
 Appelez cette fonction après l’appel `DoModal` pour déterminer s’il faut imprimer la page actuelle dans le document.  
  
```  
BOOL PrintCurrentPage() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si **imprimer la Page actuelle** est sélectionné dans la boîte de dialogue impression ; sinon, FALSE.  
  
##  <a name="printrange"></a>  CPrintDialogEx::PrintRange  
 Appelez cette fonction après l’appel `DoModal` pour déterminer s’il faut N'imprimer qu’une plage de pages dans le document.  
  
```  
BOOL PrintRange() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE uniquement si une plage de pages dans le document sont à imprimer ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Les plages de pages spécifié peuvent être déterminés à partir [m_pdex](#m_pdex) (consultez `nPageRanges`, `nMaxPageRanges`, et `lpPageRanges` dans le [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) structure dans le SDK Windows).  
  
##  <a name="printselection"></a>  CPrintDialogEx::PrintSelection  
 Appelez cette fonction après l’appel `DoModal` pour déterminer s’il faut imprimer uniquement les éléments actuellement sélectionnés.  
  
```  
BOOL PrintSelection() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si seuls les éléments sélectionnés doivent être affichés ; Sinon, FALSE.  
  
## <a name="see-also"></a>Voir aussi  
 [Ccommondialog, classe](../../mfc/reference/ccommondialog-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CPrintInfo, structure](../../mfc/reference/cprintinfo-structure.md)
