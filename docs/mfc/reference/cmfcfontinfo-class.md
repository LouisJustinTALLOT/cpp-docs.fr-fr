---
title: CMFCFontInfo, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::GetFullName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nCharSet
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nPitchAndFamily
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nType
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strScript
helpviewer_keywords:
- CMFCFontInfo [MFC], GetFullName
- CMFCFontInfo [MFC], m_nCharSet
- CMFCFontInfo [MFC], m_nPitchAndFamily
- CMFCFontInfo [MFC], m_nType
- CMFCFontInfo [MFC], m_strName
- CMFCFontInfo [MFC], m_strScript
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
ms.openlocfilehash: a27606b494b13cd7b50f01b38fa95a918bacc7aa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505275"
---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo, classe

La `CMFCFontInfo` classe décrit le nom et d’autres attributs d’une police.

## <a name="syntax"></a>Syntaxe

```
class CMFCFontInfo : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMFCFontInfo`|Construit un objet `CMFCFontInfo`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCFontInfo:: GetFullName](#getfullname)|Récupère les noms concaténés d’une police et de son jeu de caractères (script).|

### <a name="data-members"></a>Membres de données

|Name|Description|
|----------|-----------------|
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Valeur qui spécifie le jeu de caractères (script) associé à la police.|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Valeur qui spécifie le pas et la famille de la police.|
|[CMFCFontInfo::m_nType](#m_ntype)|Valeur qui spécifie le type de la police.|
|[CMFCFontInfo::m_strName](#m_strname)|Nom de la police; par exemple, **Arial**.|
|[CMFCFontInfo::m_strScript](#m_strscript)|Nom d’un jeu de caractères (script) associé à la police.|

## <a name="remarks"></a>Notes

Vous pouvez attacher un `CMFCFontInfo` objet à un élément de la classe de [classe CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) . Appelez la méthode [CMFCToolBarFontComboBox:: GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) pour récupérer un pointeur vers un `CMFCFontInfo` objet.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser les différents membres de la `CMFCFontInfo` classe. L’exemple montre comment obtenir un `CMFCFontInfo` objet à partir d’un `CMFCRibbonFontComboBox`et comment accéder à ses variables locales. Cet exemple fait partie de l' [exemple de démonstration de MSOffice 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>Configuration requise

**En-tête:** afxtoolbarfontcombobox. h

##  <a name="cmfcfontinfo"></a>  CMFCFontInfo::CMFCFontInfo

Construit un objet `CMFCFontInfo`.

```
CMFCFontInfo(
    LPCTSTR lpszName,
    LPCTSTR lpszScript,
    BYTE nCharSet,
    BYTE nPitchAndFamily,
    int nType);

CMFCFontInfo(const CMFCFontInfo& src);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
dans Nom de la police. Pour plus d’informations, consultez `lfFaceName` le membre de la structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*lpszScript*<br/>
dans Nom du script (jeu de caractères) de la police.

*nCharSet*<br/>
dans Valeur qui spécifie le jeu de caractères (script) de la police. Pour plus d’informations, consultez `lfCharSet` le membre de la structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*nPitchAndFamily*<br/>
dans Valeur qui spécifie le pas et la famille de la police. Pour plus d’informations, consultez `lfPitchAndFamily` le membre de la structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*nType*<br/>
dans Valeur qui spécifie le type de police. Ce paramètre peut être une combinaison au niveau du bit (ou) de DEVICE_FONTTYPE, RASTER_FONTTYPE et TRUETYPE_FONTTYPE.

*src*<br/>
dans Objet existant `CMFCFontInfo` dont les membres sont utilisés pour construire cet `CMFCFontInfo` objet.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Cette documentation utilise les termes *jeu de caractères* et *script* de manière interchangeable. Un *script*, également appelé «système d’écriture», est une collection de caractères et de règles permettant d’écrire ces caractères dans une ou plusieurs langues. La collection de caractères comprend l’alphabet et la ponctuation utilisés dans ce script. Par exemple, le script latin est utilisé pour l’anglais tel qu’il est parlé dans le États-Unis, et son alphabet comprend les caractères de A à Z. Le `lfCharSet` membre de la structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) spécifie un jeu de caractères. Par exemple, la valeur ANSI_CHARSET spécifie le jeu de caractères ANSI, qui comprend l’alphabet du script latin.

##  <a name="getfullname"></a>  CMFCFontInfo::GetFullName

Récupère les noms concaténés d’une police et de son jeu de caractères (script).

```
CString GetFullName() const;
```

### <a name="return-value"></a>Valeur de retour

Chaîne qui contient le nom et le script de la police.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour obtenir le nom complet de la police. Par exemple, si le nom de police est **Arial** et que le script de police est **cyrillique**, cette méthode retourne «Arial (cyrillique)».

##  <a name="m_ncharset"></a>  CMFCFontInfo::m_nCharSet

Valeur qui spécifie le jeu de caractères (script) associé à la police.

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le paramètre *nCharSet* du constructeur [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_npitchandfamily"></a>  CMFCFontInfo::m_nPitchAndFamily

Valeur qui spécifie le pas (taille de point) et la famille (par exemple, Serif, sans empattement et monoespace) de la police.

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le paramètre *nPitchAndFamily* du constructeur [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_ntype"></a>  CMFCFontInfo::m_nType

Valeur qui spécifie le type de la police.

```
const int m_nType;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le paramètre *ndéclarations* du constructeur [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_strname"></a>  CMFCFontInfo::m_strName

Nom de la police: par exemple, **Arial**.

```
const CString m_strName;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le paramètre *lpszName* du constructeur [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

##  <a name="m_strscript"></a>  CMFCFontInfo::m_strScript

Nom d’un jeu de caractères (script) associé à la police.

```
const CString m_strScript;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le paramètre *lpszScript* du constructeur [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) .

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox, classe](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCToolBarFontSizeComboBox, classe](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
