---
title: Routines de validation des données de boîte de dialogue standard
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: 2511e2ec6dbd4e27c0e12e35bdc1cd671bf72eaa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213981"
---
# <a name="standard-dialog-data-validation-routines"></a>Routines de validation des données de boîte de dialogue standard

Cette rubrique répertorie les routines de validation de données de boîte de dialogue standard (DDV) utilisées pour les contrôles de boîte de dialogue MFC courants.

> [!NOTE]
> Les routines d’échange de données de boîte de dialogue standard sont définies dans le fichier d’en-tête afxdd_. h. Toutefois, les applications doivent inclure AFXWIN. h.

### <a name="ddv-functions"></a>Fonctions DDV

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|Vérifie que le nombre de caractères dans une valeur de contrôle donnée ne dépasse pas un maximum donné.|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une plage d' **octets** donnée.|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une plage de temps donnée.|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une **`double`** plage donnée.|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une plage **DWORD** donnée.|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une **`float`** plage donnée.|
|[DDV_MinMaxInt](#ddv_minmaxint)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une **`int`** plage donnée.|
|[DDV_MinMaxLong](#ddv_minmaxlong)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une **`long`** plage donnée.|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une plage de **LongLong** donnée.|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une plage de dates donnée.|
|[DDV_MinMaxShort](#ddv_minmaxshort)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une **`short`** plage donnée.|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|Vérifie si une valeur de contrôle Slider donnée est comprise dans la plage donnée.|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une plage **uint** donnée.|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|Vérifie si une valeur de contrôle donnée est comprise entre deux valeurs spécifiées.|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|Vérifie qu’une valeur de contrôle donnée ne dépasse pas une plage de **ULONGLONG** donnée.|

## <a name="ddv_maxchars"></a><a name="ddv_maxchars"></a>DDV_MaxChars

Appelez `DDV_MaxChars` pour vérifier que la quantité de caractères dans le contrôle associé à *value* ne dépasse pas *nChars*.

```cpp
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont validées.

*nChars*<br/>
Nombre maximal de caractères autorisés.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="ddv_minmaxbyte"></a><a name="ddv_minmaxbyte"></a>DDV_MinMaxByte

Appelez `DDV_MinMaxByte` pour vérifier que la valeur du contrôle associé à *value* est comprise entre *minVal* et *MaxVal*.

```cpp
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,
    BYTE value,
    BYTE minVal,
    BYTE maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
La valeur minimale (de type BYTE) est autorisée.

*maxVal*<br/>
Valeur maximale (de type BYTE) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="ddv_minmaxdatetime"></a><a name="ddv_minmaxdatetime"></a>DDV_MinMaxDateTime

Appelez `DDV_MinMaxDateTime` pour vérifier que la valeur de date/heure dans le contrôle de sélecteur de date et heure ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) associé à *refValue* est comprise entre *refMinRange* et *refMaxRange*.

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

*pDX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction. Vous n’avez pas besoin de supprimer cet objet.

*refValue*<br/>
Référence à un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) ou [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) associé à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle. Cet objet contient les données à valider.

*refMinRange*<br/>
Valeur de date/heure minimale autorisée.

*refMaxRange*<br/>
Valeur de date/heure maximale autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="ddv_minmaxdouble"></a><a name="ddv_minmaxdouble"></a>DDV_MinMaxDouble

Appelez `DDV_MinMaxDouble` pour vérifier que la valeur du contrôle associé à *value* est comprise entre *minVal* et *MaxVal*.

```cpp
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,
    double const& value,
    double minVal,
    double maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale autorisée (de type **`double`** ).

*maxVal*<br/>
Valeur maximale autorisée (de type **`double`** ).

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="ddv_minmaxdword"></a><a name="ddv_minmaxdword"></a>DDV_MinMaxDWord

Appelez `DDV_MinMaxDWord` pour vérifier que la valeur du contrôle associé à *value* est comprise entre *minVal* et *MaxVal*.

```cpp
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,
    DWORD const& value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
La valeur minimale (de type DWORD) est autorisée.

*maxVal*<br/>
Valeur maximale autorisée (de type DWORD).

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="ddv_minmaxfloat"></a><a name="ddv_minmaxfloat"></a>DDV_MinMaxFloat

Appelez `DDV_MinMaxFloat` pour vérifier que la valeur du contrôle associé à *value* est comprise entre *minVal* et *MaxVal*.

```cpp
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,
    float value,
    float minVal,
    float maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale autorisée (de type **`float`** ).

*maxVal*<br/>
Valeur maximale autorisée (de type **`float`** ).

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="ddv_minmaxint"></a><a name="ddv_minmaxint"></a>DDV_MinMaxInt

Appelez `DDV_MinMaxInt` pour vérifier que la valeur du contrôle associé à *value* est comprise entre *minVal* et *MaxVal*.

```cpp
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,
    int value,
    int minVal,
    int maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale autorisée (de type **`int`** ).

*maxVal*<br/>
Valeur maximale autorisée (de type **`int`** ).

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="ddv_minmaxlong"></a><a name="ddv_minmaxlong"></a>DDV_MinMaxLong

Appelez `DDV_MinMaxLong` pour vérifier que la valeur du contrôle associé à *value* est comprise entre *minVal* et *MaxVal*.

```cpp
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,
    long value,
    long minVal,
    long maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale autorisée (de type **`long`** ).

*maxVal*<br/>
Valeur maximale autorisée (de type **`long`** ).

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="ddv_minmaxlonglong"></a><a name="ddv_minmaxlonglong"></a>DDV_MinMaxLongLong

Appelez `DDV_MinMaxLongLong` pour vérifier que la valeur du contrôle associé à *value* est comprise entre *minVal* et *MaxVal*.

```cpp
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,
    LONGLONG value,
    LONGLONG minVal,
    LONGLONG maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
La valeur minimale (de type LONGLONG) est autorisée.

*maxVal*<br/>
Valeur maximale (de type LONGLONG) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="ddv_minmaxmonth"></a><a name="ddv_minmaxmonth"></a>DDV_MinMaxMonth

Appelez `DDV_MinMaxMonth` pour vérifier que la valeur de date/heure dans le contrôle Month Calendar ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) associé à *RefValue* se situe entre *refMinRange* et *refMaxRange*.

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

*pDX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*refValue*<br/>
Référence à un objet de type `CTime` ou `COleDateTime` associée à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle. Cet objet contient les données à valider. MFC transmet cette référence quand `DDV_MinMaxMonth` est appelé.

*refMinRange*<br/>
Valeur de date/heure minimale autorisée.

*refMaxRange*<br/>
Valeur de date/heure maximale autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="ddv_minmaxshort"></a><a name="ddv_minmaxshort"></a>DDV_MinMaxShort

Appelez `DDV_MinMaxShort` pour vérifier que la valeur du contrôle associé à *value* est comprise entre *minVal* et *MaxVal*.

```cpp
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,
    short value,
    short minVal,
    short maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale autorisée (de type **`short`** ).

*maxVal*<br/>
Valeur maximale autorisée (de type **`short`** ).

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="ddv_minmaxslider"></a><a name="ddv_minmaxslider"></a>DDV_MinMaxSlider

Appelez `DDV_MinMaxSlider` pour vérifier que la valeur du contrôle associé à *value* est comprise entre *minVal* et *MaxVal*.

```cpp
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Référence à la valeur à valider. Ce paramètre contient ou définit la position actuelle du curseur du contrôle Slider.

*minVal*<br/>
Valeur minimale autorisée.

*maxVal*<br/>
Valeur maximale autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur les contrôles Slider, consultez [utilisation de CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="ddv_minmaxuint"></a><a name="ddv_minmaxuint"></a>DDV_MinMaxUInt

Appelez `DDV_MinMaxUInt` pour vérifier que la valeur du contrôle associé à *value* est comprise entre *minVal* et *MaxVal*.

```cpp
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,
    UINT value,
    UINT minVal,
    UINT maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
La valeur minimale (de type UINT) est autorisée.

*maxVal*<br/>
Valeur maximale autorisée (de type UINT).

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="ddv_minmaxulonglong"></a><a name="ddv_minmaxulonglong"></a>DDV_MinMaxULongLong

Appelez `DDV_MinMaxULongLong` pour vérifier que la valeur du contrôle associé à *value* est comprise entre *minVal* et *MaxVal*.

```cpp
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,
    ULONGLONG value,
    ULONGLONG  minVal ,
    ULONGLONG  maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
La valeur minimale (de type ULONGLONG) est autorisée.

*maxVal*<br/>
Valeur maximale (de type ULONGLONG) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdd_. h

## <a name="ddv_minmaxunsigned"></a>DDV_MinMaxUnsigned

Appelez `DDV_MinMaxUnsigned` pour vérifier que la valeur du contrôle associé à *value* est comprise entre *minVal* et *MaxVal*.

### <a name="syntax"></a>Syntaxe

```cpp
   void AFXAPI DDV_MinMaxUnsigned(
       CDataExchange* pDX,
       unsigned value,
       unsigned minVal,
       unsigned maxVal );
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*value*<br/>
Référence à une variable membre de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale autorisée (de type **`unsigned`** ).

*maxVal*<br/>
Valeur maximale autorisée (de type **`unsigned`** ).

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange et validation de données de boîtes de dialogue](../dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxdd_. h

## <a name="see-also"></a>Voir aussi

[Routines d’échange de données de boîtes de dialogue standard](standard-dialog-data-exchange-routines.md)<br/>
[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
