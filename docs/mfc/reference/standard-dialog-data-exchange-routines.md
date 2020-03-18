---
title: Routines d'échange de données de boîte de dialogue standard
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 47586f9cff0fcbe2cd7bad31f3d93fed08190830
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421225"
---
# <a name="standard-dialog-data-exchange-routines"></a>Routines d'échange de données de boîte de dialogue standard

Cette rubrique répertorie les routines d’échange de données de boîte de dialogue standard (DDX) utilisées pour les contrôles de boîte de dialogue MFC courants.

> [!NOTE]
>  Les routines d’échange de données de boîte de dialogue standard sont définies dans le fichier d’en-tête afxdd_. h. Toutefois, les applications doivent inclure AFXWIN. h.

### <a name="ddx-functions"></a>Fonctions DDX

|||
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|Initialise ou récupère l’index de la sélection actuelle d’un contrôle zone de liste déroulante.|
|[DDX_CBString](#ddx_cbstring)|Initialise ou récupère le contenu actuel du champ d’édition d’un contrôle zone de liste déroulante.|
|[DDX_CBStringExact](#ddx_cbstringexact)|Initialise ou récupère le contenu actuel du champ d’édition d’un contrôle zone de liste déroulante.|
|[DDX_Check](#ddx_check)|Initialise ou récupère l’état actuel d’un contrôle de case à cocher.|
|[DDX_Control](#ddx_control)|Sous-classe un contrôle donné dans une boîte de dialogue.|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|Initialise ou récupère les données de date et/ou d’heure d’un contrôle de sélecteur de date et d’heure.|
|[DDX_IPAddress](#ddx_ipaddress)|Initialise ou récupère la valeur actuelle d’un contrôle d’adresse IP.|
|[DDX_LBIndex](#ddx_lbindex)|Initialise ou récupère l’index de la sélection actuelle d’un contrôle de zone de liste.|
|[DDX_LBString](#ddx_lbstring)|Initialise ou récupère la sélection actuelle dans un contrôle de zone de liste.|
|[DDX_LBStringExact](#ddx_lbstringexact)|Initialise ou récupère la sélection actuelle dans un contrôle de zone de liste.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Crée un contrôle .NET correspondant à l’ID de ressource du contrôle.|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Initialise ou récupère la valeur actuelle d’un contrôle Month Calendar.|
|[DDX_Radio](#ddx_radio)|Initialise ou récupère l’index de base 0 du contrôle radio actuellement vérifié dans un groupe de contrôle radio.|
|[DDX_Scroll](#ddx_scroll)|Initialise ou récupère la position actuelle du curseur du contrôle Scroll.|
|[DDX_Slider](#ddx_slider)|Initialise ou récupère la position actuelle du curseur de défilement d’un contrôle Slider.|
|[DDX_Text](#ddx_text)|Initialise ou récupère la valeur actuelle d’un contrôle d’édition.|

##  <a name="ddx_cbindex"></a>DDX_CBIndex

La fonction `DDX_CBIndex` gère le transfert de données **int** entre un contrôle de zone de liste déroulante dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un membre de données **int** de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID de ressource du contrôle de zone de liste déroulante associé à la propriété de contrôle.

*index*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_CBIndex` est appelé, *index* est défini sur l’index de la sélection de zone de liste déroulante actuelle. Si aucun élément n’est sélectionné, *index* a la valeur 0.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

##  <a name="ddx_cbstring"></a>DDX_CBString

La fonction `DDX_CBString` gère le transfert de données `CString` entre le contrôle d’édition d’un contrôle de zone de liste déroulante dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un `CString` membre de données de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID de ressource du contrôle de zone de liste déroulante associé à la propriété de contrôle.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_CBString` est appelé, la *valeur* est définie sur la sélection de la zone de liste déroulante actuelle. Si aucun élément n’est sélectionné, la *valeur* est définie sur une chaîne de longueur nulle.

> [!NOTE]
>  Si la zone de liste déroulante est une zone de liste déroulante, la valeur échangée est limitée à 255 caractères.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

##  <a name="ddx_cbstringexact"></a>DDX_CBStringExact

La fonction `DDX_CBStringExact` gère le transfert de données `CString` entre le contrôle d’édition d’un contrôle de zone de liste déroulante dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un `CString` membre de données de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID de ressource du contrôle de zone de liste déroulante associé à la propriété de contrôle.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_CBStringExact` est appelé, la *valeur* est définie sur la sélection de la zone de liste déroulante actuelle. Si aucun élément n’est sélectionné, la *valeur* est définie sur une chaîne de longueur nulle.

> [!NOTE]
>  Si la zone de liste déroulante est une zone de liste déroulante, la valeur échangée est limitée à 255 caractères.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

##  <a name="ddx_check"></a>DDX_Check

La fonction `DDX_Check` gère le transfert de données **int** entre un contrôle de case à cocher dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un membre de données **int** de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID de ressource du contrôle de case à cocher associé à la propriété de contrôle.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_Check` est appelé, la *valeur* est définie sur l’état actuel du contrôle de case à cocher. Pour obtenir la liste des valeurs d’État possibles, consultez [BM_GETCHECK](/windows/win32/Controls/bm-getcheck) dans le SDK Windows.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

##  <a name="ddx_control"></a>DDX_Control

La fonction `DDX_Control` sous-classe le contrôle, spécifié par *nIDC*, de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*nIDC*<br/>
ID de ressource du contrôle à sous-classé.

*rControl*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle associé au contrôle spécifié.

### <a name="remarks"></a>Notes

L’objet *pDX* est fourni par le Framework lorsque la fonction `DoDataExchange` est appelée. Par conséquent, `DDX_Control` doit être appelé uniquement dans votre remplacement de `DoDataExchange`.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

##  <a name="ddx_datetimectrl"></a>DDX_DateTimeCtrl

La fonction `DDX_DateTimeCtrl` gère le transfert de données de date et/ou d’heure entre un contrôle de sélecteur de date et d’heure ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) dans un objet de boîte de dialogue ou de mode formulaire et une donnée membre [ctime](../../atl-mfc-shared/reference/ctime-class.md) ou [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) de la boîte de dialogue ou de l’objet de vue de formulaire.

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
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction. Vous n’avez pas besoin de supprimer cet objet.

*nIDC*<br/>
ID de ressource du contrôle de sélecteur de date et heure associé à la variable membre.

*value*<br/>
Dans les deux premières versions, il s’agit d’une référence à une variable membre `CTime` ou `COleDateTime`, une boîte de dialogue, un mode formulaire ou un objet de vue de contrôle avec lequel les données sont échangées. Dans la troisième version, référence à un objet de vue de contrôle de membre de données `CString`.

### <a name="remarks"></a>Notes

Lorsque `DDX_DateTimeCtrl` est appelé, la *valeur* est définie sur l’état actuel du contrôle de sélecteur de date et d’heure, ou le contrôle est défini sur *value*, en fonction de la direction de l’échange.

Dans la troisième version ci-dessus, `DDX_DateTimeCtrl` gère le transfert de données `CString` entre un contrôle de date et d’heure et un membre de données [CString](../../atl-mfc-shared/reference/cstringt-class.md) de l’objet de vue de contrôle. La chaîne est mise en forme à l’aide des règles des paramètres régionaux actuels pour la mise en forme des dates et des heures.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="ddx_managedcontrol"></a>DDX_ManagedControl

Crée un contrôle .NET correspondant à l’ID de ressource du contrôle.

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
Pointeur vers un objet de [classe CDataExchange](cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID de ressource du contrôle associé à la propriété de contrôle.

*control*<br/>
Référence à un objet de [classe CWinFormsControl](cwinformscontrol-class.md) .

### <a name="remarks"></a>Notes

`DDX_ManagedControl` appelle [CWinFormsControl :: CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) pour créer un contrôle correspondant à l’ID de contrôle de ressource. Utilisez `DDX_ManagedControl` pour créer des contrôles à partir d’ID de ressource dans [CDialog :: OnInitDialog](cdialog-class.md#oninitdialog). Pour l’échange de données, vous n’avez pas besoin d’utiliser les fonctions DDX/DDV avec les contrôles Windows Forms.

Pour plus d’informations, consultez [Comment : effectuer une liaison de données DDX/DDV avec Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxwinforms. h

##  <a name="ddx_ipaddress"></a>DDX_IPAddress

La fonction `DDX_IPAddress` gère le transfert de données entre un contrôle d’adresse IP et un membre de données de l’objet de vue de contrôle.

```
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID de ressource du contrôle d’adresse IP associé à la propriété de contrôle.

*value*<br/>
Référence à la valeur DWORD contenant la valeur à quatre champs du contrôle d’adresse IP. Les champs sont remplis ou lus comme suit.

|Champ|Bits contenant la valeur du champ|
|-----------|-------------------------------------|
|3|de 0 à 7|
|2|de 8 à 15|
|1|16 à 23|
|0|24 à 31|

Utilisez la [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress) Win32 pour lire la valeur, ou utilisez [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress) pour remplir la valeur. Ces messages sont décrits dans le SDK Windows.

### <a name="remarks"></a>Notes

Lorsque `DDX_IPAddress` est appelé, la *valeur* est lue à partir du contrôle d’adresse IP ou la *valeur* est écrite dans le contrôle, en fonction de la direction de l’échange.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

##  <a name="ddx_lbindex"></a>DDX_LBIndex

La fonction `DDX_LBIndex` gère le transfert de données **int** entre un contrôle de zone de liste dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un membre de données **int** de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID de ressource du contrôle de zone de liste associé à la propriété de contrôle.

*index*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_LBIndex` est appelé, *index* est défini sur l’index de la sélection de la zone de liste actuelle. Si aucun élément n’est sélectionné, *index* a la valeur-1.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

##  <a name="ddx_lbstring"></a>DDX_LBString

La fonction `DDX_LBString` gère le transfert de données `CString` entre un contrôle de zone de liste dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un `CString` membre de données de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID de ressource du contrôle de zone de liste associé à la propriété de contrôle.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_LBString` est appelé pour transférer des données vers un contrôle de zone de liste, le premier élément du contrôle dont la *valeur* de début correspond à est sélectionné. (Pour qu’il corresponde à la totalité de l’élément plutôt qu’à un simple préfixe, utilisez [DDX_LBStringExact](#ddx_lbstringexact).) S’il n’y a aucune correspondance, aucun élément n’est sélectionné. La correspondance ne respecte pas la casse.

Lorsque `DDX_LBString` est appelé pour transférer des données à partir d’un contrôle de zone de liste, la *valeur* de la zone de liste actuelle est définie. Si aucun élément n’est sélectionné, la *valeur* est définie sur une chaîne de longueur nulle.

> [!NOTE]
>  Si la zone de liste est une zone de liste déroulante, la valeur échangée est limitée à 255 caractères.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

##  <a name="ddx_lbstringexact"></a>DDX_LBStringExact

La fonction `DDX_CBStringExact` gère le transfert de données `CString` entre le contrôle d’édition d’un contrôle de zone de liste dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un `CString` membre de données de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID de ressource du contrôle de zone de liste associé à la propriété de contrôle.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_LBStringExact` est appelé pour transférer des données vers un contrôle de zone de liste, le premier élément du contrôle qui correspond à la *valeur* est sélectionné. (Pour qu’il corresponde à un seul préfixe plutôt qu’à l’élément entier, utilisez [DDX_LBString](#ddx_lbstring).) S’il n’y a aucune correspondance, aucun élément n’est sélectionné. La correspondance ne respecte pas la casse.

Lorsque `DDX_CBStringExact` est appelé pour transférer des données à partir d’un contrôle de zone de liste, la *valeur* de la zone de liste actuelle est définie. Si aucun élément n’est sélectionné, la *valeur* est définie sur une chaîne de longueur nulle.

> [!NOTE]
>  Si la zone de liste est une zone de liste déroulante, la valeur échangée est limitée à 255 caractères.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

##  <a name="ddx_monthcalctrl"></a>DDX_MonthCalCtrl

La fonction `DDX_MonthCalCtrl` gère le transfert de données de date entre un contrôle Month Calendar ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) dans une boîte de dialogue, un mode formulaire ou un objet de vue de contrôle, ainsi qu’une donnée membre [ctime](../../atl-mfc-shared/reference/ctime-class.md) ou [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

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
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction. Vous n’avez pas besoin de supprimer cet objet.

*nIDC*<br/>
ID de ressource du contrôle Month Calendar associé à la variable membre.

*value*<br/>
Référence à une variable membre `CTime` ou `COleDateTime` de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

> [!NOTE]
>  Le contrôle gère une valeur de date uniquement. Les champs d’heure de l’objet heure sont définis pour refléter l’heure de création de la fenêtre de contrôle, ou l’heure à laquelle a été défini dans le contrôle avec un appel à `CMonthCalCtrl::SetCurSel`.

Lorsque `DDX_MonthCalCtrl` est appelé, la *valeur* est définie sur l’état actuel du contrôle Month Calendar.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

##  <a name="ddx_radio"></a>DDX_Radio

La fonction `DDX_Radio` gère le transfert de données **int** entre un groupe de contrôle radio dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un membre de données **int** de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle. La valeur du membre de données **int** est déterminée en fonction de la case d’option du groupe qui est sélectionnée.

```
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID de ressource du premier contrôle radio du groupe.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_Radio` est appelé, la *valeur* est définie sur l’état actuel du groupe de contrôle radio. La valeur est définie sous la forme d’un index de base 0 du contrôle radio actuellement activé, ou-1 si aucun contrôle radio n’est activé.

Par exemple, si la première case d’option du groupe est cochée (le bouton avec WS_GROUP style) la valeur du membre **int** est 0, et ainsi de suite.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

##  <a name="ddx_scroll"></a>DDX_Scroll

La fonction `DDX_Scroll` gère le transfert de données **int** entre un contrôle de barre de défilement dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un membre de données **int** de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID de ressource du contrôle de barre de défilement associé à la propriété de contrôle.

*value*<br/>
Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_Scroll` est appelé, la *valeur* est définie à la position actuelle du curseur de contrôle. Pour plus d’informations sur les valeurs associées à la position actuelle du curseur de contrôle, consultez [GetScrollPos](/windows/win32/api/winuser/nf-winuser-getscrollpos) dans le SDK Windows.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

##  <a name="ddx_slider"></a>DDX_Slider

La fonction `DDX_Slider` gère le transfert de données **int** entre un contrôle Slider dans une boîte de dialogue ou un mode formulaire et un membre de données **int** de la boîte de dialogue ou de l’objet de vue de formulaire.

```
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID de ressource du contrôle Slider.

*value*<br/>
Référence à la valeur à échanger. Ce paramètre contient ou définit la position actuelle du contrôle Slider.

### <a name="remarks"></a>Notes

Lorsque `DDX_Slider` est appelé, la *valeur* est définie à la position actuelle du curseur de contrôle, ou la valeur reçoit la position, selon la direction de l’échange.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur les contrôles Slider, consultez [utilisation de CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

##  <a name="ddx_text"></a>DDX_Text

La fonction `DDX_Text` gère le transfert de données **int**, **uint**, **long**, DWORD, `CString`, **float**ou **double** entre un contrôle d’édition dans une boîte de dialogue, un mode formulaire ou un affichage de contrôle et un membre de données [CString](../../atl-mfc-shared/reference/cstringt-class.md) de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

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
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle d’édition dans la boîte de dialogue, le mode formulaire ou l’objet de vue de contrôle.

*value*<br/>
Référence à un membre de données dans la boîte de dialogue, le mode formulaire ou l’objet de vue de contrôle. Le type de données de la *valeur* dépend de la version surchargée de `DDX_Text` que vous utilisez.

### <a name="remarks"></a>Notes

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="see-also"></a>Voir aussi

[Routines de validation des données de boîte de dialogue standard](standard-dialog-data-validation-routines.md)<br/>
[Macros et globales](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog :: OnInitDialog](cdialog-class.md#oninitdialog)
