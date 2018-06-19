---
title: Fonctions d’échange de données de la boîte de dialogue pour contrôles OLE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5dd7e1b9b18e8478cfa4e61a22806cf067cb3699
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375971"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>Fonctions d'échange de données de boîtes de dialogue pour contrôles OLE
Cette rubrique répertorie les fonctions DDX_OC utilisées pour échanger des données entre une propriété d’un contrôle OLE dans une boîte de dialogue, mode formulaire ou un objet de vue de contrôle et un membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
### <a name="ddxoc-functions"></a>Fonctions DDX_OC  
  
|||  
|-|-|  
|[DDX_OCBool](#ddx_ocbool)|Gère le transfert de **BOOL** des données entre une propriété d’un contrôle OLE et un **BOOL** membre de données.|  
|[DDX_OCBoolRO](#ddx_ocboolro)|Gère le transfert de **BOOL** des données entre une propriété en lecture seule d’un contrôle OLE et un **BOOL** membre de données.|  
|[DDX_OCColor](#ddx_occolor)|Gère le transfert de **OLE_COLOR** des données entre une propriété d’un contrôle OLE et un **OLE_COLOR** membre de données.|  
|[DDX_OCColorRO](#ddx_occolorro)|Gère le transfert de **OLE_COLOR** des données entre une propriété en lecture seule d’un contrôle OLE et un **OLE_COLOR** membre de données.|  
|[DDX_OCFloat](#ddx_ocfloat)|Gère le transfert de **float** (ou **double**) des données entre une propriété d’un contrôle OLE et un **float** (ou **double**) membre de données.|  
|[DDX_OCFloatRO](#ddx_ocfloatro)|Gère le transfert de **float** (ou **double**) des données entre une propriété en lecture seule d’un contrôle OLE et un **float** (ou **double**) données membre.|  
|[DDX_OCInt](#ddx_ocint)|Gère le transfert de `int` (ou **long**) des données entre une propriété d’un contrôle OLE et un `int` (ou **long**) membre de données.|  
|[DDX_OCIntRO](#ddx_ocintro)|Gère le transfert de `int` (ou **long**) des données entre une propriété en lecture seule d’un contrôle OLE et un `int` (ou **long**) membre de données.|  
|[DDX_OCShort](#ddx_ocshort)|Gère le transfert de **court** des données entre une propriété d’un contrôle OLE et un **court** membre de données.|  
|[DDX_OCShortRO](#ddx_ocshortro)|Gère le transfert de **court** des données entre une propriété en lecture seule d’un contrôle OLE et un **court** membre de données.|  
|[DDX_OCText](#ddx_octext)|Gère le transfert de **CString** des données entre une propriété d’un contrôle OLE et un **CString** membre de données.|  
|[DDX_OCTextRO](#ddx_octextro)|Gère le transfert de **CString** des données entre une propriété en lecture seule d’un contrôle OLE et un **CString** membre de données.|  
  
##  <a name="ddx_ocbool"></a>  DDX_OCBool  
 Le `DDX_OCBool` fonction gère le transfert de **BOOL** des données entre une propriété d’un contrôle OLE dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un **BOOL** membre de données de la boîte de dialogue, vue de formulaire, ou objet de vue de contrôle.  
  
```   
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    BOOL& value);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.  
  
 `dispid`  
 ID de distribution d’une propriété du contrôle.  
  
 *valeur*  
 Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête :** afxdisp.h  
  
##  <a name="ddx_ocboolro"></a>  DDX_OCBoolRO  
 Le `DDX_OCBoolRO` fonction gère le transfert de **BOOL** des données entre une propriété en lecture seule d’un contrôle OLE dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un **BOOL** membre de données de la boîte de dialogue mode formulaire, ou un objet de vue de contrôle.  
  
```   
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    BOOL& value);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.  
  
 `dispid`  
 ID de distribution d’une propriété du contrôle.  
  
 *valeur*  
 Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="ddx_occolor"></a>  DDX_OCColor  
 Le `DDX_OCColor` fonction gère le transfert de **OLE_COLOR** des données entre une propriété d’un contrôle OLE dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un **OLE_COLOR** membre de données de la boîte de dialogue mode formulaire, ou un objet de vue de contrôle.  
  
```   
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    OLE_COLOR& value);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.  
  
 `dispid`  
 ID de distribution d’une propriété du contrôle.  
  
 *valeur*  
 Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="ddx_occolorro"></a>  DDX_OCColorRO  
 Le `DDX_OCColorRO` fonction gère le transfert de **OLE_COLOR** des données entre une propriété en lecture seule d’un contrôle OLE dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un **OLE_COLOR** membre de données de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle.  
  
```   
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    OLE_COLOR& value);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.  
  
 `dispid`  
 ID de distribution d’une propriété du contrôle.  
  
 *valeur*  
 Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="ddx_ocfloat"></a>  DDX_OCFloat  
 Le `DDX_OCFloat` fonction gère le transfert de **float** (ou **double**) des données entre une propriété d’un contrôle OLE dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un **float** (ou **double**) membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
```   
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
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.  
  
 `dispid`  
 ID de distribution d’une propriété du contrôle.  
  
 *valeur*  
 Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="ddx_ocfloatro"></a>  DDX_OCFloatRO  
 Le `DDX_OCFloatRO` fonction gère le transfert de **float** (ou **double**) des données entre une propriété en lecture seule d’un contrôle OLE dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un  **float** (ou **double**) membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
```   
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
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.  
  
 `dispid`  
 ID de distribution d’une propriété du contrôle.  
  
 *valeur*  
 Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="ddx_ocint"></a>  DDX_OCInt  
 Le `DDX_OCInt` fonction gère le transfert de `int` (ou **long**) des données entre une propriété d’un contrôle OLE dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un `int` (ou **long**) membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
```   
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
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.  
  
 `dispid`  
 ID de distribution d’une propriété du contrôle.  
  
 *valeur*  
 Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="ddx_ocintro"></a>  DDX_OCIntRO  
 Le `DDX_OCIntRO` fonction gère le transfert de `int` (ou **long**) des données entre une propriété en lecture seule d’un contrôle OLE dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un `int` (ou **long** ) membre de données de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
```   
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
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.  
  
 `dispid`  
 ID de distribution d’une propriété du contrôle.  
  
 *valeur*  
 Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="ddx_ocshort"></a>  DDX_OCShort  
 Le `DDX_OCShort` fonction gère le transfert de données de type short entre une propriété d’un contrôle OLE dans une boîte de dialogue, vue de formulaire, ou objet de vue de contrôle et un membre de données de type short de la boîte de dialogue mode formulaire, ou objet de vue de contrôle.  
  
```   
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    short& value);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.  
  
 `dispid`  
 ID de distribution d’une propriété du contrôle.  
  
 *valeur*  
 Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="ddx_ocshortro"></a>  DDX_OCShortRO  
 Le `DDX_OCShortRO` fonction gère le transfert de données de type short entre une propriété en lecture seule d’un contrôle OLE dans une boîte de dialogue, vue de formulaire, ou objet de vue de contrôle et un membre de données de type short de la boîte de dialogue mode formulaire, ou objet de vue de contrôle.  
  
```   
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    short& value);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.  
  
 `dispid`  
 ID de distribution d’une propriété du contrôle.  
  
 *valeur*  
 Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="ddx_octext"></a>  DDX_OCText  
 Le **DDX_OCText** fonction gère le transfert de **CString** des données entre une propriété d’un contrôle OLE dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un **CString** données membre de la boîte de dialogue, un mode formulaire ou un objet de vue de contrôle.  
  
```   
void AFXAPI DDX_OCText(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    CString& value); 
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Un pointeur vers un **CDataExchange** objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.  
  
 `dispid`  
 ID de distribution d’une propriété du contrôle.  
  
 *valeur*  
 Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="ddx_octextro"></a>  DDX_OCTextRO  
 La fonction `DDX_OCTextRO` gère le transfert de données `CString` entre une propriété en lecture seule d’un contrôle OLE d’objet boîte de dialogue, vue de formulaire ou vue de contrôle et un membre de données `CString` de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.  
  
```  
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    CString& value); 
```  
  
### <a name="parameters"></a>Paramètres  
 `pDX`  
 Pointeur vers un objet `CDataExchange` . L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 `nIDC`  
 ID d’un contrôle OLE situé dans l’objet boîte de dialogue, vue de formulaire ou vue de contrôle.  
  
 `dispid`  
 ID de distribution d’une propriété du contrôle.  
  
 *valeur*  
 Référence à une variable membre de l’objet boîte de dialogue, vue de formulaire ou vue de contrôle avec lequel les données sont échangées.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur DDX, consultez [échange de données de boîtes de dialogue et la Validation](../../mfc/dialog-data-exchange-and-validation.md).  

### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h
    
## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
