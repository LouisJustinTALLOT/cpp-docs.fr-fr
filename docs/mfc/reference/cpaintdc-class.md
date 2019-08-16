---
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
ms.openlocfilehash: d587f1cfa6ec38dd564da196da8130bffac11302
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503135"
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
|[CPaintDC::CPaintDC](#cpaintdc)|Construit un `CPaintDC` connecté au [CWnd](../../mfc/reference/cwnd-class.md)spécifié.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|Contient le [PAINTSTRUCT,](/windows/win32/api/winuser/ns-winuser-paintstruct) utilisé pour peindre la zone cliente.|

### <a name="protected-data-members"></a>Membres de données protégés

|Name|Description|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|HWND auquel cet `CPaintDC` objet est attaché.|

## <a name="remarks"></a>Notes

Il exécute [CWnd:: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) au moment de la construction et [CWnd:: EndPaint](../../mfc/reference/cwnd-class.md#endpaint) au moment de la destruction.

Un `CPaintDC` objet ne peut être utilisé que lors de la réponse à un message [WM_PAINT](/windows/win32/gdi/wm-paint) , `OnPaint` généralement dans la fonction membre du gestionnaire de messages.

Pour plus d’informations sur `CPaintDC`l’utilisation de, consultez contextes de [périphérique](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cpaintdc"></a>  CPaintDC::CPaintDC

Construit un `CPaintDC` objet, prépare la fenêtre d’application pour la peinture et stocke la structure [PAINTSTRUCT,](/windows/win32/api/winuser/ns-winuser-paintstruct) dans la variable membre [m_ps](#m_ps) .

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers l' `CWnd` objet auquel l' `CPaintDC` objet appartient.

### <a name="remarks"></a>Notes

Une exception (de type `CResourceException`) est levée en cas d’échec de l’appel de [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) Windows. Un contexte de périphérique peut ne pas être disponible si Windows a déjà alloué tous les contextes de périphérique disponibles. Votre application est en concurrence pour les cinq contextes d’affichage courants disponibles à un moment donné sous Windows.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CPaintDC::m_hWnd

`HWND` Auquel cet`CPaintDC` objet est attaché.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Notes

*m_hWnd* est une variable protégée de type HWND.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

##  <a name="m_ps"></a>  CPaintDC::m_ps

`m_ps`variable membre publique de type [PAINTSTRUCT,](/windows/win32/api/winuser/ns-winuser-paintstruct).

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>Notes

Il s’agit `PAINTSTRUCT` du qui est passé à et renseigné par [CWnd:: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).

Le `PAINTSTRUCT` contient des informations que l’application utilise pour peindre la zone cliente de la fenêtre associée `CPaintDC` à un objet.

Notez que vous pouvez accéder au handle de contexte de périphérique à `PAINTSTRUCT`l’aide de. Toutefois, vous pouvez accéder à la poignée plus directement via `m_hDC` la variable membre `CPaintDC` qui hérite de la capture de données modifiées.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CPaintDC:: m_hWnd](#m_hwnd).

## <a name="see-also"></a>Voir aussi

[Exemple MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[CDC, classe](../../mfc/reference/cdc-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
