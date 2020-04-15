---
title: Classe CPropExchange
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
ms.openlocfilehash: 7818b15e502bb32640d6b9dbfe1a6e4927c70650
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363991"
---
# <a name="cpropexchange-class"></a>Classe CPropExchange

Prend en charge l'implémentation de la persistance de vos contrôles OLE.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CPropExchange
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|Échange d’une propriété binaire grand objet (BLOB).|
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|Échange d’une propriété de police.|
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|Échange d’une propriété entre un contrôle et un fichier.|
|[CPropExchange::ExchangeProp](#exchangeprop)|Échange des propriétés de tout type intégré.|
|[CPropExchange::ExchangeVersion](#exchangeversion)|Échange le numéro de version d’un contrôle OLE.|
|[CPropExchange::GetVersion](#getversion)|Récupère le numéro de version d’un contrôle OLE.|
|[CPropExchange::IsAsynchrone](#isasynchronous)|Détermine si les échanges de propriétés se font asynchroneously.|
|[CPropExchange::IsLoading](#isloading)|Indique si les propriétés sont chargées dans le contrôle ou sauvées de lui.|

## <a name="remarks"></a>Notes

`CPropExchange`n’a pas de classe de base.

Établit le contexte et la direction d’un échange de biens.

La persistance est l’échange des informations d’état du contrôle, généralement représentées par ses propriétés, entre le contrôle lui-même et un support.

Le cadre construit un `CPropExchange` objet dérivé du moment où il est informé que les propriétés d’un contrôle OLE doivent être chargées ou stockées à un stockage persistant.

Le cadre passe un `CPropExchange` pointeur à `DoPropExchange` cet objet à la fonction de votre contrôle. Si vous avez utilisé un assistant pour créer les `DoPropExchange` fichiers `COleControl::DoPropExchange`de démarrage pour votre contrôle, la fonction de votre contrôle appelle . La version de base échange les propriétés des actions du contrôle; vous modifiez la version de votre classe dérivée pour échanger des propriétés que vous avez ajoutées à votre contrôle.

`CPropExchange`peut être utilisé pour sérialiser les propriétés d’un contrôle ou initialiser les propriétés d’un contrôle sur la charge ou la création d’un contrôle. Les `ExchangeProp` `ExchangeFontProp` fonctions et `CPropExchange` les fonctions des membres sont en mesure de stocker des propriétés et de les charger à partir de différents supports.

Pour plus d’informations sur l’utilisation `CPropExchange`, voir l’article [MFC ActiveX Controls: Property Pages](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CPropExchange`

## <a name="requirements"></a>Spécifications

**En-tête:** afxctl.h

## <a name="cpropexchangeexchangeblobprop"></a><a name="exchangeblobprop"></a>CPropExchange::ExchangeBlobProp

Sérialise une propriété qui stocke les données binaires de gros objets (BLOB).

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>Paramètres

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*phBlob*<br/>
Pointeur vers une variable pointant vers l’endroit où la propriété est stockée (variable est généralement un membre de votre classe).

*hBlobDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

La valeur de la propriété est lue ou écrite à, le cas échéant, la variable référencée par *phBlob*. Si *hBlobDefault* est spécifié, il sera utilisé comme valeur par défaut de la propriété. Cette valeur est utilisée si, pour quelque raison que ce soit, la sérialisation du contrôle échoue.

Les fonctions, `CArchivePropExchange::ExchangeBlobProp` `CResetPropExchange::ExchangeBlobProp` `CPropsetPropExchange::ExchangeBlobProp` , et l’emporter sur cette fonction virtuelle pure.

## <a name="cpropexchangeexchangefontprop"></a><a name="exchangefontprop"></a>CPropExchange::ExchangeFontProp

Échange d’une propriété de police entre un support de stockage et le contrôle.

```
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC* pFontDesc,
    LPFONTDISP pFontDispAmbient) = 0;
```

### <a name="parameters"></a>Paramètres

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*Polices*<br/>
Une référence à un objet [CFontHolder](../../mfc/reference/cfontholder-class.md) qui contient la propriété de police.

*pFontDesc (en)*<br/>
Un pointeur d’une structure [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc) contenant des valeurs pour l’initialisation de l’état par défaut de la propriété de police lorsque *pFontDispAmbient* est NULL.

*pFontDispAmbient*<br/>
Un pointeur `IFontDisp` à l’interface d’une police à utiliser pour l’initialisation de l’état par défaut de la propriété de police.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

Si la propriété de police est chargée du milieu au contrôle, les caractéristiques `CFontHolder` de la police sont récupérées à partir du milieu et l’objet référencé par *la police* est initialisé avec eux. Si la propriété de police est stockée, les caractéristiques de l’objet de police sont écrites au support.

Les fonctions, `CArchivePropExchange::ExchangeFontProp` `CResetPropExchange::ExchangeFontProp` `CPropsetPropExchange::ExchangeFontProp` , et l’emporter sur cette fonction virtuelle pure.

## <a name="cpropexchangeexchangepersistentprop"></a><a name="exchangepersistentprop"></a>CPropExchange::ExchangePersistentProp

Échange d’une propriété entre le contrôle et un fichier.

```
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,
    LPUNKNOWN* ppUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault) = 0;
```

### <a name="parameters"></a>Paramètres

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*ppUnk*<br/>
Un pointeur à une variable contenant `IUnknown` un pointeur à l’interface de la propriété (cette variable est généralement un membre de votre classe).

*Iid*<br/>
Interface ID de l’interface sur la propriété que le contrôle utilisera.

*pUnkDefault*<br/>
Valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

Si la propriété est chargée du fichier au contrôle, la propriété est créée et parascée à partir du fichier. Si la propriété est stockée, sa valeur est inscrite au fichier.

Les fonctions, `CArchivePropExchange::ExchangePersistentProp` `CResetPropExchange::ExchangePersistentProp` `CPropsetPropExchange::ExchangePersistentProp` , et l’emporter sur cette fonction virtuelle pure.

## <a name="cpropexchangeexchangeprop"></a><a name="exchangeprop"></a>CPropExchange::ExchangeProp

Échange d’une propriété entre un support de stockage et le contrôle.

```
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,
    VARTYPE vtProp,
    void* pvProp,
    const void* pvDefault = NULL) = 0 ;
```

### <a name="parameters"></a>Paramètres

*pszPropName (en)*<br/>
Le nom de la propriété échangée.

*vtProp (en)*<br/>
Un symbole spécifiant le type de propriété échangée. Les valeurs possibles sont les suivantes :

|Symbole|Type de propriété|
|------------|-------------------|
|VT_I2|**short**|
|VT_I4|**Long**|
|VT_BOOL|**Bool**|
|VT_BSTR|`CString`|
|VT_CY|**CY**|
|VT_R4|**Flotteur**|
|VT_R8|**double**|

*pvProp (en)*<br/>
Un pointeur de la valeur de la propriété.

*pvDefault*<br/>
Pointeur à une valeur par défaut pour la propriété.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’échange a été un succès; 0 en cas d’échec.

### <a name="remarks"></a>Notes

Si la propriété est chargée du milieu au contrôle, la valeur de la propriété est récupérée à partir du milieu et stockée dans l’objet pointé par *pvProp*. Si la propriété est stockée au milieu, la valeur de l’objet pointé par *pvProp* est écrite au milieu.

Les fonctions, `CArchivePropExchange::ExchangeProp` `CResetPropExchange::ExchangeProp` `CPropsetPropExchange::ExchangeProp` , et l’emporter sur cette fonction virtuelle pure.

## <a name="cpropexchangeexchangeversion"></a><a name="exchangeversion"></a>CPropExchange::ExchangeVersion

Appelé par le cadre pour gérer la persistance d’un numéro de version.

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>Paramètres

*dwVersionLoaded*<br/>
Référence à une variable où le nombre de versions des données persistantes chargées sera stocké.

*dwVersionDefault*<br/>
Le numéro de version actuel du contrôle.

*bConvert*<br/>
Indique s’il faut convertir les données persistantes à la version actuelle ou les conserver à la même version qui a été chargée.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction a réussi; 0 autrement.

## <a name="cpropexchangegetversion"></a><a name="getversion"></a>CPropExchange::GetVersion

Appelez cette fonction pour récupérer le numéro de version du contrôle.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Valeur de retour

Le numéro de version du contrôle.

## <a name="cpropexchangeisasynchronous"></a><a name="isasynchronous"></a>CPropExchange::IsAsynchrone

Détermine si les échanges de propriétés se font asynchroneously.

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si les propriétés sont échangées asynchronement, sinon FALSE.

## <a name="cpropexchangeisloading"></a><a name="isloading"></a>CPropExchange::IsLoading

Appelez cette fonction pour déterminer si les propriétés sont chargées au contrôle ou sauvées de celui-ci.

```
BOOL IsLoading();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si les propriétés sont chargées; sinon 0.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleControl::DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
