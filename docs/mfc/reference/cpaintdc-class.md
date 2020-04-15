---
title: Classe CPaintDC
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
ms.openlocfilehash: 55342b03454a6dba07bc10ea5f0464c34e0e8db3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374777"
---
# <a name="cpaintdc-class"></a>Classe CPaintDC

Une classe de contexte d’appareil dérivée de [CDC](../../mfc/reference/cdc-class.md).

## <a name="syntax"></a>Syntaxe

```
class CPaintDC : public CDC
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|Construit un `CPaintDC` connecté au [CWnd](../../mfc/reference/cwnd-class.md)spécifié .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|Contient le [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct) utilisé pour peindre la zone client.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|Le HWND auquel `CPaintDC` cet objet est attaché.|

## <a name="remarks"></a>Notes

Il effectue un [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) à l’heure de construction et [CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint) au moment de destruction.

Un `CPaintDC` objet ne peut être utilisé que lorsque vous `OnPaint` répondez à un [message WM_PAINT,](/windows/win32/gdi/wm-paint) généralement dans votre fonction de membre de gestionnaire de messages.

Pour plus d’informations sur l’utilisation `CPaintDC`, voir [Contextes périphériques](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cpaintdccpaintdc"></a><a name="cpaintdc"></a>CPaintDC::CPaintDC

Construit un `CPaintDC` objet, prépare la fenêtre d’application pour la peinture, et stocke la structure [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct) dans la variable [m_ps](#m_ps) membre.

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Indique l’objet `CWnd` auquel `CPaintDC` appartient l’objet.

### <a name="remarks"></a>Notes

Une exception (de type `CResourceException`) est lancée si l’appel Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) échoue. Un contexte d’appareil peut ne pas être disponible si Windows a déjà alloué tous ses contextes d’appareils disponibles. Votre application est en concurrence pour les cinq contextes d’affichage communs disponibles à un moment donné sous Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

## <a name="cpaintdcm_hwnd"></a><a name="m_hwnd"></a>CPaintDC::m_hWnd

L’objet `HWND` `CPaintDC` auquel cet objet est attaché.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Notes

*m_hWnd* est une variable protégée de type HWND.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

## <a name="cpaintdcm_ps"></a><a name="m_ps"></a>CPaintDC::m_ps

`m_ps`est une variable de membre public de type [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct).

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>Notes

C’est `PAINTSTRUCT` le qui est passé et rempli par [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).

L’application `PAINTSTRUCT` contient des informations que l’application utilise `CPaintDC` pour peindre la zone cliente de la fenêtre associée à un objet.

Notez que vous pouvez accéder à `PAINTSTRUCT`la poignée de l’appareil-contexte par le . Cependant, vous pouvez accéder à `m_hDC` la poignée `CPaintDC` plus directement grâce à la variable membre qui hérite de CDC.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPaintDC:m_hWnd](#m_hwnd).

## <a name="see-also"></a>Voir aussi

[MFC Échantillon MDI](../../overview/visual-cpp-samples.md)<br/>
[Classe CDC](../../mfc/reference/cdc-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
