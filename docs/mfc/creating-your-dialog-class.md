---
description: 'En savoir plus sur : création de votre classe de boîte de dialogue'
title: Création de votre classe de boîte de dialogue
ms.date: 09/06/2019
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
ms.openlocfilehash: d135d6acaefbc73f435e48db8f72add7081fdac2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309444"
---
# <a name="creating-your-dialog-class"></a>Création de votre classe de boîte de dialogue

Pour chaque boîte de dialogue de votre programme, créez une nouvelle classe de boîte de dialogue pour travailler avec la ressource de boîte de dialogue.

L' [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md) explique comment créer une classe de boîte de dialogue. Quand vous créez une classe de boîte de dialogue avec l' [Assistant classe](reference/mfc-class-wizard.md), elle écrit les éléments suivants dans les fichiers. h et. cpp que vous spécifiez :

Dans le fichier. h :

- Déclaration de classe pour la classe dialog. La classe est dérivée de [CDialog](reference/cdialog-class.md).

Dans le fichier. cpp :

- Une table des messages pour la classe.

- Constructeur standard pour la boîte de dialogue.

- Substitution de la fonction membre [DoDataExchange](reference/cwnd-class.md#dodataexchange) . Modifiez cette fonction. Il est utilisé pour l’échange de données de boîtes de dialogue et les fonctionnalités de validation, comme décrit plus loin dans [échange et validation de données de boîtes de dialogue](dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Voir aussi

[Création d’une classe de boîte de dialogue à l’aide des assistants code](creating-a-dialog-class-with-code-wizards.md)<br/>
[Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)
