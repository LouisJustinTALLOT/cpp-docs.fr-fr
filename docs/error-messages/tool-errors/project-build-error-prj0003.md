---
title: Erreur de génération de projet PRJ0003
ms.date: 11/04/2016
f1_keywords:
- PRJ0003
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
ms.openlocfilehash: 00d101e62d49078ebfcfff9455497f30224b84fe
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039504"
---
# <a name="project-build-error-prj0003"></a>Erreur de génération de projet PRJ0003

> Erreur lors de la génération '*ligne de commande*».

Le *ligne de commande* commande formée à partir de l’entrée dans le **Pages de propriétés** boîte de dialogue retourné un code d’erreur, mais aucune information n’apparaît dans le **sortie** fenêtre.

Les raisons possibles de cette erreur sont les suivantes :

- Votre projet dépend d’ATL Server. À compter de Visual Studio 2008, ATL Server n’est plus inclus dans le cadre de Visual Studio, mais a été publié comme projet source partagé sur CodePlex. Pour télécharger les outils et le code source ATL Server, accédez à [outils et la bibliothèque ATL Server](http://go.microsoft.com/fwlink/p/?linkid=81979).

- Ressources système faibles. Fermez certaines applications pour résoudre ce problème.

- Privilèges de sécurité insuffisantes. Vérifiez que vous disposez des privilèges de sécurité suffisants.

- Les chemins d’accès à l’exécutables spécifiés dans **répertoires VC ++** n’incluent pas le chemin d’accès de l’outil que vous essayez d’exécuter. Pour plus d’informations, consultez [définir du compilateur et les propriétés de build](../../build/working-with-project-properties.md)

- Pour les projets makefile, il manque une commande à exécuter sur **générer la ligne de commande** ou **ligne de commande Rebuild**.

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements de génération de projet (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)