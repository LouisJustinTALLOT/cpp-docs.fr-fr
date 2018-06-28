---
title: COleDBRecordView (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
dev_langs:
- C++
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 122ceb1715323e1482b2a8a8544cbe3f6270c713
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037855"
---
# <a name="coledbrecordview-class"></a>COleDBRecordView (classe)
Vue qui affiche des enregistrements de base de données dans des contrôles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDBRecordView : public CFormView  
```  
  
## <a name="members"></a>Membres  
  
### <a name="protected-constructors"></a>Constructeurs protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDBRecordView::COleDBRecordView](#coledbrecordview)|Construit un objet `COleDBRecordView`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDBRecordView::OnGetRowset](#ongetrowset)|Retourne une norme `HRESULT` valeur.|  
|[COleDBRecordView::OnMove](#onmove)|Met à jour l’enregistrement en cours (si elle est « Dirty ») sur la source de données, puis déplace à l’enregistrement spécifié (suivante, précédente, première ou dernière).|  
  
## <a name="remarks"></a>Notes  
 La vue est une vue de formulaire directement connectée à un `CRowset` objet. La vue est créée à partir d’une ressource de modèle de boîte de dialogue et affiche les champs de la `CRowset` objet dans les contrôles du modèle de boîte de dialogue. Le `COleDBRecordView` objet utilise l’échange de données de boîtes de dialogue (DDX) et les fonctionnalités de navigation intégrées `CRowset`, pour automatiser le déplacement des données entre les contrôles du formulaire et les champs de l’ensemble de lignes. `COleDBRecordView` fournit également une implémentation par défaut pour le déplacement à la première, suivant, précédent ou le dernier enregistrement et une interface pour la mise à jour de l’enregistrement actuellement affiché.  
  
 Vous pouvez utiliser des fonctions DDX avec **COleDbRecordView** pour obtenir des données directement à partir de l’ensemble d’enregistrements de base de données et les afficher dans un contrôle de boîte de dialogue. Vous devez utiliser le **DDX_\***  méthodes (tel que `DDX_Text`), et non le **DDX_Field\***  fonctions (telles que `DDX_FieldText`) avec **COleDbRecordView** . `DDX_FieldText` ne fonctionne pas avec **COleDbRecordView** car `DDX_FieldText` prend un argument supplémentaire de type **CRecordset\***  (pour `CRecordView`) ou **CDaoRecordset\***  (pour `CDaoRecordView`).  
  
> [!NOTE]
>  Si vous travaillez avec les classes d’objets d’accès aux données (DAO) plutôt que les classes de modèles du consommateur OLE DB, utilisez la classe [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) à la place. Pour plus d’informations, consultez l’article [vue d’ensemble : programmation de base de données](../../data/data-access-programming-mfc-atl.md).  
  
 `COleDBRecordView` conserve le suivi de la position de l’utilisateur dans l’ensemble de lignes afin que la vue de l’enregistrement peut mettre à jour l’interface utilisateur. Quand l’utilisateur passe à des extrémités de l’ensemble de lignes, la vue d’enregistrement désactive les objets d’interface utilisateur, tels que les éléments de menu ou des boutons de barre d’outils, pour déplacer ultérieurement dans la même direction.  
  
 Pour plus d’informations sur les classes de l’ensemble de lignes, consultez le [à l’aide de OLE DB modèles du consommateur](../../data/oledb/ole-db-consumer-templates-cpp.md) l’article.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `COleDBRecordView`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxoledb.h  
  
##  <a name="coledbrecordview"></a>  COleDBRecordView::COleDBRecordView  
 Construit un objet `COleDBRecordView`.  
  
```  
COleDBRecordView(LPCTSTR lpszTemplateName);  
COleDBRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszTemplateName*  
 Contient une chaîne se terminant par null qui est le nom d’une ressource de modèle de boîte de dialogue.  
  
 *nIDTemplate*  
 Contient le numéro d’ID d’une ressource de modèle de boîte de dialogue.  
  
### <a name="remarks"></a>Notes  
 Lorsque vous créez un objet d’un type dérivé de `COleDBRecordView`, appelez un des constructeurs pour créer l’objet de vue et identifier la ressource de boîte de dialogue sur lequel est basée la vue. Vous pouvez identifier la ressource par son nom (passez une chaîne comme argument au constructeur) ou par son ID (passer un entier non signé en tant que l’argument).  
  
> [!NOTE]
>  Votre classe dérivée *doit* fournir son propre constructeur. Dans le constructeur, appelez le constructeur, `COleDBRecordView::COleDBRecordView`, avec le nom de la ressource ou l’ID en tant qu’argument.  
  
##  <a name="ongetrowset"></a>  COleDBRecordView::OnGetRowset  
 Retourne un handle pour le **CRowset <>** objet associé à la vue de l’enregistrement.  
  
```  
virtual CRowset<>* OnGetRowset() = 0;  
 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Vous devez substituer cette fonction membre pour créer ou obtenir un objet d’ensemble de lignes et de retourner un handle à ce dernier. Si vous déclarez votre classe de vue de l’enregistrement avec ClassWizard, l’Assistant écrit un remplacement par défaut pour vous. Implémentation de ClassWizard par défaut retourne le handle de l’ensemble de lignes stocké dans la vue de l’enregistrement s’il en existe. Si non, il construit un objet d’ensemble de lignes du type que vous avez spécifié avec ClassWizard et appelle son `Open` membres de fonction pour ouvrir la table ou exécuter la requête, puis retourne un handle vers l’objet.  
  
> [!NOTE]
>  Antérieures à MFC 7.0, `OnGetRowset` retourné un pointeur vers `CRowset`. Si vous avez le code qui appelle `OnGetRowset`, vous devez modifier le type de retour à la classe modélisée **CRowset <>**.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]  
  
 Pour plus d’informations et d’exemples, consultez l’article [vues des enregistrements : utilisation d’une vue d’enregistrement](../../data/using-a-record-view-mfc-data-access.md).  
  
##  <a name="onmove"></a>  COleDBRecordView::OnMove  
 Permet d’afficher se déplace vers un autre enregistrement dans l’ensemble de lignes et afficher ses champs dans les contrôles de l’enregistrement.  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>Paramètres  
 *nIDMoveCommand*  
 Une des valeurs d’ID de commande standard suivantes :  
  
- `ID_RECORD_FIRST` : Permet de déplacer vers le premier enregistrement dans le jeu d’enregistrements.  
  
- `ID_RECORD_LAST` : Déplace le dernier enregistrement dans le jeu d’enregistrements.  
  
- `ID_RECORD_NEXT` Migrez vers l’enregistrement suivant dans le jeu d’enregistrements.  
  
- `ID_RECORD_PREV` Migrez vers l’enregistrement précédent dans le jeu d’enregistrements.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le déplacement a réussi ; 0 dans le cas contraire, si la demande de déplacement a été refusée.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut appelle approprié `Move` fonction membre de la `CRowset` objet associé à la vue de l’enregistrement.  
  
 Par défaut, `OnMove` met à jour l’enregistrement en cours sur la source de données si l’utilisateur a été modifié dans la vue de l’enregistrement.  
  
 L’Assistant Application crée une ressource de menu avec des éléments de menu premier enregistrement, dernier enregistrement, enregistrement suivant et enregistrement précédent. Si vous sélectionnez l’option de la barre d’outils ancrable, l’Assistant Application crée également une barre d’outils avec des boutons correspondant à ces commandes.  
  
 Si vous déplacez au-delà du dernier enregistrement du jeu d’enregistrements, la vue de l’enregistrement continue d’afficher le dernier enregistrement. Si vous déplacez vers l’arrière au-delà du premier enregistrement, la vue de l’enregistrement continue à afficher le premier enregistrement.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



