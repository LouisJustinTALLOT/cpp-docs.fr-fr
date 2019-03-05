---
title: À l’aide d’une fenêtre (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- CWindow class, about CWindow class
- windows [C++], ATL
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
ms.openlocfilehash: 3a1843bfedc30e7d3b47c2916af08c8b53aaa965
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268861"
---
# <a name="using-a-window"></a>À l’aide d’une fenêtre

Classe [CWindow](../atl/reference/cwindow-class.md) vous permet d’utiliser une fenêtre. Une fois que vous attachez une fenêtre à un `CWindow` de l’objet, vous pouvez ensuite appeler `CWindow` méthodes permettant de manipuler la fenêtre. `CWindow` contient également un opérateur HWND pour convertir un `CWindow` objet en un HWND. Par conséquent, vous pouvez passer un `CWindow` objet à n’importe quelle fonction nécessitant un handle de fenêtre. Vous pouvez facilement combiner `CWindow` appels de méthode et les appels de fonction Win32, sans créer d’objets temporaires.

Étant donné que `CWindow` n'a que deux données membres (un handle de fenêtre et les dimensions par défaut), il n’impose pas de surcharge sur votre code. En outre, la plupart de la `CWindow` méthodes ne font qu’envelopper les fonctions API Win32 correspondantes. À l’aide de `CWindow`, le membre HWND est automatiquement passé à la fonction Win32.

Outre l’utilisation de `CWindow` directement, vous pouvez également dériver à partir de celle-ci pour ajouter des données ou le code à votre classe. ATL lui-même dérive les trois classes de `CWindow`: [CWindowImpl](../atl/implementing-a-window.md), [CDialogImpl](../atl/implementing-a-dialog-box.md), et [CContainedWindowT](../atl/using-contained-windows.md).

## <a name="see-also"></a>Voir aussi

[Classes de fenêtre](../atl/atl-window-classes.md)
