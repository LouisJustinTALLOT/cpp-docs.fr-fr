---
title: 'TN003 : Mappage de handles Windows à des objets'
ms.date: 11/04/2016
f1_keywords:
- vc.mapping
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
ms.openlocfilehash: 45492963e1b686e03eb59c320fdc3d52d1534f7d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513538"
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003 : Mappage de handles Windows à des objets

Cette note décrit les routines MFC qui prennent en charge le mappage des C++ descripteurs d’objets Windows aux objets.

## <a name="the-problem"></a>Le problème

Les objets Windows sont généralement représentés par différents objets de [handle](/windows/win32/WinProg/windows-data-types) . les classes MFC encapsulent les handles d’objet Windows avec des C++ objets. Les fonctions d’encapsulage de handle de la bibliothèque de classes MFC C++ vous permettent de Rechercher l’objet qui encapsule l’objet Windows qui a un handle particulier. Toutefois, parfois, un objet n’a pas C++ d’objet wrapper et, à ce moment-là, le système crée un objet C++ temporaire pour agir en tant que wrapper.

Les objets Windows qui utilisent des mappages de descripteur sont les suivants:

- HWND (classes dérivées[CWnd](../mfc/reference/cwnd-class.md) et `CWnd`)

- HDC (classes dérivées[CDC](../mfc/reference/cdc-class.md) et `CDC`)

- HMENU ([CMenu](../mfc/reference/cmenu-class.md))

- HPEN ([CGdiObject](../mfc/reference/cgdiobject-class.md))

- HBRUSH (`CGdiObject`)

- HFONT (`CGdiObject`)

- HBITMAP (`CGdiObject`)

- HPALETTE (`CGdiObject`)

- HRGN (`CGdiObject`)

- HIMAGELIST ([CImageList](../mfc/reference/cimagelist-class.md))

- SOCKET ([CSocket](../mfc/reference/csocket-class.md))

Étant donné un handle à l’un de ces objets, vous pouvez trouver l’objet MFC qui encapsule le handle en appelant la méthode `FromHandle`statique. Par exemple, à partir d’un HWND nommé *HWND*, la ligne suivante retourne un pointeur vers `CWnd` qui encapsule *HWND*:

```
CWnd::FromHandle(hWnd)
```

Si *HWND* n’a pas d’objet de wrapper spécifique, un `CWnd` temporaire est créé pour encapsuler *HWND*. Cela permet d’obtenir un objet valide C++ à partir de n’importe quel handle.

Une fois que vous avez un objet wrapper, vous pouvez récupérer son handle d’une variable de membre public de la classe wrapper. Dans le cas d’un `CWnd`, *m_hWnd* contient le HWND de cet objet.

## <a name="attaching-handles-to-mfc-objects"></a>Attachement de handles aux objets MFC

À partir d’un objet handle-Wrapper nouvellement créé et d’un handle vers un objet Windows, vous pouvez associer les deux `Attach` en appelant la fonction comme dans l’exemple suivant:

```
CWnd myWnd;
myWnd.Attach(hWnd);
```

Cela crée une entrée dans la carte permanente associant *myWnd* et *HWND*. L' `CWnd::FromHandle(hWnd)` appel de retourne alors un pointeur vers *myWnd*. Quand *myWnd* est supprimé, le destructeur détruit automatiquement *HWND* en appelant la fonction [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow) de Windows. Si ce n’est pas souhaité, *HWND* doit être détaché de *MyWnd* avant que *myWnd* soit détruit (normalement, lorsque vous quittez l’étendue à laquelle *myWnd* a été défini). La `Detach` méthode le fait.

```
myWnd.Detach();
```

## <a name="more-about-temporary-objects"></a>En savoir plus sur les objets temporaires

Les objets temporaires sont créés `FromHandle` chaque fois que reçoit un handle qui ne dispose pas déjà d’un objet wrapper. Ces objets temporaires sont détachés de leur handle et supprimés par les `DeleteTempMap` fonctions. Par défaut, [CWinThread:: OnIdle](../mfc/reference/cwinthread-class.md#onidle) appelle `DeleteTempMap` automatiquement pour chaque classe qui prend en charge les mappages de handle temporaires. Cela signifie que vous ne pouvez pas supposer qu’un pointeur vers un objet temporaire sera valide au-delà du point de sortie de la fonction où le pointeur a été obtenu.

## <a name="wrapper-objects-and-multiple-threads"></a>Objets Wrapper et threads multiples

Les objets temporaires et permanents sont conservés en fonction du thread. Autrement dit, un thread ne peut pas accéder aux C++ objets wrapper d’un autre thread, qu’il soit temporaire ou permanent.

Pour passer ces objets d’un thread à un autre, envoyez-les toujours comme `HANDLE` leur type natif. Le passage C++ d’un objet wrapper d’un thread à un autre entraîne souvent des résultats inattendus.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
