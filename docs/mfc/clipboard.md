---
title: Presse-papiers
ms.date: 11/04/2016
helpviewer_keywords:
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
ms.openlocfilehash: 4fcf53f1d861a85d830d0fb4244e8af9c11af163
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326902"
---
# <a name="clipboard"></a>Presse-papiers

Cette série d’articles explique comment implémenter la prise en charge pour le Presse-papiers Windows dans les applications MFC. Le Presse-papiers de Windows est utilisé de deux manières :

- Implémentation de commandes du menu Edition standards, telles que couper, copier et coller.

- Implémentation de données uniforme transférer avec glisser et déposer (OLE).

Le Presse-papiers est la méthode Windows standard de transfert de données entre une source et une destination. Il peut également être très utile pour les opérations OLE. Avec l’avènement des OLE, il existe deux mécanismes de Presse-papiers de Windows. L’API de Presse-papiers standard de Windows est toujours disponible, mais elle a été complétée avec le mécanisme de transfert de données OLE. Transfert de données uniforme OLE (UDT) prend en charge les opérations couper, copier et coller avec le Presse-papiers et glisser -déplacer.

Le Presse-papiers est un service système partagé par la session Windows entière, donc il n’a pas un handle ou une classe de son propre. Vous gérez le Presse-papiers via les fonctions membres de classe [CWnd](../mfc/reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Quand utiliser chaque mécanisme de Presse-papiers](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)

- [À l’aide de l’API du Presse-papiers Windows traditionnel](../mfc/clipboard-using-the-windows-clipboard.md)

- [À l’aide du mécanisme de Presse-papiers OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

- [Copier et coller des données](../mfc/clipboard-copying-and-pasting-data.md)

- [Ajout d’autres formats](../mfc/clipboard-adding-other-formats.md)

- [Le Presse-papiers Windows](https://msdn.microsoft.com/library/ms648709)

- [Implémentation du glisser- déposer (OLE)](../mfc/drag-and-drop-ole.md)

## <a name="see-also"></a>Voir aussi

[Éléments d’Interface utilisateur](../mfc/user-interface-elements-mfc.md)
