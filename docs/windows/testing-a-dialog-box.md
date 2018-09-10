---
title: Test d’une boîte de dialogue (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f0680ac7b926e3956efdadfa9342cfc5cd5f1239
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314610"
---
# <a name="testing-a-dialog-box-c"></a>Test d’une boîte de dialogue (C++)

Lorsque vous créez une boîte de dialogue, vous pouvez simuler et tester son comportement au moment de l’exécution sans compiler votre programme. Dans ce mode, vous pouvez :

- Taper du texte, effectuer des sélections dans des listes de zone de liste déroulante, activer ou désactiver des options, et choisir des commandes

- Tester l’ordre de tabulation

- Tester le groupement des contrôles tels que les cases à cocher et les cases d’option

- Tester les raccourcis clavier pour les contrôles dans la boîte de dialogue

   > [!NOTE]
   > Les connexions au code de boîte de dialogue effectuées à l’aide des Assistants ne sont pas incluses dans la simulation.

Quand vous testez une boîte de dialogue, elle s’affiche généralement à un emplacement qui est relatif à la fenêtre principale du programme. Si vous avez défini la boîte de dialogue **Absolute Align** propriété **True**, la boîte de dialogue affiche à une position qui est relative à l’angle supérieur gauche de l’écran.

### <a name="to-test-a-dialog-box"></a>Pour tester une boîte de dialogue

1. Lorsque le **boîte de dialogue** éditeur est la fenêtre active, dans la barre de menus, choisissez **Format** > **boîte de dialogue Test**.

2. Pour arrêter la simulation, appuyez sur **ÉCHAP**, ou sélectionnez simplement le **fermer** bouton dans la boîte de dialogue que vous testez.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)  
[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)  
[Affichage ou masquage de la barre d’outils Éditeur de boîtes de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)