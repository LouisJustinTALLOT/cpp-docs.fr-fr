---
title: Définition des Variables membres pour les contrôles de boîte de dialogue (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog Editor [C++], defining member variables for controls
ms.assetid: 84347c63-c33c-4b04-91f5-6d008c45ba58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fa4d894fb3fc436abab84bfee11199f59bd66f78
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402393"
---
# <a name="defining-member-variables-for-dialog-controls-c"></a>Définition des Variables membres pour les contrôles de boîte de dialogue (C++)

Pour définir une variable membre pour un contrôle de boîte de dialogue à l'exception des boutons, vous pouvez utiliser la méthode suivante.

> [!NOTE]
> Cet article s'applique uniquement aux contrôles de boîte de dialogue dans un projet MFC. Les projets ATL doivent utiliser la **nouveaux Messages Windows et gestionnaires d’événements** boîte de dialogue.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Pour définir une variable membre pour un contrôle de boîte de dialogue (à l'exception d'un bouton)

1. Dans le [éditeur de boîte de dialogue](../windows/dialog-editor.md), sélectionnez un contrôle.

2. Tout en maintenant la **Ctrl** enfoncée, double-cliquez sur le contrôle de boîte de dialogue.

   Le [Assistant Ajout de Variable membre](../ide/add-member-variable-wizard.md) s’affiche.

3. Tapez les informations appropriées dans le **ajouter une Variable membre** Assistant. Pour plus d’informations, consultez [échange de données de boîtes de dialogue](../mfc/dialog-data-exchange.md).

4. Cliquez sur **OK** pour revenir à la **boîte de dialogue** éditeur.

   > [!TIP]
   > Pour passer d'un contrôle de boîte de dialogue à son gestionnaire existant, double-cliquez sur le contrôle.

Vous pouvez également utiliser le **Variables membres** onglet **Assistant classe MFC** pour ajouter de nouvelles variables de membre pour une classe spécifiée et afficher ceux qui ont déjà été définis.

## <a name="requirements"></a>Configuration requise

MFC

## <a name="see-also"></a>Voir aussi

[Mappage des messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Classe MFC, Assistant](../mfc/reference/mfc-class-wizard.md)<br/>
[Ajout d’une classe](../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout d’une fonction membre](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Ajout d’une variable membre](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Une fonction virtuelle de substitution](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Gestionnaire de messages MFC](../mfc/reference/adding-an-mfc-message-handler.md)