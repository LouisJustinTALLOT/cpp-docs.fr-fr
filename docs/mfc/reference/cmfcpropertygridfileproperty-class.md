---
title: Classe CMFCPropertyGridFileProperty
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
ms.openlocfilehash: 0ce3321968f0c29ce3b946f6127e4435b531c422
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360581"
---
# <a name="cmfcpropertygridfileproperty-class"></a>Classe CMFCPropertyGridFileProperty

La `CMFCPropertyGridFileProperty` classe prend en charge un élément de contrôle de liste de propriété qui ouvre une boîte de dialogue de sélection de fichiers.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|Construit un objet `CMFCPropertyGridFileProperty`.|
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCPropertyGridFileProperty::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|`CMFCPropertyGridFileProperty::OnClickButton`|(Overrides [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

### <a name="remarks"></a>Notes

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxpropertygridctrl.h

## <a name="cmfcpropertygridfilepropertycmfcpropertygridfileproperty"></a><a name="cmfcpropertygridfileproperty"></a>CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty

Construit un objet `CMFCPropertyGridFileProperty`.

```
CMFCPropertyGridFileProperty(
    const CString& strName,
    BOOL bOpenFileDialog,
    const CString& strFileName,
    LPCTSTR lpszDefExt=NULL,
    DWORD dwFlags=OFN_HIDEREADONLY|OFN_OVERWRITEPROMPT,
    LPCTSTR lpszFilter=NULL,
    LPCTSTR lpszDescr=NULL,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Paramètres

*strName*<br/>
[in] Nom de la propriété.

*bOpenFileDialog*<br/>
[dans] VRAI d’ouvrir une boîte de dialogue **Open File;** FALSE pour ouvrir une boîte de dialogue **Save File.**

*strFileName (en)*<br/>
[dans] Le nom initial du fichier.

*lpszDefExt*<br/>
[dans] Une série d’extensions d’un ou plusieurs noms de fichiers. La valeur par défaut est NULL.

*dwFlags*<br/>
[dans] Drapeaux de boîte de dialogue. La valeur par défaut est une combinaison (OR) au niveau du bit de OFN_HIDEREADONLY et OFN_OVERWRITEPROMPT.

*lpszFilter (lpszFilter)*<br/>
[dans] Une chaîne d’un ou plusieurs filtres de fichiers. La valeur par défaut est NULL.

*lpszDescr*<br/>
[dans] La description de l’article de propriété. La valeur par défaut est NULL.

*dwData dwData*<br/>
[dans] Données spécifiques à l’application qui sont associées à l’élément de propriété. Par exemple, un entier 32 bits ou un pointeur vers d'autres données. La valeur par défaut est 0.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Pour une liste complète des drapeaux disponibles, voir [la structure OPENFILENAME](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

### <a name="example"></a>Exemple

L'exemple suivant montre comment créer un objet en utilisant le constructeur de la classe `CMFCPropertyGridFileProperty`. Cet exemple fait partie de [l’échantillon Visual Studio Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl, classe](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[Classe CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)
