---
title: Ajout d’un composant ATL ASP
ms.date: 05/09/2019
ms.assetid: 7be2204c-6e58-4099-8892-001b848c8987
ms.openlocfilehash: b6c1d23efdff6885cc8ab900aaf552db39631e6e
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706934"
---
# <a name="adding-an-atl-active-server-page-component"></a>Ajout d’un composant ATL ASP


::: moniker range="vs-2019"

L’Assistant Composant ATL ASP (Active Template Library) n’est pas disponible dans Visual Studio 2019 et ultérieur.

::: moniker-end

::: moniker range="<=vs-2017"

Pour ajouter un objet ATL à votre projet, celui-ci doit avoir été créé en tant qu’application ATL COM ou en tant qu’application MFC contenant la prise en charge d’ATL. Vous pouvez utiliser l’[Assistant Projet ATL](../../atl/reference/atl-project-wizard.md) pour créer une application ATL, vous pouvez sélectionner **Ajouter la prise en charge ATL à MFC** dans la boîte de dialogue [Ajouter une classe](../../ide/add-class-dialog-box.md) ou vous pouvez [ajouter un objet ATL à votre application MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) pour implémenter la prise en charge d’ATL dans une application MFC.

Les composants ASP font partie de l’architecture Internet Information Services, qui fournit les fonctionnalités de développement web avancées suivantes :

- Vous pouvez incorporer des composants ASP dans vos pages HTML pour créer du contenu dynamique, indépendant du navigateur.

- Vous pouvez utiliser des pages ASP pour fournir une connectivité de base de données basée sur des standards.

- Vous pouvez utiliser les fonctionnalités de gestion des erreurs d’ASP pour vos applications web.

## <a name="to-add-an-atl-active-server-pages-component-to-your-project"></a>Pour ajouter un composant ATL ASP à votre projet

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet auquel vous voulez ajouter le composant ATL ASP.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Ajouter une classe**.

1. Dans la boîte de dialogue [Ajouter une classe](../../ide/add-class-dialog-box.md), dans le volet **Modèles**, cliquez sur **Composant ATL ASP**, puis sur **Ouvrir** pour afficher l’[Assistant Composant ATL ASP](../../atl/reference/atl-active-server-page-component-wizard.md).

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout d’une nouvelle interface à un projet ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[Ajout de points de connexion à un objet](../../atl/adding-connection-points-to-an-object.md)<br/>
[Ajout d’une méthode](../../ide/adding-a-method-visual-cpp.md)<br/>
[Classe MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Ajout d’une classe C++ générique](../../ide/adding-a-generic-cpp-class.md)
