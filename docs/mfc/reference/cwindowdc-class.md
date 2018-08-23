---
title: Cwindowdc, classe | Microsoft Docs
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
ms.openlocfilehash: b692d974b5397d73f7e328330f71d8f9688be3e2
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "42539090"
---
# <a name="cwindowdc-class"></a>Cwindowdc, classe
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
|[CWindowDC::m_hWnd](#m_hwnd)|Le HWND à laquelle cet `CWindowDC` est attaché.|  
  
## <a name="remarks"></a>Notes  
 Appelle la fonction Windows [GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc)au moment de la construction et [ReleaseDC](/windows/desktop/api/winuser/nf-winuser-releasedc) au moment de la destruction. Cela signifie qu’un `CWindowDC` objet accède à la zone de la totalité de l’écran d’un [CWnd](../../mfc/reference/cwnd-class.md) (zones clientes et non clientes).  
  
 Pour plus d’informations sur l’utilisation de `CWindowDC`, consultez [contextes de périphérique](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAPTURE DE DONNÉES MODIFIÉES](../../mfc/reference/cdc-class.md)  
  
 `CWindowDC`  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : afxwin.h  
  
##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC  
 Construit un `CWindowDC` objet qui accède à la zone de l’écran (clientes et non clientes) de la `CWnd` objet vers lequel pointe *pWnd*.  
  
```  
explicit CWindowDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 La fenêtre dont la zone cliente accède à l’objet de contexte de périphérique.  
  
### <a name="remarks"></a>Notes  
 Le constructeur appelle la fonction Windows [GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947).  
  
 Une exception (de type `CResourceException`) est levée si le Windows `GetWindowDC` appeler échoue. Un contexte de périphérique n’est peut-être pas disponible si Windows a déjà alloué tous ses contextes de périphérique disponible. Votre application est en concurrence pour les contextes d’affichage courants cinq disponibles à un moment donné sous Windows.  
  
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
