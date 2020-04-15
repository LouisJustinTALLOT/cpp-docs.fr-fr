---
title: Routines d'échange de données de boîte de dialogue standard
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 83d4a66cd3ec41008506b55f0b351fd9bcbc24b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372928"
---
# <a name="standard-dialog-data-exchange-routines"></a>Routines d'échange de données de boîte de dialogue standard

Ce sujet répertorie les routines standard d’échange de données de dialogue (DDX) utilisées pour les contrôles courants de dialogue MFC.

> [!NOTE]
> Les routines standard d’échange de données de dialogue sont définies dans le fichier d’en-tête afxdd_.h. Toutefois, les applications doivent inclure afxwin.h.

### <a name="ddx-functions"></a>Fonctions DDX

|||
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|Initialise ou récupère l’index de la sélection actuelle d’un contrôle de boîte combo.|
|[DDX_CBString](#ddx_cbstring)|Initialise ou récupère le contenu actuel du champ d’édition d’un contrôle de boîte combo.|
|[DDX_CBStringExact](#ddx_cbstringexact)|Initialise ou récupère le contenu actuel du champ d’édition d’un contrôle de boîte combo.|
|[DDX_Check](#ddx_check)|Initialise ou récupère l’état actuel d’un contrôle de la case à cocher.|
|[DDX_Control](#ddx_control)|Sous-classe un contrôle donné dans une boîte de dialogue.|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|Initialise ou récupère les données de date et/ou d’heure d’un contrôle de la date et de l’heure du cueilleur.|
|[DDX_IPAddress](#ddx_ipaddress)|Initialise ou récupère la valeur actuelle d’un contrôle d’adresse IP.|
|[DDX_LBIndex](#ddx_lbindex)|Initialise ou récupère l’index de la sélection actuelle d’un contrôle de boîte de liste.|
|[DDX_LBString](#ddx_lbstring)|Initialise ou récupère la sélection actuelle dans un contrôle de boîte de liste.|
|[DDX_LBStringExact](#ddx_lbstringexact)|Initialise ou récupère la sélection actuelle dans un contrôle de boîte de liste.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Crée un contrôle .NET correspondant à l’ID de ressources du contrôle.|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Initialise ou récupère la valeur actuelle d’un contrôle de calendrier de mois.|
|[DDX_Radio](#ddx_radio)|Initialise ou récupère l’index à 0 du contrôle radio qui est actuellement vérifié au sein d’un groupe de contrôle radio.|
|[DDX_Scroll](#ddx_scroll)|Initialise ou récupère la position actuelle du pouce d’un contrôle de défilement.|
|[DDX_Slider](#ddx_slider)|Initialise ou récupère la position actuelle du pouce d’un contrôle de curseur.|
|[DDX_Text](#ddx_text)|Initialise ou récupère la valeur actuelle d’un contrôle de modification.|

## <a name="ddx_cbindex"></a><a name="ddx_cbindex"></a>DDX_CBIndex

La `DDX_CBIndex` fonction gère le transfert de données **int** entre un contrôle de boîte combo dans une boîte de dialogue, une vue de forme ou un objet de vue de contrôle et un membre des données **int** de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID de ressource du contrôle de la boîte combo associé à la propriété de commande.

*index*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsqu’il `DDX_CBIndex` est appelé, *l’index* est réglé à l’index de la sélection actuelle de la boîte combo. Si aucun élément n’est sélectionné, *l’index* est réglé à 0.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddx_cbstring"></a><a name="ddx_cbstring"></a>DDX_CBString

La `DDX_CBString` fonction gère `CString` le transfert de données entre le contrôle de modification d’un contrôle de `CString` boîte de combo dans une boîte de dialogue, une vue de formulaire ou un objet de vue de contrôle et un membre de données de la boîte de dialogue, de la vue de forme ou de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID de ressource du contrôle de la boîte combo associé à la propriété de commande.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsqu’on `DDX_CBString` l’appelle, la *valeur* est définie à la sélection actuelle de la boîte combo. Si aucun élément n’est sélectionné, *la valeur* est réglée sur une chaîne de longueur zéro.

> [!NOTE]
> Si la boîte combo est une boîte de liste de décrochage, la valeur échangée est limitée à 255 caractères.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddx_cbstringexact"></a><a name="ddx_cbstringexact"></a>DDX_CBStringExact

La `DDX_CBStringExact` fonction gère `CString` le transfert de données entre le contrôle de modification d’un contrôle de `CString` boîte de combo dans une boîte de dialogue, une vue de formulaire ou un objet de vue de contrôle et un membre de données de la boîte de dialogue, de la vue de forme ou de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID de ressource du contrôle de la boîte combo associé à la propriété de commande.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsqu’on `DDX_CBStringExact` l’appelle, la *valeur* est définie à la sélection actuelle de la boîte combo. Si aucun élément n’est sélectionné, *la valeur* est réglée sur une chaîne de longueur zéro.

> [!NOTE]
> Si la boîte combo est une boîte de liste de décrochage, la valeur échangée est limitée à 255 caractères.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddx_check"></a><a name="ddx_check"></a>DDX_Check

La `DDX_Check` fonction gère le transfert de données **int** entre un contrôle de case à cocher dans une boîte de dialogue, une vue de formulaire ou un objet de vue de contrôle et un membre des données **int** de la boîte de dialogue, la vue de forme, ou l’objet de vue de commande.

```cpp
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID de ressource du contrôle de la case à cocher associé à la propriété de commande.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsqu’on `DDX_Check` l’appelle, la *valeur* est réglée à l’état actuel du contrôle de la case à cocher. Pour une liste des valeurs d’état possibles, voir [BM_GETCHECK](/windows/win32/Controls/bm-getcheck) dans le SDK Windows.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddx_control"></a><a name="ddx_control"></a>DDX_Control

La `DDX_Control` fonction sous-classe le contrôle, spécifié par *nIDC*, de la boîte de dialogue, la vue de forme, ou l’objet de vue de commande.

```cpp
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*nIDC (en)*<br/>
L’ID de ressource du contrôle à sous-classer.

*rControl (en)*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle lié au contrôle spécifié.

### <a name="remarks"></a>Notes

*L’objet pDX* est fourni `DoDataExchange` par le cadre lorsque la fonction est appelée. Par `DDX_Control` conséquent, ne devrait être `DoDataExchange`appelé dans votre remplacement de .

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddx_datetimectrl"></a><a name="ddx_datetimectrl"></a>DDX_DateTimeCtrl

La `DDX_DateTimeCtrl` fonction gère le transfert de données de date et/ou d’heure entre un contrôle de la date et de l’heure ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) dans une boîte de dialogue ou un objet de vue de formulaire et soit un [CTime](../../atl-mfc-shared/reference/ctime-class.md) ou un membre de données [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) de la boîte de dialogue ou de l’objet de vue de formulaire.

```cpp
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

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction. Vous n’avez pas besoin de supprimer cet objet.

*nIDC (en)*<br/>
L’ID de ressource de la date et du contrôle du cueilleur d’heure associés à la variable du membre.

*value*<br/>
Dans les deux premières versions, `CTime` `COleDateTime` une référence à une variable ou à un membre, une boîte de dialogue, une vue de formulaire ou un objet de vue de contrôle avec lesquels les données sont échangées. Dans la troisième version, `CString` une référence à un objet de contrôle de contrôle de membre de données.

### <a name="remarks"></a>Notes

Lorsqu’on `DDX_DateTimeCtrl` l’appelle, la *valeur* est réglée à l’état actuel du contrôle du cueilleur de date et d’heure, ou le contrôle est réglé pour *la valeur*, selon la direction de l’échange.

Dans la troisième `DDX_DateTimeCtrl` version ci-dessus, gère le transfert de données entre un contrôle de `CString` l’heure de date et un membre des données [CString](../../atl-mfc-shared/reference/cstringt-class.md) de l’objet de vue de contrôle. La chaîne est formatée en utilisant les règles de la localisation actuelle pour le formatage des dates et des heures.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddx_managedcontrol"></a><a name="ddx_managedcontrol"></a>DDX_ManagedControl

Crée un contrôle .NET correspondant à l’ID de ressources du contrôle.

### <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
void DDX_ManagedControl(
   CDataExchange* pDX,
   int nIDC,
   CWinFormsControl<T>& control );
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur vers un objet [de classe CDataExchange.](cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID de ressource du contrôle associé à la propriété de commande.

*Contrôle*<br/>
Une référence à un objet [de classe CWinFormsControl.](cwinformscontrol-class.md)

### <a name="remarks"></a>Notes

`DDX_ManagedControl`appelle [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) pour créer un contrôle correspondant à l’ID de contrôle des ressources. Utiliser `DDX_ManagedControl` pour créer des contrôles à partir de ressources IDs dans [CDialog::OnInitDialog](cdialog-class.md#oninitdialog). Pour l’échange de données, vous n’avez pas besoin d’utiliser les fonctions DDX/DDV avec les commandes Windows Forms.

Pour plus d’informations, voir [Comment : Ne DDX/DDV Data Binding with Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

### <a name="requirements"></a>Spécifications

**En-tête:** afxwinforms.h

## <a name="ddx_ipaddress"></a><a name="ddx_ipaddress"></a>DDX_IPAddress

La `DDX_IPAddress` fonction gère le transfert de données entre un contrôle d’adresse IP et un membre des données de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID de ressource du contrôle d’adresse IP associé à la propriété de commande.

*value*<br/>
Une référence au DWORD contenant la valeur à quatre champs du contrôle de l’adresse IP. Les champs sont remplis ou lus comme suit.

|Champ|Bits contenant la valeur du champ|
|-----------|-------------------------------------|
|3|0 à 7|
|2|8 à 15 ans|
|1|16 à 23 ans|
|0|24 à 31 ans|

Utilisez le [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress) Win32 pour lire la valeur, ou utilisez [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress) pour remplir la valeur. Ces messages sont décrits dans le Windows SDK.

### <a name="remarks"></a>Notes

Lorsqu’on `DDX_IPAddress` l’appelle, la *valeur* est soit lue à partir du contrôle de l’adresse IP, soit la *valeur* est écrite au contrôle, selon la direction de l’échange.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddx_lbindex"></a><a name="ddx_lbindex"></a>DDX_LBIndex

La `DDX_LBIndex` fonction gère le transfert de données **int** entre un contrôle de boîte de liste dans une boîte de dialogue, une vue de formulaire ou un objet de vue de contrôle et un membre des données **int** de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID de ressource du contrôle de la boîte de liste associé à la propriété de commande.

*index*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsqu’on `DDX_LBIndex` l’appelle, *l’index* est réglé à l’index de la sélection actuelle de la boîte de liste. Si aucun élément n’est sélectionné, *l’index* est réglé à -1.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddx_lbstring"></a><a name="ddx_lbstring"></a>DDX_LBString

La `DDX_LBString` fonction gère `CString` le transfert de données entre un contrôle de boîte de liste `CString` dans une boîte de dialogue, une vue de formulaire ou un objet de vue de contrôle et un membre de données de la boîte de dialogue, de la vue de formulaire ou de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID de ressource du contrôle de la boîte de liste associé à la propriété de commande.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsqu’il `DDX_LBString` est appelé à transférer des données à un contrôle de boîte de liste, le premier élément dans le contrôle dont la *valeur* de début correspond est sélectionnée. (Pour correspondre à l’élément entier plutôt qu’à un simple préfixe, utilisez [DDX_LBStringExact.)](#ddx_lbstringexact) S’il n’y a pas d’allumettes, aucun élément n’est sélectionné. L’appariement est insensible aux cas.

Lorsqu’on `DDX_LBString` appelle pour transférer des données à partir d’un contrôle de boîte de liste, la *valeur* est définie à la sélection actuelle de la boîte de liste. Si aucun élément n’est sélectionné, *la valeur* est réglée sur une chaîne de longueur zéro.

> [!NOTE]
> Si la boîte de liste est une boîte de liste de décrochage, la valeur échangée est limitée à 255 caractères.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddx_lbstringexact"></a><a name="ddx_lbstringexact"></a>DDX_LBStringExact

La `DDX_CBStringExact` fonction gère `CString` le transfert de données entre le contrôle de modification d’un contrôle de `CString` boîte de liste dans une boîte de dialogue, une vue de formulaire ou un objet de vue de contrôle et un membre des données de la boîte de dialogue, de la vue de forme ou de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID de ressource du contrôle de la boîte de liste associé à la propriété de commande.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsqu’on `DDX_LBStringExact` appelle pour transférer des données à un contrôle de boîte de liste, le premier élément dans le contrôle qui correspond à la *valeur* est sélectionné. (Pour correspondre à juste un préfixe plutôt que l’élément entier, utilisez [DDX_LBString](#ddx_lbstring).) S’il n’y a pas d’allumettes, aucun élément n’est sélectionné. L’appariement est insensible aux cas.

Lorsqu’on `DDX_CBStringExact` appelle pour transférer des données à partir d’un contrôle de boîte de liste, la *valeur* est définie à la sélection actuelle de la boîte de liste. Si aucun élément n’est sélectionné, *la valeur* est réglée sur une chaîne de longueur zéro.

> [!NOTE]
> Si la boîte de liste est une boîte de liste de décrochage, la valeur échangée est limitée à 255 caractères.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddx_monthcalctrl"></a><a name="ddx_monthcalctrl"></a>DDX_MonthCalCtrl

La `DDX_MonthCalCtrl` fonction gère le transfert de données de date entre un contrôle de calendrier de mois ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) dans une boîte de dialogue, une vue de formulaire ou un objet de vue de contrôle et soit un [CTime](../../atl-mfc-shared/reference/ctime-class.md) ou un membre de données [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) de la boîte de dialogue, une vue de forme ou un objet de vue de contrôle.

```cpp
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

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction. Vous n’avez pas besoin de supprimer cet objet.

*nIDC (en)*<br/>
L’ID de ressources du contrôle du calendrier du mois associé à la variable du membre.

*value*<br/>
Une référence `CTime` à `COleDateTime` une variable ou à une variable de membre de la boîte de dialogue, de la vue de forme ou de l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

> [!NOTE]
> Le contrôle gère une valeur de date seulement. Les champs de temps dans l’objet de temps sont réglés pour refléter le temps `CMonthCalCtrl::SetCurSel`de création de la fenêtre de contrôle, ou quel que soit le temps a été fixé dans le contrôle avec un appel à .

Lorsqu’on `DDX_MonthCalCtrl` l’appelle, la *valeur* est définie à l’état actuel du contrôle du calendrier du mois.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddx_radio"></a><a name="ddx_radio"></a>DDX_Radio

La `DDX_Radio` fonction gère le transfert de données **int** entre un groupe de contrôle radio dans une boîte de dialogue, une vue de formulaire ou un objet de vue de contrôle et un membre des données **int** de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle. La valeur du membre des données **int** est déterminée en fonction du bouton radio du groupe sélectionné.

```cpp
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID de ressource du premier contrôle radio du groupe.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsqu’on `DDX_Radio` l’appelle, la *valeur* est réglée à l’état actuel du groupe de contrôle radio. La valeur est définie comme un index à 0 du contrôle radio qui est actuellement vérifié, ou -1 si aucune commande radio n’est vérifiée.

Par exemple, au cas où le premier bouton radio du groupe est vérifié (le bouton avec WS_GROUP style) la valeur du membre **int** est de 0 et ainsi de suite.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddx_scroll"></a><a name="ddx_scroll"></a>DDX_Scroll

La `DDX_Scroll` fonction gère le transfert de données **int** entre un contrôle de barre de défilement dans une boîte de dialogue, une vue de formulaire ou un objet de vue de contrôle et un membre des données **int** de la boîte de dialogue, la vue de forme, ou l’objet de vue de commande.

```cpp
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID de ressource du contrôle de la barre de défilement associé à la propriété de commande.

*value*<br/>
Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsqu’on `DDX_Scroll` l’appelle, la *valeur* est réglée à la position actuelle du pouce du contrôle. Pour plus d’informations sur les valeurs associées à la position actuelle du pouce du contrôleur, voir [GetScrollPos](/windows/win32/api/winuser/nf-winuser-getscrollpos) dans le SDK Windows.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddx_slider"></a><a name="ddx_slider"></a>DDX_Slider

La `DDX_Slider` fonction gère le transfert de données **int** entre un contrôle de curseur dans une boîte de dialogue ou une vue de forme et un membre des données **int** de la boîte de dialogue ou de l’objet de vue de forme.

```cpp
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID de ressource du contrôle du curseur.

*value*<br/>
Une référence à la valeur à échanger. Ce paramètre maintient ou définit la position actuelle du contrôle du curseur.

### <a name="remarks"></a>Notes

Lorsqu’on `DDX_Slider` l’appelle, la *valeur* est réglée à la position actuelle du pouce du contrôle, ou la valeur reçoit la position, selon la direction de l’échange.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur les commandes de curseurs, voir [à l’aide de CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddx_text"></a><a name="ddx_text"></a>DDX_Text

La `DDX_Text` fonction gère le transfert de **l’int** `CString`, **UINT**, **long**, DWORD, , **flotteur**, ou **double** données entre un contrôle de modification dans une boîte de dialogue, vue de forme, ou vue de contrôle et un membre de données [CString](../../atl-mfc-shared/reference/cstringt-class.md) de la boîte de dialogue, vue de forme, ou objet de vue de contrôle.

```cpp
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

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC (en)*<br/>
L’ID d’un contrôle de modification dans la boîte de dialogue, la vue de forme, ou l’objet de vue de commande.

*value*<br/>
Une référence à un membre de données dans la boîte de dialogue, la vue de forme, ou l’objet de vue de commande. Le type de *valeur* de données dépend de `DDX_Text` laquelle des versions surchargées de votre utilisation.

### <a name="remarks"></a>Notes

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="see-also"></a>Voir aussi

[Routines standard de validation des données de dialogue](standard-dialog-data-validation-routines.md)<br/>
[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
