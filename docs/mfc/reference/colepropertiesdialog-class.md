---
title: Classe de COlePropertiesDialog | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d61d773e2c35bb67f34ae2b4a989a388d8b4015
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371684"
---
# <a name="colepropertiesdialog-class"></a>Classe de COlePropertiesDialog
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
|[COlePropertiesDialog::DoModal](#domodal)|Affiche la boîte de dialogue et permet à l’utilisateur à effectuer une sélection.|  
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Appelé par l’infrastructure lors de la mise à l’échelle de l’élément de document a changé.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COlePropertiesDialog::m_gp](#m_gp)|Une structure utilisée pour initialiser la page « Générale » d’un `COlePropertiesDialog` objet.|  
|[COlePropertiesDialog::m_lp](#m_lp)|Une structure utilisée pour initialiser la page « Liaison » d’un `COlePropertiesDialog` objet.|  
|[COlePropertiesDialog::m_op](#m_op)|Une structure utilisée pour initialiser le `COlePropertiesDialog` objet.|  
|[COlePropertiesDialog::m_psh](#m_psh)|Structure utilisée pour ajouter des pages de propriétés personnalisées supplémentaires.|  
|[COlePropertiesDialog::m_vp](#m_vp)|Une structure utilisée pour personnaliser la page « Vue » d’un `COlePropertiesDialog` objet.|  
  
## <a name="remarks"></a>Notes  
 Les boîtes de dialogue Propriétés de l’objet OLE communes fournissent un moyen simple pour afficher et modifier les propriétés d’un élément de document OLE de manière cohérente avec les normes de Windows. Ces propriétés comprennent, entre autres, des informations sur le fichier représenté par l’élément de document, options d’affichage de l’icône et la mise à l’échelle de l’image et les informations sur le lien de l’élément (si l’élément est lié).  
  
 Pour utiliser un `COlePropertiesDialog` d’objet, commencez par créer l’objet en utilisant la `COlePropertiesDialog` constructeur. Une fois que la boîte de dialogue a été construite, appelez le `DoModal` fonction membre pour afficher la boîte de dialogue et autoriser l’utilisateur à modifier les propriétés de l’élément. `DoModal` Retourne si l’utilisateur a sélectionné le OK ( **IDOK**) ou l’annulation ( **IDCANCEL**) bouton. Outre les boutons OK et Annuler, il est un bouton Appliquer. Lorsque l’utilisateur sélectionne l’appliquer, toutes les modifications apportées aux propriétés de l’élément de document sont appliquées à l’élément et son image est automatiquement mis à jour, mais reste active.  
  
 Le [m_psh](#m_psh) membre de données est un pointeur vers un **PROPSHEETHEADER** structure et dans la plupart des cas, vous ne devrez pas accéder de manière explicite. Une exception est lorsque vous avez besoin de pages de propriétés supplémentaires au-delà de pages Général, de vue et de lien par défaut. Dans ce cas, vous pouvez modifier le `m_psh` membre de données à inclure vos pages personnalisées avant d’appeler le `DoModal` fonction membre.  
  
 Pour plus d’informations sur les boîtes de dialogue OLE, consultez l’article [boîtes de dialogue OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePropertiesDialog`  
  
## <a name="requirements"></a>Spécifications  
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
 `pItem`  
 Pointeur vers l’élément de document dont les propriétés sont en cours d’accès.  
  
 *nScaleMin*  
 Au minimum de la mise à l’échelle de pourcentage de l’image d’élément de document.  
  
 *nScaleMax*  
 Maximum de pourcentage de l’image d’élément de document de mise à l’échelle.  
  
 `pParentWnd`  
 Pointeur vers le parent ou le propriétaire de la boîte de dialogue.  
  
### <a name="remarks"></a>Notes  
 Dérivez votre classe de boîte de dialogue Propriétés de l’objet OLE courants de `COlePropertiesDialog` pour implémenter la mise à l’échelle des éléments de votre document. Les boîtes de dialogue implémentées par une instance de cette classe ne prendra pas en charge mise à l’échelle de l’élément de document.  
  
 Par défaut, la boîte de dialogue Propriétés de l’objet OLE a trois pages par défaut :  
  
-   Général  
  
     Cette page contient des informations système pour le fichier représenté par l’élément de document sélectionné. Cette page, l’utilisateur peut convertir l’élément sélectionné vers un autre type.  
  
-   Vue  
  
     Cette page contient des options pour afficher l’élément et modifiant l’icône de modification de la mise à l’échelle de l’image.  
  
-   Lien  
  
     Cette page contient des options pour modifier l’emplacement de l’élément lié et de mise à jour de l’élément lié. À partir de cette page, l’utilisateur peut endommager le lien de l’élément sélectionné.  
  
 Pour ajouter des pages au-delà de celles fournies par défaut, modifiez le [m_psh](#m_psh) variable membre avant de quitter le constructeur de votre `COlePropertiesDialog`-classe dérivée. Il s’agit d’une implémentation avancée de la `COlePropertiesDialog` constructeur.  
  
##  <a name="domodal"></a>  COlePropertiesDialog::DoModal  
 Appelez cette fonction membre pour afficher la boîte de dialogue Propriétés de l’objet OLE Windows courants et d’autoriser l’utilisateur à afficher ou modifier les diverses propriétés de l’élément de document.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valeur de retour  
 **IDOK** ou **IDCANCEL** cas de réussite ; sinon, 0. **IDOK** et **IDCANCEL** sont des constantes qui indiquent si l’utilisateur a sélectionné le bouton OK ou sur Annuler.  
  
 Si **IDCANCEL** est retourné, vous pouvez appeler les fenêtres [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) fonction pour déterminer si une erreur s’est produite.  
  
##  <a name="m_gp"></a>  COlePropertiesDialog::m_gp  
 Une structure de type [OLEUIGNRLPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687297), utilisée pour initialiser la page Général de la boîte de dialogue Propriétés de l’objet OLE.  
  
```  
OLEUIGNRLPROPS m_gp;  
```  
  
### <a name="remarks"></a>Notes  
 Cette page affiche le type et la taille d’une incorporation et autorise l’accès utilisateur à la boîte de dialogue de conversion. Cette page affiche également la destination du lien si l’objet est un lien.  
  
 Pour plus d’informations sur la **OLEUIGNRLPROPS** de la structure, consultez le Kit de développement logiciel Windows.  
  
##  <a name="m_lp"></a>  COlePropertiesDialog::m_lp  
 Une structure de type [OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735), utilisée pour initialiser la page de lien de la boîte de dialogue Propriétés de l’objet OLE.  
  
```  
OLEUILINKPROPS m_lp;  
```  
  
### <a name="remarks"></a>Notes  
 Cette page indique l’emplacement de l’élément lié et permet à l’utilisateur à mettre à jour, ou interrompre, le lien vers l’élément.  
  
 Pour plus d’informations sur la **OLEUILINKPROPS** de la structure, consultez le Kit de développement logiciel Windows.  
  
##  <a name="m_op"></a>  COlePropertiesDialog::m_op  
 Une structure de type [OLEUIOBJECTPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687199), utilisée pour initialiser la boîte de dialogue Propriétés de l’objet OLE.  
  
```  
OLEUIOBJECTPROPS m_op;  
```  
  
### <a name="remarks"></a>Notes  
 Cette structure contient les membres utilisés pour initialiser les pages de vue général et lien.  
  
 Pour plus d’informations, consultez la **OLEUIOBJECTPROPS** et [OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735) structures dans le SDK Windows.  
  
##  <a name="m_psh"></a>  COlePropertiesDialog::m_psh  
 Une structure de type [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546), dont les membres stockent les caractéristiques de l’objet de la boîte de dialogue.  
  
```  
PROPSHEETHEADER m_psh;  
```  
  
### <a name="remarks"></a>Notes  
 Après avoir construit un `COlePropertiesDialog` de l’objet, vous pouvez utiliser `m_psh` pour définir les divers aspects de la boîte de dialogue avant d’appeler le `DoModal` fonction membre.  
  
 Si vous modifiez le `m_psh` membre de données directement, remplace un comportement par défaut.  
  
 Pour plus d’informations sur la **PROPSHEETHEADER** structure, consultez le Kit de développement logiciel Windows.  
  
##  <a name="m_vp"></a>  COlePropertiesDialog::m_vp  
 Une structure de type [OLEUIVIEWPROPS](http://msdn.microsoft.com/library/windows/desktop/ms693751), utilisée pour initialiser la page de vue de la boîte de dialogue Propriétés de l’objet OLE.  
  
```  
OLEUIVIEWPROPS m_vp;  
```  
  
### <a name="remarks"></a>Notes  
 Cette page permet à l’utilisateur de basculer entre le « contenu » et « sous forme d’icône » vues de l’objet et modifier sa mise à l’échelle dans le conteneur. Il permet également l’accès utilisateur à la boîte de dialogue Changer d’icône lorsque l’objet est affiché sous forme d’icône.  
  
 Pour plus d’informations sur la **OLEUIVIEWPROPS** de la structure, consultez le Kit de développement logiciel Windows.  
  
##  <a name="onapplyscale"></a>  COlePropertiesDialog::OnApplyScale  
 Appelé par le framework lorsque la valeur de mise à l’échelle et OK ou appliquer a été sélectionné.  
  
```  
virtual BOOL OnApplyScale(
    COleClientItem* pItem,  
    int nCurrentScale,  
    BOOL bRelativeToOrig);
```  
  
### <a name="parameters"></a>Paramètres  
 `pItem`  
 Pointeur vers l’élément de document dont les propriétés sont en cours d’accès.  
  
 `nCurrentScale`  
 Valeur numérique de l’échelle de la boîte de dialogue.  
  
 *bRelativeToOrig*  
 Indique si l’échelle s’applique à la taille d’origine de l’élément de document.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si gérée ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L'implémentation par défaut n'exécute aucune opération. Vous devez substituer cette fonction pour activer les contrôles de mise à l’échelle.  
  
> [!NOTE]
>  Avant l’affichage de la boîte de dialogue Propriétés de l’objet OLE, l’infrastructure appelle cette fonction avec un **NULL** pour `pItem` et - 1 pour `nCurrentScale`. Cela est effectuée pour déterminer si les contrôles de mise à l’échelle doivent être activés.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC CIRC](../../visual-cpp-samples.md)   
 [Classe de COleDialog](../../mfc/reference/coledialog-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe de COleDialog](../../mfc/reference/coledialog-class.md)   
 [CPropertyPage, classe](../../mfc/reference/cpropertypage-class.md)
