---
description: 'En savoir plus sur : CPaintDC, classe'
title: CPaintDC, classe
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
ms.openlocfilehash: cb8f3b81615390ab6af8e9a244a95f91a3b3f96c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345210"
---
# <a name="cpaintdc-class"></a>CPaintDC, classe

Classe de contexte de périphérique dérivée de [CDC](../../mfc/reference/cdc-class.md).

## <a name="syntax"></a>Syntaxe

```
class CPaintDC : public CDC
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPaintDC :: CPaintDC](#cpaintdc)|Construit un `CPaintDC` connecté au [CWnd](../../mfc/reference/cwnd-class.md)spécifié.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPaintDC :: m_ps](#m_ps)|Contient le [PAINTSTRUCT,](/windows/win32/api/winuser/ns-winuser-paintstruct) utilisé pour peindre la zone cliente.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CPaintDC :: m_hWnd](#m_hwnd)|HWND auquel cet `CPaintDC` objet est attaché.|

## <a name="remarks"></a>Notes

Il exécute [CWnd :: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) au moment de la construction et [CWnd :: EndPaint](../../mfc/reference/cwnd-class.md#endpaint) au moment de la destruction.

Un `CPaintDC` objet ne peut être utilisé que lors de la réponse à un message de [WM_PAINT](/windows/win32/gdi/wm-paint) , généralement dans la `OnPaint` fonction membre du gestionnaire de messages.

Pour plus d’informations sur l’utilisation de `CPaintDC` , consultez [contextes de périphérique](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cpaintdccpaintdc"></a><a name="cpaintdc"></a> CPaintDC :: CPaintDC

Construit un `CPaintDC` objet, prépare la fenêtre d’application pour la peinture et stocke la structure [PAINTSTRUCT,](/windows/win32/api/winuser/ns-winuser-paintstruct) dans la variable membre [m_ps](#m_ps) .

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers l' `CWnd` objet auquel l' `CPaintDC` objet appartient.

### <a name="remarks"></a>Notes

Une exception (de type `CResourceException` ) est levée en cas d’échec de l’appel de [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) Windows. Un contexte de périphérique peut ne pas être disponible si Windows a déjà alloué tous les contextes de périphérique disponibles. Votre application est en concurrence pour les cinq contextes d’affichage courants disponibles à un moment donné sous Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

## <a name="cpaintdcm_hwnd"></a><a name="m_hwnd"></a> CPaintDC :: m_hWnd

Auquel `HWND` cet `CPaintDC` objet est attaché.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Notes

*m_hWnd* est une variable protégée de type HWND.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

## <a name="cpaintdcm_ps"></a><a name="m_ps"></a> CPaintDC :: m_ps

`m_ps` variable membre publique de type [PAINTSTRUCT,](/windows/win32/api/winuser/ns-winuser-paintstruct).

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>Notes

Il s’agit du `PAINTSTRUCT` qui est passé à et renseigné par [CWnd :: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).

Le `PAINTSTRUCT` contient des informations que l’application utilise pour peindre la zone cliente de la fenêtre associée à un `CPaintDC` objet.

Notez que vous pouvez accéder au handle de contexte de périphérique à l’aide de `PAINTSTRUCT` . Toutefois, vous pouvez accéder à la poignée plus directement via la `m_hDC` variable membre qui `CPaintDC` hérite de la capture de données modifiées.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CPaintDC :: m_hWnd](#m_hwnd).

## <a name="see-also"></a>Voir aussi

[Exemple MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Classe CDC](../../mfc/reference/cdc-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
