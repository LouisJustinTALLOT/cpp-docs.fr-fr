---
title: Aperçu des ressources (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- resources [C++], viewing
ms.assetid: d6abda66-0e2b-4ac3-a59a-a57b8c6fb70b
ms.openlocfilehash: 79756bd71dfc731b78b21bd4df311e4848beb899
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589546"
---
# <a name="previewing-resources"></a>Aperçu des ressources

L’aperçu des ressources permet d’afficher des ressources graphiques sans les ouvrir. L’aperçu est également utile pour les exécutables une fois que vous les avez compilé, car les identificateurs de ressource se transformer en nombres. Dans la mesure où ces identificateurs numériques ne fournissent pas suffisamment d’informations, l’aperçu des ressources vous aide à identifier rapidement les.

Vous pouvez afficher un aperçu de la présentation visuelle des types de ressources suivants :

- Bitmap

- Boîte de dialogue

- Icône

- Menu

- Curseur

- ToolBar

La fonction d’aperçu visuel ne s’applique pas aux ressources accélérateur, manifeste, Table de chaînes et informations de Version.

### <a name="to-preview-resources"></a>Pour afficher un aperçu des ressources

1. Dans [affichage des ressources](../windows/resource-view-window.md) ou une fenêtre de document, sélectionnez votre ressource, par exemple, **IDD_ABOUTBOX**.

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), cliquez sur le **Pages de propriétés** bouton.

   \- ou -

3. Dans le menu **vue**, cliquez sur **Pages de propriétés**.

   Le **Page de propriétés** pour la ressource s’ouvre affichant un aperçu de cette ressource. Vous pouvez ensuite utiliser le **des** et **vers le bas** dans contrôlent des touches de direction pour parcourir l’arborescence **affichage des ressources** ou la fenêtre de document. Le **Page de propriétés** reste ouverte et affiche toutes les ressources qui a le focus et sont en mesure d’afficher un aperçu.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Guide pratique pour ouvrir un fichier de script de ressources en dehors d’un projet (autonome)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)