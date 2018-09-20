---
title: WINDOWPLACEMENT, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WINDOWPLACEMENT
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPLACEMENT structure [MFC]
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b163d93de22d313d72ca5dbfd384788077ae1b01
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447271"
---
# <a name="windowplacement-structure"></a>WINDOWPLACEMENT, structure

Le `WINDOWPLACEMENT` structure contient des informations sur le placement d’une fenêtre sur l’écran.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagWINDOWPLACEMENT {     /* wndpl */
    UINT length;
    UINT flags;
    UINT showCmd;
    POINT ptMinPosition;
    POINT ptMaxPosition;
    RECT rcNormalPosition;
} WINDOWPLACEMENT;
```

#### <a name="parameters"></a>Paramètres

*length*<br/>
Spécifie la longueur, en octets, de la structure.

*flags*<br/>
Spécifie les indicateurs qui contrôlent la position de la fenêtre réduite et la méthode par laquelle la fenêtre est restaurée. Ce membre peut être une ou les deux des indicateurs suivants :

- WPF_SETMINPOSITION Spécifie que les positions x et y de la fenêtre réduite peut être spécifiée. Cet indicateur doit être spécifié si les coordonnées sont définies le `ptMinPosition` membre.

- WPF_RESTORETOMAXIMIZED Spécifie que la fenêtre restaurée sera agrandie, indépendamment de si elle a été agrandie avant qu’il a été réduit. Ce paramètre est valide uniquement la prochaine fois que la fenêtre est restaurée. Il ne modifie pas le comportement de restauration par défaut. Cet indicateur est valide uniquement lorsque la valeur SW_SHOWMINIMIZED est spécifiée pour le `showCmd` membre.

*showCmd*<br/>
Spécifie l’état d’affichage actuel de la fenêtre. Ce membre peut être une des valeurs suivantes :

- SW_HIDE masque la fenêtre et passe d’activation vers une autre fenêtre.

- SW_MINIMIZE réduit la fenêtre spécifiée et Active la fenêtre de niveau supérieur dans la liste du système.

- SW_RESTORE active et affiche une fenêtre. Si la fenêtre est réduite ou agrandie, Windows le restaure à sa taille d’origine et sa position (identique à la valeur SW_SHOWNORMAL).

- SW_SHOW Active une fenêtre et l’affiche dans sa taille actuelle et sa position.

- SW_SHOWMAXIMIZED Active une fenêtre et il s’affiche sous la forme d’une fenêtre agrandie.

- SW_SHOWMINIMIZED Active une fenêtre et l’affiche sous forme d’icône.

- SW_SHOWMINNOACTIVE affiche une fenêtre sous la forme d’une icône. La fenêtre actuellement active reste active.

- SW_SHOWNA affiche une fenêtre dans son état actuel. La fenêtre actuellement active reste active.

- SW_SHOWNOACTIVATE affiche une fenêtre dans sa taille et sa position la plus récente. La fenêtre actuellement active reste active.

- SW_SHOWNORMAL active et affiche une fenêtre. Si la fenêtre est réduite ou agrandie, Windows le restaure à sa taille d’origine et sa position (identique à SW_RESTORE).

*ptMinPosition*<br/>
Spécifie la position du coin supérieur gauche de la fenêtre lorsque la fenêtre est réduite.

*ptMaxPosition*<br/>
Spécifie la position du coin supérieur gauche de la fenêtre lorsque la fenêtre est agrandie.

*rcNormalPosition*<br/>
Spécifie les coordonnées de la fenêtre lorsque la fenêtre est en position normale (restaurée).

## <a name="requirements"></a>Configuration requise

**En-tête :** winuser.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::SetWindowPlacement](../../mfc/reference/cwnd-class.md#setwindowplacement)

