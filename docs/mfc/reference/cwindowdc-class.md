---
description: 'En savoir plus sur : classe CWindowDC'
title: CWindowDC, classe
ms.date: 11/04/2016
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
ms.openlocfilehash: 1fc36614f5e6ded32a47146771991c3ab06998eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344924"
---
# <a name="cwindowdc-class"></a>CWindowDC, classe

Dérivé de `CDC`.

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

|Nom|Description|
|----------|-----------------|
|[CWindowDC :: m_hWnd](#m_hwnd)|HWND auquel ce `CWindowDC` est attaché.|

## <a name="remarks"></a>Notes

Appelle la fonction Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc)au moment de la construction et [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) au moment de la destruction. Cela signifie qu’un `CWindowDC` objet accède à la totalité de la zone d’écran d’un [CWnd](../../mfc/reference/cwnd-class.md) (zones clientes et non clientes).

Pour plus d’informations sur l’utilisation de `CWindowDC` , consultez [contextes de périphérique](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>Spécifications

En-tête : afxwin.h

## <a name="cwindowdccwindowdc"></a><a name="cwindowdc"></a> CWindowDC::CWindowDC

Construit un `CWindowDC` objet qui accède à la totalité de la zone d’écran (client et non client) de l' `CWnd` objet vers lequel pointe *pwnd*.

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Fenêtre dont l’objet de contexte de périphérique doit accéder à la zone cliente.

### <a name="remarks"></a>Notes

Le constructeur appelle la fonction Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc).

Une exception (de type `CResourceException` ) est levée en cas d' `GetWindowDC` échec de l’appel Windows. Un contexte de périphérique peut ne pas être disponible si Windows a déjà alloué tous les contextes de périphérique disponibles. Votre application est en concurrence pour les cinq contextes d’affichage courants disponibles à un moment donné sous Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

## <a name="cwindowdcm_hwnd"></a><a name="m_hwnd"></a> CWindowDC :: m_hWnd

Le HWND du `CWnd` pointeur est utilisé pour construire l' `CWindowDC` objet.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Notes

`m_hWnd` variable protégée de type HWND.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CWindowDC :: CWindowDC](#cwindowdc).

## <a name="see-also"></a>Voir aussi

[Classe CDC](../../mfc/reference/cdc-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CDC](../../mfc/reference/cdc-class.md)
