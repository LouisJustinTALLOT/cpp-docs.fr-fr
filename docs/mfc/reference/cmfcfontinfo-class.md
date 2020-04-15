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
ms.openlocfilehash: 6e87971e2afefc9cf1574abe951920c254dcd2ae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367481"
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
|[CMFCFontInfo::GetFullName](#getfullname)|Récupère les noms concatenated d’une police et de son ensemble de personnages (script).|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCFontInfo:m_nCharSet](#m_ncharset)|Une valeur qui spécifie l’ensemble de personnages (script) associé à la police.|
|[CMFCFontInfo:m_nPitchAndFamily](#m_npitchandfamily)|Une valeur qui spécifie le pitch et la famille de la police.|
|[CMFCFontInfo:m_nType](#m_ntype)|Une valeur qui spécifie le type de police.|
|[CMFCFontInfo:m_strName](#m_strname)|Le nom de la police; par exemple, **Arial**.|
|[CMFCFontInfo:m_strScript](#m_strscript)|Le nom d’un ensemble de personnages (script) associé à la police.|

## <a name="remarks"></a>Notes

Vous pouvez `CMFCFontInfo` joindre un objet à un élément de la classe [CMFCToolBarFontComboBox.](../../mfc/reference/cmfctoolbarfontcombobox-class.md) Appelez la [CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) méthode pour `CMFCFontInfo` récupérer un pointeur à un objet.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser `CMFCFontInfo` divers membres de la classe. L’exemple montre comment `CMFCFontInfo` obtenir un `CMFCRibbonFontComboBox`objet à partir d’un , et comment accéder à ses variables locales. Cet exemple fait partie de [l’échantillon msOffice 2007 Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête:** afxtoolbarfontcombobox.h

## <a name="cmfcfontinfocmfcfontinfo"></a><a name="cmfcfontinfo"></a>CMFCFontInfo::CMFCFontInfo

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

*lpszName (en)*<br/>
[dans] Le nom de la police. Pour plus d’informations, consultez le `lfFaceName` membre de la structure [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*lpszScript*<br/>
[dans] Le nom du script (ensemble de caractères) de la police.

*nCharSet (en anglais)*<br/>
[dans] Une valeur qui spécifie l’ensemble de caractères (script) de la police. Pour plus d’informations, consultez le `lfCharSet` membre de la structure [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*nPitchAndFamily (en)*<br/>
[dans] Une valeur qui spécifie le pitch et la famille de la police. Pour plus d’informations, consultez le `lfPitchAndFamily` membre de la structure [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*nType*<br/>
[dans] Une valeur qui spécifie le type de police. Ce paramètre peut être une combinaison un peu sage (OU) de DEVICE_FONTTYPE, RASTER_FONTTYPE et TRUETYPE_FONTTYPE.

*src*<br/>
[dans] Un `CMFCFontInfo` objet existant dont les `CMFCFontInfo` membres sont utilisés pour construire cet objet.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Cette documentation utilise les termes *ensemble de caractères* et *script* de façon interchangeable. Un *script*, qui est également connu comme un système d’écriture, est une collection de personnages et de règles pour écrire ces personnages dans une ou plusieurs langues. La collection de personnages comprend l’alphabet et la ponctuation utilisée dans ce script. Par exemple, l’écriture latine est utilisée pour l’anglais tel qu’il est parlé aux États-Unis, et son alphabet comprend les caractères de A à Z. Le `lfCharSet` membre de la structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) spécifie un ensemble de personnages. Par exemple, la valeur ANSI_CHARSET spécifie l’ensemble de caractères ANSI, qui comprend l’alphabet de l’écriture latine.

## <a name="cmfcfontinfogetfullname"></a><a name="getfullname"></a>CMFCFontInfo::GetFullName

Récupère les noms concatenated d’une police et de son ensemble de personnages (script).

```
CString GetFullName() const;
```

### <a name="return-value"></a>Valeur de retour

Une chaîne qui contient le nom et le script de la police.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour obtenir le nom complet de la police. Par exemple, si le nom de police est **Arial** et que le script de police est **cyrillique,** cette méthode renvoie "Arial (Cyrillique)".

## <a name="cmfcfontinfom_ncharset"></a><a name="m_ncharset"></a>CMFCFontInfo:m_nCharSet

Une valeur qui spécifie l’ensemble de personnages (script) associé à la police.

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le paramètre *nCharSet* du [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructeur.

## <a name="cmfcfontinfom_npitchandfamily"></a><a name="m_npitchandfamily"></a>CMFCFontInfo:m_nPitchAndFamily

Une valeur qui spécifie le pitch (taille de point) et la famille (par exemple, serif, sans-serif, et monospace) de la police.

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le paramètre *nPitchAndFamily* du [CMFCFontInfo:CMFCFontInfo](#cmfcfontinfo) constructeur.

## <a name="cmfcfontinfom_ntype"></a><a name="m_ntype"></a>CMFCFontInfo:m_nType

Une valeur qui spécifie le type de police.

```
const int m_nType;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le paramètre *nType* du [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructeur.

## <a name="cmfcfontinfom_strname"></a><a name="m_strname"></a>CMFCFontInfo:m_strName

Le nom de la police: par exemple, **Arial**.

```
const CString m_strName;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le paramètre *lpszName* du [CMFCFontInfo:CMFCFontInfo](#cmfcfontinfo) constructeur.

## <a name="cmfcfontinfom_strscript"></a><a name="m_strscript"></a>CMFCFontInfo:m_strScript

Le nom d’un ensemble de personnages (script) associé à la police.

```
const CString m_strScript;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le paramètre *lpszScript* du [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructor.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[Classe CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
