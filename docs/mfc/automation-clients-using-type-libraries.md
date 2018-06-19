---
title: 'Clients Automation : Utilisation des bibliothèques de types | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MkTypLib
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 67fa0f5d164ae325caff576fb41695fc8689fda0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342587"
---
# <a name="automation-clients-using-type-libraries"></a>Clients Automation : utilisation des bibliothèques de types
Clients Automation doivent disposer d’informations sur les propriétés et méthodes des objets serveur si les clients sont de manipuler des objets de serveurs. Les propriétés ont des types de données. souvent les méthodes retournent des valeurs et acceptent des paramètres. Le client a besoin d’informations sur les types de données de tous ces éléments afin de se lier statiquement au type d’objet serveur.  
  
 Ces informations de type peuvent avoir connaissance de plusieurs façons. La méthode recommandée est de créer une bibliothèque de types.  
  
 Pour plus d’informations sur [MkTypLib](http://msdn.microsoft.com/library/windows/desktop/aa366797), consultez le Kit de développement logiciel Windows.  
  
 Visual C++ peut lire un fichier de bibliothèque de types et créer une classe de dispatch dérivée [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md). Un objet de cette classe a des propriétés et des opérations qui dupliquent celles de l’objet serveur. Votre application appelle les opérations et les propriétés de cet objet et la fonctionnalité héritée `COleDispatchDriver` achemine ces appels vers le système OLE, qui à son tour de les acheminer vers l’objet serveur.  
  
 Visual C++ gère automatiquement ce fichier de bibliothèque de types pour vous si vous avez choisi d’inclure Automation lorsque le projet a été créé. Dans le cadre de chaque build, le fichier .tlb sera compilé avec MkTypLib.  
  
### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>Pour créer une classe de distribution à partir d’un fichier de bibliothèque de types (.tlb)  
  
1.  Dans l’affichage de classes ou dans l’Explorateur de solutions, cliquez sur le projet, puis cliquez sur **ajouter** puis cliquez sur **ajouter une classe** dans le menu contextuel.  
  
2.  Dans le **ajouter une classe** boîte de dialogue, sélectionnez le **c++ de Visual c++ / MFC** dossier dans le volet gauche. Sélectionnez le **classe MFC à partir de la TypeLib** icône dans le volet droit et cliquez sur **ouvrir**.  
  
3.  Dans le **Assistant Ajouter une classe à partir d’un Typelib** boîte de dialogue, sélectionnez une bibliothèque de types à partir de la **bibliothèques de types disponibles** liste déroulante. Le **Interfaces** affiche les interfaces disponibles pour la bibliothèque de types sélectionnée.  
  
    > [!NOTE]
    >  Vous pouvez sélectionner des interfaces à partir de plusieurs bibliothèques de type.  
  
     Pour sélectionner des interfaces, double-cliquez dessus ou cliquez sur le **ajouter** bouton. Lorsque vous procédez ainsi, les noms pour les classes de distribution s’affichent dans le **classes générées** boîte. Vous pouvez modifier les noms de classe dans le `Class` boîte.  
  
     Le **fichier** affiche le fichier dans lequel la classe sera déclarée. (vous pouvez modifier ce nom de fichier ainsi). Vous pouvez également utiliser le bouton Parcourir pour sélectionner d’autres fichiers, si vous préférez que les informations d’en-tête et d’implémentation écrites dans les fichiers existants ou dans un répertoire autre que le répertoire du projet.  
  
    > [!NOTE]
    >  Toutes les classes de distribution pour les interfaces sélectionnées seront placées dans le fichier spécifié ici. Si vous souhaitez que les interfaces d’être déclarés dans des en-têtes séparées, vous devez exécuter cet Assistant pour chaque fichier d’en-tête à créer.  
  
    > [!NOTE]
    >  Des informations de bibliothèque de type peuvent être stockées dans des fichiers avec. DLL. OCX, ou. Extensions de fichier OLB.  
  
4.  Cliquez sur **Terminer**.  
  
     L’Assistant écrit le code pour vos classes de répartition à l’aide de la classe spécifiée et les noms de fichiers.  
  
## <a name="see-also"></a>Voir aussi  
 [Clients Automation](../mfc/automation-clients.md)

