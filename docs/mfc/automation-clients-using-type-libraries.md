---
description: 'En savoir plus sur les clients Automation : utilisation des bibliothèques de types'
title: 'Clients Automation : utilisation des bibliothèques de types'
ms.date: 11/04/2016
f1_keywords:
- MkTypLib
helpviewer_keywords:
- clients, Automation
- dispatch class [MFC]
- Automation clients, type libraries
- type libraries, Automation clients
- ODL (Object Description Language)
- ODL files
- classes [MFC], dispatch
- MkTypLib tool
- .odl files
ms.assetid: d405bc47-118d-4786-b371-920d035b2047
ms.openlocfilehash: c50425da1327f97fe410723df1e21136f1bd6f98
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274006"
---
# <a name="automation-clients-using-type-libraries"></a>Clients Automation : utilisation des bibliothèques de types

Les clients Automation doivent avoir des informations sur les propriétés et les méthodes des objets serveur si les clients doivent manipuler les objets des serveurs. Les propriétés ont des types de données ; les méthodes retournent souvent des valeurs et acceptent des paramètres. Le client nécessite des informations sur les types de données de tous ces types afin de lier statiquement au type d’objet serveur.

Ces informations de type peuvent être rendues de plusieurs façons. La méthode recommandée consiste à créer une bibliothèque de types.

Pour plus d’informations sur [mktyplib](/windows/win32/Midl/differences-between-midl-and-mktyplib), consultez le SDK Windows.

Visual C++ pouvez lire un fichier de bibliothèque de types et créer une classe de dispatch dérivée de [COleDispatchDriver](reference/coledispatchdriver-class.md). Un objet de cette classe possède des propriétés et des opérations qui dupliquent celles de l’objet serveur. Votre application appelle les propriétés et les opérations de cet objet, et les fonctionnalités héritées de `COleDispatchDriver` acheminent ces appels au système OLE, qui à son tour les achemine vers l’objet serveur.

Visual C++ gère automatiquement ce fichier de bibliothèque de types pour vous si vous avez choisi d’inclure l’automatisation lors de la création du projet. Dans le cadre de chaque Build, le fichier. tlb sera généré avec MkTypLib.

### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>Pour créer une classe de dispatch à partir d’un fichier de bibliothèque de types (. tlb)

1. Dans Affichage de classes ou Explorateur de solutions, cliquez avec le bouton droit sur le projet, cliquez sur **Ajouter** , puis sur **Ajouter une classe** dans le menu contextuel.

1. Dans la boîte de dialogue **Ajouter une classe** , sélectionnez le dossier **Visual C++/MFC** dans le volet gauche. Sélectionnez l’icône **classe MFC à partir d’une TypeLib** dans le volet droit, puis cliquez sur **ouvrir**.

1. Dans la boîte de dialogue **Assistant Ajout d’une classe à partir d’une TypeLib** , sélectionnez une bibliothèque de types dans la liste déroulante **bibliothèques de types disponibles** . La zone **interfaces** affiche les interfaces disponibles pour la bibliothèque de types sélectionnée.

    > [!NOTE]
    >  Vous pouvez sélectionner des interfaces à partir de plusieurs bibliothèques de types.

   Pour sélectionner des interfaces, double-cliquez dessus ou cliquez sur le bouton **Ajouter** . Dans ce cas, les noms des classes de dispatch s’affichent dans la zone **classes générées** . Vous pouvez modifier les noms de classe dans la `Class` zone.

   La zone **fichier** affiche le fichier dans lequel la classe doit être déclarée. (vous pouvez également modifier ce nom de fichier). Vous pouvez également utiliser le bouton Parcourir pour sélectionner d’autres fichiers, si vous préférez que les informations d’en-tête et d’implémentation soient écrites dans des fichiers existants ou dans un répertoire autre que le répertoire du projet.

    > [!NOTE]
    >  Toutes les classes de dispatch pour les interfaces sélectionnées seront placées dans le fichier spécifié ici. Si vous souhaitez que les interfaces soient déclarées dans des en-têtes distincts, vous devez exécuter cet Assistant pour chaque fichier d’en-tête que vous souhaitez créer.

    > [!NOTE]
    >  Certaines informations de bibliothèque de types peuvent être stockées dans des fichiers avec. DLL,. OCX ou. Extensions de fichier OLB.

1. Cliquez sur **Terminer**.

   L’Assistant écrira ensuite le code de vos classes de dispatch en utilisant les noms de classe et de fichier spécifiés.

## <a name="see-also"></a>Voir aussi

[Clients Automation](automation-clients.md)
