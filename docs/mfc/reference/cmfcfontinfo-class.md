---
title: Cmfcfontinfo, classe
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
ms.openlocfilehash: 2377b7f6afdf78a0e8b7c8ac97a36a4920c06bb8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281185"
---
# <a name="cmfcfontinfo-class"></a>Cmfcfontinfo, classe

Le `CMFCFontInfo` classe décrit le nom et autres attributs d’une police.

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
|[CMFCFontInfo::GetFullName](#getfullname)|Récupère les noms concaténés d’une police et son caractère du jeu (script).|

### <a name="data-members"></a>Membres de données

|Name|Description|
|----------|-----------------|
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Une valeur qui spécifie le jeu de caractères (script) associé à la police.|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Une valeur qui spécifie la hauteur et la famille de la police.|
|[CMFCFontInfo::m_nType](#m_ntype)|Une valeur qui spécifie le type de la police.|
|[CMFCFontInfo::m_strName](#m_strname)|Le nom de la police. par exemple, **Arial**.|
|[CMFCFontInfo::m_strScript](#m_strscript)|Le nom d’un jeu de caractères (script) associé à la police.|

## <a name="remarks"></a>Notes

Vous pouvez attacher un `CMFCFontInfo` objet à un élément de la [cmfctoolbarfontcombobox, classe](../../mfc/reference/cmfctoolbarfontcombobox-class.md) classe. Appelez le [CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) méthode pour récupérer un pointeur vers un `CMFCFontInfo` objet.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser les différents membres de la `CMFCFontInfo` classe. L’exemple montre comment obtenir un `CMFCFontInfo` de l’objet à partir d’un `CMFCRibbonFontComboBox`et comment accéder à ses variables locales. Cet exemple fait partie de la [exemple de type 2007 démonstration](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête :** afxtoolbarfontcombobox.h

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
[in] Le nom de la police. Pour plus d’informations, consultez le `lfFaceName` membre de la [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) structure.

*lpszScript*<br/>
[in] Le nom du script (jeu de caractères) de la police.

*nCharSet*<br/>
[in] Une valeur qui spécifie le jeu de caractères (script) de la police. Pour plus d’informations, consultez le `lfCharSet` membre de la [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) structure.

*nPitchAndFamily*<br/>
[in] Une valeur qui spécifie la hauteur et la famille de la police. Pour plus d’informations, consultez le `lfPitchAndFamily` membre de la [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) structure.

*nType*<br/>
[in] Une valeur qui spécifie le type de police. Ce paramètre peut être une combinaison au niveau du bit (ou) de DEVICE_FONTTYPE, RASTER_FONTTYPE et TRUETYPE_FONTTYPE.

*src*<br/>
[in] Un existant `CMFCFontInfo` objet dont les membres sont utilisés pour construire ce `CMFCFontInfo` objet.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Cette documentation utilise les termes du contrat *jeu de caractères* et *script* indifféremment. Un *script*, qui est également connu sous un système d’écriture, est une collection de caractères et des règles pour l’écriture de ces caractères dans une ou plusieurs langues. La collection de caractères inclut l’alphabet et les signes de ponctuation utilisés dans ce script. Par exemple, script Latin est utilisé pour l’anglais comme il est parlé aux États-Unis, et son alphabet inclut les caractères de A à Z. Le `lfCharSet` membre de la [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) structure spécifie un jeu de caractères. Par exemple, la valeur ANSI_CHARSET Spécifie le jeu de caractères ANSI, ce qui inclut l’alphabet du script Latin.

##  <a name="getfullname"></a>  CMFCFontInfo::GetFullName

Récupère les noms concaténés d’une police et son caractère du jeu (script).

```
CString GetFullName() const;
```

### <a name="return-value"></a>Valeur de retour

Chaîne qui contient le nom de la police et le script.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour obtenir le nom complet de la police. Par exemple, si le nom de police est **Arial** et le script de police est **cyrillique**, cette méthode retourne « Arial (cyrillique) ».

##  <a name="m_ncharset"></a>  CMFCFontInfo::m_nCharSet

Une valeur qui spécifie le jeu de caractères (script) associé à la police.

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le *nCharSet* paramètre de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructeur.

##  <a name="m_npitchandfamily"></a>  CMFCFontInfo::m_nPitchAndFamily

Une valeur qui spécifie la hauteur (taille) et la famille (par exemple, serif serif et à espacement fixe) de la police.

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le *nPitchAndFamily* paramètre de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructeur.

##  <a name="m_ntype"></a>  CMFCFontInfo::m_nType

Une valeur qui spécifie le type de la police.

```
const int m_nType;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le *%nLes* paramètre de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructeur.

##  <a name="m_strname"></a>  CMFCFontInfo::m_strName

Le nom de la police : par exemple, **Arial**.

```
const CString m_strName;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le *le caractère* paramètre de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructeur.

##  <a name="m_strscript"></a>  CMFCFontInfo::m_strScript

Le nom d’un jeu de caractères (script) associé à la police.

```
const CString m_strScript;
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le *lpszScript* paramètre de la [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) constructeur.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox, classe](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCToolBarFontSizeComboBox, classe](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
