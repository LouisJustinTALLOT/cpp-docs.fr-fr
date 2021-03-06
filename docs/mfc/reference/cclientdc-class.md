---
description: 'En savoir plus sur : classe CClientDC'
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
ms.openlocfilehash: 27735929734388ccb25eaf178e49d63884beed0d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122458"
---
# <a name="cclientdc-class"></a>CClientDC, classe

Prend en charge l’appel des fonctions Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) au moment de la construction et [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) au moment de la destruction.

## <a name="syntax"></a>Syntaxe

```
class CClientDC : public CDC
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CClientDC :: CClientDC](#cclientdc)|Construit un `CClientDC` objet connecté à `CWnd` .|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CClientDC :: m_hWnd](#m_hwnd)|HWND de la fenêtre pour laquelle ce `CClientDC` est valide.|

## <a name="remarks"></a>Notes

Cela signifie que le contexte de périphérique associé à un `CClientDC` objet est la zone cliente d’une fenêtre.

Pour plus d’informations sur `CClientDC` , consultez [contextes de périphérique](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cclientdccclientdc"></a><a name="cclientdc"></a> CClientDC :: CClientDC

Construit un `CClientDC` objet qui accède à la zone cliente de [CWnd](../../mfc/reference/cwnd-class.md) vers laquelle pointe *pwnd*.

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Fenêtre dont l’objet de contexte de périphérique doit accéder à la zone cliente.

### <a name="remarks"></a>Notes

Le constructeur appelle la fonction Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc).

Une exception (de type `CResourceException` ) est levée en cas d' `GetDC` échec de l’appel Windows. Un contexte de périphérique peut ne pas être disponible si Windows a déjà alloué tous les contextes de périphérique disponibles. Votre application est en concurrence pour les cinq contextes d’affichage courants disponibles à un moment donné sous Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

## <a name="cclientdcm_hwnd"></a><a name="m_hwnd"></a> CClientDC :: m_hWnd

`HWND`Du `CWnd` pointeur utilisé pour construire l' `CClientDC` objet.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Notes

*m_hWnd* est une variable protégée.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CClientDC :: CClientDC](#cclientdc).

## <a name="see-also"></a>Voir aussi

[Exemple MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Classe CDC](../../mfc/reference/cdc-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CDC](../../mfc/reference/cdc-class.md)
