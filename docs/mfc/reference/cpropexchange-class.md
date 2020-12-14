---
description: 'En savoir plus sur : classe CPropExchange'
title: CPropExchange, classe
ms.date: 11/04/2016
f1_keywords:
- CPropExchange
- AFXCTL/CPropExchange
- AFXCTL/CPropExchange::ExchangeBlobProp
- AFXCTL/CPropExchange::ExchangeFontProp
- AFXCTL/CPropExchange::ExchangePersistentProp
- AFXCTL/CPropExchange::ExchangeProp
- AFXCTL/CPropExchange::ExchangeVersion
- AFXCTL/CPropExchange::GetVersion
- AFXCTL/CPropExchange::IsAsynchronous
- AFXCTL/CPropExchange::IsLoading
helpviewer_keywords:
- CPropExchange [MFC], ExchangeBlobProp
- CPropExchange [MFC], ExchangeFontProp
- CPropExchange [MFC], ExchangePersistentProp
- CPropExchange [MFC], ExchangeProp
- CPropExchange [MFC], ExchangeVersion
- CPropExchange [MFC], GetVersion
- CPropExchange [MFC], IsAsynchronous
- CPropExchange [MFC], IsLoading
ms.assetid: ed872180-e770-4942-892a-92139d501fab
ms.openlocfilehash: 3e95940a6ba649b134df3cfc79abcf85e03f7e8d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343309"
---
# <a name="cpropexchange-class"></a>CPropExchange, classe

Prend en charge l'implémentation de la persistance de vos contrôles OLE.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CPropExchange
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPropExchange :: ExchangeBlobProp](#exchangeblobprop)|Échange une propriété d’objet BLOB (Binary Large Object).|
|[CPropExchange :: ExchangeFontProp](#exchangefontprop)|Échange une propriété font.|
|[CPropExchange :: ExchangePersistentProp](#exchangepersistentprop)|Échange une propriété entre un contrôle et un fichier.|
|[CPropExchange :: ExchangeProp](#exchangeprop)|Échange les propriétés de tout type intégré.|
|[CPropExchange :: ExchangeVersion](#exchangeversion)|Échange le numéro de version d’un contrôle OLE.|
|[CPropExchange :: GetVersion](#getversion)|Récupère le numéro de version d’un contrôle OLE.|
|[CPropExchange :: IsAsynchronous](#isasynchronous)|Détermine si les échanges de propriétés sont effectués de manière asynchrone.|
|[CPropExchange :: IsLoading](#isloading)|Indique si les propriétés sont chargées dans le contrôle ou enregistrées à partir de celle-ci.|

## <a name="remarks"></a>Notes

`CPropExchange` n’a pas de classe de base.

Établit le contexte et la direction d’un échange de propriétés.

La persistance est l’échange des informations d’État du contrôle, généralement représenté par ses propriétés, entre le contrôle lui-même et un support.

L’infrastructure construit un objet dérivé de `CPropExchange` lorsqu’il est notifié que les propriétés d’un contrôle OLE doivent être chargées à partir de ou stockées dans un stockage persistant.

L’infrastructure passe un pointeur vers cet `CPropExchange` objet à la fonction de votre contrôle `DoPropExchange` . Si vous avez utilisé un Assistant pour créer les fichiers de démarrage pour votre contrôle, la fonction de votre contrôle `DoPropExchange` appelle `COleControl::DoPropExchange` . La version de la classe de base échange les propriétés stock du contrôle ; vous modifiez la version de votre classe dérivée pour échanger les propriétés que vous avez ajoutées à votre contrôle.

`CPropExchange` peut être utilisé pour sérialiser les propriétés d’un contrôle ou initialiser les propriétés d’un contrôle lors du chargement ou de la création d’un contrôle. Les `ExchangeProp` `ExchangeFontProp` fonctions membres et de `CPropExchange` peuvent stocker des propriétés et les charger à partir de différents médias.

Pour plus d’informations sur l’utilisation de `CPropExchange` , consultez l’article [contrôles ActiveX MFC : pages de propriétés](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CPropExchange`

## <a name="requirements"></a>Spécifications

**En-tête :** afxctl. h

## <a name="cpropexchangeexchangeblobprop"></a><a name="exchangeblobprop"></a> CPropExchange :: ExchangeBlobProp

Sérialise une propriété qui stocke des données BLOB (Binary Large Object).

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>Paramètres

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*phBlob*<br/>
Pointeur vers une variable qui pointe vers l’emplacement où la propriété est stockée (la variable est généralement un membre de votre classe).

*hBlobDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue ou écrite dans, selon le cas, la variable référencée par *phBlob*. Si *hBlobDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour une raison quelconque, la sérialisation du contrôle échoue.

Les fonctions `CArchivePropExchange::ExchangeBlobProp` , `CResetPropExchange::ExchangeBlobProp` et `CPropsetPropExchange::ExchangeBlobProp` remplacent cette fonction virtuelle pure.

## <a name="cpropexchangeexchangefontprop"></a><a name="exchangefontprop"></a> CPropExchange :: ExchangeFontProp

Échange une propriété de police entre un support de stockage et le contrôle.

```
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC* pFontDesc,
    LPFONTDISP pFontDispAmbient) = 0;
```

### <a name="parameters"></a>Paramètres

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*son*<br/>
Référence à un objet [CFontHolder](../../mfc/reference/cfontholder-class.md) qui contient la propriété font.

*pFontDesc*<br/>
Pointeur vers une structure [fontdesc](/windows/win32/api/olectl/ns-olectl-fontdesc) contenant des valeurs pour initialiser l’État par défaut de la propriété font lorsque *pFontDispAmbient* a la valeur null.

*pFontDispAmbient*<br/>
Pointeur vers l' `IFontDisp` interface d’une police à utiliser pour initialiser l’État par défaut de la propriété font.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

Si la propriété font est chargée du support au contrôle, les caractéristiques de la police sont extraites du support et l' `CFontHolder` objet référencé par la *police* est initialisé avec eux. Si la propriété font est stockée, les caractéristiques de l’objet font sont écrites sur le support.

Les fonctions `CArchivePropExchange::ExchangeFontProp` , `CResetPropExchange::ExchangeFontProp` et `CPropsetPropExchange::ExchangeFontProp` remplacent cette fonction virtuelle pure.

## <a name="cpropexchangeexchangepersistentprop"></a><a name="exchangepersistentprop"></a> CPropExchange :: ExchangePersistentProp

Échange une propriété entre le contrôle et un fichier.

```
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,
    LPUNKNOWN* ppUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault) = 0;
```

### <a name="parameters"></a>Paramètres

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*ppUnk*<br/>
Pointeur vers une variable qui contient un pointeur vers l’interface de la propriété `IUnknown` (cette variable est généralement un membre de votre classe).

*vaut*<br/>
ID d’interface de l’interface sur la propriété que le contrôle utilisera.

*pUnkDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

Si la propriété est chargée à partir du fichier dans le contrôle, la propriété est créée et initialisée à partir du fichier. Si la propriété est stockée, sa valeur est écrite dans le fichier.

Les fonctions `CArchivePropExchange::ExchangePersistentProp` , `CResetPropExchange::ExchangePersistentProp` et `CPropsetPropExchange::ExchangePersistentProp` remplacent cette fonction virtuelle pure.

## <a name="cpropexchangeexchangeprop"></a><a name="exchangeprop"></a> CPropExchange :: ExchangeProp

Échange une propriété entre un support de stockage et le contrôle.

```
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,
    VARTYPE vtProp,
    void* pvProp,
    const void* pvDefault = NULL) = 0 ;
```

### <a name="parameters"></a>Paramètres

*pszPropName*<br/>
Nom de la propriété en cours d’échange.

*vtProp*<br/>
Symbole spécifiant le type de la propriété en cours d’échange. Les valeurs possibles sont les suivantes :

|Symbole|Type de propriété|
|------------|-------------------|
|VT_I2|**`short`**|
|VT_I4|**`long`**|
|VT_BOOL|**Boolean**|
|VT_BSTR|`CString`|
|VT_CY|**CY**|
|VT_R4|**`float`**|
|VT_R8|**`double`**|

*pvProp*<br/>
Pointeur vers la valeur de la propriété.

*pvDefault*<br/>
Pointeur désignant une valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’échange a réussi ; 0 en cas d’échec.

### <a name="remarks"></a>Notes

Si la propriété est chargée du support au contrôle, la valeur de la propriété est récupérée à partir du support et stockée dans l’objet désigné par *pvProp*. Si la propriété est stockée sur le support, la valeur de l’objet pointé par *pvProp* est écrite sur le support.

Les fonctions `CArchivePropExchange::ExchangeProp` , `CResetPropExchange::ExchangeProp` et `CPropsetPropExchange::ExchangeProp` remplacent cette fonction virtuelle pure.

## <a name="cpropexchangeexchangeversion"></a><a name="exchangeversion"></a> CPropExchange :: ExchangeVersion

Appelé par l’infrastructure pour gérer la persistance d’un numéro de version.

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>Paramètres

*dwVersionLoaded*<br/>
Référence à une variable où le numéro de version des données persistantes en cours de chargement sera stocké.

*dwVersionDefault*<br/>
Numéro de la version actuelle du contrôle.

*bConvert*<br/>
Indique si les données persistantes doivent être converties dans la version actuelle ou conservées dans la même version que celle qui a été chargée.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la fonction a réussi ; Sinon, 0.

## <a name="cpropexchangegetversion"></a><a name="getversion"></a> CPropExchange :: GetVersion

Appelez cette fonction pour récupérer le numéro de version du contrôle.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Valeur renvoyée

Numéro de version du contrôle.

## <a name="cpropexchangeisasynchronous"></a><a name="isasynchronous"></a> CPropExchange :: IsAsynchronous

Détermine si les échanges de propriétés sont effectués de manière asynchrone.

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si les propriétés sont échangées de façon asynchrone ; sinon, FALSe.

## <a name="cpropexchangeisloading"></a><a name="isloading"></a> CPropExchange :: IsLoading

Appelez cette fonction pour déterminer si les propriétés sont chargées dans le contrôle ou enregistrées à partir de celle-ci.

```
BOOL IsLoading();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si les propriétés sont en cours de chargement ; Sinon, 0.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleControl ::D oPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
