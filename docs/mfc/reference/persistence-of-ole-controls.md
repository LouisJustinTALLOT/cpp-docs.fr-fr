---
title: Persistance des contrôles OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
ms.openlocfilehash: 88707da503b1d1cdc809827dc4d1bac0ccad9b5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373009"
---
# <a name="persistence-of-ole-controls"></a>Persistance des contrôles OLE

Une capacité de contrôles OLE est la persistance des propriétés (ou la sérialisation), qui permet au contrôle OLE de lire ou d’écrire les valeurs de propriété à et à partir d’un fichier ou d’un flux. Une application de conteneur peut utiliser la sérialisation pour stocker la valeur de propriété d’un contrôle même après que l’application a détruit le contrôle. Les valeurs de propriété du contrôle OLE peuvent alors être lues à partir du fichier ou du flux lorsqu’une nouvelle instance du contrôle est créée ultérieurement.

### <a name="persistence-of-ole-controls"></a>Persistance des contrôles OLE

|||
|-|-|
|[PX_Blob](#px_blob)|Échange une propriété de contrôle qui stocke les données binaires de gros objets (BLOB).|
|[PX_Bool](#px_bool)|Échanges d’une propriété de contrôle de type **BOOL**.|
|[PX_Color](#px_color)|Échange une propriété de couleur d’un contrôle.|
|[PX_Currency](#px_currency)|Échange d’une propriété de contrôle de type **CY**.|
|[PX_DataPath](#px_datapath)|Échange d’une `CDataPathProperty`propriété de contrôle de type .|
|[PX_Double](#px_double)|Échanges d’une propriété de contrôle de type **double**.|
|[PX_Font](#px_font)|Échange d’une propriété de police d’un contrôle.|
|[PX_Float](#px_float)|Échanges d’une propriété de contrôle de type **flotteur**.|
|[PX_IUnknown](#px_iunknown)|Échange d’une propriété de contrôle de type indéfini.|
|[PX_Long](#px_long)|Échanges d’une propriété de contrôle de type **long**.|
|[PX_Picture](#px_picture)|Échange d’une propriété d’image d’un contrôle.|
|[PX_Short](#px_short)|Échanges d’une propriété de contrôle de type **court**.|
|[PX_ULong](#px_ulong)|Échange d’une propriété de contrôle de type **ULONG**.|
|[PX_UShort](#px_ushort)|Échange d’une propriété de contrôle de type **USHORT**.|
|[PXstring (en)](#px_string)|Échange une propriété de contrôle des cordes de caractère.|
|[PX_VBXFontConvert](#px_vbxfontconvert)|Échange les propriétés de police d’un contrôle VBX dans une propriété de police de contrôle OLE.|

En outre, `AfxOleTypeMatchGuid` la fonction globale est fournie pour tester un match entre un TYPEDESC et un GUID donné.

## <a name="px_blob"></a><a name="px_blob"></a>PX_Blob

Appelez cette fonction dans `DoPropExchange` la fonction membre de votre contrôle pour sérialiser ou initialiser une propriété qui stocke les données binaires de gros objets (BLOB).

```cpp
BOOL PX_Blob(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    HGLOBAL& hBlob,
    HGLOBAL hBlobDefault = NULL);
```

### <a name="parameters"></a>Paramètres

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*hBlob (hBlob)*<br/>
Référence à la variable où la propriété est stockée (généralement une variable membre de votre classe).

*hBlobDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété sera lue ou écrite à la variable référencée par *hBlob*, le cas échéant. Cette variable doit être parasitée à NULL avant d’appeler `PX_Blob` initialement pour la première fois (généralement, cela peut être fait dans le constructeur du contrôle). Si *hBlobDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour quelque raison que ce soit, le processus d’initialisation ou de sérialisation du contrôle échoue.

Les poignées *hBlob* et *hBlobDefault* se réfèrent à un bloc de mémoire qui contient ce qui suit:

- Un DWORD qui contient la longueur, dans les octets, des données binaires qui suit, suivi immédiatement par

- Un bloc de mémoire contenant les données binaires réelles.

Notez `PX_Blob` que vous allouerez la mémoire, en utilisant l’API Windows [GlobalAlloc,](/windows/win32/api/winbase/nf-winbase-globalalloc) lors du chargement des propriétés de type BLOB. Vous êtes responsable de la libération de cette mémoire. Par conséquent, le destructeur de votre contrôle devrait appeler [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) sur toutes les poignées de propriété de type BLOB pour libérer toute mémoire allouée à votre contrôle.

## <a name="px_bool"></a><a name="px_bool"></a>PX_Bool

Appelez cette fonction dans `DoPropExchange` la fonction de membre de votre contrôle pour sérialiser ou initialiser une propriété de type BOOL.

```cpp
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

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*bValue (en)*<br/>
Référence à la variable où la propriété est stockée (généralement une variable membre de votre classe).

*bDefault (en)*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété sera lue ou écrite à la variable référencée par *bValue*, le cas échéant. Si *bDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour quelque raison que ce soit, le processus de sérialisation du contrôle échoue.

## <a name="px_color"></a><a name="px_color"></a>PX_Color

Appelez cette fonction dans `DoPropExchange` la fonction de membre de votre contrôle pour sérialiser ou initialiser une propriété de type OLE_COLOR.

```cpp
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

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*clrValue*<br/>
Référence à la variable où la propriété est stockée (généralement une variable membre de votre classe).

*clrDefault*<br/>
Valeur par défaut pour la propriété, telle que définie par le développeur de contrôle.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété sera lue ou écrite à la variable référencée par *clrValue*, le cas échéant. Si *clrDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour quelque raison que ce soit, le processus de sérialisation du contrôle échoue.

## <a name="px_currency"></a><a name="px_currency"></a>PX_Currency

Appelez cette fonction dans `DoPropExchange` la fonction de membre de votre contrôle pour sérialiser ou initialiser une propriété de type **monnaie**.

```cpp
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

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*cyValue (en)*<br/>
Référence à la variable où la propriété est stockée (généralement une variable membre de votre classe).

*cyDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété sera lue ou écrite à la variable référencée par *cyValue*, le cas échéant. Si *cyDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour quelque raison que ce soit, le processus de sérialisation du contrôle échoue.

## <a name="px_datapath"></a><a name="px_datapath"></a>PX_DataPath

Appelez cette fonction dans `DoPropExchange` la fonction de membre de votre contrôle pour sérialiser ou initialiser une propriété de chemin de données de type [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md).

```cpp
BOOL PX_DataPath(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CDataPathProperty& dataPathProperty);

BOOL PX_DataPath(
    CPropExchange* pPX,
    CDataPathProperty& dataPathProperty);
```

### <a name="parameters"></a>Paramètres

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*donnéesPathProperty*<br/>
Référence à la variable où la propriété est stockée (généralement une variable membre de votre classe).

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

Les propriétés de trajectoire de données implémenter des propriétés de contrôle asynchrones. La valeur de la propriété sera lue ou écrite à la variable référencée par *dataPathProperty*, le cas échéant.

## <a name="px_double"></a><a name="px_double"></a>PX_Double

Appelez cette fonction dans `DoPropExchange` la fonction de membre de votre contrôle pour sérialiser ou initialiser une propriété de type **double**.

```cpp
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

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*Doublevalue*<br/>
Référence à la variable où la propriété est stockée (généralement une variable membre de votre classe).

*doubleDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue ou écrite à la variable référencée par *doubleValue*, le cas échéant. Si *doubleDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour quelque raison que ce soit, le processus de sérialisation du contrôle échoue.

## <a name="px_font"></a><a name="px_font"></a>PX_Font

Appelez cette fonction dans `DoPropExchange` la fonction de membre de votre contrôle pour sérialiser ou initialiser une propriété de police de type.

```cpp
BOOL PX_Font(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC FAR* pFontDesc = NULL,
    LPFONTDISP pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Paramètres

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*Polices*<br/>
Une référence `CFontHolder` à un objet qui contient la propriété de police.

*pFontDesc (en)*<br/>
Un pointeur `FONTDESC` vers une structure contenant les valeurs à utiliser en initialisant l’état par défaut de la propriété de police, dans le cas où *pFontDispAmbient* est NULL.

*pFontDispAmbient*<br/>
Un pointeur `IFontDisp` à l’interface d’une police à utiliser en initialisant l’état par défaut de la propriété de police.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est `font`lue ou écrite à , une `CFontHolder` référence, le cas échéant. Si *pFontDesc* et *pFontDispAmbient* sont spécifiés, ils sont utilisés pour initialiser la valeur par défaut de la propriété, en cas de besoin. Ces valeurs sont utilisées si, pour quelque raison que ce soit, le processus de sérialisation du contrôle échoue. Typiquement, vous passez NULL pour *pFontDesc* et `COleControl::AmbientFont` la valeur ambiante retournée par pour *pFontDispAmbient*. Notez que l’objet de police retourné `COleControl::AmbientFont` `IFontDisp::Release` par doit être libéré par un appel à la fonction membre.

## <a name="px_float"></a><a name="px_float"></a>PX_Float

Appelez cette fonction dans `DoPropExchange` la fonction de membre de votre contrôle pour sérialiser ou initialiser une propriété de type **flotteur**.

```cpp
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

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*floatValue*<br/>
Référence à la variable où la propriété est stockée (généralement une variable membre de votre classe).

*floatDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue ou écrite à la variable référencée par *floatValue*, le cas échéant. Si *floatDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour quelque raison que ce soit, le processus de sérialisation du contrôle échoue.

## <a name="px_iunknown"></a><a name="px_iunknown"></a>PX_IUnknown

Appelez cette fonction dans `DoPropExchange` la fonction membre de votre contrôle pour sérialiser ou initialiser une propriété représentée par un objet ayant une `IUnknown`interface dérivée.

```cpp
BOOL PX_IUnknown(
    CPropExchange* pPX,
    LPCTSTR pszPropName,
    LPUNKNOWN& pUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault = NULL);
```

### <a name="parameters"></a>Paramètres

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*Punk*<br/>
Référence à une variable contenant l’interface de l’objet qui représente la valeur de la propriété.

*Iid*<br/>
Un ID d’interface indiquant quelle interface de l’objet de propriété est utilisé par le contrôle.

*pUnkDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue ou écrite à la variable référencée par *pUnk*, le cas échéant. Si *pUnkDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour quelque raison que ce soit, le processus de sérialisation du contrôle échoue.

## <a name="px_long"></a><a name="px_long"></a>PX_Long

Appelez cette fonction dans `DoPropExchange` la fonction de membre de votre contrôle pour sérialiser ou initialiser une propriété de type **long**.

```cpp
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

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*lValue (en)*<br/>
Référence à la variable où la propriété est stockée (généralement une variable membre de votre classe).

*lDefault (en)*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue ou écrite à la variable référencée par *lValue*, le cas échéant. Si *lDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour quelque raison que ce soit, le processus de sérialisation du contrôle échoue.

## <a name="px_picture"></a><a name="px_picture"></a>PX_Picture

Appelez cette fonction dans `DoPropExchange` la fonction de membre de votre contrôle pour sérialiser ou initialiser une propriété d’image de votre contrôle.

```cpp
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

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*Pict*<br/>
Référence à un objet [CPictureHolder](../../mfc/reference/cpictureholder-class.md) où la propriété est stockée (généralement une variable membre de votre classe).

*pictDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue ou écrite à la variable référencée par *pict,* le cas échéant. Si *pictDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour quelque raison que ce soit, le processus de sérialisation du contrôle échoue.

## <a name="px_short"></a><a name="px_short"></a>PX_Short

Appelez cette fonction dans `DoPropExchange` la fonction de membre de votre contrôle pour sérialiser ou initialiser une propriété de type **court**.

```cpp
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

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*sValue (en)*<br/>
Référence à la variable où la propriété est stockée (généralement une variable membre de votre classe).

*sDefault (en)*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue ou écrite à la variable référencée par *sValue*, le cas échéant. Si *sDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour quelque raison que ce soit, le processus de sérialisation du contrôle échoue.

## <a name="px_ulong"></a><a name="px_ulong"></a>PX_ULong

Appelez cette fonction dans `DoPropExchange` la fonction de membre de votre contrôle pour sérialiser ou initialiser une propriété de type **ULONG**.

```cpp
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

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*pszPropName (en)*<br/>
Nom de la propriété échangée.

*ulValue ulValue*<br/>
Référence à la variable où la propriété est stockée (généralement une variable membre de votre classe).

*ulDefault ulDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue ou écrite à la variable référencée par *ulValue*, le cas échéant. Si *ulDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour quelque raison que ce soit, le processus de sérialisation du contrôle échoue.

## <a name="px_ushort"></a><a name="px_ushort"></a>PX_UShort

Appelez cette fonction dans `DoPropExchange` la fonction de membre de votre contrôle pour sérialiser ou initialiser une propriété de type **non signé court**.

```cpp
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

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*pszPropName (en)*<br/>
Nom de la propriété échangée.

*usValue*<br/>
Référence à la variable où la propriété est stockée (généralement une variable membre de votre classe).

*usDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue ou écrite à la variable référencée par *usValue*, le cas échéant. Si *usDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour quelque raison que ce soit, le processus de sérialisation du contrôle échoue.

## <a name="pxstring"></a><a name="px_string"></a>PXstring (en)

Appelez cette fonction dans `DoPropExchange` la fonction de membre de votre contrôle pour sérialiser ou initialiser une propriété de chaîne de caractères.

```cpp
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

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*strValue*<br/>
Référence à la variable où la propriété est stockée (généralement une variable membre de votre classe).

*strDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue ou écrite à la variable référencée par *strValue*, le cas échéant. Si *strDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour quelque raison que ce soit, le processus de sérialisation du contrôle échoue.

## <a name="px_vbxfontconvert"></a><a name="px_vbxfontconvert"></a>PX_VBXFontConvert

Appelez cette fonction dans `DoPropExchange` la fonction de membre de votre contrôle pour initialiser une propriété de police en convertissant les propriétés de police d’un contrôle VBX.

```cpp
BOOL PX_VBXFontConvert(
    CPropExchange* pPX,
    CFontHolder& font);
```

### <a name="parameters"></a>Paramètres

*Ppx*<br/>
Pointeur à l’objet [CPropExchange](../../mfc/reference/cpropexchange-class.md) (généralement passé comme un paramètre à `DoPropExchange`).

*Polices*<br/>
La propriété de police du contrôle OLE qui contiendra les propriétés liées à la police VBX converties.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction ne doit être utilisée que par un contrôle OLE qui est conçu comme un remplacement direct pour un contrôle VBX. Lorsque l’environnement de développement Visual Basic convertit un formulaire contenant un contrôle VBX pour `IDataObject::SetData` utiliser le contrôle OLE de remplacement correspondant, il appellera la fonction du contrôle, en passant dans un ensemble de propriété qui contient les données de propriété du contrôle VBX. Cette opération, à son tour, `DoPropExchange` provoque l’invoquage de la fonction du contrôle. `DoPropExchange`peut `PX_VBXFontConvert` appeler à convertir les propriétés de police du contrôle VBX (par exemple, «FontName», «FontSize», et ainsi de suite) en composants correspondants de la propriété de police du contrôle OLE.

`PX_VBXFontConvert`ne doit être appelé que lorsque le contrôle est effectivement converti à partir d’une application de formulaire VBX. Par exemple :

[!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
