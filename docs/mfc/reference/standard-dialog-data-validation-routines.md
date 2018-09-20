---
title: Routines de Validation de données de boîte de dialogue standard | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 116cd9ee86ca29aac6da489916f78c3884ba8bdd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446543"
---
# <a name="standard-dialog-data-validation-routines"></a>Routines de validation des données de boîte de dialogue standard

Cette rubrique répertorie les routines de validation (DDV) de données boîte de dialogue standard utilisés pour les contrôles de boîte de dialogue MFC courants.

> [!NOTE]
>  Les routines d’échange de données boîte de dialogue standard sont définis dans le afxdd_.h de fichier d’en-tête. Toutefois, les applications doivent inclure afxwin.h.

### <a name="ddv-functions"></a>Fonctions DDV

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|Vérifie que le nombre de caractères dans une valeur de contrôle donné ne dépasse pas un maximum donné.|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|Vérifie une valeur de contrôle donné ne dépasse pas un donné **octets** plage.|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|Vérifie qu'une valeur de contrôle donné ne dépasse pas un intervalle de temps donné.|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|Vérifie une valeur de contrôle donné ne dépasse pas un donné **double** plage.|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|Vérifie une valeur de contrôle donné ne dépasse pas un donné **DWORD** plage.|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|Vérifie une valeur de contrôle donné ne dépasse pas un donné **float** plage.|
|[DDV_MinMaxInt](#ddv_minmaxint)|Vérifie une valeur de contrôle donné ne dépasse pas un donné **int** plage.|
|[DDV_MinMaxLong](#ddv_minmaxlong)|Vérifie une valeur de contrôle donné ne dépasse pas un donné **long** plage.|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|Vérifie une valeur de contrôle donné ne dépasse pas un donné **LONGLONG** plage.|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|Vérifie qu'une valeur de contrôle donné ne dépasse pas une plage de dates donnée.|
|[DDV_MinMaxShort](#ddv_minmaxshort)|Vérifie une valeur de contrôle donné ne dépasse pas un donné **court** plage.|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|Vérifie qu'une valeur de contrôle de curseur donné se trouve dans la plage donnée.|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|Vérifie une valeur de contrôle donné ne dépasse pas un donné **UINT** plage.|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|Vérifie qu'une valeur de contrôle donné se situe entre deux valeurs spécifiées.|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|Vérifie une valeur de contrôle donné ne dépasse pas un donné **ULONGLONG** plage.|



##  <a name="ddv_maxchars"></a>  DDV_MaxChars

Appelez `DDV_MaxChars` pour vérifier que la quantité de caractères dans le contrôle associé à *valeur* ne dépasse pas *nChars*.

```
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*valeur*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont validées.

*nChars*<br/>
Nombre maximal de caractères autorisés.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdd_.h

##  <a name="ddv_minmaxbyte"></a>  DDV_MinMaxByte

Appelez `DDV_MinMaxByte` pour vérifier que la valeur dans le contrôle associé à *valeur* se situe entre *minVal* et *maxVal*.

```
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,
    BYTE value,
    BYTE minVal,
    BYTE maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*valeur*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale (de type BYTE) autorisée.

*maxVal*<br/>
Valeur maximale (de type BYTE) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdd_.h

##  <a name="ddv_minmaxdatetime"></a>  DDV_MinMaxDateTime

Appelez `DDV_MinMaxDateTime` pour vérifier que la valeur de date/heure dans le sélecteur de date et heure de contrôle ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) associé *refValue* se situe entre *refMinRange*et *refMaxRange*.

```
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
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction. Vous n’avez pas besoin de supprimer cet objet.

*refValue*<br/>
Une référence à un [CTime](../../atl-mfc-shared/reference/ctime-class.md) ou [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objet associé à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle. Cet objet contient les données à valider.

*refMinRange*<br/>
Valeur minimale autorisée de valeur de date/heure.

*refMaxRange*<br/>
Valeur de date/heure maximale autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdd_.h

##  <a name="ddv_minmaxdouble"></a>  DDV_MinMaxDouble

Appelez `DDV_MinMaxDouble` pour vérifier que la valeur dans le contrôle associé à *valeur* se situe entre *minVal* et *maxVal*.

```
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,
    double const& value,
    double minVal,
    double maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*valeur*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale (de type **double**) autorisée.

*maxVal*<br/>
Valeur maximale (de type **double**) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdd_.h

##  <a name="ddv_minmaxdword"></a>  DDV_MinMaxDWord

Appelez `DDV_MinMaxDWord` pour vérifier que la valeur dans le contrôle associé à *valeur* se situe entre *minVal* et *maxVal*.

```
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,
    DWORD const& value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*valeur*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale (de type DWORD) autorisée.

*maxVal*<br/>
Valeur maximale (de type DWORD) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdd_.h

##  <a name="ddv_minmaxfloat"></a>  DDV_MinMaxFloat

Appelez `DDV_MinMaxFloat` pour vérifier que la valeur dans le contrôle associé à *valeur* se situe entre *minVal* et *maxVal*.

```
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,
    float value,
    float minVal,
    float maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*valeur*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale (de type **float**) autorisée.

*maxVal*<br/>
Valeur maximale (de type **float**) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdd_.h

##  <a name="ddv_minmaxint"></a>  DDV_MinMaxInt

Appelez `DDV_MinMaxInt` pour vérifier que la valeur dans le contrôle associé à *valeur* se situe entre *minVal* et *maxVal*.

```
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,
    int value,
    int minVal,
    int maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*valeur*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale (de type **int**) autorisée.

*maxVal*<br/>
Valeur maximale (de type **int**) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdd_.h

##  <a name="ddv_minmaxlong"></a>  DDV_MinMaxLong

Appelez `DDV_MinMaxLong` pour vérifier que la valeur dans le contrôle associé à *valeur* se situe entre *minVal* et *maxVal*.

```
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,
    long value,
    long minVal,
    long maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*valeur*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale (de type **long**) autorisée.

*maxVal*<br/>
Valeur maximale (de type **long**) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdd_.h

##  <a name="ddv_minmaxlonglong"></a>  DDV_MinMaxLongLong

Appelez `DDV_MinMaxLongLong` pour vérifier que la valeur dans le contrôle associé à *valeur* se situe entre *minVal* et *maxVal*.

```
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,
    LONGLONG value,
    LONGLONG minVal,
    LONGLONG maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*valeur*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale (de type LONGLONG) autorisée.

*maxVal*<br/>
Valeur maximale (de type LONGLONG) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdd_.h

##  <a name="ddv_minmaxmonth"></a>  DDV_MinMaxMonth

Appelez `DDV_MinMaxMonth` pour vérifier que la valeur de date/heure dans le calendrier du mois contrôler ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) associé *refValue* se situe entre *refMinRange* et *refMaxRange*.

```
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
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*refValue*<br/>
Une référence à un objet de type `CTime` ou `COleDateTime` associé à une variable membre de la boîte de dialogue, mode formulaire, ou contrôler l’objet de vue. Cet objet contient les données à valider. Passes MFC de référence this lorsque `DDV_MinMaxMonth` est appelée.

*refMinRange*<br/>
Valeur minimale autorisée de valeur de date/heure.

*refMaxRange*<br/>
Valeur de date/heure maximale autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdd_.h

##  <a name="ddv_minmaxshort"></a>  DDV_MinMaxShort

Appelez `DDV_MinMaxShort` pour vérifier que la valeur dans le contrôle associé à *valeur* se situe entre *minVal* et *maxVal*.

```
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,
    short value,
    short minVal,
    short maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*valeur*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale (de type **court**) autorisée.

*maxVal*<br/>
Valeur maximale (de type **court**) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdd_.h

##  <a name="ddv_minmaxslider"></a>  DDV_MinMaxSlider

Appelez `DDV_MinMaxSlider` pour vérifier que la valeur dans le contrôle associé à *valeur* se situe entre *minVal* et *maxVal*.

```
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*valeur*<br/>
Une référence à la valeur à valider. Ce paramètre contienne ou définit la position de curseur de défilement actuelle du contrôle slider.

*minVal*<br/>
Valeur minimale autorisée.

*maxVal*<br/>
Valeur maximale autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur les contrôles de curseur, consultez [à l’aide de CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdd_.h

##  <a name="ddv_minmaxuint"></a>  DDV_MinMaxUInt

Appelez `DDV_MinMaxUInt` pour vérifier que la valeur dans le contrôle associé à *valeur* se situe entre *minVal* et *maxVal*.

```
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,
    UINT value,
    UINT minVal,
    UINT maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*valeur*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale (de type UINT) autorisée.

*maxVal*<br/>
Valeur maximale (de type UINT) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdd_.h

##  <a name="ddv_minmaxulonglong"></a>  DDV_MinMaxULongLong

Appelez `DDV_MinMaxULongLong` pour vérifier que la valeur dans le contrôle associé à *valeur* se situe entre *minVal* et *maxVal*.

```
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,
    ULONGLONG value,
    ULONGLONG  minVal ,
    ULONGLONG  maxVal);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*valeur*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale (de type ULONGLONG) autorisée.

*maxVal*<br/>
Valeur maximale (de type ULONGLONG) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdd_.h

## <a name="see-also"></a>Voir aussi

[Routines d’échange de données de boîte de dialogue standard](../../mfc/reference/standard-dialog-data-exchange-routines.md)<br/>
[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)

## <a name="ddvminmaxunsigned"></a>DDV_MinMaxUnsigned

Appelez `DDV_MinMaxUnsigned` pour vérifier que la valeur dans le contrôle associé à *valeur* se situe entre *minVal* et *maxVal*.

### <a name="syntax"></a>Syntaxe

```
   void AFXAPI DDV_MinMaxUnsigned(
       CDataExchange* pDX,
       unsigned value,
       unsigned minVal,
       unsigned maxVal );
```
### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*valeur*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont validées.

*minVal*<br/>
Valeur minimale (de type **non signé** ) autorisée.

*maxVal*<br/>
Valeur maximale (de type **non signé** ) autorisée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur DDV, consultez [échange de données de boîtes de dialogue et la Validation](../dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdd_.h

### <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[DDX_Slider](#ddx_slider)<br/>
[DDX_FieldSlider](#ddx_fieldslider)



