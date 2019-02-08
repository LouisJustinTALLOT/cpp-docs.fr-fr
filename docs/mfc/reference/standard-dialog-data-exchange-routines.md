---
title: Routines d'échange de données de boîte de dialogue standard
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 374618aba297fb2c055ce02f93d0c7c93b38dc06
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850175"
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
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|Initialise ou récupère les données de date et/ou une heure d’un contrôle de sélecteur de date et d’heure.|
|[DDX_IPAddress](#ddx_ipaddress)|Initialise ou récupère la valeur actuelle d’un contrôle d’adresse IP.|
|[DDX_LBIndex](#ddx_lbindex)|Initialise ou récupère l’index de la sélection actuelle d’un contrôle de zone de liste.|
|[DDX_LBString](#ddx_lbstring)|Initialise ou récupère la sélection actuelle dans un contrôle de zone de liste.|
|[DDX_LBStringExact](#ddx_lbstringexact)|Initialise ou récupère la sélection actuelle dans un contrôle de zone de liste.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Crée un contrôle .NET mise en correspondance les ID de ressource. du contrôle|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Initialise ou récupère la valeur actuelle d’un contrôle month calendar.|
|[DDX_Radio](#ddx_radio)|Initialise ou récupère l’index de base 0 du contrôle de case d’option qui est actuellement activé dans un groupe de contrôle de case d’option.|
|[DDX_Scroll](#ddx_scroll)|Initialise ou récupère la position actuelle du curseur de défilement d’un contrôle de défilement.|
|[DDX_Slider](#ddx_slider)|Initialise ou récupère la position actuelle du curseur de défilement d’un contrôle slider.|
|[DDX_Text](#ddx_text)|Initialise ou récupère la valeur actuelle d’un contrôle d’édition.|

##  <a name="ddx_cbindex"></a>  DDX_CBIndex

Le `DDX_CBIndex` fonction gère le transfert de **int** des données entre un contrôle combo box dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un **int** membre de données de la boîte de dialogue, le mode formulaire ou le contrôle objet de vue.

```
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de ressource du contrôle de zone de liste déroulante associé à la propriété du contrôle.

*index*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_CBIndex` est appelée, *index* est définie à l’index de la sélection de zone de liste déroulante actuelle. Si aucun élément n’est sélectionné, *index* est définie sur 0.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

##  <a name="ddx_cbstring"></a>  DDX_CBString

Le `DDX_CBString` fonction gère le transfert de `CString` des données entre le contrôle d’édition d’un contrôle de zone de liste déroulante dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un `CString` membre de données de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle.

```
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de ressource du contrôle de zone de liste déroulante associé à la propriété du contrôle.

*value*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_CBString` est appelée, *valeur* est définie sur la sélection de zone de liste déroulante actuelle. Si aucun élément n’est sélectionné, *valeur* est définie sur une chaîne de longueur nulle.

> [!NOTE]
>  Si la zone de liste modifiable est une zone de liste déroulante, la valeur échangée est limitée à 255 caractères.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

##  <a name="ddx_cbstringexact"></a>  DDX_CBStringExact

Le `DDX_CBStringExact` fonction gère le transfert de `CString` des données entre le contrôle d’édition d’un contrôle de zone de liste déroulante dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un `CString` membre de données de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle.

```
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de ressource du contrôle de zone de liste déroulante associé à la propriété du contrôle.

*value*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_CBStringExact` est appelée, *valeur* est définie sur la sélection de zone de liste déroulante actuelle. Si aucun élément n’est sélectionné, *valeur* est définie sur une chaîne de longueur nulle.

> [!NOTE]
>  Si la zone de liste modifiable est une zone de liste déroulante, la valeur échangée est limitée à 255 caractères.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

##  <a name="ddx_check"></a>  DDX_Check

Le `DDX_Check` fonction gère le transfert de **int** des données entre un contrôle check box dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un **int** membre de données de la boîte de dialogue, le mode formulaire ou le contrôle objet de vue.

```
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de ressource du contrôle de case à cocher associé à la propriété du contrôle.

*value*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_Check` est appelée, *valeur* est définie sur l’état actuel du contrôle de case à cocher. Pour obtenir la liste des valeurs d’état possibles, consultez [BM_GETCHECK](/windows/desktop/Controls/bm-getcheck) dans le SDK Windows.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

##  <a name="ddx_control"></a>  DDX_Control

Le `DDX_Control` fonction sous-classes le contrôle spécifié par *nIDC*, de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle.

```
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*nIDC*<br/>
L’ID de ressource du contrôle à sous-classer.

*rControl*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle associée au contrôle spécifié.

### <a name="remarks"></a>Notes

Le *pDX* objet est fourni par le framework lorsque le `DoDataExchange` fonction est appelée. Par conséquent, `DDX_Control` doit uniquement être appelée dans la substitution de `DoDataExchange`.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

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

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction. Vous n’avez pas besoin de supprimer cet objet.

*nIDC*<br/>
L’ID de ressource du contrôle de sélecteur de date et l’heure associé à la variable de membre.

*value*<br/>
Dans les deux premières versions, une référence à un `CTime` ou `COleDateTime` membre variable, boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont échangées. Dans la troisième version, une référence à un `CString` objet de vue de données membre contrôle.

### <a name="remarks"></a>Notes

Lorsque `DDX_DateTimeCtrl` est appelée, *valeur* actuel a la valeur état de la date et de contrôle de sélecteur de temps ou le contrôle est défini sur *valeur*, selon la direction de l’échange.

Dans la troisième version ci-dessus, `DDX_DateTimeCtrl` gère le transfert de `CString` contrôle de données entre une date et heure et une [CString](../../atl-mfc-shared/reference/cstringt-class.md) membre de données de l’objet de vue de contrôle. La chaîne est mise en forme à l’aide des règles de paramètres régionaux actuels pour mettre en forme des dates et heures.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddx_managedcontrol"></a>  DDX_ManagedControl

Crée un contrôle .NET mise en correspondance les ID de ressource. du contrôle

### <a name="syntax"></a>Syntaxe

```
template <typename T>
void DDX_ManagedControl(
   CDataExchange* pDX,
   int nIDC,
   CWinFormsControl<T>& control );
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange (classe)](cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de ressource du contrôle associé à la propriété du contrôle.

*control*<br/>
Une référence à un [CWinFormsControl, classe](cwinformscontrol-class.md) objet.

### <a name="remarks"></a>Notes

`DDX_ManagedControl` appels [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) pour créer un contrôle correspondant à l’ID de contrôle de ressource. Utilisez `DDX_ManagedControl` pour créer des contrôles à partir de l’ID de ressource dans [CDialog::OnInitDialog](cdialog-class.md#oninitdialog). Échange de données, vous n’avez pas besoin d’utiliser les fonctions DDX/DDV avec les contrôles Windows Forms.

Pour plus d'informations, voir [Procédure : Liaison des données DDX/DDV avec Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxwinforms.h

##  <a name="ddx_ipaddress"></a>  DDX_IPAddress

Le `DDX_IPAddress` fonction gère le transfert de données entre un contrôle d’adresse IP et un membre de données de l’objet de vue de contrôle.

```
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de ressource du contrôle d’adresse IP associé à la propriété du contrôle.

*value*<br/>
Une référence à la valeur DWORD contenant la valeur de champ de quatre du contrôle d’adresse IP. Les champs sont remplis ou comme suits.

|Champ|Contenant la valeur du champ de bits|
|-----------|-------------------------------------|
|3|0 à 7|
|2|8 à 15|
|1|16 à 23|
|0|24 à 31|

Utiliser Win32 [IPM_GETADDRESS](/windows/desktop/Controls/ipm-getaddress) pour lire la valeur, ou utilisez [IPM_SETADDRESS](/windows/desktop/Controls/ipm-setaddress) pour remplir la valeur. Ces messages sont décrits dans le SDK Windows.

### <a name="remarks"></a>Notes

Lorsque `DDX_IPAddress` est appelée, *valeur* est soit en lecture à partir du contrôle de l’adresse IP, ou *valeur* est écrit dans le contrôle, selon la direction de l’échange.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

##  <a name="ddx_lbindex"></a>  DDX_LBIndex

Le `DDX_LBIndex` fonction gère le transfert de **int** des données entre un contrôle de zone de liste dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un **int** membre de données de la boîte de dialogue, le mode formulaire ou le contrôle objet de vue.

```
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de ressource du contrôle de zone de liste associé à la propriété du contrôle.

*index*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_LBIndex` est appelée, *index* est définie à l’index de la sélection de zone de liste actuel. Si aucun élément n’est sélectionné, *index* a la valeur -1.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

##  <a name="ddx_lbstring"></a>  DDX_LBString

Le `DDX_LBString` fonction gère le transfert de `CString` des données entre un contrôle de zone de liste dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un `CString` membre de données de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle.

```
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de ressource du contrôle de zone de liste associé à la propriété du contrôle.

*value*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_LBString` est appelée pour transférer des données vers un contrôle de zone de liste, le premier élément dans le contrôle dont le début correspond à *valeur* est sélectionné. (Pour faire correspondre l’élément entier plutôt que simplement un préfixe, utilisez [DDX_LBStringExact](#ddx_lbstringexact).) S’il n’y a aucune correspondance, aucun élément n’est sélectionnées. La mise en correspondance respecte la casse.

Lorsque `DDX_LBString` est appelée pour transférer des données à partir d’un contrôle de zone de liste, *valeur* est définie sur la sélection de la liste actuelle. Si aucun élément n’est sélectionné, *valeur* est définie sur une chaîne de longueur nulle.

> [!NOTE]
>  Si la zone de liste est une zone de liste déroulante, la valeur échangée est limitée à 255 caractères.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

##  <a name="ddx_lbstringexact"></a>  DDX_LBStringExact

Le `DDX_CBStringExact` fonction gère le transfert de `CString` des données entre le contrôle d’édition d’un contrôle de zone de liste dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un `CString` membre de données de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle.

```
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de ressource du contrôle de zone de liste associé à la propriété du contrôle.

*value*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_LBStringExact` est appelée pour transférer des données vers un contrôle de zone de liste, le premier élément dans le contrôle qui correspond à *valeur* est sélectionné. (Pour faire correspondre simplement un préfixe plutôt que l’élément entier, utilisez [DDX_LBString](#ddx_lbstring).) S’il n’y a aucune correspondance, aucun élément n’est sélectionnées. La mise en correspondance respecte la casse.

Lorsque `DDX_CBStringExact` est appelée pour transférer des données à partir d’un contrôle de zone de liste, *valeur* est définie sur la sélection de la liste actuelle. Si aucun élément n’est sélectionné, *valeur* est définie sur une chaîne de longueur nulle.

> [!NOTE]
>  Si la zone de liste est une zone de liste déroulante, la valeur échangée est limitée à 255 caractères.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

##  <a name="ddx_monthcalctrl"></a>  DDX_MonthCalCtrl

Le `DDX_MonthCalCtrl` fonction gère le transfert de données de date entre un contrôle month calendar ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) dans une boîte de dialogue, vue de formulaire, ou objet de vue de contrôle et soit un [CTime](../../atl-mfc-shared/reference/ctime-class.md) ou un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) membre de données de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle.

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

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction. Vous n’avez pas besoin de supprimer cet objet.

*nIDC*<br/>
L’ID de ressource de contrôle month calendar associé à la variable membre.

*value*<br/>
Une référence à un `CTime` ou `COleDateTime` variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

> [!NOTE]
>  Le contrôle gère uniquement une valeur de date. Les champs d’heure dans l’objet de temps sont ensemble afin de refléter l’heure de création de la fenêtre de contrôle, ou quelque temps a été défini dans le contrôle avec un appel à `CMonthCalCtrl::SetCurSel`.

Lorsque `DDX_MonthCalCtrl` est appelée, *valeur* est définie sur l’état actuel du contrôle month calendar.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

##  <a name="ddx_radio"></a>  DDX_Radio

Le `DDX_Radio` fonction gère le transfert de **int** des données entre un groupe de contrôle de case d’option dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un **int** membre de données de la boîte de dialogue, le mode formulaire ou le contrôle objet de vue. La valeur de la **int** membre de données est déterminé selon les cases d’option dans le groupe avec le bouton est sélectionné.

```
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de ressource du premier contrôle de case d’option dans le groupe.

*value*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_Radio` est appelée, *valeur* est définie sur l’état actuel du groupe de contrôle de case d’option. La valeur est définie comme un index de base 0 du contrôle de case d’option qui est actuellement activé, ou -1 si aucun contrôle de case d’option sont vérifiées.

Par exemple, dans les cas où le premier bouton de case d’option dans le groupe est activée (le bouton avec les style WS_GROUP) la valeur de la **int** membre est 0 et ainsi de suite.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

##  <a name="ddx_scroll"></a>  DDX_Scroll

Le `DDX_Scroll` fonction gère le transfert de **int** des données entre un contrôle de barre de défilement dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un **int** membre de données de la boîte de dialogue, le mode formulaire ou le contrôle objet de vue.

```
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de ressource du contrôle de barre de défilement associé à la propriété du contrôle.

*value*<br/>
Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_Scroll` est appelée, *valeur* est définie sur la position actuelle du curseur de défilement du contrôle. Pour plus d’informations sur les valeurs associées à la position actuelle du curseur de défilement du contrôle, consultez [GetScrollPos](/windows/desktop/api/winuser/nf-winuser-getscrollpos) dans le SDK Windows.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

##  <a name="ddx_slider"></a>  DDX_Slider

Le `DDX_Slider` fonction gère le transfert de **int** des données entre un contrôle slider dans une vue de formulaire ou de boîte de dialogue et un **int** membre de données de l’objet de vue de zone ou un formulaire de boîte de dialogue.

```
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de ressource du contrôle slider.

*value*<br/>
Une référence à la valeur à échanger. Ce paramètre contienne ou définit la position actuelle du contrôle slider.

### <a name="remarks"></a>Notes

Lorsque `DDX_Slider` est appelée, *valeur* est définie sur la position actuelle du curseur de défilement du contrôle, ou la valeur reçoit la position, selon la direction de l’échange.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur les contrôles de curseur, consultez [à l’aide de CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

##  <a name="ddx_text"></a>  DDX_Text

Le `DDX_Text` fonction gère le transfert de **int**, **UINT**, **long**, DWORD, `CString`, **float**, ou **double** des données entre un contrôle d’édition dans une boîte de dialogue, mode formulaire ou vue de contrôle et un [CString](../../atl-mfc-shared/reference/cstringt-class.md) membre de données de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle.

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

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID d’un contrôle d’édition dans la boîte de dialogue, vue de formulaire ou objet de vue de contrôle.

*value*<br/>
Une référence à un membre de données dans la boîte de dialogue, vue de formulaire ou objet de vue de contrôle. Le type de données de *valeur* varie en fonction des versions surchargées de `DDX_Text` vous utilisez.

### <a name="remarks"></a>Notes

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="see-also"></a>Voir aussi

[Routines de validation des données de boîte de dialogue standard](standard-dialog-data-validation-routines.md)<br/>
[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
