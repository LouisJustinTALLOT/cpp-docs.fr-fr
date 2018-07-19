---
title: CClientDC, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: add135c353366ed54a24c63fcce2101c49d24fe7
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338579"
---
# <a name="cclientdc-class"></a>CClientDC (classe)
Prend en charge de l’appel de fonctions Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871) au moment de la construction et [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920) au moment de la destruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CClientDC : public CDC  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CClientDC::CClientDC](#cclientdc)|Construit un `CClientDC` objet connecté à la `CWnd`.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CClientDC::m_hWnd](#m_hwnd)|Le HWND de la fenêtre pour lequel ce `CClientDC` est valide.|  
  
## <a name="remarks"></a>Notes  
 Cela signifie que le contexte de périphérique associé à un `CClientDC` objet est la zone cliente d’une fenêtre.  
  
 Pour plus d’informations sur `CClientDC`, consultez [contextes de périphérique](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAPTURE DE DONNÉES MODIFIÉES](../../mfc/reference/cdc-class.md)  
  
 `CClientDC`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxwin.h  
  
##  <a name="cclientdc"></a>  CClientDC::CClientDC  
 Construit un `CClientDC` objet qui accède à la zone cliente de la [CWnd](../../mfc/reference/cwnd-class.md) vers lequel pointe *pWnd*.  
  
```  
explicit CClientDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 La fenêtre dont la zone cliente accède à l’objet de contexte de périphérique.  
  
### <a name="remarks"></a>Notes  
 Le constructeur appelle la fonction Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871).  
  
 Une exception (de type `CResourceException`) est levée si le Windows `GetDC` appeler échoue. Un contexte de périphérique n’est peut-être pas disponible si Windows a déjà alloué tous ses contextes de périphérique disponible. Votre application est en concurrence pour les contextes d’affichage courants cinq disponibles à un moment donné sous Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>  CClientDC::m_hWnd  
 Le `HWND` de la `CWnd` pointeur utilisé pour construire le `CClientDC` objet.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Notes  
 *m_hWnd* est une variable protégée.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CClientDC::CClientDC](#cclientdc).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC MDI](../../visual-cpp-samples.md)   
 [CDC (classe)](../../mfc/reference/cdc-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CDC, classe](../../mfc/reference/cdc-class.md)
