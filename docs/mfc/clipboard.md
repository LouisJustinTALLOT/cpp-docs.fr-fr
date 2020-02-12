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
ms.openlocfilehash: 1db089110904ab88eb9c0c111d9da4e4e6869c82
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127905"
---
# <a name="clipboard"></a>Presse-papiers

Cette famille d’articles explique comment implémenter la prise en charge du presse-papiers Windows dans les applications MFC. Le presse-papiers Windows est utilisé de deux manières :

- Implémentation de commandes de menu Edition standard, telles que couper, copier et coller.

- Implémentation du transfert de données uniforme avec glisser-déplacer OLE.

Le presse-papiers est la méthode Windows standard de transfert de données entre une source et une destination. Elle peut également être très utile dans les opérations OLE. Avec l’avènement d’OLE, il existe deux mécanismes de presse-papiers dans Windows. L’API du presse-papiers Windows standard est toujours disponible, mais elle a été complétée par le mécanisme de transfert de données OLE. Le transfert de données uniforme OLE (UDT) prend en charge les opérations couper, copier et coller avec le presse-papiers et le glisser-déplacer.

Le presse-papiers est un service système partagé par l’ensemble de la session Windows. il n’a donc pas de descripteur ou de classe propre. Vous gérez le presse-papiers à l’aide des fonctions membres de la classe [CWnd](../mfc/reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Quand utiliser chaque mécanisme de presse-papiers](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)

- [Utilisation de l’API du presse-papiers Windows classique](../mfc/clipboard-using-the-windows-clipboard.md)

- [Utilisation du mécanisme de presse-papiers OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

- [Copier et coller des données](../mfc/clipboard-copying-and-pasting-data.md)

- [Ajout d’autres formats](../mfc/clipboard-adding-other-formats.md)

- [Le presse-papiers Windows](/windows/win32/dataxchg/clipboard)

- [Glisser-déplacer OLE](../mfc/drag-and-drop-ole.md)

## <a name="see-also"></a>Voir aussi

[Éléments de l’interface utilisateur](../mfc/user-interface-elements-mfc.md)
