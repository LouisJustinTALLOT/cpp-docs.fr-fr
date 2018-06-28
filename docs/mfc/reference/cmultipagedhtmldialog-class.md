---
title: Classe de CMultiPageDHtmlDialog | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
dev_langs:
- C++
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a1a4ca77e4b7a2cda10d87bd657e73931a50612
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038004"
---
# <a name="cmultipagedhtmldialog-class"></a>Classe de CMultiPageDHtmlDialog
Une boîte de dialogue multipage affiche plusieurs pages HTML de manière séquentielle et gère les événements de chaque page.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMultiPageDHtmlDialog : public CDHtmlDialog  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|Construit un objet de boîte de dialogue multipage (de type Assistant) DHTML.|  
|[CMultiPageDHtmlDialog :: ~ CMultiPageDHtmlDialog](#cmultipagedhtmldialog__~cmultipagedhtmldialog)|Détruit un objet de boîte de dialogue multipage DHTML.|  
  
## <a name="remarks"></a>Notes  
 Le mécanisme de cette opération est un [table d’événements DHTML et l’URL](dhtml-event-maps.md), tables d’événements pour chaque page contenant des images.  
  
## <a name="example"></a>Exemple  
 Cette boîte de dialogue multipage suppose trois ressources HTML qui définissent des fonctionnalités de type Assistant simple. La première page a un `Next` bouton, le second une **Prev** et `Next` bouton et le troisième une **Prev** bouton. Lorsqu’un des boutons est activé, une fonction de gestionnaire appelle [CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource) pour charger la nouvelle page appropriée.  
  
 Les parties pertinentes de la déclaration de classe (dans CMyMultiPageDlg.h) :  
  
 [!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]  
  
 Les parties pertinentes de l’implémentation de classe (dans CMyMultipageDlg.cpp) :  
  
 [!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDHtmlSinkHandlerBase2`  
  
 `CDHtmlSinkHandlerBase1`  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDHtmlSinkHandler`  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDHtmlEventSink`  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)  
  
 `CMultiPageDHtmlDialog`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdhtml.h  
  
##  <a name="cmultipagedhtmldialog"></a>  CMultiPageDHtmlDialog::CMultiPageDHtmlDialog  
 Construit un objet de boîte de dialogue multipage (de type Assistant) DHTML.  
  
```  
CMultiPageDHtmlDialog(
    LPCTSTR lpszTemplateName,  
    LPCTSTR szHtmlResID = NULL,  
    CWnd* pParentWnd = NULL);

 
CMultiPageDHtmlDialog(
    UINT nIDTemplate,  
    UINT nHtmlResID = 0,  
    CWnd* pParentWnd = NULL);  
  
CMultiPageDHtmlDialog();
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszTemplateName*  
 La chaîne se terminant par null qui est le nom d’une ressource de modèle de boîte de dialogue.  
  
 *szHtmlResID*  
 La chaîne se terminant par null qui est le nom d’une ressource HTML.  
  
 *pParentWnd*  
 Un pointeur vers l’objet de fenêtre parente ou propriétaire (de type [CWnd](../../mfc/reference/cwnd-class.md)) auquel appartient l’objet de la boîte de dialogue. S’il s’agit **NULL**, la boîte de dialogue fenêtre l’objet parent est définie dans la fenêtre principale de l’application.  
  
 *nIDTemplate*  
 Contient le numéro d’ID d’une ressource de modèle de boîte de dialogue.  
  
 *nHtmlResID*  
 Contient le numéro d’ID d’une ressource HTML.  
  
##  <a name="_dtorcmultipagedhtmldialog"></a>  CMultiPageDHtmlDialog :: ~ CMultiPageDHtmlDialog  
 Détruit un objet de boîte de dialogue multipage DHTML.  
  
```  
virtual ~CMultiPageDHtmlDialog();
```  
  
## <a name="see-also"></a>Voir aussi  
 [CDHtmlDialog, classe](../../mfc/reference/cdhtmldialog-class.md)
