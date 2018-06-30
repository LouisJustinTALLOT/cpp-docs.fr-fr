---
title: Classe de CWindowDC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8b757da27f2b4ae79a0192df0598f833b3d1e7b9
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121540"
---
# <a name="cwindowdc-class"></a>Classe de CWindowDC
Dérivée de `CDC`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CWindowDC : public CDC  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CWindowDC::CWindowDC](#cwindowdc)|Construit un objet `CWindowDC`.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CWindowDC::m_hWnd](#m_hwnd)|Le HWND auquel ce `CWindowDC` est attaché.|  
  
## <a name="remarks"></a>Notes  
 Appelle la fonction Windows [GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947\(v=vs.85\).aspx)au moment de la construction et [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920\(v=vs.85\).aspx) au moment de la destruction. Cela signifie qu’un `CWindowDC` objet accède à la zone de l’écran d’un [CWnd](../../mfc/reference/cwnd-class.md) (les zones clientes et).  
  
 Pour plus d’informations sur l’utilisation de `CWindowDC`, consultez [contextes de périphérique](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAPTURE DE DONNÉES MODIFIÉES](../../mfc/reference/cdc-class.md)  
  
 `CWindowDC`  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : afxwin.h  
  
##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC  
 Construit un `CWindowDC` objet qui accède à la zone de l’écran (client et non cliente) de la `CWnd` objet pointé par *pWnd*.  
  
```  
explicit CWindowDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 La fenêtre dont l’objet de contexte de périphérique sera accéder à la zone cliente.  
  
### <a name="remarks"></a>Notes  
 Le constructeur appelle la fonction Windows [GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947).  
  
 Une exception (de type `CResourceException`) est levée si les fenêtres `GetWindowDC` appel échoue. Un contexte de périphérique n’est peut-être pas disponible si Windows a déjà alloué à tous ses contextes de périphérique disponible. Votre application en concurrence pour les contextes d’affichage courantes cinq disponibles à un moment donné sous Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd  
 Le HWND de la `CWnd` pointeur est utilisé pour construire le `CWindowDC` objet.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Notes  
 `m_hWnd` est une variable protégée de type HWND.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CWindowDC::CWindowDC](#cwindowdc).  
  
## <a name="see-also"></a>Voir aussi  
 [CDC (classe)](../../mfc/reference/cdc-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CDC, classe](../../mfc/reference/cdc-class.md)
