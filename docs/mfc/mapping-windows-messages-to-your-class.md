---
description: 'En savoir plus sur : mappage des messages Windows à votre classe'
title: Mappage des messages Windows à votre classe
ms.date: 09/06/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
- Class Wizard [MFC]
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: cca13c4b262c6373fa3d968438331d5e0ce5f7d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280779"
---
# <a name="mapping-windows-messages-to-your-class"></a>Mappage des messages Windows à votre classe

Si vous avez besoin que votre boîte de dialogue gère les messages Windows, substituez les fonctions de gestionnaire appropriées. Pour ce faire, choisissez l’onglet **affichage de classes** dans **Explorateur de solutions**, cliquez avec le bouton droit sur la classe qui représente la boîte de dialogue, puis choisissez [Assistant classe](reference/mfc-class-wizard.md). Utilisez l’Assistant pour [mapper les messages](reference/mapping-messages-to-functions.md) à la classe dialog. Cela écrit une entrée de table des messages pour chaque message et ajoute les fonctions membres du gestionnaire de messages à la classe. Utilisez l’éditeur de code pour écrire du code dans les gestionnaires de messages.

Vous pouvez également substituer les fonctions membres de [CDialog](reference/cdialog-class.md) et ses classes de base, en particulier [CWnd](reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Gestion et mappage des messages](message-handling-and-mapping.md)

- [Fonctions membres couramment substituées](commonly-overridden-member-functions.md)

- [Fonctions membres couramment ajoutées](commonly-added-member-functions.md)

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](dialog-boxes.md)<br/>
[Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)
