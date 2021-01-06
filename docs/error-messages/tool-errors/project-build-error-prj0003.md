---
description: 'En savoir plus sur : erreur de génération de projet projet PRJ0003'
title: Erreur de génération de projet PRJ0003
ms.date: 11/04/2016
f1_keywords:
- PRJ0003
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
ms.openlocfilehash: b5ca521bdddb78c3cd7c5dd41f8999b99cb92e20
ms.sourcegitcommit: 6183207b11575d7b44ebd7c18918e916a0d8c63d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97951435"
---
# <a name="project-build-error-prj0003"></a>Erreur de génération de projet PRJ0003

> Erreur lors de la génération de la *ligne de commande*.

La commande de *ligne de commande* formée à partir d’une entrée dans la boîte de dialogue **pages de propriétés** a retourné un code d’erreur, mais aucune information n’apparaît dans la fenêtre **sortie** .

Les raisons possibles de cette erreur sont les suivantes :

- Votre projet dépend de ATL Server. À compter de Visual Studio 2008, ATL Server n’est plus inclus dans Visual Studio, mais il a été publié en tant que projet de source partagée sur CodePlex. Pour télécharger le code source et les outils ATL Server, accédez à [bibliothèque et outils ATL Server](https://archive.codeplex.com/?p=atlserver).

- Ressources système insuffisantes. Fermez certaines applications pour résoudre ce qui se passe.

- Privilèges de sécurité insuffisants. Vérifiez que vous disposez des privilèges de sécurité suffisants.

- Les chemins d’accès aux fichiers exécutables spécifiés dans les **Répertoires VC + +** n’incluent pas le chemin d’accès de l’outil que vous tentez d’exécuter. Pour plus d’informations, consultez [définir les propriétés de compilation et de génération](../../build/working-with-project-properties.md)

- Pour les projets Makefile, vous ne disposez pas d’une commande à exécuter sur une ligne de **commande Build** ou une **ligne de commande** Rebuild.

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements de génération de projet (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
