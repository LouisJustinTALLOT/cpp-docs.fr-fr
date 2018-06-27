---
title: Classe de CDocObjectServerItem | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
dev_langs:
- C++
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 30daf42d54b66d4e3c4ad47a406748ab023be79d
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956626"
---
# <a name="cdocobjectserveritem-class"></a>Classe de CDocObjectServerItem
Implémente les verbes de serveur OLE , en particulier pour les serveurs DocObject.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDocObjectServerItem : public COleServerItem  
```  
  
## <a name="members"></a>Membres  
  
### <a name="protected-constructors"></a>Constructeurs protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|Construit un objet `CDocObjectServerItem`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDocObjectServerItem::GetDocument](#getdocument)|Récupère un pointeur vers le document qui contient l’élément.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CDocObjectServerItem::OnHide](#onhide)|Lève une exception si le framework tente de masquer un élément DocObject.|  
|[CDocObjectServerItem::OnShow](#onshow)|Appelé par le framework pour rendre le DocObject élément in situ active. Si l’élément n’est pas un DocObject, appelle [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow).|  
  
## <a name="remarks"></a>Notes  
 `CDocObjectServerItem` définit les fonctions membres substituables : [OnHide](#onhide), [OnOpen](http://msdn.microsoft.com/en-us/7a9b1363-6ad8-4732-9959-4e35c07644fd), et [OnShow](#onshow).  
  
 Pour utiliser `CDocObjectServerItem`, s’assurer que les [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) remplacer dans votre `COleServerDoc`-classe dérivée retourne un nouveau `CDocObjectServerItem` objet. Si vous devez modifier toutes les fonctionnalités dans votre article, vous pouvez créer une nouvelle instance de votre propre `CDocObjectServerItem`-classe dérivée.  
  
 Pour plus d’informations sur DocObjects, consultez [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) et [COleCmdUI](../../mfc/reference/colecmdui-class.md) dans les *référence MFC*. Consultez également [Internet premières étapes : Documents actifs](../../mfc/active-documents-on-the-internet.md) et [Documents actifs](../../mfc/active-documents-on-the-internet.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleServerItem](../../mfc/reference/coleserveritem-class.md)  
  
 `CDocObjectServerItem`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdocob.h  
  
##  <a name="cdocobjectserveritem"></a>  CDocObjectServerItem::CDocObjectServerItem  
 Construit un objet `CDocObjectServerItem`.  
  
```  
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Paramètres  
 *pServerDoc*  
 Pointeur vers le document qui contiendra le nouvel élément DocObject.  
  
 *bAutoDelete*  
 Indique si l’objet peut être supprimé lors de la libération d’un lien vers celui-ci. L’argument de la valeur **FALSE** si le `CDocObjectServerItem` objet fait partie intégrante de données de votre document. Affectez-lui la valeur **TRUE** si l’objet est une structure secondaire utilisée pour identifier une plage de données de votre document qui peuvent être supprimées par l’infrastructure.  
  
##  <a name="getdocument"></a>  CDocObjectServerItem::GetDocument  
 Récupère un pointeur vers le document qui contient l’élément.  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le document qui contient l’élément ; **NULL** si l’élément n’est pas partie d’un document.  
  
### <a name="remarks"></a>Notes  
 Cela permet d’accéder au document serveur que vous avez transmise en tant qu’argument à la [CDocObjectServerItem](#cdocobjectserveritem) constructeur.  
  
##  <a name="onhide"></a>  CDocObjectServerItem::OnHide  
 Appelé par l’infrastructure pour masquer l’élément.  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut lève une exception si l’élément est un DocObject. Vous ne pouvez pas masquer un élément de DocObject actif car elle accepte la vue entière. Vous devez désactiver l’élément DocObject pour la faire disparaître. Si l’élément n’est pas un DocObject, l’implémentation par défaut appelle [COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide).  
  
##  <a name="onshow"></a>  CDocObjectServerItem::OnShow  
 Appelé par le framework pour indiquer à l’application de serveur pour effectuer le DocObject élément in situ active.  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>Notes  
 Si l’élément n’est pas un DocObject, l’implémentation par défaut appelle [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen). Remplacez cette fonction si vous souhaitez effectuer un traitement lors de l’ouverture d’un élément DocObject particulier.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe COleServerItem](../../mfc/reference/coleserveritem-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe de CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)   
 [COleDocObjectItem, classe](../../mfc/reference/coledocobjectitem-class.md)
