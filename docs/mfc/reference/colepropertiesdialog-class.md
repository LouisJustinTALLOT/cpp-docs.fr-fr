---
title: Colepropertiesdialog, classe
ms.date: 11/04/2016
f1_keywords:
- COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::DoModal
- AFXODLGS/COlePropertiesDialog::OnApplyScale
- AFXODLGS/COlePropertiesDialog::m_gp
- AFXODLGS/COlePropertiesDialog::m_lp
- AFXODLGS/COlePropertiesDialog::m_op
- AFXODLGS/COlePropertiesDialog::m_psh
- AFXODLGS/COlePropertiesDialog::m_vp
helpviewer_keywords:
- COlePropertiesDialog [MFC], COlePropertiesDialog
- COlePropertiesDialog [MFC], DoModal
- COlePropertiesDialog [MFC], OnApplyScale
- COlePropertiesDialog [MFC], m_gp
- COlePropertiesDialog [MFC], m_lp
- COlePropertiesDialog [MFC], m_op
- COlePropertiesDialog [MFC], m_psh
- COlePropertiesDialog [MFC], m_vp
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
ms.openlocfilehash: e40483781427e3135d89a9339a34f606d45db77c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547353"
---
# <a name="colepropertiesdialog-class"></a>Colepropertiesdialog, classe

Encapsule la boîte de dialogue Propriétés d'objet OLE courante Windows.

## <a name="syntax"></a>Syntaxe

```
class COlePropertiesDialog : public COleDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|Construit un objet `COlePropertiesDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COlePropertiesDialog::DoModal](#domodal)|Affiche la boîte de dialogue et permet à l’utilisateur d’effectuer une sélection.|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Appelé par l’infrastructure lors de la mise à l’échelle de l’élément de document a changé.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|Une structure utilisée pour initialiser la page « Générale » d’un `COlePropertiesDialog` objet.|
|[COlePropertiesDialog::m_lp](#m_lp)|Une structure utilisée pour initialiser la page « Lien » d’un `COlePropertiesDialog` objet.|
|[COlePropertiesDialog::m_op](#m_op)|Une structure utilisée pour initialiser le `COlePropertiesDialog` objet.|
|[COlePropertiesDialog::m_psh](#m_psh)|Une structure utilisée pour ajouter des pages de propriétés personnalisées supplémentaires.|
|[COlePropertiesDialog::m_vp](#m_vp)|Une structure utilisée pour personnaliser la page « Vue » d’un `COlePropertiesDialog` objet.|

## <a name="remarks"></a>Notes

Les boîtes de dialogue Propriétés de l’objet OLE communes fournissent un moyen simple pour afficher et modifier les propriétés d’un élément de document OLE de manière cohérente avec les normes de Windows. Ces propriétés incluent, entre autres, des informations sur le fichier représenté par l’élément de document, options d’affichage de l’icône et la mise à l’échelle de l’image et les informations sur le lien de l’élément (si l’élément est lié).

Pour utiliser un `COlePropertiesDialog` d’objet, commencez par créer l’objet en utilisant le `COlePropertiesDialog` constructeur. Une fois que la boîte de dialogue a été construite, appelez le `DoModal` fonction membre pour afficher la boîte de dialogue et de permettre à l’utilisateur modifier les propriétés de l’élément. `DoModal` Retourne si l’utilisateur a sélectionné OK (IDOK) ou sur le bouton Annuler (IDCANCEL). Outre les boutons OK et Annuler, il existe un bouton Appliquer. Lorsque l’utilisateur sélectionne l’appliquer, toutes les modifications apportées aux propriétés de l’élément de document sont appliquées à l’élément et son image est automatiquement mis à jour, mais reste active.

Le [m_psh](#m_psh) membre de données est un pointeur vers un `PROPSHEETHEADER` structure et dans la plupart des cas, vous ne devrez pas y accéder explicitement. Une exception est lorsque vous avez besoin des pages de propriétés supplémentaires au-delà de pages par défaut généraux, vue et de lien. Dans ce cas, vous pouvez modifier le `m_psh` membre de données à inclure vos pages personnalisées avant d’appeler le `DoModal` fonction membre.

Pour plus d’informations sur les boîtes de dialogue OLE, consultez l’article [boîtes de dialogue dans OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxodlgs.h

##  <a name="colepropertiesdialog"></a>  COlePropertiesDialog::COlePropertiesDialog

Crée un objet `COlePropertiesDialog`.

```
COlePropertiesDialog(
    COleClientItem* pItem,
    UINT nScaleMin = 10,
    UINT nScaleMax = 500,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointeur vers l’élément de document dont les propriétés sont en cours d’accès.

*nScaleMin*<br/>
Valeur minimale de la mise à l’échelle de pourcentage pour l’image d’élément de document.

*nScaleMax*<br/>
Valeur maximale de la mise à l’échelle de pourcentage pour l’image d’élément de document.

*pParentWnd*<br/>
Pointeur vers le parent ou le propriétaire de la boîte de dialogue.

### <a name="remarks"></a>Notes

Dérivez votre classe de boîte de dialogue Propriétés de l’objet OLE courants de `COlePropertiesDialog` pour implémenter la mise à l’échelle pour vos éléments de document. Les boîtes de dialogue implémentées par une instance de cette classe ne prendra pas en charge mise à l’échelle de l’élément de document.

Par défaut, la boîte de dialogue Propriétés de l’objet OLE a trois pages par défaut :

- Général

   Cette page contient des informations système pour le fichier représenté par l’élément de document sélectionné. Cette page, l’utilisateur peut convertir l’élément sélectionné vers un autre type.

- Vue

   Cette page contient des options pour afficher l’élément, la modification de l’icône et la modification de la mise à l’échelle de l’image.

- Lien

   Cette page contient des options de modification de l’emplacement de l’élément lié et de la mise à jour de l’élément lié. À partir de cette page, l’utilisateur peut rompre la liaison de l’élément sélectionné.

Pour ajouter des pages au-delà de ceux fournis par défaut, modifiez le [m_psh](#m_psh) variable membre avant de quitter le constructeur de votre `COlePropertiesDialog`-classe dérivée. Il s’agit d’une implémentation avancée de la `COlePropertiesDialog` constructeur.

##  <a name="domodal"></a>  COlePropertiesDialog::DoModal

Appelez cette fonction membre pour afficher la boîte de dialogue Propriétés de l’objet OLE Windows courants et permettre à l’utilisateur afficher et/ou modifier les diverses propriétés de l’élément de document.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

IDOK ou IDCANCEL en cas de réussite ; sinon 0. IDOK et IDCANCEL sont des constantes qui indiquent si l’utilisateur a sélectionné le bouton OK ou sur Annuler.

Si IDCANCEL est retourné, vous pouvez appeler la Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) fonction permettant de déterminer si une erreur s’est produite.

##  <a name="m_gp"></a>  COlePropertiesDialog::m_gp

Une structure de type [OLEUIGNRLPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuignrlpropsa), utilisé pour initialiser la page Général de la boîte de dialogue Propriétés de l’objet OLE.

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>Notes

Cette page affiche le type et la taille d’une imbrication et permet l’accès utilisateur à la boîte de dialogue Convertir. Cette page affiche également la destination du lien si l’objet est un lien.

Pour plus d’informations sur la `OLEUIGNRLPROPS` structure, consultez le kit SDK Windows.

##  <a name="m_lp"></a>  COlePropertiesDialog::m_lp

Une structure de type [OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa), utilisé pour initialiser la page de lien de la boîte de dialogue Propriétés de l’objet OLE.

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>Notes

Cette page affiche l’emplacement de l’élément lié et autorise l’utilisateur à mettre à jour ou une rupture, le lien vers l’élément.

Pour plus d’informations sur la `OLEUILINKPROPS` structure, consultez le kit SDK Windows.

##  <a name="m_op"></a>  COlePropertiesDialog::m_op

Une structure de type [OLEUIOBJECTPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiobjectpropsa), utilisé pour initialiser la boîte de dialogue Propriétés de l’objet OLE.

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>Notes

Cette structure contient les membres utilisés pour initialiser les pages de vue général et lien.

Pour plus d’informations, consultez le OLEUIOBJECTPROPS et [OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa) structures dans le SDK Windows.

##  <a name="m_psh"></a>  COlePropertiesDialog::m_psh

Une structure de type [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2), dont les membres stockent les caractéristiques de l’objet de la boîte de dialogue.

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>Notes

Après avoir construit un `COlePropertiesDialog` de l’objet, vous pouvez utiliser `m_psh` pour définir les divers aspects de la boîte de dialogue avant d’appeler le `DoModal` fonction membre.

Si vous modifiez le `m_psh` membre de données directement, vous remplacerez tout comportement par défaut.

Pour plus d’informations sur la `PROPSHEETHEADER` structure, consultez le kit SDK Windows.

##  <a name="m_vp"></a>  COlePropertiesDialog::m_vp

Une structure de type [OLEUIVIEWPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiviewpropsa), utilisé pour initialiser la page de vue de la boîte de dialogue Propriétés de l’objet OLE.

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>Notes

Cette page permet à l’utilisateur de basculer entre « content » et « sous forme d’icône » vues de l’objet et de modifier sa mise à l’échelle au sein du conteneur. Il permet également l’accès utilisateur à la boîte de dialogue Changer d’icône lorsque l’objet est affiché sous forme d’icône.

Pour plus d’informations sur la `OLEUIVIEWPROPS` structure, consultez le kit SDK Windows.

##  <a name="onapplyscale"></a>  COlePropertiesDialog::OnApplyScale

Appelé par l’infrastructure quand la valeur de mise à l’échelle a changé et OK ou appliquer a été sélectionné.

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointeur vers l’élément de document dont les propriétés sont en cours d’accès.

*nCurrentScale*<br/>
Valeur numérique de l’échelle de la boîte de dialogue.

*bRelativeToOrig*<br/>
Indique si mise à l’échelle s’applique à la taille d’origine de l’élément de document.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si géré ; sinon 0.

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération. Vous devez substituer cette fonction pour activer les contrôles de mise à l’échelle.

> [!NOTE]
>  Avant l’affichage de la boîte de dialogue Propriétés de l’objet OLE, l’infrastructure appelle cette fonction avec une valeur NULL pour *pItem* et - 1 pour *nCurrentScale*. Cela vise à déterminer si les contrôles de mise à l’échelle doivent être activés.

## <a name="see-also"></a>Voir aussi

[Exemple MFC CERC](../../visual-cpp-samples.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage, classe](../../mfc/reference/cpropertypage-class.md)
