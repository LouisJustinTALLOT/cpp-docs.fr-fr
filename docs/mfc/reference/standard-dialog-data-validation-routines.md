---
title: Routines de validation des données de boîte de dialogue standard
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: 83e3e215ec8d66321bbac5a4a308b04ef69dc68c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372905"
---
# <a name="standard-dialog-data-validation-routines"></a>Routines de validation des données de boîte de dialogue standard

Ce sujet répertorie les routines standard de validation des données de dialogue (DDV) utilisées pour les contrôles courants de dialogue MFC.

> [!NOTE]
> Les routines standard d’échange de données de dialogue sont définies dans le fichier d’en-tête afxdd_.h. Toutefois, les applications doivent inclure afxwin.h.

### <a name="ddv-functions"></a>Fonctions DDV

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|Vérifie que le nombre de caractères dans une valeur de contrôle donnée ne dépasse pas un maximum donné.|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une plage **BYTE** donnée.|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une plage de temps donnée.|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une **double** plage donnée.|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une plage **DWORD** donnée.|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|Vérifie qu’une valeur de commande donnée ne dépasse pas une plage **de flotteur** donnée.|
|[DDV_MinMaxInt](#ddv_minmaxint)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une plage **d’int** donnée.|
|[DDV_MinMaxLong](#ddv_minmaxlong)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une **longue** portée donnée.|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une plage **LONGLONG** donnée.|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas la plage de date donnée.|
|[DDV_MinMaxShort](#ddv_minmaxshort)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une **courte** portée donnée.|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|Vérifie qu’une valeur de contrôle de curseur donnée se situe dans la plage donnée.|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une plage **UINT** donnée.|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|Vérifie qu’une valeur de contrôle donnée se situe entre deux valeurs spécifiées.|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une plage **ULONGLONG** donnée.|

## <a name="ddv_maxchars"></a><a name="ddv_maxchars"></a>DDV_MaxChars

Appelez `DDV_MaxChars` pour vérifier que la quantité de caractères dans le contrôle associé à la *valeur* ne dépasse pas *nChars*.

```cpp
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont validées.

*nChars (nChars)*<br/>
Nombre maximum de caractères autorisés.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddv_minmaxbyte"></a><a name="ddv_minmaxbyte"></a>DDV_MinMaxByte

Appelez `DDV_MinMaxByte` pour vérifier que la valeur dans le contrôle associé à la *valeur* tombe entre *minVal* et *maxVal*.

```cpp
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,
    BYTE value,
    BYTE minVal,
    BYTE maxVal);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont validées.

*minVal (en)*<br/>
Valeur minimale (de type BYTE) autorisée.

*maxVal (en)*<br/>
Valeur maximale (de type BYTE) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddv_minmaxdatetime"></a><a name="ddv_minmaxdatetime"></a>DDV_MinMaxDateTime

Appelez `DDV_MinMaxDateTime` pour vérifier que la valeur d’heure/date dans le contrôle de la date et de l’heure de cueilleur ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) associée à *refValue* tombe entre *refMinRange* et *refMaxRange*.

```cpp
void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction. Vous n’avez pas besoin de supprimer cet objet.

*refValue*<br/>
Une référence à un objet [CTime](../../atl-mfc-shared/reference/ctime-class.md) ou [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) associé à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de commande. Cet objet contient les données à valider.

*refMinRange*<br/>
Date minimale/valeur temporelle autorisée.

*refMaxRange*<br/>
Date maximale/valeur temporelle autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddv_minmaxdouble"></a><a name="ddv_minmaxdouble"></a>DDV_MinMaxDouble

Appelez `DDV_MinMaxDouble` pour vérifier que la valeur dans le contrôle associé à la *valeur* tombe entre *minVal* et *maxVal*.

```cpp
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,
    double const& value,
    double minVal,
    double maxVal);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont validées.

*minVal (en)*<br/>
Valeur minimale (de type **double**) autorisée.

*maxVal (en)*<br/>
Valeur maximale (de type **double**) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddv_minmaxdword"></a><a name="ddv_minmaxdword"></a>DDV_MinMaxDWord

Appelez `DDV_MinMaxDWord` pour vérifier que la valeur dans le contrôle associé à la *valeur* tombe entre *minVal* et *maxVal*.

```cpp
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,
    DWORD const& value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont validées.

*minVal (en)*<br/>
Valeur minimale (de type DWORD) autorisée.

*maxVal (en)*<br/>
Valeur maximale (de type DWORD) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddv_minmaxfloat"></a><a name="ddv_minmaxfloat"></a>DDV_MinMaxFloat

Appelez `DDV_MinMaxFloat` pour vérifier que la valeur dans le contrôle associé à la *valeur* tombe entre *minVal* et *maxVal*.

```cpp
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,
    float value,
    float minVal,
    float maxVal);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont validées.

*minVal (en)*<br/>
Valeur minimale (de type **flotteur**) autorisée.

*maxVal (en)*<br/>
Valeur maximale (de type **flotteur**) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddv_minmaxint"></a><a name="ddv_minmaxint"></a>DDV_MinMaxInt

Appelez `DDV_MinMaxInt` pour vérifier que la valeur dans le contrôle associé à la *valeur* tombe entre *minVal* et *maxVal*.

```cpp
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,
    int value,
    int minVal,
    int maxVal);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont validées.

*minVal (en)*<br/>
Valeur minimale (de type **int**) autorisée.

*maxVal (en)*<br/>
Valeur maximale (de type **int**) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddv_minmaxlong"></a><a name="ddv_minmaxlong"></a>DDV_MinMaxLong

Appelez `DDV_MinMaxLong` pour vérifier que la valeur dans le contrôle associé à la *valeur* tombe entre *minVal* et *maxVal*.

```cpp
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,
    long value,
    long minVal,
    long maxVal);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont validées.

*minVal (en)*<br/>
Valeur minimale (de type **long)** autorisée.

*maxVal (en)*<br/>
Valeur maximale (de type **long)** autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddv_minmaxlonglong"></a><a name="ddv_minmaxlonglong"></a>DDV_MinMaxLongLong

Appelez `DDV_MinMaxLongLong` pour vérifier que la valeur dans le contrôle associé à la *valeur* tombe entre *minVal* et *maxVal*.

```cpp
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,
    LONGLONG value,
    LONGLONG minVal,
    LONGLONG maxVal);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont validées.

*minVal (en)*<br/>
Valeur minimale (de type LONGLONG) autorisée.

*maxVal (en)*<br/>
Valeur maximale (de type LONGLONG) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddv_minmaxmonth"></a><a name="ddv_minmaxmonth"></a>DDV_MinMaxMonth

Appelez `DDV_MinMaxMonth` pour vérifier que la valeur d’heure/date dans le contrôle de calendrier du mois ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) associée à *refValue* tombe entre *refMinRange* et *refMaxRange*.

```cpp
void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*refValue*<br/>
Une référence à un `CTime` `COleDateTime` objet de type ou associé à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de commande. Cet objet contient les données à valider. MFC passe cette `DDV_MinMaxMonth` référence lorsqu’on l’appelle.

*refMinRange*<br/>
Date minimale/valeur temporelle autorisée.

*refMaxRange*<br/>
Date maximale/valeur temporelle autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddv_minmaxshort"></a><a name="ddv_minmaxshort"></a>DDV_MinMaxShort

Appelez `DDV_MinMaxShort` pour vérifier que la valeur dans le contrôle associé à la *valeur* tombe entre *minVal* et *maxVal*.

```cpp
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,
    short value,
    short minVal,
    short maxVal);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont validées.

*minVal (en)*<br/>
Valeur minimale (de type **court**) autorisée.

*maxVal (en)*<br/>
Valeur maximale (de type **court**) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddv_minmaxslider"></a><a name="ddv_minmaxslider"></a>DDV_MinMaxSlider

Appelez `DDV_MinMaxSlider` pour vérifier que la valeur dans le contrôle associé à la *valeur* tombe entre *minVal* et *maxVal*.

```cpp
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md) L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Une référence à la valeur à valider. Ce paramètre maintient ou définit la position actuelle du pouce du contrôle du curseur.

*minVal (en)*<br/>
Valeur minimale autorisée.

*maxVal (en)*<br/>
Valeur maximale autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur les commandes de curseurs, voir [à l’aide de CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddv_minmaxuint"></a><a name="ddv_minmaxuint"></a>DDV_MinMaxUInt

Appelez `DDV_MinMaxUInt` pour vérifier que la valeur dans le contrôle associé à la *valeur* tombe entre *minVal* et *maxVal*.

```cpp
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,
    UINT value,
    UINT minVal,
    UINT maxVal);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont validées.

*minVal (en)*<br/>
Valeur minimale (de type UINT) autorisée.

*maxVal (en)*<br/>
Valeur maximale (de type UINT) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddv_minmaxulonglong"></a><a name="ddv_minmaxulonglong"></a>DDV_MinMaxULongLong

Appelez `DDV_MinMaxULongLong` pour vérifier que la valeur dans le contrôle associé à la *valeur* tombe entre *minVal* et *maxVal*.

```cpp
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,
    ULONGLONG value,
    ULONGLONG  minVal ,
    ULONGLONG  maxVal);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont validées.

*minVal (en)*<br/>
Valeur minimale (de type ULONGLONG) autorisée.

*maxVal (en)*<br/>
Valeur maximale (de type ULONGLONG) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, voir [Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_.h

## <a name="ddv_minmaxunsigned"></a>DDV_MinMaxUnsigned

Appelez `DDV_MinMaxUnsigned` pour vérifier que la valeur dans le contrôle associé à la *valeur* tombe entre *minVal* et *maxVal*.

### <a name="syntax"></a>Syntaxe

```cpp
   void AFXAPI DDV_MinMaxUnsigned(
       CDataExchange* pDX,
       unsigned value,
       unsigned minVal,
       unsigned maxVal );
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Une référence à une variable de membre de la boîte de dialogue, la vue de forme, ou l’objet de vue de contrôle avec lequel les données sont validées.

*minVal (en)*<br/>
Valeur minimale (de type **non signé)** autorisée.

*maxVal (en)*<br/>
Valeur maximale (de type **non signé)** autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, voir [Dialog Data Exchange and Validation](../dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdd_.h

## <a name="see-also"></a>Voir aussi

[Routines d’échange de données de boîte de dialogue standard](standard-dialog-data-exchange-routines.md)<br/>
[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
