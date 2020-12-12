---
description: 'En savoir plus sur : TN070 : noms des classes de fenêtre MFC'
title: 'TN070 : noms des classes de fenêtre MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: 963f343f480a5805a3c1ec3cf5499583a17535ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214518"
---
# <a name="tn070-mfc-window-class-names"></a>TN070 : noms des classes de fenêtre MFC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Les fenêtres MFC utilisent un nom de classe créé dynamiquement qui reflète les fonctionnalités de la fenêtre. MFC génère dynamiquement des noms de classe pour les fenêtres Frame, les vues et les fenêtres contextuelles produites par l’application. Les boîtes de dialogue et les contrôles produits par une application MFC ont le nom fourni par Windows pour la classe de la fenêtre en question.

Vous pouvez remplacer le nom de classe fourni dynamiquement en inscrivant votre propre classe de fenêtre et en l’utilisant dans une substitution de [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow). Leurs noms de classes fournis par MFC correspondent à l’une des deux formes suivantes :

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

Les chiffres hexadécimaux qui remplacent les `%x` caractères sont renseignés à partir des données de la structure [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) . MFC utilise cette technique pour que plusieurs classes C++ nécessitant des structures **WNDCLASS** identiques puissent partager la même classe de fenêtre inscrite. Contrairement à la plupart des applications Win32 simples, les applications MFC n’ont qu’une **WNDPROC**, ce qui vous permet de partager facilement des structures **WNDCLASS** pour gagner du temps et de la mémoire. Les valeurs remplaçables pour les `%x` caractères indiqués ci-dessus sont les suivantes :

- **WNDCLASS. hInstance**

- **WNDCLASS. style**

- **WNDCLASS. hCursor**

- **WNDCLASS. hbrBackground**

- **WNDCLASS. hIcon**

La première forme ( `Afx:%x:%x` ) est utilisée lorsque **hCursor**, **hbrBackground** et **HICON** ont tous la **valeur null**.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)<br/>
[TN020 : conventions de dénomination et de numérotation des ID](../mfc/tn020-id-naming-and-numbering-conventions.md)
