---
title: Routines d’échange de données de la boîte de dialogue standard | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f6c79a96439605bcf9ab670c1f75dda2d50169f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377653"
---
# <a name="standard-dialog-data-exchange-routines"></a>Routines d'échange de données de boîte de dialogue standard
Cette rubrique répertorie les routines d’échange (DDX) de données boîte de dialogue standard utilisés pour les contrôles de boîte de dialogue MFC courants.  
  
> [!NOTE]
>  Les routines d’échange de données boîte de dialogue standard sont définis dans le afxdd_.h de fichier d’en-tête. Toutefois, les applications doivent inclure afxwin.h.  
  
### <a name="ddx-functions"></a>DDX (fonctions)  
  
|||  
|-|-|  
|[DDX_CBIndex](#ddx_cbindex)|Initialise ou récupère l’index de la sélection actuelle d’un contrôle de zone de liste déroulante.|  
|[DDX_CBString](#ddx_cbstring)|Initialise ou récupère le contenu actuel du champ d’édition d’un contrôle de zone de liste déroulante.|  
|[DDX_CBStringExact](#ddx_cbstringexact)|Initialise ou récupère le contenu actuel du champ d’édition d’un contrôle de zone de liste déroulante.|  
|[DDX_Check](#ddx_check)|Initialise ou récupère l’état actuel d’un contrôle de case à cocher.|  
|[DDX_Control](#ddx_control)|Sous-classe un contrôle donné au sein d’une boîte de dialogue.|  
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|Initialise ou récupère des données de date et/ou une heure d’un contrôle de sélecteur de date et d’heure.|  
|[DDX_IPAddress](#ddx_ipaddress)|Initialise ou récupère la valeur actuelle d’un contrôle d’adresse IP.|  
|[DDX_LBIndex](#ddx_lbindex)|Initialise ou récupère l’index de la sélection actuelle d’un contrôle de zone de liste.|  
|[DDX_LBString](#ddx_lbstring)|Initialise ou récupère la sélection actuelle dans un contrôle de zone de liste.|  
|[DDX_LBStringExact](#ddx_lbstringexact)|Initialise ou récupère la sélection actuelle dans un contrôle de zone de liste.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Crée un contrôle .NET correspondant ID de ressource. du contrôle|  
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Initialise ou récupère la valeur actuelle d’un contrôle month calendar.|  
|[DDX_Radio](#ddx_radio)|Initialise ou récupère l’index de base 0 du contrôle de case d’option qui est actuellement modifié au sein d’un groupe de contrôles de case d’option.|  
|[DDX_Scroll](#ddx_scroll)|Initialise ou récupère la position actuelle du curseur de défilement d’un contrôle de défilement.|  
|[DDX_Slider](#ddx_slider)|Initialise ou récupère la position actuelle du curseur de défilement d’un contrôle slider.|  
|[DDX_Text](#ddx_text)|Initialise ou récupère la valeur actuelle d’un contrôle d’édition.|  
  
##  <a name="ddx_cbindex"></a>  DDX_CBIndex  
 Le `DDX_CBIndex` fonction gère le transfert de `int` des données entre un contrôle de zone de liste déroulante dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un `int` membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
```  
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 L’ID de ressource du contrôle de zone de liste déroulante associé à la propriété du contrôle.  
  
 *index*  
 Une référence à une variable membre de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Lorsque `DDX_CBIndex` est appelée, *index* est définie à l’index de la sélection de la zone de liste déroulante en cours. Si aucun élément n’est sélectionné, *index* est définie sur 0.  
  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdd_.h  
  
##  <a name="ddx_cbstring"></a>  DDX_CBString  
 Le `DDX_CBString` fonction gère le transfert de `CString` des données entre le contrôle d’édition d’un contrôle de zone de liste déroulante dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un `CString` membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
```  
void AFXAPI DDX_CBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 L’ID de ressource du contrôle de zone de liste déroulante associé à la propriété du contrôle.  
  
 *valeur*  
 Une référence à une variable membre de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Lorsque `DDX_CBString` est appelée, *valeur* est définie sur la sélection de la zone de liste déroulante en cours. Si aucun élément n’est sélectionné, *valeur* est définie sur une chaîne de longueur nulle.  
  
> [!NOTE]
>  Si la zone de liste modifiable est une zone de liste déroulante, la valeur échangée est limitée à 255 caractères.  
  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdd_.h  
  
##  <a name="ddx_cbstringexact"></a>  DDX_CBStringExact  
 Le `DDX_CBStringExact` fonction gère le transfert de `CString` des données entre le contrôle d’édition d’un contrôle de zone de liste déroulante dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un `CString` membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
```  
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 L’ID de ressource du contrôle de zone de liste déroulante associé à la propriété du contrôle.  
  
 *valeur*  
 Une référence à une variable membre de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Lorsque `DDX_CBStringExact` est appelée, *valeur* est définie sur la sélection de la zone de liste déroulante en cours. Si aucun élément n’est sélectionné, *valeur* est définie sur une chaîne de longueur nulle.  
  
> [!NOTE]
>  Si la zone de liste modifiable est une zone de liste déroulante, la valeur échangée est limitée à 255 caractères.  
  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdd_.h  
  
##  <a name="ddx_check"></a>  DDX_Check  
 Le `DDX_Check` fonction gère le transfert de `int` des données entre un contrôle de case à cocher dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un `int` membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
```  
void AFXAPI DDX_Check(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 L’ID de ressource du contrôle de case à cocher associé à la propriété du contrôle.  
  
 *valeur*  
 Une référence à une variable membre de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Lorsque `DDX_Check` est appelée, *valeur* est définie sur l’état actuel du contrôle de case à cocher. Pour obtenir la liste des valeurs d’état possibles, consultez [BM_GETCHECK](http://msdn.microsoft.com/library/windows/desktop/bb775986) dans le Kit de développement logiciel Windows.  
  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdd_.h  
  
##  <a name="ddx_control"></a>  DDX_Control  
 Le `DDX_Control` fonction sous-classes le contrôle spécifié par `nIDC`, de la boîte de dialogue, le mode formulaire ou l’objet de vue de contrôle.  
  
```  
void AFXAPI DDX_Control(
    CDataExchange* pDX,  
    int nIDC,  
    CWnd& rControl);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.  
  
 `nIDC`  
 L’ID de ressource du contrôle pour être sous-classé.  
  
 *rControl*  
 Une référence à une variable membre de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle associée au contrôle spécifié.  
  
### <a name="remarks"></a>Notes  
 Le `pDX` objet est fourni par le framework lorsque le `DoDataExchange` est appelée. Par conséquent, `DDX_Control` doit uniquement être appelée dans la substitution de `DoDataExchange`.  
  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdd_.h  
  
##  <a name="ddx_datetimectrl"></a>  DDX_DateTimeCtrl  
 Le `DDX_DateTimeCtrl` fonction gère le transfert de données de date et/ou une heure entre un contrôle de sélecteur de date et d’heure ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) dans un objet de vue de formulaire ou de boîte de dialogue et soit un [CTime](../../atl-mfc-shared/reference/ctime-class.md) ou un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) membre de données de l’objet de vue de zone ou un formulaire de boîte de dialogue.  
  
```  
void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    CTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    COleDateTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction. Vous n’avez pas besoin de supprimer cet objet.  
  
 `nIDC`  
 L’ID de la ressource du contrôle de sélecteur de date et l’heure associé à la variable membre.  
  
 *valeur*  
 Dans les deux premières versions, une référence à un `CTime` ou `COleDateTime` variable membre, boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont échangées. Dans la troisième version, une référence à un `CString` objet de vue de données membre contrôle.  
  
### <a name="remarks"></a>Notes  
 Lorsque `DDX_DateTimeCtrl` est appelée, *valeur* est définie sur l’état de la date et de contrôle de sélecteur de temps ou le contrôle est défini sur *valeur*, en fonction de la direction de l’échange.  
  
 Dans la troisième version ci-dessus, `DDX_DateTimeCtrl` gère le transfert de `CString` contrôle de données entre une date et heure et une [CString](../../atl-mfc-shared/reference/cstringt-class.md) membre de données de l’objet de vue de contrôle. La chaîne est mise en forme à l’aide des règles de paramètres régionaux actuels pour mettre en forme des dates et heures.  
  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdd_.h  

   

 
## <a name="ddx_managedcontrol"></a>  DDX_ManagedControl
Crée un contrôle .NET correspondant ID de ressource. du contrôle  
   
### <a name="syntax"></a>Syntaxe  
  ```  
template <typename T>  
void DDX_ManagedControl(  
     CDataExchange* pDX,   
     int nIDC,   
     CWinFormsControl<T>& control );  
```
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Un pointeur vers un [CDataExchange (classe)](cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 L’ID de ressource du contrôle associé à la propriété du contrôle.  
  
 `control`  
 Une référence à un [CWinFormsControl classe](cwinformscontrol-class.md) objet.  
   
### <a name="remarks"></a>Notes  
 `DDX_ManagedControl` appels [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) pour créer un contrôle correspondant à l’ID du contrôle de ressource. Utilisez `DDX_ManagedControl` pour créer des contrôles à partir de l’ID de ressource dans [CDialog::OnInitDialog](cdialog-class.md#oninitdialog). Pour l’échange de données, vous n’avez pas besoin d’utiliser les fonctions DDX/DDV avec les contrôles Windows Forms.  
  
 Pour plus d’informations, consultez [Comment : effectuer une liaison de données DDX/DDV avec Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).  
   
### <a name="requirements"></a>Spécifications  
 **En-tête :** afxwinforms.h  
   
### <a name="see-also"></a>Voir aussi  
 [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)   
 [CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
 

  
##  <a name="ddx_ipaddress"></a>  DDX_IPAddress  
 Le `DDX_IPAddress` fonction gère le transfert de données entre un contrôle d’adresse IP et un membre de données de l’objet de vue de contrôle.  
  
```  
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,  
    int nIDC,  
    DWORD& value);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 L’ID de ressource du contrôle d’adresse IP associé à la propriété du contrôle.  
  
 *valeur*  
 Une référence à la `DWORD` contenant la valeur du champ de quatre du contrôle d’adresse IP. Les champs sont remplis ou comme suits.  
  
|Champ|Contenant la valeur du champ de bits|  
|-----------|-------------------------------------|  
|3|0 à 7|  
|2|8 à 15|  
|1|16 à 23|  
|0|24 à 31|  
  
 Utiliser Win32 [IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378) pour lire la valeur, ou utilisez [IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380) pour remplir la valeur. Ces messages sont décrits dans le Kit de développement logiciel Windows.  
  
### <a name="remarks"></a>Notes  
 Lorsque `DDX_IPAddress` est appelée, *valeur* est soit en lecture à partir du contrôle de l’adresse IP, ou *valeur* est écrit dans le contrôle, en fonction de la direction de l’échange.  
  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdd_.h  
  
##  <a name="ddx_lbindex"></a>  DDX_LBIndex  
 Le `DDX_LBIndex` fonction gère le transfert de `int` des données entre un contrôle de zone de liste dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un `int` membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
```  
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 L’ID de ressource de contrôle de zone de liste associé à la propriété du contrôle.  
  
 *index*  
 Une référence à une variable membre de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Lorsque `DDX_LBIndex` est appelée, *index* est définie à l’index de la sélection de la liste actuelle. Si aucun élément n’est sélectionné, *index* a la valeur -1.  
  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdd_.h  
  
##  <a name="ddx_lbstring"></a>  DDX_LBString  
 Le `DDX_LBString` fonction gère le transfert de `CString` des données entre un contrôle de zone de liste dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un `CString` membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
```  
void AFXAPI DDX_LBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 L’ID de ressource de contrôle de zone de liste associé à la propriété du contrôle.  
  
 *valeur*  
 Une référence à une variable membre de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Lorsque `DDX_LBString` est appelée pour transférer des données à un contrôle de zone de liste, le premier élément dans le contrôle dont le début correspond à *valeur* est sélectionnée. (Pour faire correspondre l’élément entier plutôt que simplement un préfixe, utilisez [DDX_LBStringExact](#ddx_lbstringexact).) S’il n’y a aucune correspondance, aucun des éléments ne sont sélectionnés. La mise en correspondance respecte la casse.  
  
 Lorsque `DDX_LBString` est appelée pour transférer des données à partir d’un contrôle de zone de liste, *valeur* est définie sur la sélection de la liste actuelle. Si aucun élément n’est sélectionné, *valeur* est définie sur une chaîne de longueur nulle.  
  
> [!NOTE]
>  Si la zone de liste est une zone de liste déroulante, la valeur échangée est limitée à 255 caractères.  
  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdd_.h  
  
##  <a name="ddx_lbstringexact"></a>  DDX_LBStringExact  
 Le `DDX_CBStringExact` fonction gère le transfert de `CString` des données entre le contrôle d’édition d’un contrôle de zone de liste dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un `CString` membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
```  
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 L’ID de ressource de contrôle de zone de liste associé à la propriété du contrôle.  
  
 *valeur*  
 Une référence à une variable membre de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Lorsque `DDX_LBStringExact` est appelée pour transférer des données à un contrôle de zone de liste, le premier élément dans le contrôle qui correspond aux *valeur* est sélectionnée. (Pour faire correspondre uniquement à un préfixe plutôt que l’élément entier, utilisez [DDX_LBString](#ddx_lbstring).) S’il n’y a aucune correspondance, aucun des éléments ne sont sélectionnés. La mise en correspondance respecte la casse.  
  
 Lorsque `DDX_CBStringExact` est appelée pour transférer des données à partir d’un contrôle de zone de liste, *valeur* est définie sur la sélection de la liste actuelle. Si aucun élément n’est sélectionné, *valeur* est définie sur une chaîne de longueur nulle.  
  
> [!NOTE]
>  Si la zone de liste est une zone de liste déroulante, la valeur échangée est limitée à 255 caractères.  
  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdd_.h  
  
##  <a name="ddx_monthcalctrl"></a>  DDX_MonthCalCtrl  
 Le `DDX_MonthCalCtrl` fonction gère le transfert de données de date entre un contrôle month calendar ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) dans une boîte de dialogue, vue de formulaire, ou objet de vue de contrôle et soit un [CTime](../../atl-mfc-shared/reference/ctime-class.md) ou un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
```  
void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    CTime& value);

void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    COleDateTime& value);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction. Vous n’avez pas besoin de supprimer cet objet.  
  
 `nIDC`  
 L’ID de ressource de contrôle month calendar associé à la variable membre.  
  
 *valeur*  
 Une référence à un `CTime` ou `COleDateTime` variable membre de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Le contrôle gère la valeur de date uniquement. Les champs d’heure dans l’objet time sont ensemble pour refléter l’heure de création de la fenêtre de contrôle, ou quelque temps a été défini dans le contrôle avec un appel à `CMonthCalCtrl::SetCurSel`.  
  
 Lorsque `DDX_MonthCalCtrl` est appelée, *valeur* est définie sur l’état actuel du contrôle month calendar.  
  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdd_.h  
  
##  <a name="ddx_radio"></a>  DDX_Radio  
 Le `DDX_Radio` fonction gère le transfert de `int` des données entre un groupe de contrôles de case d’option dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un `int` membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle. La valeur de la `int` membre de données est déterminé selon les cases d’option est sélectionnée dans le groupe.  
  
```  
void AFXAPI DDX_Radio(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 L’ID de ressource du premier contrôle de case d’option dans le groupe.  
  
 *valeur*  
 Une référence à une variable membre de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Lorsque `DDX_Radio` est appelée, *valeur* est définie sur l’état actuel du groupe de contrôle de case d’option. La valeur est définie comme un index de base 0 du contrôle de case d’option qui est actuellement activé, ou -1 si aucun contrôle de case d’option sont vérifiées.  
  
 Par exemple, dans les cas où la première case dans le groupe est activée (le bouton avec les style WS_GROUP) la valeur de la `int` membre est 0 et ainsi de suite.  
  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdd_.h  
  
##  <a name="ddx_scroll"></a>  DDX_Scroll  
 Le `DDX_Scroll` fonction gère le transfert de `int` des données entre un contrôle de barre de défilement dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un `int` membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
```  
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 L’ID de ressource du contrôle de barre de défilement associé à la propriété du contrôle.  
  
 *valeur*  
 Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Lorsque `DDX_Scroll` est appelée, *valeur* est définie sur la position actuelle du curseur de défilement du contrôle. Pour plus d’informations sur les valeurs associées à la position actuelle du curseur de défilement du contrôle, consultez [GetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787585) dans le Kit de développement logiciel Windows.  
  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdd_.h  
  
##  <a name="ddx_slider"></a>  DDX_Slider  
 Le `DDX_Slider` fonction gère le transfert de `int` des données entre un contrôle slider dans un affichage de boîte de dialogue ou formulaire et un `int` membre de données de l’objet de vue de zone ou un formulaire de boîte de dialogue.  
  
```  
void AFXAPI DDX_Slider(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 L’ID de ressource du contrôle slider.  
  
 *valeur*  
 Une référence à la valeur à échanger. Ce paramètre conserve ou définit la position actuelle du contrôle slider.  
  
### <a name="remarks"></a>Notes  
 Lorsque `DDX_Slider` est appelée, *valeur* est définie sur la position actuelle du curseur de défilement du contrôle, ou la valeur reçoit la position, en fonction de la direction de l’échange.  
  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur les contrôles de curseur, consultez [à l’aide de CSliderCtrl](../../mfc/using-csliderctrl.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdd_.h  
  
##  <a name="ddx_text"></a>  DDX_Text  
 Le `DDX_Text` fonction gère le transfert de `int`, **UINT**, **long**, `DWORD`, `CString`, **float**, ou  **Double** des données entre un contrôle d’édition dans une boîte de dialogue mode formulaire ou vue de contrôle et un [CString](../../atl-mfc-shared/reference/cstringt-class.md) membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
```  
void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    BYTE& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    short& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    UINT& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    long& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    DWORD& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    float& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    double& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    COleCurrency& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    COleDateTime& value);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 L’ID d’un contrôle d’édition dans la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
 *valeur*  
 Une référence à un membre de données dans la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle. Type de données de *valeur* dépend des versions surchargées de `DDX_Text` vous utilisez.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  

### <a name="requirements"></a>Spécifications  
  **En-tête** afxdd_.h  

## <a name="see-also"></a>Voir aussi  
 [Routines de Validation de données de boîte de dialogue standard](../../mfc/reference/standard-dialog-data-validation-routines.md)   
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
