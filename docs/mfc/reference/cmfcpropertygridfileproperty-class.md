---
title: Cmfcpropertygridfileproperty, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc80d2a40ee9381ad982cd548dddc0702ce7bdad
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390122"
---
# <a name="cmfcpropertygridfileproperty-class"></a>Cmfcpropertygridfileproperty, classe

Le `CMFCPropertyGridFileProperty` classe prend en charge un élément de contrôle de liste de propriétés qui ouvre une boîte de dialogue de sélection de fichier.

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
|`CMFCPropertyGridFileProperty::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|
|`CMFCPropertyGridFileProperty::OnClickButton`|(Substitue [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

### <a name="remarks"></a>Notes

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxpropertygridctrl.h

##  <a name="cmfcpropertygridfileproperty"></a>  CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty

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
[in] Le nom de propriété.

*bOpenFileDialog*<br/>
[in] True pour ouvrir un **ouvrir un fichier** boîte de dialogue ; FALSE pour ouvrir un **enregistrer le fichier** boîte de dialogue.

*strFileName*<br/>
[in] Le nom de fichier initial.

*lpszDefExt*<br/>
[in] Une chaîne d’une ou plusieurs extensions de nom de fichier. La valeur par défaut est NULL.

*dwFlags*<br/>
[in] Indicateurs de boîte de dialogue. La valeur par défaut est une combinaison (OR) au niveau du bit de OFN_HIDEREADONLY et OFN_OVERWRITEPROMPT.

*lpszFilter*<br/>
[in] Une chaîne d’un ou plusieurs filtres de fichier. La valeur par défaut est NULL.

*lpszDescr*<br/>
[in] La description d’élément de propriété. La valeur par défaut est NULL.

*dwData*<br/>
[in] Données spécifiques à l’application qui sont associées à l’élément de propriété. Par exemple, un entier 32 bits ou un pointeur vers d'autres données. La valeur par défaut est 0.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Pour obtenir une liste complète des indicateurs disponibles, consultez [structure OPENFILENAME](/windows/desktop/api/commdlg/ns-commdlg-tagofna).

### <a name="example"></a>Exemple

L'exemple suivant montre comment créer un objet en utilisant le constructeur de la classe `CMFCPropertyGridFileProperty`. Cet exemple fait partie de la [exemple de démonstration Visual Studio](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl, classe](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty, classe](../../mfc/reference/cmfcpropertygridproperty-class.md)
