---
title: 'TN070 : Noms de classe de fenêtre MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.classes
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: 8b06f7b3656284de18632185877fdbe382343f95
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62168035"
---
# <a name="tn070-mfc-window-class-names"></a>TN070 : Noms de classe de fenêtre MFC

> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Windows MFC utilisent un nom de classe créé dynamiquement qui reflète les fonctionnalités de la fenêtre. MFC génère des noms de classe dynamiquement pour les fenêtres frame, vues et fenêtres contextuelles produits par l’application. Boîtes de dialogue et les contrôles de produits par une application MFC ont le nom fourni par Windows pour la classe de fenêtre en question.

Vous pouvez remplacer le nom de classe dynamiquement fournie par l’inscription de votre propre classe de fenêtre et son utilisation dans une substitution de [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow). Leurs noms de classe fournie par MFC rentre dans l’une des deux formes suivantes :

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

Les chiffres hexadécimaux qui remplacent la `%x` caractères sont renseignés à partir des données à partir de la [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa) structure. MFC utilise cette technique afin que plusieurs classes C++ nécessitant identiques **WNDCLASS** structures peuvent partager la même classe de fenêtres inscrites. Contrairement à la plupart des applications Win32 simple, les applications MFC ont un seul **WNDPROC**, de sorte que vous pouvez facilement partager **WNDCLASS** structures pour gagner du temps et mémoire. Les valeurs remplaçables pour la `%x` caractères indiqués ci-dessus sont les suivants :

- **WNDCLASS.hInstance**

- **WNDCLASS.style**

- **WNDCLASS.hCursor**

- **WNDCLASS.hbrBackground**

- **WNDCLASS.hIcon**

La première forme (`Afx:%x:%x`) est utilisé lorsque **hCursor**, **hbrBackground**, et **hIcon** sont tous **NULL**.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)<br/>
[TN020 : Conventions de dénomination d’ID et de numérotation](../mfc/tn020-id-naming-and-numbering-conventions.md)
