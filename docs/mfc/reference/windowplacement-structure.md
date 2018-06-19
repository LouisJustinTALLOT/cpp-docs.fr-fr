---
title: WINDOWPLACEMENT, Structure | Documents Microsoft
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
ms.openlocfilehash: 829b3c90acb089bd91d71c498df5906fff919f22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379471"
---
# <a name="windowplacement-structure"></a>WINDOWPLACEMENT, structure
Le `WINDOWPLACEMENT` structure contient des informations relatives à l’emplacement d’une fenêtre à l’écran **.**  
  
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
 *length*  
 Spécifie la longueur, en octets, de la structure **.**  
  
 `flags`  
 Spécifie des indicateurs qui contrôlent la position de la fenêtre réduite et la méthode par laquelle la fenêtre est restaurée. Ce membre peut être une ou les deux des indicateurs suivants :  
  
- **WPF_SETMINPOSITION** Spécifie que les positions x et y de la fenêtre réduite peut être spécifiée **.** Cet indicateur doit être spécifié si les coordonnées sont définies dans le **ptMinPosition** membre.  
  
- **WPF_RESTORETOMAXIMIZED** Spécifie que la fenêtre restaurée sera agrandie, indépendamment de si elle a été agrandie avant qu’il a été réduit. Ce paramètre est valid uniquement la prochaine fois que la fenêtre est restaurée. Il ne modifie pas le comportement de restauration par défaut. Cet indicateur est valide uniquement lorsque le **SW_SHOWMINIMIZED** valeur est spécifiée pour le **showCmd** membre.  
  
 *showCmd*  
 Spécifie l’état d’affichage actuel de la fenêtre. Ce membre peut être une des valeurs suivantes :  
  
- **SW_HIDE** masque la fenêtre et passe d’activation vers une autre fenêtre.  
  
- **SW_MINIMIZE** réduit la fenêtre spécifiée et Active la fenêtre de niveau supérieur dans la liste du système.  
  
- **SW_RESTORE** active et affiche une fenêtre. Si la fenêtre est réduite ou agrandie, Windows le restaure à sa taille et la position d’origine (identique à **SW_SHOWNORMAL**).  
  
- **SW_SHOW** Active une fenêtre et l’affiche dans sa taille actuelle et sa position.  
  
- **SW_SHOWMAXIMIZED** Active une fenêtre et l’affiche sous une fenêtre agrandie.  
  
- **SW_SHOWMINIMIZED** Active une fenêtre et l’affiche sous forme d’icône.  
  
- **SW_SHOWMINNOACTIVE** affiche une fenêtre sous forme d’icône. La fenêtre actuellement active reste active.  
  
- **SW_SHOWNA** affiche une fenêtre dans son état actuel. La fenêtre actuellement active reste active.  
  
- **SW_SHOWNOACTIVATE** affiche une fenêtre dans sa taille et la position la plus récente. La fenêtre actuellement active reste active.  
  
- **SW_SHOWNORMAL** active et affiche une fenêtre. Si la fenêtre est réduite ou agrandie, Windows le restaure à sa taille et la position d’origine (identique à **SW_RESTORE**).  
  
 *ptMinPosition*  
 Spécifie la position de l’angle supérieur gauche de la fenêtre lorsque la fenêtre est réduite.  
  
 `ptMaxPosition`  
 Spécifie la position de l’angle supérieur gauche de la fenêtre lorsque la fenêtre est agrandie.  
  
 *rcNormalPosition*  
 Spécifie les coordonnées de la fenêtre lorsque la fenêtre est en position normale (restaurée).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** winuser.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::SetWindowPlacement](../../mfc/reference/cwnd-class.md#setwindowplacement)

