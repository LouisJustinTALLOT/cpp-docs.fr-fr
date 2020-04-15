---
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
ms.openlocfilehash: 89a822280ddebca942016f9a3a334a7128d8456a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371980"
---
# <a name="cwindowdc-class"></a>CWindowDC, classe

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

|Nom|Description|
|----------|-----------------|
|[CWindowDC:m_hWnd](#m_hwnd)|Le HWND auquel `CWindowDC` il est attaché.|

## <a name="remarks"></a>Notes

Appelle la fonction Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc)au moment de la construction et [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) au moment de la destruction. Cela signifie `CWindowDC` qu’un objet accède à toute la surface de l’écran [d’un CWnd](../../mfc/reference/cwnd-class.md) (zones clientes et non-civientes).

Pour plus d’informations sur l’utilisation `CWindowDC`, voir [Contextes périphériques](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>Spécifications

En-tête : afxwin.h

## <a name="cwindowdccwindowdc"></a><a name="cwindowdc"></a>CWindowDC::CWindowDC

Construit un `CWindowDC` objet qui accède à toute la surface de `CWnd` l’écran (client et non-civient) de l’objet pointé par *pWnd*.

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
La fenêtre dont la zone client de l’objet de l’appareil-contexte y accédera.

### <a name="remarks"></a>Notes

Le constructeur appelle la fonction Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc).

Une exception (de type `CResourceException`) `GetWindowDC` est lancée si l’appel Windows échoue. Un contexte d’appareil peut ne pas être disponible si Windows a déjà alloué tous ses contextes d’appareils disponibles. Votre application est en concurrence pour les cinq contextes d’affichage communs disponibles à un moment donné sous Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

## <a name="cwindowdcm_hwnd"></a><a name="m_hwnd"></a>CWindowDC:m_hWnd

Le HWND `CWnd` du pointeur est `CWindowDC` utilisé pour construire l’objet.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Notes

`m_hWnd`est une variable protégée de type HWND.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CWindowDC:CWindowDC](#cwindowdc).

## <a name="see-also"></a>Voir aussi

[Classe CDC](../../mfc/reference/cdc-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CDC](../../mfc/reference/cdc-class.md)
