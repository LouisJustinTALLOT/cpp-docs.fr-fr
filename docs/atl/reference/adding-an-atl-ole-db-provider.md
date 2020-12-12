---
description: 'En savoir plus sur : ajout d’un fournisseur de OLE DB ATL'
title: Ajout d’un fournisseur OLE DB ATL
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, adding ATL OLE DB provider to projects
- ATL projects, adding ATL OLE DB providers
- ATL OLE DB providers
ms.assetid: 26fba1e3-880f-4bc6-90e5-2096a48a3a6c
ms.openlocfilehash: e60150e2d8dc57e16a55c75556d109583a95f054
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165665"
---
# <a name="adding-an-atl-ole-db-provider"></a>Ajout d’un fournisseur OLE DB ATL

::: moniker range="msvc-160"

L’Assistant Fournisseur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et versions ultérieures.

::: moniker-end

::: moniker range="<=msvc-150"

Utilisez cet Assistant pour ajouter un fournisseur OLE DB ATL à un projet. Un fournisseur OLE DB ATL se compose de classes data source, session, command et rowset. Le projet doit avoir été créé en tant qu’application COM ATL.

## <a name="to-add-an-atl-ole-db-provider-to-your-project"></a>Pour ajouter un fournisseur OLE DB ATL à votre projet

1. Dans **Affichage de classes**, cliquez avec le bouton droit sur le projet. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter une classe**.

1. Dans le dossier **Visual C++**, double-cliquez sur l’icône **ATL OLE DB Provider** (Fournisseur OLE DB ATL) ou sélectionnez-le et cliquez sur **Ouvrir**.

   L’Assistant Fournisseur OLE DB ATL s’affiche.

1. Définissez les paramètres comme décrit dans [Assistant Fournisseur OLE DB ATL](../../atl/reference/atl-ole-db-provider-wizard.md).

1. Cliquez sur **Terminer** pour fermer l’Assistant, ce qui va insérer le code du fournisseur OLE DB nouvellement créé dans votre projet.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)
