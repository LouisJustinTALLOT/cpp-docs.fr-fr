---
title: CPaintDC (classe)
ms.date: 11/04/2016
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
helpviewer_keywords:
- CPaintDC [MFC], CPaintDC
- CPaintDC [MFC], m_ps
- CPaintDC [MFC], m_hWnd
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
ms.openlocfilehash: 5dbe08eae911433c256d3f8dd1f60dea2db9478c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274425"
---
# <a name="cpaintdc-class"></a>CPaintDC (classe)

Une classe de contexte de périphérique dérivée de [CDC](../../mfc/reference/cdc-class.md).

## <a name="syntax"></a>Syntaxe

```
class CPaintDC : public CDC
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|Construit un `CPaintDC` connecté spécifié [CWnd](../../mfc/reference/cwnd-class.md).|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|Contient le [PAINTSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagpaintstruct) utilisé pour peindre la zone cliente.|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|Le HWND à laquelle cet `CPaintDC` objet est attaché.|

## <a name="remarks"></a>Notes

Il effectue une [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) au moment de la construction et [CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint) au moment de la destruction.

Un `CPaintDC` objet peut uniquement être utilisé lors de la réponse à une [WM_PAINT](/windows/desktop/gdi/wm-paint) du message, généralement dans votre `OnPaint` fonction membre de gestionnaire de messages.

Pour plus d’informations sur l’utilisation de `CPaintDC`, consultez [contextes de périphérique](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="cpaintdc"></a>  CPaintDC::CPaintDC

Construit un `CPaintDC` objet, prépare la fenêtre d’application pour la peinture et stocke le [PAINTSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagpaintstruct) structure dans le [m_ps](#m_ps) variable membre.

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers le `CWnd` objet vers lequel le `CPaintDC` objet appartient.

### <a name="remarks"></a>Notes

Une exception (de type `CResourceException`) est levée si le Windows [GetDC](/windows/desktop/api/winuser/nf-winuser-getdc) appeler échoue. Un contexte de périphérique n’est peut-être pas disponible si Windows a déjà alloué tous ses contextes de périphérique disponible. Votre application est en concurrence pour les contextes d’affichage courants cinq disponibles à un moment donné sous Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CPaintDC::m_hWnd

Le `HWND` auquel ce `CPaintDC` objet est attaché.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Notes

*m_hWnd* protégé variable de type HWND.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

##  <a name="m_ps"></a>  CPaintDC::m_ps

`m_ps` est une variable de membre public de type [PAINTSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagpaintstruct).

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>Notes

Il s’agit du `PAINTSTRUCT` qui est passé à et rempli par [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).

Le `PAINTSTRUCT` contient des informations que l’application utilise pour peindre la zone cliente de la fenêtre associée à un `CPaintDC` objet.

Notez que vous pouvez accéder au handle de contexte de périphérique via le `PAINTSTRUCT`. Toutefois, vous pouvez accéder à la poignée plus directement via le `m_hDC` variable membre qui `CPaintDC` hérite de capture de données modifiées.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPaintDC::m_hWnd](#m_hwnd).

## <a name="see-also"></a>Voir aussi

[Exemple MFC MDI](../../visual-cpp-samples.md)<br/>
[CDC, classe](../../mfc/reference/cdc-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
