---
title: Ajout d’objets et de contrôles à un projet ATL
ms.date: 05/09/2019
f1_keywords:
- vc.appwiz.ATL.controls
helpviewer_keywords:
- ATL projects, adding objects
- wizards [C++], ATL projects
- ATL projects, adding controls
- controls [ATL], adding to projects
- objects [C++], adding to ATL projects
- ATL Control Wizard
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
ms.openlocfilehash: b1bf4f85ccf7a0bb2d77bfb96c512349f581f193
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832449"
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>Ajout d’objets et de contrôles à un projet ATL

> [!NOTE]
> L’Assistant Composant ATL COM+ 1.0, l’Assistant Consommateur OLE DB ATL et l’Assistant Composant ASP ATL ne sont pas disponibles dans Visual Studio 2019 et ultérieur.

Vous pouvez utiliser l’un des Assistants de code ATL pour ajouter un objet ou un contrôle à vos projets ATL ou MFC. Pour chaque objet ou contrôle COM que vous ajoutez, l’Assistant génère des fichiers .cpp et .h, mais également un fichier .rgs pour une prise en charge du registre basée sur un script. Les Assistants de code ATL suivants sont disponibles dans Visual Studio :

- [Objet simple ATL](../../atl/reference/atl-simple-object-wizard.md)
- [Boîte de dialogue ATL](../../atl/reference/atl-dialog-wizard.md)
- [Contrôle ATL](../../atl/reference/atl-control-wizard.md)
- [Page de propriétés ATL](../../atl/reference/atl-property-page-wizard.md)
- [Composant ASP ATL](../../atl/reference/atl-active-server-page-component-wizard.md)
- [Consommateur ATL OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md)
- [Ajouter la prise en charge ATL à MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)
- [Assistant Composant COM+ 1.0 ATL](../../atl/reference/atl-com-plus-1-0-component-wizard.md)
- [Ajout d’un fournisseur OLE DB ATL](../../atl/reference/atl-ole-db-provider-wizard.md)

> [!NOTE]
> Avant d’ajouter un objet ATL à votre projet, vous devez passer en revue les détails et les exigences de cet objet dans les rubriques d’aide connexes.

## <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>Pour ajouter un objet ou un contrôle à l’aide de l’Assistant Contrôle ATL

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet, puis cliquez sur **Ajouter** dans le menu contextuel. Cliquez sur **Ajouter une classe**.

   La boîte de dialogue [Ajouter une classe](../../ide/add-class-dialog-box.md) s’affiche.

1. Sélectionnez le dossier **ATL** situé dans le volet **Catégories**, puis sélectionnez un objet à insérer dans le volet **Modèles**. Cliquez sur **Ouvrir**. L’Assistant Code de l’objet sélectionné s’affiche.

   > [!NOTE]
   > Si vous souhaitez ajouter un objet ATL à un projet MFC, vous devez ajouter la prise en charge ATL au projet existant. Pour cela, vous pouvez suivre les instructions fournies dans [Ajout de la prise en charge ATL à votre projet MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md).

   Si vous essayez d’ajouter un objet ATL à votre projet MFC sans ajouter au préalable une prise en charge ATL, Visual Studio vous demande si vous souhaitez ajouter la prise en charge ATL à votre projet. Cliquez sur **Oui** pour ajouter la prise en charge ATL au projet et ouvrir l’Assistant ATL sélectionné.

## <a name="see-also"></a>Voir aussi

[Assistant Projet ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Types de projets C++ dans Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Notions de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programmation à l’aide du code ATL et Runtime C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)
