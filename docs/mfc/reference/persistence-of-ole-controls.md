---
title: Persistance des contrôles OLE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 661735e91084bad45553de71e80a599afd674028
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336824"
---
# <a name="persistence-of-ole-controls"></a>Persistance des contrôles OLE
Une fonctionnalité des contrôles OLE est propriété persistance (sérialisation), ce qui permet le contrôle lire ou écrire des valeurs de propriété vers et depuis un fichier ou un flux OLE. Une application de conteneur peut utiliser la sérialisation pour stocker des valeurs de propriété d’un contrôle même après que l’application a détruit le contrôle. Les valeurs de propriété du contrôle OLE peuvent alors être lu à partir du fichier ou flux de données lorsqu’une nouvelle instance du contrôle est créé ultérieurement.  
  
### <a name="persistence-of-ole-controls"></a>Persistance des contrôles OLE  
  
|||  
|-|-|  
|[PX_Blob](#px_blob)|Échange d’une propriété du contrôle qui stocke les données d’objet binaire volumineux (BLOB).|  
|[PX_Bool](#px_bool)|Échange d’une propriété du contrôle de type **BOOL**.|  
|[PX_Color](#px_color)|Échange d’une propriété de couleur d’un contrôle.|  
|[PX_Currency](#px_currency)|Échange d’une propriété du contrôle de type **CY**.|  
|[PX_DataPath](#px_datapath)|Échange d’une propriété du contrôle de type `CDataPathProperty`.|  
|[PX_Double](#px_double)|Échange d’une propriété du contrôle de type **double**.|  
|[PX_Font](#px_font)|Échange d’une propriété de police d’un contrôle.|  
|[PX_Float](#px_float)|Échange d’une propriété du contrôle de type **float**.|  
|[PX_IUnknown](#px_iunknown)|Échange d’une propriété de contrôle du type non défini.|  
|[PX_Long](#px_long)|Échange d’une propriété du contrôle de type **long**.|  
|[PX_Picture](#px_picture)|Échange d’une propriété picture d’un contrôle.|  
|[PX_Short](#px_short)|Échange d’une propriété du contrôle de type **court**.|  
|[PX_ULong](#px_ulong)|Échange d’une propriété du contrôle de type **ULONG**.|  
|[PX_UShort](#px_ushort)|Échange d’une propriété du contrôle de type **USHORT**.|  
|[PXstring](#px_string)|Échange d’une propriété de contrôle de chaîne de caractères.|  
|[PX_VBXFontConvert](#px_vbxfontconvert)|Échange les propriétés de police d’un contrôle VBX dans une propriété de police du contrôle OLE.|  
  
 En outre, le `AfxOleTypeMatchGuid` fonction globale est fournie à tester pour une correspondance entre un TYPEDESC et un GUID donné.  
  
##  <a name="px_blob"></a>  PX_Blob  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre à sérialiser ou à initialiser une propriété qui stocke les données d’objet binaire volumineux (BLOB).  
  
```  
 
BOOL  
PX_Blob(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    HGLOBAL& 
hBlob  ,  
    HGLOBAL 
hBlobDefault  
= NULL);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *pszPropName*  
 Le nom de la propriété qui est échangé.  
  
 *hBlob*  
 Référence à la variable dans laquelle la propriété est stockée (généralement une variable membre de votre classe).  
  
 *hBlobDefault*  
 Valeur par défaut pour la propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 La valeur de propriété est lues ou écrite dans la variable référencée par *hBlob*, le cas échéant. Cette variable doit être initialisée avec la valeur NULL avant d’appeler initialement `PX_Blob` pour la première fois (en règle générale, cela est possible dans le constructeur du contrôle). Si *hBlobDefault* est spécifié, il sera utilisé en tant que la valeur de propriété par défaut. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation ou de l’initialisation du contrôle échoue.  
  
 Les handles *hBlob* et *hBlobDefault* font référence à un bloc de mémoire qui contient les éléments suivants :  
  
-   Une valeur DWORD qui contient la longueur, en octets, des données binaires qui suit, immédiatement suivie  
  
-   Un bloc de mémoire contenant des données binaires réelles.  
  
 Notez que `PX_Blob` alloue la mémoire, à l’aide de la Windows [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) API, lors du chargement des propriétés de type d’objet BLOB. Vous êtes chargé de libérer cette mémoire. Par conséquent, le destructeur de votre contrôle doit appeler [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579) sur n’importe quelle propriété de type d’objet BLOB poignées pour libérer jusqu'à toute mémoire allouée à votre contrôle.  
  
##  <a name="px_bool"></a>  PX_Bool  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre à sérialiser ou à initialiser une propriété de type BOOL.  
  
```  
 
BOOL  
PX_Bool(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    BOOL& bValue);

BOOL  
PX_Bool(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    BOOL& 
bValue  ,  
    BOOL bDefault);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *pszPropName*  
 Le nom de la propriété qui est échangé.  
  
 *bValue*  
 Référence à la variable dans laquelle la propriété est stockée (généralement une variable membre de votre classe).  
  
 *bNiveau par défaut*  
 Valeur par défaut pour la propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 La valeur de propriété est lues ou écrite dans la variable référencée par *bValue*, le cas échéant. Si *bNiveau par défaut* est spécifié, il sera utilisé en tant que la valeur de propriété par défaut. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.  
  
##  <a name="px_color"></a>  PX_Color  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre à sérialiser ou à initialiser une propriété de type OLE_COLOR.  
  
```  
 
BOOL PX_Color(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    OLE_COLOR& clrValue);

BOOL PX_Color(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    OLE_COLOR& 
clrValue  ,  
    OLE_COLOR 
clrDefault);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *pszPropName*  
 Le nom de la propriété qui est échangé.  
  
 *clrValue*  
 Référence à la variable dans laquelle la propriété est stockée (généralement une variable membre de votre classe).  
  
 *clrDefault*  
 Valeur par défaut pour la propriété, tel que défini par le développeur de contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 La valeur de propriété est lues ou écrite dans la variable référencée par *clrValue*, le cas échéant. Si *clrDefault* est spécifié, il sera utilisé en tant que la valeur de propriété par défaut. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.  
  
##  <a name="px_currency"></a>  PX_Currency  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre à sérialiser ou à initialiser une propriété de type **devise**.  
  
```  
 
BOOL  
PX_Currency(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CY& cyValue);

BOOL  
PX_Currency(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CY& 
cyValue  ,  
    CY cyDefault);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *pszPropName*  
 Le nom de la propriété qui est échangé.  
  
 *cyValue*  
 Référence à la variable dans laquelle la propriété est stockée (généralement une variable membre de votre classe).  
  
 *cyDefault*  
 Valeur par défaut pour la propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 La valeur de propriété est lues ou écrite dans la variable référencée par *cyValue*, le cas échéant. Si *cyDefault* est spécifié, il sera utilisé en tant que la valeur de propriété par défaut. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.  
  
##  <a name="px_datapath"></a>  PX_DataPath  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre à sérialiser ou à initialiser une propriété de chemin d’accès de données de type [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md).  
  
```  
 
BOOL  
PX_DataPath(
    CPropExchange* 
pPX,  
    LPCTSTR 
pszPropName,  
    CDataPathProperty& dataPathProperty);

BOOL  
PX_DataPath(
    CPropExchange* 
pPX,  
    CDataPathProperty& dataPathProperty);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *pszPropName*  
 Le nom de la propriété qui est échangé.  
  
 *dataPathProperty*  
 Référence à la variable dans laquelle la propriété est stockée (généralement une variable membre de votre classe).  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Propriétés de chemin d’accès de données implémentent des propriétés de contrôle asynchrone. La valeur de propriété est lues ou écrite dans la variable référencée par *dataPathProperty*, le cas échéant.  
  
##  <a name="px_double"></a>  PX_Double  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre à sérialiser ou à initialiser une propriété de type **double**.  
  
```  
 
BOOL  
PX_Double(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    double& doubleValue);

BOOL  
PX_Double(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    double& 
doubleValue  ,  
    double doubleDefault);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *pszPropName*  
 Le nom de la propriété qui est échangé.  
  
 *doubleValue*  
 Référence à la variable dans laquelle la propriété est stockée (généralement une variable membre de votre classe).  
  
 *doubleDefault*  
 Valeur par défaut pour la propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 La valeur de propriété est lu ou écrite à la variable référencée par *doubleValue*, le cas échéant. Si *doubleDefault* est spécifié, il sera utilisé en tant que la valeur de propriété par défaut. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.  
  
##  <a name="px_font"></a>  PX_Font  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre à sérialiser ou à initialiser une propriété de police de type.  
  
```  
 
BOOL  
PX_Font(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CFontHolder& 
font  ,  
    const 
FONTDESC  
FAR* 
pFontDesc  
= 
NULL,  
    LPFONTDISP 
pFontDispAmbient  
= NULL);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *pszPropName*  
 Le nom de la propriété qui est échangé.  
  
 *police*  
 Une référence à un `CFontHolder` objet qui contient la propriété de police.  
  
 *pFontDesc*  
 Un pointeur vers un `FONTDESC` structure contenant les valeurs à utiliser lors de l’initialisation de l’état par défaut de la propriété de police, dans le cas où *pFontDispAmbient* a la valeur NULL.  
  
 *pFontDispAmbient*  
 Un pointeur vers le `IFontDisp` interface d’une police à utiliser lors de l’initialisation de l’état par défaut de la propriété de police.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 La valeur de propriété est lues ou écrite dans `font`, un `CFontHolder` de référence, le cas échéant. Si *pFontDesc* et *pFontDispAmbient* sont spécifiés, ils sont utilisés pour initialiser la valeur de propriété par défaut, si nécessaire. Ces valeurs sont utilisées si, pour une raison quelconque, le processus de sérialisation du contrôle échoue. En règle générale, vous passez la valeur NULL *pFontDesc* et la valeur ambiante retournée par `COleControl::AmbientFont` pour *pFontDispAmbient*. Notez que l’objet de police retourné par `COleControl::AmbientFont` doivent être libérées par un appel à la `IFontDisp::Release` fonction membre.  
  
##  <a name="px_float"></a>  PX_Float  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre à sérialiser ou à initialiser une propriété de type **float**.  
  
```  
 
BOOL  
PX_Float(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    float& floatValue);

BOOL  
PX_Float(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    float& 
floatValue  ,  
    float floatDefault);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *pszPropName*  
 Le nom de la propriété qui est échangé.  
  
 *floatValue*  
 Référence à la variable dans laquelle la propriété est stockée (généralement une variable membre de votre classe).  
  
 *floatDefault*  
 Valeur par défaut pour la propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 La valeur de propriété est lu ou écrite à la variable référencée par *floatValue*, le cas échéant. Si *floatDefault* est spécifié, il sera utilisé en tant que la valeur de propriété par défaut. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.  
  
##  <a name="px_iunknown"></a>  PX_IUnknown  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre à sérialiser ou à initialiser une propriété représentée par un objet ayant un `IUnknown`-interface dérivée.  
  
```  
 
BOOL  
PX_IUnknown(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    LPUNKNOWN& 
pUnk  ,  
    REFIID 
iid  ,  
    LPUNKNOWN 
pUnkDefault  
= NULL);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *pszPropName*  
 Le nom de la propriété qui est échangé.  
  
 *pUnk*  
 Référence à une variable contenant l’interface de l’objet qui représente la valeur de la propriété.  
  
 *IID*  
 Un ID d’interface indiquant quelle interface de l’objet de propriété est utilisée par le contrôle.  
  
 *pUnkDefault*  
 Valeur par défaut pour la propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 La valeur de propriété est lu ou écrite à la variable référencée par *pUnk*, le cas échéant. Si *pUnkDefault* est spécifié, il sera utilisé en tant que la valeur de propriété par défaut. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.  
  
##  <a name="px_long"></a>  PX_Long  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre à sérialiser ou à initialiser une propriété de type **long**.  
  
```  
 
BOOL  
PX_Long(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    long& lValue);

BOOL  
PX_Long(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    long& 
lValue  ,  
    long lDefault);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *pszPropName*  
 Le nom de la propriété qui est échangé.  
  
 *lValue*  
 Référence à la variable dans laquelle la propriété est stockée (généralement une variable membre de votre classe).  
  
 *lDefault*  
 Valeur par défaut pour la propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 La valeur de propriété est lu ou écrite à la variable référencée par *lValue*, le cas échéant. Si *lDefault* est spécifié, il sera utilisé en tant que la valeur de propriété par défaut. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.  
  
##  <a name="px_picture"></a>  PX_Picture  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre à sérialiser ou à initialiser une propriété d’image de votre contrôle.  
  
```  
 
BOOL  
PX_Picture(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CPictureHolder& pict);

BOOL  
PX_Picture(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CPictureHolder& 
pict  ,  
    CPictureHolder& pictDefault);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *pszPropName*  
 Le nom de la propriété qui est échangé.  
  
 *PICT*  
 Référence à un [CPictureHolder](../../mfc/reference/cpictureholder-class.md) objet où la propriété est stockée (généralement une variable membre de votre classe).  
  
 *pictDefault*  
 Valeur par défaut pour la propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 La valeur de propriété est lu ou écrite à la variable référencée par *pict*, le cas échéant. Si *pictDefault* est spécifié, il sera utilisé en tant que la valeur de propriété par défaut. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.  
  
##  <a name="px_short"></a>  PX_Short  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre à sérialiser ou à initialiser une propriété de type **court**.  
  
```  
 
BOOL  
PX_Short(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    short& sValue);

BOOL  
PX_Short(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    short& 
sValue  ,  
    short sDefault);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *pszPropName*  
 Le nom de la propriété qui est échangé.  
  
 *sValue*  
 Référence à la variable dans laquelle la propriété est stockée (généralement une variable membre de votre classe).  
  
 *sDefault*  
 Valeur par défaut pour la propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 La valeur de propriété est lu ou écrite à la variable référencée par *sValue*, le cas échéant. Si *sDefault* est spécifié, il sera utilisé en tant que la valeur de propriété par défaut. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.  
  
##  <a name="px_ulong"></a>  PX_ULong  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre à sérialiser ou à initialiser une propriété de type **ULONG**.  
  
```  
 
BOOL  
PX_ULong(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    ULONG& ulValue);

BOOL  
PX_ULong(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    ULONG& 
ulValue  ,  
    long ulDefault);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *pszPropName*  
 Nom de la propriété qui est échangée.  
  
 *ulValue*  
 Référence à la variable dans laquelle la propriété est stockée (généralement une variable membre de votre classe).  
  
 *ulDefault*  
 Valeur par défaut pour la propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 La valeur de propriété est lu ou écrite à la variable référencée par *ulValue*, le cas échéant. Si *ulDefault* est spécifié, il sera utilisé en tant que la valeur de propriété par défaut. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.  
  
##  <a name="px_ushort"></a>  PX_UShort  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre à sérialiser ou à initialiser une propriété de type **unsigned short**.  
  
```  
 
BOOL  
PX_UShort(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    USHORT& usValue);

BOOL  
PX_UShort(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    USHORT& 
usValue  ,  
    USHORT usDefault);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *pszPropName*  
 Nom de la propriété qui est échangée.  
  
 *usValue*  
 Référence à la variable dans laquelle la propriété est stockée (généralement une variable membre de votre classe).  
  
 *usDefault*  
 Valeur par défaut pour la propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 La valeur de propriété est lu ou écrite à la variable référencée par *usValue*, le cas échéant. Si *usDefault* est spécifié, il sera utilisé en tant que la valeur de propriété par défaut. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.  
  
##  <a name="px_string"></a>  PXstring  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre à sérialiser ou à initialiser une propriété de chaîne de caractères.  
  
```  
 
BOOL  
PXstring(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CString& strValue);

BOOL  
PXstring(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CString& 
strValue  ,  
    CString strDefault);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *pszPropName*  
 Le nom de la propriété qui est échangé.  
  
 *strValue*  
 Référence à la variable dans laquelle la propriété est stockée (généralement une variable membre de votre classe).  
  
 *strDefault*  
 Valeur par défaut pour la propriété.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 La valeur de propriété est lu ou écrite à la variable référencée par *strValue*, le cas échéant. Si *strDefault* est spécifié, il sera utilisé en tant que la valeur de propriété par défaut. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.  
  
##  <a name="px_vbxfontconvert"></a>  PX_VBXFontConvert  
 Appelez cette fonction au sein de votre contrôle `DoPropExchange` fonction membre pour initialiser une propriété de police en convertissant les propriétés de police d’un contrôle VBX.  
  
```  
 
BOOL  
PX_VBXFontConvert(
    CPropExchange* 
pPX  ,  
    CFontHolder& font);  
```  
  
### <a name="parameters"></a>Paramètres  
 *pPX*  
 Pointeur vers le [CPropExchange](../../mfc/reference/cpropexchange-class.md) objet (généralement passé en tant que paramètre à `DoPropExchange`).  
  
 *police*  
 La propriété de police du contrôle OLE qui contiendra les propriétés liées à la police VBX converties.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’échange a réussi ; 0 en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit être utilisée uniquement par un contrôle OLE qui est conçu comme un remplacement pour un contrôle VBX direct. Lorsque l’environnement de développement Visual Basic convertit un formulaire contenant un contrôle VBX pour utiliser le contrôle OLE de remplacement correspondant, il appellera le contrôle `IDataObject::SetData` fonction, en passant dans un jeu de propriétés qui contient les données de propriété du contrôle VBX. Cette opération, provoque à son tour, le contrôle `DoPropExchange` fonction à appeler. `DoPropExchange` peut appeler `PX_VBXFontConvert` pour convertir les propriétés de police du contrôle VBX (par exemple, « FontName, » « FontSize », et ainsi de suite) dans les composants correspondants des propriétés de police du contrôle OLE.  
  
 `PX_VBXFontConvert` doit être appelée uniquement lorsque le contrôle est réellement est converti depuis une application de formulaire VBX. Exemple :  
  
 [!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]  
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
