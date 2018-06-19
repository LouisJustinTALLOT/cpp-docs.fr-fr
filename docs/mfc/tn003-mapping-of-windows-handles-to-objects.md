---
title: 'TN003 : Mappage des Handles Windows à des objets | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mapping
dev_langs:
- C++
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc8658868c36008c5ed6b9db9747eb63ae37e4d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382971"
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003 : mappage des handles Windows à des objets
Cette note décrit les classes MFC des routines qui prennent en charge le mappage Windows handles vers des objets C++ de l’objet.  
  
## <a name="the-problem"></a>Le problème  
 Objets Windows sont généralement représentées par différents [gérer](http://msdn.microsoft.com/library/windows/desktop/aa383751) objets classes MFC l’encapsulent les handles d’objet Windows avec des objets C++. Le handle d’envelopper les fonctions de la bibliothèque de classes MFC vous permettre de trouver l’objet C++ qui encapsule l’objet de Windows qui possède un descripteur spécifique. Toutefois, parfois un objet ne dispose pas d’un objet de wrapper C++ et à ces moments, le système crée un objet temporaire en tant que le wrapper C++.  
  
 Les objets de Windows qui utilisent des cartes de handle sont les suivantes :  
  
-   HWND ([CWnd](../mfc/reference/cwnd-class.md) et `CWnd`-classes dérivées)  
  
-   HDC ([CDC](../mfc/reference/cdc-class.md) et `CDC`-classes dérivées)  
  
-   HMENU ([CMenu](../mfc/reference/cmenu-class.md))  
  
-   HPEN ([CGdiObject](../mfc/reference/cgdiobject-class.md))  
  
-   HBRUSH (`CGdiObject`)  
  
-   HFONT (`CGdiObject`)  
  
-   HBITMAP (`CGdiObject`)  
  
-   HPALETTE (`CGdiObject`)  
  
-   HRGN (`CGdiObject`)  
  
-   HIMAGELIST ([CImageList](../mfc/reference/cimagelist-class.md))  
  
-   SOCKET ([CSocket](../mfc/reference/csocket-class.md))  
  
 Étant donné un handle à l’une de ces objets, vous pouvez trouver l’objet MFC qui encapsule le handle en appelant la méthode statique `FromHandle`. Par exemple, prenons un HWND appelé `hWnd`, la ligne suivante retourne un pointeur vers le `CWnd` qui encapsule `hWnd`:  
  
```  
CWnd::FromHandle(hWnd)  
```  
  
 Si `hWnd` n’a pas d’un objet de wrapper spécifique, une valeur temporaire `CWnd` est créée pour encapsuler `hWnd`. Cela rend possible d’obtenir un objet C++ valide à partir d’un handle quelconque.  
  
 Après avoir configuré un objet de wrapper, vous pouvez récupérer son handle à partir d’une variable membre public de la classe wrapper. Dans le cas d’un `CWnd`, `m_hWnd` contient le HWND de cet objet.  
  
## <a name="attaching-handles-to-mfc-objects"></a>Attachement de Handles pour les objets MFC  
 Étant donné un objet de wrapper de descripteur nouvellement créé et un handle à un objet de Windows, vous pouvez associer les deux en appelant le `Attach` fonctionnent comme dans cet exemple :  
  
```  
CWnd myWnd;  
myWnd.Attach(hWnd);
```  
  
 Cela crée une entrée dans l’association de carte permanente `myWnd` et `hWnd`. Appel de `CWnd::FromHandle(hWnd)` retourne maintenant un pointeur vers `myWnd`. Lorsque `myWnd` est supprimé, le destructeur automatiquement détruira `hWnd` en appelant les fenêtres [DestroyWindow](http://msdn.microsoft.com/library/windows/desktop/ms632682) (fonction). Si ce n’est pas souhaité, `hWnd` doit être détaché de `myWnd` avant `myWnd` est détruit (normalement, lorsque vous quittez la portée à laquelle `myWnd` a été défini). Le `Detach` méthode.  
  
```  
myWnd.Detach();
```  
  
## <a name="more-about-temporary-objects"></a>Plus d’informations sur les objets temporaires  
 Objets temporaires sont créés chaque fois que `FromHandle` reçoit un descripteur qui ne dispose pas déjà d’un objet de wrapper. Ces objets temporaires sont détachées de leur handle et supprimés par la `DeleteTempMap` fonctions. Par défaut [CWinThread::OnIdle](../mfc/reference/cwinthread-class.md#onidle) appelle automatiquement `DeleteTempMap` pour chaque classe qui prend en charge des cartes de handles temporaire. Cela signifie que vous ne peut pas supposer qu'un pointeur vers un objet temporaire sera valide après le point de sortie de la fonction dans laquelle le pointeur a été obtenu.  
  
## <a name="wrapper-objects-and-multiple-threads"></a>Objets wrapper et plusieurs Threads  
 Les objets temporaires et permanents sont conservées sur une base par thread. Autrement dit, un thread ne peut pas accéder aux objets de wrapper C++ d’un autre thread, qu’il soit temporaire ou permanent.  
  
 Pour passer ces objets à partir d’un thread à un autre, toujours les envoyer en tant que leur natif `HANDLE` type. En passant un objet de wrapper C++ à partir d’un thread à un autre entraîne souvent des résultats inattendus.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

