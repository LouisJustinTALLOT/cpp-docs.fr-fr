---
title: À l’aide d’une fenêtre (ATL) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- CWindow class, about CWindow class
- windows [C++], ATL
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f946f99fd198db281418e2a471489b2236972435
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358392"
---
# <a name="using-a-window"></a>À l’aide d’une fenêtre
Classe [CWindow](../atl/reference/cwindow-class.md) vous permet d’utiliser une fenêtre. Une fois que vous attachez une fenêtre à un `CWindow` de l’objet, vous pouvez ensuite appeler `CWindow` méthodes pour manipuler la fenêtre. `CWindow` contient également une `HWND` pour convertir un `CWindow` de l’objet à un `HWND`. Par conséquent, vous pouvez passer un `CWindow` objet à n’importe quelle fonction qui requiert un handle de fenêtre. Vous pouvez facilement combiner `CWindow` appels de méthode et les appels de fonction Win32, sans créer d’objets temporaires.  
  
 Étant donné que `CWindow` a un membre de données uniquement deux (un handle de fenêtre et les dimensions par défaut), il n’impose pas de surcharge sur votre code. En outre, la plupart de la `CWindow` encapsulent simplement les fonctions API Win32 correspondantes. À l’aide de `CWindow`, le `HWND` membres est automatiquement passée à la fonction Win32.  
  
 Outre l’utilisation de `CWindow` directement, vous pouvez également dériver pour ajouter des données ou du code à votre classe. ATL elle-même dérive les trois classes de `CWindow`: [CWindowImpl](../atl/implementing-a-window.md), [CDialogImpl](../atl/implementing-a-dialog-box.md), et [CContainedWindowT](../atl/using-contained-windows.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Classes de fenêtre](../atl/atl-window-classes.md)

