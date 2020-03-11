---
title: Persistance des contrôles OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: 42e70f9e48339eddb2a5af4fa288400cce01f490
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855748"
---
# <a name="persistence-of-ole-controls"></a>Persistance des contrôles OLE

L’une des fonctionnalités des contrôles OLE est la persistance des propriétés (ou la sérialisation), qui permet au contrôle OLE de lire ou d’écrire des valeurs de propriété vers et à partir d’un fichier ou d’un flux. Une application conteneur peut utiliser la sérialisation pour stocker les valeurs de propriété d’un contrôle même après que l’application a détruit le contrôle. Les valeurs de propriété du contrôle OLE peuvent ensuite être lues à partir du fichier ou du flux quand une nouvelle instance du contrôle est créée ultérieurement.

### <a name="persistence-of-ole-controls"></a>Persistance des contrôles OLE

|||
|-|-|
|[PX_Blob](#px_blob)|Échange une propriété de contrôle qui stocke des données BLOB (Binary Large Object).|
|[PX_Bool](#px_bool)|Échange une propriété de contrôle de type **bool**.|
|[PX_Color](#px_color)|Échange une propriété de couleur d’un contrôle.|
|[PX_Currency](#px_currency)|Échange une propriété de contrôle de type **CY**.|
|[PX_DataPath](#px_datapath)|Échange une propriété de contrôle de type `CDataPathProperty`.|
|[PX_Double](#px_double)|Échange une propriété de contrôle de type **double**.|
|[PX_Font](#px_font)|Échange une propriété font d’un contrôle.|
|[PX_Float](#px_float)|Échange une propriété de contrôle de type **float**.|
|[PX_IUnknown](#px_iunknown)|Échange une propriété de contrôle de type non défini.|
|[PX_Long](#px_long)|Échange une propriété de contrôle de type **long**.|
|[PX_Picture](#px_picture)|Échange une propriété Picture d’un contrôle.|
|[PX_Short](#px_short)|Échange une propriété de contrôle de type **short**.|
|[PX_ULong](#px_ulong)|Échange une propriété de contrôle de type **ULong**.|
|[PX_UShort](#px_ushort)|Échange une propriété de contrôle de type **UShort**.|
|[PXstring](#px_string)|Échange une propriété de contrôle de chaîne de caractères.|
|[PX_VBXFontConvert](#px_vbxfontconvert)|Échange les propriétés de police d’un contrôle VBX dans une propriété de police de contrôle OLE.|

En outre, la fonction globale `AfxOleTypeMatchGuid` est fournie pour tester une correspondance entre un TYPEDESC et un GUID donné.

##  <a name="px_blob"></a>PX_Blob

Appelez cette fonction dans la fonction membre `DoPropExchange` de votre contrôle pour sérialiser ou initialiser une propriété qui stocke des données BLOB (Binary Large Object).

```
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*hBlob*<br/>
Référence à la variable dans laquelle la propriété est stockée (généralement une variable de membre de votre classe).

*hBlobDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété sera lue ou écrite dans la variable référencée par *hBlob*, selon le cas. Cette variable doit être initialisée à la valeur NULL avant d’appeler initialement `PX_Blob` pour la première fois (en général, cela peut être fait dans le constructeur du contrôle). Si *hBlobDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour une raison quelconque, le processus d’initialisation ou de sérialisation du contrôle échoue.

Les handles *hBlob* et *hBlobDefault* font référence à un bloc de mémoire qui contient les éléments suivants :

- Valeur DWORD qui contient la longueur, en octets, des données binaires qui suivent, suivies immédiatement par

- Bloc de mémoire contenant les données binaires réelles.

Notez que `PX_Blob` allouera de la mémoire, à l’aide de l’API [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) de Windows, lors du chargement des propriétés de type BLOB. Vous êtes chargé de libérer cette mémoire. Par conséquent, le destructeur de votre contrôle doit appeler [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) sur n’importe quelle poignée de propriété de type BLOB pour libérer de la mémoire allouée à votre contrôle.

##  <a name="px_bool"></a>PX_Bool

Appelez cette fonction dans la fonction membre de `DoPropExchange` de votre contrôle pour sérialiser ou initialiser une propriété de type BOOL.

```
BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue);

BOOL PX_Bool(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    BOOL& bValue,
    BOOL bDefault);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*bValue*<br/>
Référence à la variable dans laquelle la propriété est stockée (généralement une variable de membre de votre classe).

*bDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété sera lue ou écrite dans la variable référencée par *bValue*, selon le cas. Si *bDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.

##  <a name="px_color"></a>PX_Color

Appelez cette fonction dans la fonction membre `DoPropExchange` de votre contrôle pour sérialiser ou initialiser une propriété de type OLE_COLOR.

```
BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue);

BOOL PX_Color(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    OLE_COLOR& clrValue,
    OLE_COLOR clrDefault);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*clrValue*<br/>
Référence à la variable dans laquelle la propriété est stockée (généralement une variable de membre de votre classe).

*clrDefault*<br/>
Valeur par défaut de la propriété, telle que définie par le développeur de contrôle.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété sera lue ou écrite dans la variable référencée par *clrValue*, selon le cas. Si *clrDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.

##  <a name="px_currency"></a>PX_Currency

Appelez cette fonction dans la fonction membre de `DoPropExchange` de votre contrôle pour sérialiser ou initialiser une propriété de type **Currency**.

```
BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue);

BOOL PX_Currency(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CY& cyValue,
    CY cyDefault);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*cyValue*<br/>
Référence à la variable dans laquelle la propriété est stockée (généralement une variable de membre de votre classe).

*cyDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété sera lue ou écrite dans la variable référencée par *cyValue*, selon le cas. Si *cyDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.

##  <a name="px_datapath"></a>PX_DataPath

Appelez cette fonction dans la fonction membre de `DoPropExchange` de votre contrôle pour sérialiser ou initialiser une propriété de chemin d’accès aux données de type [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md).

```
BOOL PX_DataPath(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CDataPathProperty& dataPathProperty);

BOOL PX_DataPath(
    CPropExchange* pPX,
    CDataPathProperty& dataPathProperty);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*dataPathProperty*<br/>
Référence à la variable dans laquelle la propriété est stockée (généralement une variable de membre de votre classe).

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

Les propriétés du chemin d’accès aux données implémentent des propriétés de contrôle asynchrone. La valeur de la propriété sera lue ou écrite dans la variable référencée par *dataPathProperty*, selon le cas.

##  <a name="px_double"></a>PX_Double

Appelez cette fonction dans la fonction membre `DoPropExchange` de votre contrôle pour sérialiser ou initialiser une propriété de type **double**.

```
BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue);

BOOL PX_Double(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    double& doubleValue,
    double doubleDefault);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*doubleValue*<br/>
Référence à la variable dans laquelle la propriété est stockée (généralement une variable de membre de votre classe).

*doubleDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue à partir de la variable référencée par *DoubleValue*, ou écrite dans celle-ci, selon le cas. Si *doubleDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.

##  <a name="px_font"></a>PX_Font

Appelez cette fonction dans la fonction membre de `DoPropExchange` de votre contrôle pour sérialiser ou initialiser une propriété de type font.

```
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*son*<br/>
Référence à un objet `CFontHolder` qui contient la propriété font.

*pFontDesc*<br/>
Pointeur vers une structure `FONTDESC` contenant les valeurs à utiliser pour initialiser l’État par défaut de la propriété font, dans le cas où *pFontDispAmbient* a la valeur null.

*pFontDispAmbient*<br/>
Pointeur vers l’interface `IFontDisp` d’une police à utiliser pour initialiser l’État par défaut de la propriété font.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue ou écrite dans `font`, une référence de `CFontHolder`, le cas échéant. Si *pFontDesc* et *pFontDispAmbient* sont spécifiés, ils sont utilisés pour initialiser la valeur par défaut de la propriété, si nécessaire. Ces valeurs sont utilisées si, pour une raison quelconque, le processus de sérialisation du contrôle échoue. En général, vous transmettez NULL pour *pFontDesc* et la valeur ambiante retournée par `COleControl::AmbientFont` pour *pFontDispAmbient*. Notez que l’objet font retourné par `COleControl::AmbientFont` doit être libéré par un appel à la fonction membre `IFontDisp::Release`.

##  <a name="px_float"></a>PX_Float

Appelez cette fonction dans la fonction membre `DoPropExchange` de votre contrôle pour sérialiser ou initialiser une propriété de type **float**.

```
BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue);

BOOL PX_Float(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    float& floatValue,
    float floatDefault);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*floatValue*<br/>
Référence à la variable dans laquelle la propriété est stockée (généralement une variable de membre de votre classe).

*floatDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue à partir de la variable référencée par *floatValue*, ou écrite dans celle-ci, selon le cas. Si *floatDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.

##  <a name="px_iunknown"></a>PX_IUnknown

Appelez cette fonction dans la fonction membre de `DoPropExchange` de votre contrôle pour sérialiser ou initialiser une propriété représentée par un objet ayant une interface dérivée de `IUnknown`.

```
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*pUnk*<br/>
Référence à une variable contenant l’interface de l’objet qui représente la valeur de la propriété.

*vaut*<br/>
ID d’interface indiquant quelle interface de l’objet de propriété est utilisée par le contrôle.

*pUnkDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue à partir de la variable référencée par *punk*, ou écrite dans celle-ci, selon le cas. Si *pUnkDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.

##  <a name="px_long"></a>PX_Long

Appelez cette fonction dans la fonction membre de `DoPropExchange` de votre contrôle pour sérialiser ou initialiser une propriété de type **long**.

```
BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue);

BOOL PX_Long(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    long& lValue,
    long lDefault);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*lValue*<br/>
Référence à la variable dans laquelle la propriété est stockée (généralement une variable de membre de votre classe).

*lDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue à partir de la variable référencée par *lValue*, ou écrite dans celle-ci, selon le cas. Si *lDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.

##  <a name="px_picture"></a>PX_Picture

Appelez cette fonction dans la fonction membre `DoPropExchange` de votre contrôle pour sérialiser ou initialiser une propriété Picture de votre contrôle.

```
BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict);

BOOL PX_Picture(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CPictureHolder& pict,
    CPictureHolder& pictDefault);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*PICT*<br/>
Référence à un objet [CPictureHolder](../../mfc/reference/cpictureholder-class.md) où la propriété est stockée (généralement une variable membre de votre classe).

*pictDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue à partir de la variable référencée par *PICT*, ou écrite dans celle-ci, selon le cas. Si *pictDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.

##  <a name="px_short"></a>PX_Short

Appelez cette fonction dans la fonction membre de `DoPropExchange` de votre contrôle pour sérialiser ou initialiser une propriété de type **short**.

```
BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue);

BOOL PX_Short(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    short& sValue,
    short sDefault);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*sValue*<br/>
Référence à la variable dans laquelle la propriété est stockée (généralement une variable de membre de votre classe).

*sDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue à partir de la variable référencée par *sValue*, ou écrite dans celle-ci, selon le cas. Si *sDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.

##  <a name="px_ulong"></a>PX_ULong

Appelez cette fonction dans la fonction membre de `DoPropExchange` de votre contrôle pour sérialiser ou initialiser une propriété de type **ULong**.

```
BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue);

BOOL PX_ULong(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    ULONG& ulValue,
    long ulDefault);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*Objet*<br/>
Référence à la variable dans laquelle la propriété est stockée (généralement une variable de membre de votre classe).

*ulDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue ou écrite dans la variable référencée par *ulValue*, selon le cas. Si *ulDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.

##  <a name="px_ushort"></a>PX_UShort

Appelez cette fonction dans la fonction membre de `DoPropExchange` de votre contrôle pour sérialiser ou initialiser une propriété de type **unsigned short**.

```
BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue);

BOOL PX_UShort(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    USHORT& usValue,
    USHORT usDefault);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*usValue*<br/>
Référence à la variable dans laquelle la propriété est stockée (généralement une variable de membre de votre classe).

*usDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue à partir de la variable référencée par *usValue*, ou écrite dans celle-ci, selon le cas. Si *usDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.

##  <a name="px_string"></a>PXstring

Appelez cette fonction dans la fonction membre de `DoPropExchange` de votre contrôle pour sérialiser ou initialiser une propriété de type chaîne de caractères.

```
BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue);

BOOL PXstring(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CString& strValue,
    CString strDefault);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*strValue*<br/>
Référence à la variable dans laquelle la propriété est stockée (généralement une variable de membre de votre classe).

*strDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue à partir de la variable référencée par *strValue*, ou écrite dans celle-ci, selon le cas. Si *strDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour une raison quelconque, le processus de sérialisation du contrôle échoue.

##  <a name="px_vbxfontconvert"></a>PX_VBXFontConvert

Appelez cette fonction dans la fonction membre de `DoPropExchange` de votre contrôle pour initialiser une propriété font en convertissant les propriétés relatives à la police d’un contrôle VBX.

```
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>Paramètres

*pPX*<br/>
Pointeur vers l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme paramètre à `DoPropExchange`).

*son*<br/>
Propriété font du contrôle OLE qui contiendra les propriétés de police VBX converties.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction doit être utilisée uniquement par un contrôle OLE conçu comme un remplacement direct d’un contrôle VBX. Lorsque l’environnement de développement Visual Basic convertit un formulaire contenant un contrôle VBX pour utiliser le contrôle OLE de remplacement correspondant, il appelle la fonction `IDataObject::SetData` du contrôle, en passant un jeu de propriétés qui contient les données de propriété du contrôle VBX. Cette opération provoque à son tour l’appel de la fonction `DoPropExchange` du contrôle. `DoPropExchange` pouvez appeler `PX_VBXFontConvert` pour convertir les propriétés relatives à la police du contrôle VBX (par exemple, « FontName », « FontSize », etc.) dans les composants correspondants de la propriété font du contrôle OLE.

`PX_VBXFontConvert` doit être appelé uniquement lorsque le contrôle est en cours de conversion à partir d’une application de formulaire VBX. Par exemple :

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Macros et globales](../../mfc/reference/mfc-macros-and-globals.md)
