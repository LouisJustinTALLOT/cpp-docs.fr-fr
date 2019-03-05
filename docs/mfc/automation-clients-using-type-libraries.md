---
title: 'Clients Automation : À l’aide de bibliothèques de types'
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
ms.openlocfilehash: 32179f3913b52ca46f9ea7314b9957f4f4970713
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282940"
---
# <a name="automation-clients-using-type-libraries"></a>Clients Automation : À l’aide de bibliothèques de types

Clients Automation doivent disposer d’informations sur les propriétés et méthodes des objets serveur si les clients se pour manipuler des objets de serveurs. Propriétés des types de données ; souvent les méthodes retournent des valeurs et acceptent des paramètres. Le client requiert des informations sur les types de données de tous ces afin de lier statiquement au type d’objet serveur.

Ces informations de type peuvent être apportées connues de plusieurs façons. La méthode recommandée consiste à créer une bibliothèque de types.

Pour plus d’informations sur [MkTypLib](/windows/desktop/Midl/differences-between-midl-and-mktyplib), consultez le kit SDK Windows.

Visual C++ peut lire un fichier de bibliothèque de types et créer une classe de dispatch dérivée [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md). Un objet de cette classe possède des propriétés et opérations qui dupliquent celles de l’objet serveur. Votre application appelle les propriétés et les opérations de cet objet et les fonctionnalités héritées de `COleDispatchDriver` achemine ces appels au système OLE, qui à son tour les achemine vers l’objet serveur.

Visual C++ gère automatiquement ce fichier de bibliothèque de types pour vous si vous avez choisi d’inclure Automation lorsque le projet a été créé. Dans le cadre de chaque build, le fichier .tlb sera compilé avec MkTypLib.

### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>Pour créer une classe de distribution à partir d’un fichier de bibliothèque de types (.tlb)

1. Dans l’affichage de classes ou dans l’Explorateur de solutions, cliquez sur le projet, puis cliquez sur **ajouter** puis cliquez sur **ajouter une classe** dans le menu contextuel.

1. Dans le **ajouter une classe** boîte de dialogue, sélectionnez le **c++ de Visual c++ / MFC** dossier dans le volet gauche. Sélectionnez le **classe MFC à partir de la TypeLib** icône dans le volet droit, cliquez sur **Open**.

1. Dans le **Assistant Ajouter une classe à partir d’une Typelib** boîte de dialogue, sélectionnez une bibliothèque de types à partir de la **bibliothèques de types disponibles** liste déroulante. Le **Interfaces** zone affiche les interfaces disponibles pour la bibliothèque de types sélectionnée.

    > [!NOTE]
    >  Vous pouvez sélectionner des interfaces à partir de plus d’une bibliothèque de types.

   Pour sélectionner des interfaces, double-cliquez dessus ou cliquez sur le **ajouter** bouton. Lorsque vous procédez ainsi, les noms pour les classes de distribution s’affichent dans le **classes générées** boîte. Vous pouvez modifier les noms de classe dans le `Class` boîte.

   Le **fichier** boîte affiche le fichier dans lequel la classe sera déclarée. (vous pouvez modifier ce nom de fichier ainsi). Vous pouvez également utiliser le bouton Parcourir pour sélectionner d’autres fichiers, si vous préférez que les informations d’en-tête et d’implémentation écrites dans les fichiers existants ou dans un répertoire autre que le répertoire du projet.

    > [!NOTE]
    >  Toutes les classes de distribution pour les interfaces sélectionnés seront placés dans le fichier spécifié ici. Si vous souhaitez que les interfaces doivent être déclarées dans les en-têtes distincts, vous devez exécuter cet Assistant pour chaque fichier d’en-tête que vous souhaitez créer.

    > [!NOTE]
    >  Des informations de bibliothèque de types peuvent être stockées dans les fichiers avec. DLL. OCX, ou. Extensions de fichier OLB.

1. Cliquez sur **Terminer**.

   L’Assistant écrit le code pour vos classes de distribution à l’aide de la classe spécifiée et les noms de fichiers.

## <a name="see-also"></a>Voir aussi

[Clients Automation](../mfc/automation-clients.md)
