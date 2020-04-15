---
title: COlePropertiesDialog, classe
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
ms.openlocfilehash: f065894ff49af755ab4020f71b0213b19db49054
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374892"
---
# <a name="colepropertiesdialog-class"></a>COlePropertiesDialog, classe

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
|[COlePropertiesDialog::DoModal](#domodal)|Affiche la boîte de dialogue et permet à l’utilisateur de faire une sélection.|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Appelé par le cadre lorsque la mise à l’échelle de l’élément du document a changé.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|Une structure utilisée pour initialiser la `COlePropertiesDialog` page " Générale " d’un objet.|
|[COlePropertiesDialog::m_lp](#m_lp)|Une structure utilisée pour initialiser la `COlePropertiesDialog` page "Link" d’un objet.|
|[COlePropertiesDialog::m_op](#m_op)|Une structure utilisée pour `COlePropertiesDialog` initialiser l’objet.|
|[COlePropertiesDialog::m_psh](#m_psh)|Une structure utilisée pour ajouter des pages de propriété personnalisées supplémentaires.|
|[COlePropertiesDialog::m_vp](#m_vp)|Une structure utilisée pour personnaliser la page `COlePropertiesDialog` "Voir" d’un objet.|

## <a name="remarks"></a>Notes

Les boîtes communes de dialogue OLE Object Properties offrent un moyen facile d’afficher et de modifier les propriétés d’un élément de document OLE d’une manière conforme aux normes Windows. Ces propriétés comprennent, entre autres, des informations sur le fichier représenté par l’élément document, des options pour afficher l’icône et la mise à l’échelle de l’image, et des informations sur le lien de l’élément (si l’élément est lié).

Pour utiliser `COlePropertiesDialog` un objet, créez `COlePropertiesDialog` d’abord l’objet à l’aide du constructeur. Une fois la boîte de dialogue `DoModal` construite, appelez la fonction membre pour afficher la boîte de dialogue et permettre à l’utilisateur de modifier toutes les propriétés de l’élément. `DoModal`l’utilisateur a choisi le bouton OK (IDOK) ou le bouton Annuler (IDCANCEL). En plus des boutons OK et Annuler, il y a un bouton Apply. Lorsque l’utilisateur sélectionne Apply, toutes les modifications apportées aux propriétés de l’élément document sont appliquées à l’élément et son image est automatiquement mise à jour, mais reste active.

Le [membre m_psh](#m_psh) de données est `PROPSHEETHEADER` un pointeur vers une structure, et dans la plupart des cas, vous n’aurez pas besoin d’y accéder explicitement. Une exception est lorsque vous avez besoin de pages de propriété supplémentaires au-delà des pages générales, afficher et lien par défaut. Dans ce cas, vous `m_psh` pouvez modifier le membre des `DoModal` données pour inclure vos pages personnalisées avant d’appeler la fonction membre.

Pour plus d’informations sur les boîtes de dialogue OLE, voir l’article [Dialog Boxes in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxodlgs.h

## <a name="colepropertiesdialogcolepropertiesdialog"></a><a name="colepropertiesdialog"></a>COlePropertiesDialog::COlePropertiesDialog

Crée un objet `COlePropertiesDialog` .

```
COlePropertiesDialog(
    COleClientItem* pItem,
    UINT nScaleMin = 10,
    UINT nScaleMax = 500,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*pItem (en)*<br/>
Pointeur vers l’élément document dont les propriétés sont accessibles.

*nScaleMin (en)*<br/>
Pourcentage minimal d’échelle pour l’image de l’élément document.

*nScaleMax (en)*<br/>
Pourcentage maximal de mise à l’échelle pour l’image de l’élément document.

*pParentWnd*<br/>
Pointeur vers le parent ou le propriétaire de la boîte de dialogue.

### <a name="remarks"></a>Notes

Dérivez votre classe commune de `COlePropertiesDialog` dialogue OLE Object Properties afin d’implémenter la mise à l’échelle pour vos éléments de document. Toutes les cases de dialogue mises en œuvre par un exemple de cette classe ne soutiendront pas la mise à l’échelle de l’élément document.

Par défaut, la boîte commune de dialogue OLE Object Properties a trois pages par défaut :

- Général

   Cette page contient des informations système pour le fichier représenté par l’élément de document sélectionné. À partir de cette page, l’utilisateur peut convertir l’élément sélectionné en un autre type.

- Affichage

   Cette page contient des options pour afficher l’élément, changer l’icône et modifier la mise à l’échelle de l’image.

- Lien

   Cette page contient des options pour modifier l’emplacement de l’élément lié et mettre à jour l’élément lié. A partir de cette page, l’utilisateur peut briser le lien de l’élément sélectionné.

Pour ajouter des pages au-delà [m_psh](#m_psh) de celles fournies par défaut, modifiez `COlePropertiesDialog`la variable m_psh membre avant de quitter le constructeur de votre classe dérivée. Il s’agit d’une mise en œuvre avancée du `COlePropertiesDialog` constructeur.

## <a name="colepropertiesdialogdomodal"></a><a name="domodal"></a>COlePropertiesDialog::DoModal

Appelez cette fonction membre pour afficher la boîte de dialogue OLE Object Properties commune de Windows et permettre à l’utilisateur de visualiser et/ou de modifier les différentes propriétés de l’élément document.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

IDOK ou IDCANCEL en cas de succès; sinon 0. IDOK et IDCANCEL sont des constantes qui indiquent si l’utilisateur a choisi le bouton OK ou Annuler.

Si IDCANCEL est retourné, vous pouvez appeler la fonction Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) pour déterminer si une erreur s’est produite.

## <a name="colepropertiesdialogm_gp"></a><a name="m_gp"></a>COlePropertiesDialog::m_gp

Une structure de type [OLEUIGNRLPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuignrlpropsw), utilisée pour initialiser la page générale de la boîte de dialogue OLE Object Properties.

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>Notes

Cette page montre le type et la taille d’une intégration et permet à l’utilisateur d’accéder à la boîte de dialogue Convert. Cette page affiche également la destination de lien si l’objet est un lien.

Pour plus d’informations sur la `OLEUIGNRLPROPS` structure, voir le SDK Windows.

## <a name="colepropertiesdialogm_lp"></a><a name="m_lp"></a>COlePropertiesDialog::m_lp

Une structure de type [OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw), utilisée pour initialiser la page Link de la boîte de dialogue OLE Object Properties.

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>Notes

Cette page affiche l’emplacement de l’élément lié et permet à l’utilisateur de mettre à jour ou de casser le lien vers l’élément.

Pour plus d’informations sur la `OLEUILINKPROPS` structure, voir le SDK Windows.

## <a name="colepropertiesdialogm_op"></a><a name="m_op"></a>COlePropertiesDialog::m_op

Une structure de type [OLEUIOBJECTPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiobjectpropsw), utilisée pour initialiser la boîte commune de dialogue OLE Object Properties.

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>Notes

Cette structure contient des membres utilisés pour initialiser les pages Générale, Lien et Vue.

Pour plus d’informations, consultez les structures OLEUIOBJECTPROPS et [OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw) dans le SDK Windows.

## <a name="colepropertiesdialogm_psh"></a><a name="m_psh"></a>COlePropertiesDialog::m_psh

Une structure de type [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2), dont les membres stockent les caractéristiques de l’objet de dialogue.

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>Notes

Après la `COlePropertiesDialog` construction d’un `m_psh` objet, vous pouvez utiliser pour `DoModal` définir divers aspects de la boîte de dialogue avant d’appeler la fonction membre.

Si vous `m_psh` modifiez directement le membre des données, vous remplacerez tout comportement par défaut.

Pour plus d’informations sur la `PROPSHEETHEADER` structure, voir le SDK Windows.

## <a name="colepropertiesdialogm_vp"></a><a name="m_vp"></a>COlePropertiesDialog::m_vp

Une structure de type [OLEUIVIEWPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiviewpropsw), utilisée pour initialiser la page Vue de la boîte de dialogue OLE Object Properties.

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>Notes

Cette page permet à l’utilisateur de basculer entre les vues « contenu » et « iconiques » de l’objet, et de modifier sa mise à l’échelle dans le conteneur. Il permet également à l’utilisateur d’accéder à la boîte de dialogue Change Icon lorsque l’objet est affiché comme une icône.

Pour plus d’informations sur la `OLEUIVIEWPROPS` structure, voir le SDK Windows.

## <a name="colepropertiesdialogonapplyscale"></a><a name="onapplyscale"></a>COlePropertiesDialog::OnApplyScale

Appelé par le cadre lorsque la valeur de mise à l’échelle a changé et soit OK ou Apply a été sélectionné.

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>Paramètres

*pItem (en)*<br/>
Pointeur vers l’élément document dont les propriétés sont accessibles.

*nCurrentScale (en)*<br/>
Valeur numérique de l’échelle de dialogue.

*bRelativeToOrig*<br/>
Indique si la mise à l’échelle s’applique à la taille originale de l’élément document.

### <a name="return-value"></a>Valeur de retour

Nonzero s’il est manipulé; sinon 0.

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération. Vous devez remplacer cette fonction pour activer les contrôles d’échelle.

> [!NOTE]
> Avant que la boîte commune de dialogue OLE Object Properties ne soit affichée, le cadre appelle cette fonction avec un NULL pour *pItem* et un - 1 pour *nCurrentScale*. Ceci est fait pour déterminer si les contrôles de mise à l’échelle doivent être activés.

## <a name="see-also"></a>Voir aussi

[MFC Échantillon CIRC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage, classe](../../mfc/reference/cpropertypage-class.md)
