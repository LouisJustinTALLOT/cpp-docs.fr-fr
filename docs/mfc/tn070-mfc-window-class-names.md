---
title: 'TN070 : noms des classes de fenêtre MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: ad43f5af5d2e90cb5fc2bc90f0909c2b495b4a4c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373483"
---
# <a name="tn070-mfc-window-class-names"></a>TN070 : noms des classes de fenêtre MFC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Les fenêtres MFC utilisent un nom de classe créé dynamiquement qui reflète les caractéristiques de la fenêtre. MFC génère dynamiquement des noms de classe pour les fenêtres à cadre, les vues et les fenêtres contexturations produites par l’application. Les boîtes de dialogue et les contrôles produits par une application MFC ont le nom fourni par Windows pour la classe de fenêtre en question.

Vous pouvez remplacer le nom de classe fourni dynamiquement en enregistrant votre propre classe de fenêtre et en l’utilisant dans un remplacement de [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow). Leurs noms de classe fournis par MFC correspondent à l’un des deux formulaires suivants :

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

Les chiffres hex qui `%x` remplacent les caractères sont remplis à partir des données de la structure [WNDCLASS.](/windows/win32/api/winuser/ns-winuser-wndclassw) MFC utilise cette technique afin que plusieurs classes de CMD nécessitant des structures **WNDCLASS** identiques puissent partager la même classe de fenêtre enregistrée. Contrairement à la plupart des applications Win32 simples, les applications MFC n’ont qu’un seul **WNDPROC**, de sorte que vous pouvez facilement partager les structures **WNDCLASS** pour gagner du temps et de la mémoire. Les valeurs remplaçables pour les `%x` caractères indiqués ci-dessus sont les suivantes :

- **WNDCLASS.hInstance**

- **WNDCLASS.style**

- **WNDCLASS.hCursor (en)**

- **WNDCLASS.hbrBackground (en)**

- **WNDCLASS.hIcon (en)**

La première`Afx:%x:%x`forme ( ) est utilisée lorsque **hCursor**, **hbrBackground**, et **hIcon** sont tous **NULL**.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)<br/>
[TN020 : conventions de dénomination d'ID et de numérotation](../mfc/tn020-id-naming-and-numbering-conventions.md)
