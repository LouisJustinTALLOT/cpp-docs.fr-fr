---
title: CHtmlEditCtrl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditCtrl [MFC], CHtmlEditCtrl
- CHtmlEditCtrl [MFC], Create
- CHtmlEditCtrl [MFC], GetDHtmlDocument
- CHtmlEditCtrl [MFC], GetStartDocument
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4cc8cdc389edc8abbc424ec8277f759e7f3d81bb
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338566"
---
# <a name="chtmleditctrl-class"></a>CHtmlEditCtrl, classe
Fournit les fonctionnalités du contrôle ActiveX WebBrowser dans une fenêtre MFC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CHtmlEditCtrl: public CWnd,   
    public CHtmlEditCtrlBase<CHtmlEditCtrl>  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|Construit un objet `CHtmlEditCtrl`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CHtmlEditCtrl::Create](#create)|Crée un contrôle WebBrowser ActiveX et l’attache à la `CHtmlEditCtrl` objet. Cette fonction place automatiquement le contrôle WebBrowser ActiveX en mode édition.|  
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Récupère le [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) interface sur le document actuellement chargé dans le contrôle WebBrowser relation contenant-contenu.|  
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Récupère l’URL d’un document par défaut à charger dans le contrôle WebBrowser relation contenant-contenu.|  
  
## <a name="remarks"></a>Notes  
 Mode d’édition WebBrowser hébergé contrôle est automatiquement placé dans après sa création.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHtmlEditCtrl`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxhtml.h  
  
##  <a name="chtmleditctrl"></a>  CHtmlEditCtrl::CHtmlEditCtrl  
 Construit un objet `CHtmlEditCtrl`.  
  
```  
CHtmlEditCtrl();
```  
  
##  <a name="create"></a>  CHtmlEditCtrl::Create  
 Crée un contrôle WebBrowser ActiveX et l’attache à la `CHtmlEditCtrl` objet. Le WebBrowser ActiveX contrôle navigue automatiquement vers un document par défaut et est placé dans le mode édition par cette fonction.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszWindowName*  
 Ce paramètre est inutilisé.  
  
 *dwStyle*  
 Ce paramètre est inutilisé.  
  
 *Rect*  
 Spécifie la taille et la position du contrôle.  
  
 *pParentWnd*  
 Spécifie la fenêtre du contrôle parent. Il ne doit pas être NULL.  
  
 *nID*  
 Spécifie l’ID. du contrôle  
  
 *pContext*  
 Ce paramètre est inutilisé.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
##  <a name="getdhtmldocument"></a>  CHtmlEditCtrl::GetDHtmlDocument  
 Récupère le [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) interface sur le document actuellement chargé dans le contrôle WebBrowser relation contenant-contenu  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *ppDocument*  
 L’interface de document.  
  
##  <a name="getstartdocument"></a>  CHtmlEditCtrl::GetStartDocument  
 Récupère l’URL d’un document par défaut à charger dans le contrôle WebBrowser relation contenant-contenu.  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)

