---
description: 'En savoir plus sur : TN003 : mappage des handles Windows à des objets'
title: 'TN003 : mappage des handles Windows à des objets'
ms.date: 11/04/2016
f1_keywords:
- vc.mapping
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
ms.openlocfilehash: e4a0bfa2315ec2b9d67d884d4fdebe314599f454
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216039"
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003 : mappage des handles Windows à des objets

Cette note décrit les routines MFC qui prennent en charge le mappage des descripteurs d’objets Windows aux objets C++.

## <a name="the-problem"></a>Le problème

Les objets Windows sont généralement représentés par différents objets de [handle](/windows/win32/WinProg/windows-data-types) . les classes MFC encapsulent les handles d’objet Windows avec des objets C++. Les fonctions d’encapsulage de handle de la bibliothèque de classes MFC vous permettent de trouver l’objet C++ qui encapsule l’objet Windows qui a un handle particulier. Toutefois, parfois, un objet n’a pas d’objet wrapper C++ et, à ce moment, le système crée un objet temporaire qui agit comme le wrapper C++.

Les objets Windows qui utilisent des mappages de descripteur sont les suivants :

- HWND ([](../mfc/reference/cwnd-class.md) `CWnd` classes dérivées CWnd et)

- HDC ([](../mfc/reference/cdc-class.md) `CDC` classes dérivées CDC et)

- HMENU ([CMenu](../mfc/reference/cmenu-class.md))

- HPEN ([CGdiObject](../mfc/reference/cgdiobject-class.md))

- HBRUSH ( `CGdiObject` )

- HFONT ( `CGdiObject` )

- HBITMAP ( `CGdiObject` )

- HPALETTE ( `CGdiObject` )

- HRGN ( `CGdiObject` )

- HIMAGELIST ([CImageList](../mfc/reference/cimagelist-class.md))

- SOCKET ([CSocket](../mfc/reference/csocket-class.md))

Étant donné un handle à l’un de ces objets, vous pouvez trouver l’objet MFC qui encapsule le handle en appelant la méthode statique `FromHandle` . Par exemple, à partir d’un HWND nommé *HWND*, la ligne suivante retourne un pointeur vers `CWnd` qui encapsule *HWND*:

```
CWnd::FromHandle(hWnd)
```

Si *HWND* n’a pas d’objet de wrapper spécifique, un temporaire `CWnd` est créé pour encapsuler *HWND*. Cela permet d’obtenir un objet C++ valide à partir de n’importe quel handle.

Une fois que vous avez un objet wrapper, vous pouvez récupérer son handle d’une variable de membre public de la classe wrapper. Dans le cas d’un `CWnd` , *m_hWnd* contient le HWND de cet objet.

## <a name="attaching-handles-to-mfc-objects"></a>Attachement de handles aux objets MFC

À partir d’un objet handle-Wrapper nouvellement créé et d’un handle vers un objet Windows, vous pouvez associer les deux en appelant la `Attach` fonction comme dans l’exemple suivant :

```
CWnd myWnd;
myWnd.Attach(hWnd);
```

Cela crée une entrée dans la carte permanente associant *myWnd* et *HWND*. L’appel `CWnd::FromHandle(hWnd)` de retourne alors un pointeur vers *myWnd*. Quand *myWnd* est supprimé, le destructeur détruit automatiquement *HWND* en appelant la fonction [DestroyWindow](/windows/win32/api/winuser/nf-winuser-destroywindow) de Windows. Si ce n’est pas souhaité, *HWND* doit être détaché de *MyWnd* avant que *myWnd* soit détruit (normalement, lorsque vous quittez l’étendue à laquelle *myWnd* a été défini). La `Detach` méthode le fait.

```
myWnd.Detach();
```

## <a name="more-about-temporary-objects"></a>En savoir plus sur les objets temporaires

Les objets temporaires sont créés chaque fois `FromHandle` que reçoit un handle qui ne dispose pas déjà d’un objet wrapper. Ces objets temporaires sont détachés de leur handle et supprimés par les `DeleteTempMap` fonctions. Par défaut, [CWinThread :: OnIdle](../mfc/reference/cwinthread-class.md#onidle) appelle automatiquement `DeleteTempMap` pour chaque classe qui prend en charge les mappages de handle temporaires. Cela signifie que vous ne pouvez pas supposer qu’un pointeur vers un objet temporaire sera valide au-delà du point de sortie de la fonction où le pointeur a été obtenu.

## <a name="wrapper-objects-and-multiple-threads"></a>Objets Wrapper et threads multiples

Les objets temporaires et permanents sont conservés en fonction du thread. Autrement dit, un thread ne peut pas accéder aux objets Wrapper C++ d’un autre thread, qu’il soit temporaire ou permanent.

Pour passer ces objets d’un thread à un autre, envoyez-les toujours comme leur `HANDLE` type natif. Le passage d’un objet wrapper C++ d’un thread à un autre entraîne souvent des résultats inattendus.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
