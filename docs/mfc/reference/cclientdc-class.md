---
title: CClientDC, classe
ms.date: 11/04/2016
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
helpviewer_keywords:
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
ms.openlocfilehash: abe8a3220fd37a0375fcf37504c715edf4c6962e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352305"
---
# <a name="cclientdc-class"></a>CClientDC, classe

Prend soin d’appeler les fonctions Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) au moment de la construction et [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) au moment de la destruction.

## <a name="syntax"></a>Syntaxe

```
class CClientDC : public CDC
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CClientDC::CClientDC](#cclientdc)|Construit un `CClientDC` objet connecté `CWnd`à la .|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CClientDC::m_hWnd](#m_hwnd)|Le HWND de la `CClientDC` fenêtre pour laquelle cela est valable.|

## <a name="remarks"></a>Notes

Cela signifie que le contexte `CClientDC` de l’appareil associé à un objet est la zone client d’une fenêtre.

Pour plus `CClientDC`d’informations sur , voir [Contextes périphériques](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cclientdccclientdc"></a><a name="cclientdc"></a>CClientDC::CClientDC

Construit un `CClientDC` objet qui accède à la zone cliente du [CWnd](../../mfc/reference/cwnd-class.md) pointée par *pWnd*.

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
La fenêtre dont la zone client de l’objet de contexte de l’appareil y accédera.

### <a name="remarks"></a>Notes

Le constructeur appelle la fonction Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc).

Une exception (de type `CResourceException`) `GetDC` est lancée si l’appel Windows échoue. Un contexte d’appareil peut ne pas être disponible si Windows a déjà alloué tous ses contextes d’appareils disponibles. Votre application est en concurrence pour les cinq contextes d’affichage communs disponibles à un moment donné sous Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

## <a name="cclientdcm_hwnd"></a><a name="m_hwnd"></a>CClientDC::m_hWnd

Le `HWND` `CWnd` pointeur utilisé pour `CClientDC` construire l’objet.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Notes

*m_hWnd* est une variable protégée.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CClientDC::CClientDC](#cclientdc).

## <a name="see-also"></a>Voir aussi

[MFC Échantillon MDI](../../overview/visual-cpp-samples.md)<br/>
[Classe CDC](../../mfc/reference/cdc-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CDC](../../mfc/reference/cdc-class.md)
