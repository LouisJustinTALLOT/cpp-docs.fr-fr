---
title: Mappage de messages à des fonctions
ms.date: 09/06/2019
f1_keywords:
- vc.codewiz.mapping.msg.function
helpviewer_keywords:
- Windows messages [MFC], adding message handlers
- message maps [MFC], mapping messages to functions
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
ms.openlocfilehash: 4c7e79e31bbf9b35f9d888dce4e4fc24feacc624
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365664"
---
# <a name="mapping-messages-to-functions"></a>Mappage de messages à des fonctions

Le [Class Wizard](mfc-class-wizard.md) vous permet de lier les gestionnaires de messages (fonctions membres des classes d’interface utilisateur MFC) aux messages générés par les ressources de votre application. Ils utilisent les [cartes de messages MFC](../../mfc/messages-and-commands-in-the-framework.md) pour créer la liaison.

Lorsque vous utilisez Class View pour créer une nouvelle classe dérivée de l’une des classes-cadres, elle place automatiquement une classe complète et fonctionnelle dans les fichiers d’en-tête (.h) et de mise en œuvre (.cpp) que vous spécifiez.

> [!NOTE]
> Pour ajouter une nouvelle classe qui ne gère pas les messages, créez la classe directement dans l’éditeur de texte.

### <a name="to-define-or-remove-a-message-handler-using-the-class-wizard"></a>Définir ou supprimer un gestionnaire de message à l’aide de l’assistant de classe

1. Dans **Class View**, cliquez à droite sur la classe.

1. Dans le menu contexte, choisissez [Class Wizard](mfc-class-wizard.md).

## <a name="see-also"></a>Voir aussi

[Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Ajout d’une variable membre](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Substitution d’une fonction virtuelle](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Parcours de la structure de classe](../../ide/navigate-code-cpp.md)
