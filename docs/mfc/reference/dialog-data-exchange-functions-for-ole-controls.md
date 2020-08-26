---
title: Fonctions d'échange de données de boîtes de dialogue pour contrôles OLE
ms.date: 11/04/2016
f1_keywords:
- AFXDISP/DDX_OCBool
- AFXDISP/DDX_OCBoolRO
- AFXDISP/DDX_OCColor
- AFXDISP/DDX_OCColorRO
- AFXDISP/DDX_OCFloat
- AFXDISP/DDX_OCFloatRO
- AFXDISP/DDX_OCInt
- AFXDISP/DDX_OCIntRO
- AFXDISP/DDX_OCShort
- AFXDISP/DDX_OCShortRO
- AFXDISP/DDX_OCText
- AFXDISP/DDX_OCTextRO
helpviewer_keywords:
- OLE controls [MFC], DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
ms.openlocfilehash: 9133c30dd1ac069145862d4bf61ba0bc0d504838
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837357"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>Fonctions d'échange de données de boîtes de dialogue pour contrôles OLE

Cette rubrique répertorie les fonctions de DDX_OC utilisées pour échanger des données entre une propriété d’un contrôle OLE dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle, ainsi qu’un membre de données de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

### <a name="ddx_oc-functions"></a>Fonctions DDX_OC

|Nom|Description|
|-|-|
|[DDX_OCBool](#ddx_ocbool)|Gère le transfert de données de valeur **booléenne** entre une propriété d’un contrôle OLE et un membre de données **bool** .|
|[DDX_OCBoolRO](#ddx_ocboolro)|Gère le transfert de données de valeur **booléenne** entre une propriété en lecture seule d’un contrôle OLE et un membre de données **bool** .|
|[DDX_OCColor](#ddx_occolor)|Gère le transfert de données de **OLE_COLOR** entre une propriété d’un contrôle OLE et un membre de données **OLE_COLOR** .|
|[DDX_OCColorRO](#ddx_occolorro)|Gère le transfert de données de **OLE_COLOR** entre une propriété en lecture seule d’un contrôle OLE et un membre de données **OLE_COLOR** .|
|[DDX_OCFloat](#ddx_ocfloat)|Gère le transfert de **`float`** données (ou **`double`** ) entre une propriété d’un contrôle OLE et un **`float`** membre de **`double`** données (ou).|
|[DDX_OCFloatRO](#ddx_ocfloatro)|Gère le transfert de **`float`** données (ou **`double`** ) entre une propriété en lecture seule d’un contrôle OLE et un **`float`** membre de **`double`** données (ou).|
|[DDX_OCInt](#ddx_ocint)|Gère le transfert de **`int`** données (ou **`long`** ) entre une propriété d’un contrôle OLE et un **`int`** membre de **`long`** données (ou).|
|[DDX_OCIntRO](#ddx_ocintro)|Gère le transfert de **`int`** données (ou **`long`** ) entre une propriété en lecture seule d’un contrôle OLE et un **`int`** membre de **`long`** données (ou).|
|[DDX_OCShort](#ddx_ocshort)|Gère le transfert de **`short`** données entre une propriété d’un contrôle OLE et un **`short`** membre de données.|
|[DDX_OCShortRO](#ddx_ocshortro)|Gère le transfert de **`short`** données entre une propriété en lecture seule d’un contrôle OLE et un **`short`** membre de données.|
|[DDX_OCText](#ddx_octext)|Gère le transfert de données **CString** entre une propriété d’un contrôle OLE et un membre de données **CString** .|
|[DDX_OCTextRO](#ddx_octextro)|Gère le transfert de données **CString** entre une propriété en lecture seule d’un contrôle OLE et un membre de données **CString** .|

## <a name="ddx_ocbool"></a><a name="ddx_ocbool"></a> DDX_OCBool

La `DDX_OCBool` fonction gère le transfert de données **bool** entre une propriété d’un contrôle OLE dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un membre de données **bool** de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.

*égal*<br/>
ID de distribution d’une propriété du contrôle.

*value*<br/>
Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête :** afxdisp.h

## <a name="ddx_ocboolro"></a><a name="ddx_ocboolro"></a> DDX_OCBoolRO

La `DDX_OCBoolRO` fonction gère le transfert de données de type **bool** entre une propriété en lecture seule d’un contrôle OLE dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un membre de données **bool** de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.

*égal*<br/>
ID de distribution d’une propriété du contrôle.

*value*<br/>
Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp. h

## <a name="ddx_occolor"></a><a name="ddx_occolor"></a> DDX_OCColor

La `DDX_OCColor` fonction gère le transfert de OLE_COLOR données entre une propriété d’un contrôle OLE dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un membre de données OLE_COLOR de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.

*égal*<br/>
ID de distribution d’une propriété du contrôle.

*value*<br/>
Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp. h

## <a name="ddx_occolorro"></a><a name="ddx_occolorro"></a> DDX_OCColorRO

La `DDX_OCColorRO` fonction gère le transfert de OLE_COLOR données entre une propriété en lecture seule d’un contrôle OLE dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un membre de données OLE_COLOR de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.

*égal*<br/>
ID de distribution d’une propriété du contrôle.

*value*<br/>
Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp. h

## <a name="ddx_ocfloat"></a><a name="ddx_ocfloat"></a> DDX_OCFloat

La `DDX_OCFloat` fonction gère le transfert de **`float`** données (ou **`double`** ) entre une propriété d’un contrôle OLE dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un **`float`** membre de données (ou **`double`** ) de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.

*égal*<br/>
ID de distribution d’une propriété du contrôle.

*value*<br/>
Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp. h

## <a name="ddx_ocfloatro"></a><a name="ddx_ocfloatro"></a> DDX_OCFloatRO

La `DDX_OCFloatRO` fonction gère le transfert de **`float`** données (ou **`double`** ) entre une propriété en lecture seule d’un contrôle OLE dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un **`float`** **`double`** membre de données (ou) de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.

*égal*<br/>
ID de distribution d’une propriété du contrôle.

*value*<br/>
Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp. h

## <a name="ddx_ocint"></a><a name="ddx_ocint"></a> DDX_OCInt

La `DDX_OCInt` fonction gère le transfert de **`int`** données (ou **`long`** ) entre une propriété d’un contrôle OLE dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un **`int`** membre de données (ou **`long`** ) de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.

*égal*<br/>
ID de distribution d’une propriété du contrôle.

*value*<br/>
Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp. h

## <a name="ddx_ocintro"></a><a name="ddx_ocintro"></a> DDX_OCIntRO

La `DDX_OCIntRO` fonction gère le transfert de **`int`** données (ou **`long`** ) entre une propriété en lecture seule d’un contrôle OLE dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un **`int`** **`long`** membre de données (ou) de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.

*égal*<br/>
ID de distribution d’une propriété du contrôle.

*value*<br/>
Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp. h

## <a name="ddx_ocshort"></a><a name="ddx_ocshort"></a> DDX_OCShort

La `DDX_OCShort` fonction gère le transfert de données courtes entre une propriété d’un contrôle OLE dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un membre de données Short de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.

*égal*<br/>
ID de distribution d’une propriété du contrôle.

*value*<br/>
Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp. h

## <a name="ddx_ocshortro"></a><a name="ddx_ocshortro"></a> DDX_OCShortRO

La `DDX_OCShortRO` fonction gère le transfert de données courtes entre une propriété en lecture seule d’un contrôle OLE dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un membre de données Short de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.

*égal*<br/>
ID de distribution d’une propriété du contrôle.

*value*<br/>
Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp. h

## <a name="ddx_octext"></a><a name="ddx_octext"></a> DDX_OCText

La fonction **DDX_OCText** gère le transfert de données **CString** entre une propriété d’un contrôle OLE dans une boîte de dialogue, un affichage de formulaire ou un objet de vue de contrôle et un membre de données **CString** de la boîte de dialogue, du mode formulaire ou de l’objet de vue de contrôle.

```cpp
void AFXAPI DDX_OCText(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet **CDataExchange** . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.

*égal*<br/>
ID de distribution d’une propriété du contrôle.

*value*<br/>
Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp. h

## <a name="ddx_octextro"></a><a name="ddx_octextro"></a> DDX_OCTextRO

La fonction `DDX_OCTextRO` gère le transfert de données `CString` entre une propriété en lecture seule d’un contrôle OLE d’objet boîte de dialogue, vue de formulaire ou vue de contrôle et un membre de données `CString` de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.

```cpp
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un objet `CDataExchange`. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.

*égal*<br/>
ID de distribution d’une propriété du contrôle.

*value*<br/>
Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp. h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
