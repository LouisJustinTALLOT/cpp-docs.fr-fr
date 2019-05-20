---
title: Ajout d’un consommateur OLE DB ATL
ms.date: 05/09/2019
helpviewer_keywords:
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
ms.openlocfilehash: 1e384a283a2a149faa5b8d6e0817eac3cacfeff9
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706918"
---
# <a name="adding-an-atl-ole-db-consumer"></a>Ajout d’un consommateur OLE DB ATL

::: moniker range="vs-2019"

L’Assistant Consommateur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et les versions ultérieures. Vous pouvez toujours ajouter la fonctionnalité manuellement. Pour plus d’informations, consultez [Création d’un consommateur sans utiliser l’Assistant](../../data/oledb/creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=vs-2017"

Utilisez cet Assistant pour ajouter un consommateur OLE DB ATL à un projet. Un consommateur ATL OLE DB se compose d’une classe d’accesseur OLE DB et des liaisons de données nécessaires pour accéder à une source de données. Le projet doit avoir été créé comme une application ATL COM ou comme une application MFC ou Win32 avec support ATL (que l’Assistant Consommateur ATL OLE DB ajoute automatiquement).

> [!NOTE]
> Vous pouvez ajouter un consommateur OLE DB à un projet MFC. Si vous le faites, l’Assistant Consommateur OLE DB ATL ajoute la prise en charge COM nécessaire à votre projet. Cela suppose que lorsque vous avez créé le projet MFC, la case **contrôles ActiveX** (dans la page **Fonctionnalités avancées** de l’Assistant d’Application de projet MFC) est cochée (cochée par défaut). Cette option garantit que l’application appelle `CoInitialize` et `CoUninitialize`. Si vous n’avez pas sélectionné **contrôles ActiveX** lorsque vous avez créé le projet MFC, vous devez appeler `CoInitialize` et `CoUninitialize` dans votre code principal.

## <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>Pour ajouter un fournisseur OLE DB ATL à votre projet

1. Dans **Affichage de classes**, cliquez avec le bouton droit sur le projet. Dans le menu contextuel, cliquez sur **Ajouter**, puis cliquez sur **Ajouter une classe**.

1. Dans le dossier Visual C++, double-cliquez sur l’icône **ATL OLE DB Consumer** (Consommateur OLE DB ATL) ou sélectionnez-le et cliquez sur **Ouvrir**.

   L’Assistant Consommateur OLE DB ATL s’ouvre.

1. Définissez les paramètres comme décrit dans l’[Assistant Consommateur OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).

1. Cliquez sur **Terminer** pour fermer l’Assistant. Le code de consommateur OLE DB nouvellement créé est inséré dans votre projet.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)
