---
title: Ajout d’un consommateur ATL OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- OLE DB, adding ATL OLE DB consumer to projects
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95d0f16f88006c1e639b1f4a02965ad8dea6b818
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764278"
---
# <a name="adding-an-atl-ole-db-consumer"></a>Ajout d’un consommateur ATL OLE DB

Utilisez cet Assistant pour ajouter un consommateur OLE DB ATL à un projet. Un consommateur OLE DB ATL se compose d’une OLE DB accesseur classe et les données des liaisons nécessaires pour accéder à une source de données. Le projet doit avoir été créé comme une application ATL COM ou comme une application MFC ou Win32 qui contient la prise en charge ATL (que l’Assistant Consommateur OLE DB ATL ajoute automatiquement).

**Remarque** vous pouvez ajouter un consommateur OLE DB à un projet MFC. Si vous le faites, l’Assistant Consommateur OLE DB ATL ajoute la prise en charge COM nécessaire à votre projet. Cela suppose que lorsque vous avez créé le projet MFC, vous avez sélectionné le **contrôles ActiveX** case (dans le **fonctionnalités avancées** page de l’Assistant Application MFC), qui est activé par défaut. Cette option garantit que l’application appelle **CoInitialize** et **CoUninitialize**. Si vous n’avez pas sélectionné **contrôles ActiveX** lorsque vous avez créé le projet MFC, vous devez appeler **CoInitialize** et **CoUninitialize** dans votre code principal.

### <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>Pour ajouter un consommateur OLE DB ATL à votre projet

1. Dans l’affichage de classes, cliquez sur le projet. Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une classe**.

2. Dans le dossier Visual C++, double-cliquez sur le **consommateur ATL OLE DB** icône ou sélectionnez-la et cliquez sur **Open**.

     L’Assistant Consommateur OLE DB ATL s’ouvre.

3. Définir les paramètres comme décrit dans [Assistant Consommateur OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).

4. Cliquez sur **Terminer** pour fermer l’Assistant. Le code de consommateur OLE DB nouvellement créé vont être inséré dans votre projet.

## <a name="see-also"></a>Voir aussi

[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)

