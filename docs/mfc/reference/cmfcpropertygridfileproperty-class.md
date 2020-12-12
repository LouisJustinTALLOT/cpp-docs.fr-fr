---
description: 'En savoir plus sur : classe CMFCPropertyGridFileProperty'
title: CMFCPropertyGridFileProperty, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
ms.openlocfilehash: c18345876eb49ee2e71d3eb02776212918e5c2c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289944"
---
# <a name="cmfcpropertygridfileproperty-class"></a>CMFCPropertyGridFileProperty, classe

La `CMFCPropertyGridFileProperty` classe prend en charge un élément de contrôle de liste de propriétés qui ouvre une boîte de dialogue de sélection de fichier.

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
|`CMFCPropertyGridFileProperty::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|`CMFCPropertyGridFileProperty::OnClickButton`|(Substitue [CMFCPropertyGridProperty :: OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

### <a name="remarks"></a>Notes

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxpropertygridctrl. h

## <a name="cmfcpropertygridfilepropertycmfcpropertygridfileproperty"></a><a name="cmfcpropertygridfileproperty"></a> CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty

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
dans TRUE pour ouvrir une boîte de dialogue **ouvrir un fichier** ; FALSe pour ouvrir une boîte de dialogue **enregistrer le fichier** .

*strFileName*<br/>
dans Nom de fichier initial.

*lpszDefExt*<br/>
dans Chaîne d’une ou plusieurs extensions de nom de fichier. La valeur par défaut est NULL.

*dwFlags*<br/>
dans Indicateurs de boîte de dialogue. La valeur par défaut est une combinaison (OR) au niveau du bit de OFN_HIDEREADONLY et OFN_OVERWRITEPROMPT.

*lpszFilter*<br/>
dans Chaîne d’un ou plusieurs filtres de fichiers. La valeur par défaut est NULL.

*lpszDescr*<br/>
dans Description de l’élément de propriété. La valeur par défaut est NULL.

*dwData*<br/>
dans Données spécifiques à l’application associées à l’élément de propriété. Par exemple, un entier 32 bits ou un pointeur vers d'autres données. La valeur par défaut est 0.

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

Pour obtenir la liste complète des indicateurs disponibles, consultez la rubrique de la [structure OpenFileName](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

### <a name="example"></a>Exemple

L'exemple suivant montre comment créer un objet en utilisant le constructeur de la classe `CMFCPropertyGridFileProperty`. Cet exemple fait partie de l' [exemple de démonstration Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl, classe](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty, classe](../../mfc/reference/cmfcpropertygridproperty-class.md)
