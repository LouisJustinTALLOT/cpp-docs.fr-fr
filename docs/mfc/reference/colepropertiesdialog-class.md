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
ms.openlocfilehash: bdae64ff4a7bcfef761eaf3dd70a85a54efc28b7
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916957"
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
|[COlePropertiesDialog::DoModal](#domodal)|Affiche la boîte de dialogue et permet à l’utilisateur d’effectuer une sélection.|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Appelé par le Framework lorsque la mise à l’échelle de l’élément de document a changé.|

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|Structure utilisée pour initialiser la page «général» d’un `COlePropertiesDialog` objet.|
|[COlePropertiesDialog::m_lp](#m_lp)|Structure utilisée pour initialiser la page de liaison d’un `COlePropertiesDialog` objet.|
|[COlePropertiesDialog::m_op](#m_op)|Structure utilisée pour initialiser l' `COlePropertiesDialog` objet.|
|[COlePropertiesDialog::m_psh](#m_psh)|Structure utilisée pour ajouter des pages de propriétés personnalisées supplémentaires.|
|[COlePropertiesDialog::m_vp](#m_vp)|Structure utilisée pour personnaliser la page d’affichage d’un `COlePropertiesDialog` objet.|

## <a name="remarks"></a>Notes

Les boîtes de dialogue Propriétés d’objet OLE communes permettent d’afficher et de modifier facilement les propriétés d’un élément de document OLE d’une manière cohérente avec les normes Windows. Ces propriétés incluent, entre autres, des informations sur le fichier représenté par l’élément de document, des options pour l’affichage de l’icône et de la mise à l’échelle de l’image, ainsi que des informations sur le lien de l’élément (si l’élément est lié).

Pour utiliser un `COlePropertiesDialog` objet, commencez par créer l’objet à `COlePropertiesDialog` l’aide du constructeur. Une fois la boîte de dialogue construite, appelez la `DoModal` fonction membre pour afficher la boîte de dialogue et permettre à l’utilisateur de modifier les propriétés de l’élément. `DoModal`retourne une valeur indiquant si l’utilisateur a sélectionné le bouton OK (IDOK) ou CANCEL (IDCANCEL). En plus des boutons OK et annuler, il existe un bouton appliquer. Quand l’utilisateur sélectionne appliquer, toute modification apportée aux propriétés de l’élément de document est appliquée à l’élément et son image est mise à jour automatiquement, mais reste active.

Le membre de données [m_psh](#m_psh) est un pointeur vers `PROPSHEETHEADER` une structure. dans la plupart des cas, vous n’aurez pas besoin d’y accéder explicitement. Une exception est quand vous avez besoin de pages de propriétés supplémentaires au-delà des pages général, vue et lien par défaut. Dans ce cas, vous pouvez modifier le `m_psh` membre de données pour inclure vos pages personnalisées avant `DoModal` d’appeler la fonction membre.

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

**En-tête:** afxodlgs. h

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
Pointeur vers l’élément de document dont les propriétés sont accessibles.

*nScaleMin*<br/>
Pourcentage de mise à l’échelle minimal pour l’image de l’élément de document.

*nScaleMax*<br/>
Pourcentage de mise à l’échelle maximal pour l’image de l’élément de document.

*pParentWnd*<br/>
Pointeur vers le parent ou le propriétaire de la boîte de dialogue.

### <a name="remarks"></a>Notes

Dérivez votre classe de boîte de dialogue `COlePropertiesDialog` des propriétés de l’objet OLE courante de pour implémenter la mise à l’échelle de vos éléments de document. Les boîtes de dialogue implémentées par une instance de cette classe ne prennent pas en charge la mise à l’échelle de l’élément de document.

Par défaut, la boîte de dialogue Propriétés de l’objet OLE commun comporte trois pages par défaut:

- Généralités

   Cette page contient des informations système pour le fichier représenté par l’élément de document sélectionné. À partir de cette page, l’utilisateur peut convertir l’élément sélectionné en un autre type.

- Vue

   Cette page contient des options pour l’affichage de l’élément, la modification de l’icône et la modification de la mise à l’échelle de l’image.

- Lien

   Cette page contient des options permettant de modifier l’emplacement de l’élément lié et de mettre à jour l’élément lié. À partir de cette page, l’utilisateur peut rompre le lien de l’élément sélectionné.

Pour ajouter des pages au-delà de celles fournies par défaut, modifiez la variable de membre [m_psh](#m_psh) avant de `COlePropertiesDialog`quitter le constructeur de votre classe dérivée de. Il s’agit d’une implémentation avancée `COlePropertiesDialog` du constructeur.

##  <a name="domodal"></a>  COlePropertiesDialog::DoModal

Appelez cette fonction membre pour afficher la boîte de dialogue Propriétés de l’objet OLE commun de Windows et permettre à l’utilisateur d’afficher et/ou de modifier les différentes propriétés de l’élément de document.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

IDOK ou IDCANCEL en cas de réussite; Sinon, 0. IDOK et IDCANCEL sont des constantes qui indiquent si l’utilisateur a sélectionné le bouton OK ou annuler.

Si IDCANCEL est retourné, vous pouvez appeler la fonction [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) de Windows pour déterminer si une erreur s’est produite.

##  <a name="m_gp"></a>  COlePropertiesDialog::m_gp

Structure de type [OLEUIGNRLPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuignrlpropsa), utilisée pour initialiser la page général de la boîte de dialogue Propriétés de l’objet OLE.

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>Notes

Cette page affiche le type et la taille d’une incorporation et permet à l’utilisateur d’accéder à la boîte de dialogue convertir. Cette page affiche également la destination du lien si l’objet est un lien.

Pour plus d’informations sur `OLEUIGNRLPROPS` la structure, consultez le SDK Windows.

##  <a name="m_lp"></a>COlePropertiesDialog::m_lp

Structure de type [OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa), utilisée pour initialiser la page de liaison de la boîte de dialogue Propriétés de l’objet OLE.

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>Notes

Cette page affiche l’emplacement de l’élément lié et permet à l’utilisateur de mettre à jour ou rompre le lien vers l’élément.

Pour plus d’informations sur `OLEUILINKPROPS` la structure, consultez le SDK Windows.

##  <a name="m_op"></a>COlePropertiesDialog::m_op

Structure de type [OLEUIOBJECTPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiobjectpropsa), utilisée pour initialiser la boîte de dialogue Propriétés de l’objet OLE commun.

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>Notes

Cette structure contient les membres utilisés pour initialiser les pages général, lien et vue.

Pour plus d’informations, consultez les structures OLEUIOBJECTPROPS et [OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa) dans la SDK Windows.

##  <a name="m_psh"></a>COlePropertiesDialog::m_psh

Structure de type [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-propsheetheadera_v2), dont les membres stockent les caractéristiques de l’objet Dialog.

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>Notes

Après avoir construit un `COlePropertiesDialog` objet, vous pouvez utiliser `m_psh` pour définir différents aspects de la boîte de dialogue avant d' `DoModal` appeler la fonction membre.

Si vous modifiez directement `m_psh` le membre de données, vous remplacerez tout comportement par défaut.

Pour plus d’informations sur `PROPSHEETHEADER` la structure, consultez le SDK Windows.

##  <a name="m_vp"></a>COlePropertiesDialog::m_vp

Structure de type [OLEUIVIEWPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiviewpropsa), utilisée pour initialiser la page de vue de la boîte de dialogue Propriétés de l’objet OLE.

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>Notes

Cette page permet à l’utilisateur de basculer entre les vues «contenu» et «sous forme» de l’objet, et de modifier sa mise à l’échelle dans le conteneur. Elle permet également à l’utilisateur d’accéder à la boîte de dialogue changer d’icône lorsque l’objet est affiché sous forme d’icône.

Pour plus d’informations sur `OLEUIVIEWPROPS` la structure, consultez le SDK Windows.

##  <a name="onapplyscale"></a>  COlePropertiesDialog::OnApplyScale

Appelé par le Framework lorsque la valeur de mise à l’échelle a changé et que OK ou apply a été sélectionné.

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointeur vers l’élément de document dont les propriétés sont accessibles.

*nCurrentScale*<br/>
Valeur numérique de l’échelle de la boîte de dialogue.

*bRelativeToOrig*<br/>
Indique si la mise à l’échelle s’applique à la taille d’origine de l’élément de document.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si elle est gérée; Sinon, 0.

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération. Vous devez substituer cette fonction pour activer les contrôles de mise à l’échelle.

> [!NOTE]
>  Avant l’affichage de la boîte de dialogue Propriétés de l’objet OLE commun, l’infrastructure appelle cette fonction avec une valeur NULL pour *pItem* et une valeur-1 pour *nCurrentScale*. Cela permet de déterminer si les contrôles de mise à l’échelle doivent être activés.

## <a name="see-also"></a>Voir aussi

[Exemple MFC CIRC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDialog, classe](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage, classe](../../mfc/reference/cpropertypage-class.md)
