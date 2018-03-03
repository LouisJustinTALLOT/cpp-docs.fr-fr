---
title: "Ordre des opérations pour la génération d’Applications MFC | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], developing
ms.assetid: 6973c714-fe20-48c6-926b-de88356b3a3d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae1169b438a181e22696502352c19353421469b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sequence-of-operations-for-building-mfc-applications"></a>Ordre des opérations pour la génération d'applications MFC
Le tableau suivant explique la séquence générale que vous pouvez normalement suivre lorsque vous développez votre application MFC.  
  
### <a name="sequence-for-building-an-application-with-the-framework"></a>Séquence pour générer une application avec le framework  
  
|Tâche|Ce que vous devez faire|Ce que le framework fait|  
|----------|------------|------------------------|  
|Créer une application squelette.|Exécutez le [Assistant Application MFC](../mfc/reference/mfc-application-wizard.md). Spécifiez les options souhaitées dans les pages d'options. Les options permettent de transformer l'application en composant ou conteneur COM, ou les deux à la fois ; d'ajouter l'Automation et de la rendre compatible aux bases de données d'application.|L'Assistant Application MFC crée des fichiers pour une application squelette, notamment les fichiers sources de vos application, document, vue et fenêtres frame ; un fichier de ressources ; un fichier projet ; etc., tout en respectant vos spécifications.|  
|Consulter ce que le framework et l'Application MFC offrent sans ajouter une ligne de votre propre code.|Générez l'application squelette et exécutez-la dans Visual C++.|L’application squelette en cours d’exécution dérive des nombreuses standard **fichier**, **modifier**, **vue**, et **aide** des commandes de menu à partir du framework. Pour les applications MDI, vous obtenez également un menu Windows entièrement fonctionnel, et le framework gère la création, la disposition, ainsi que la destruction des fenêtres enfants MDI.|  
|Construire l'interface utilisateur de l'application.|Utiliser Visual C++ [éditeurs de ressources](../windows/resource-editors.md) pour modifier visuellement d’interface utilisateur de l’application :<br /><br /> -Créer des menus.<br />-Définissez des accélérateurs.<br />-Créer des boîtes de dialogue.<br />-Permet de créer et modifier des bitmaps, icônes et curseurs.<br />-Modifier la barre d’outils créée pour vous par l’Assistant Application MFC.<br />-Permet de créer et modifier d’autres ressources.<br /><br /> Vous pouvez également tester les boîtes de dialogue de l'éditeur de boîtes de dialogue.|Le fichier de ressources par défaut créé par l'Assistant Application MFC fournit plusieurs ressources dont vous avez besoin. Visual C++ vous permet de modifier les ressources existantes et d'ajouter de nouvelles ressources facilement et visuellement.|  
|Mapper les menus aux fonctions de gestionnaire.|Utilisez le **événements** situé dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour connecter des menus et des accélérateurs aux fonctions de gestionnaire dans votre code.|La fenêtre Propriétés insère des entrées de la table des messages et des modèles de fonctions vides dans les fichiers sources que vous spécifiez et gère plusieurs tâches de programmation manuelles.|  
|Écrire votre code gestionnaire.|Utilisez l'Affichage de classes pour accéder directement au code dans l'éditeur de code source. Exécutez le code pour vos fonctions gestionnaires. Pour plus d’informations sur l’affichage de la classe et sur les Assistants qui ajoutent du code à un projet, consultez [Ajout de fonctionnalités avec les Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md).|L'Affichage de classes ouvre l'éditeur, accède au modèle de fonction vide et place le curseur pour vous.|  
|Mapper les boutons de la barre d'outils aux commandes.|Mappez chaque bouton de la barre d'outils à un menu ou une commande accélérateur en affectant au bouton l'ID de commande approprié.|Le framework contrôle le dessin, l'activation, la désactivation, la vérification et d'autres aspects visuels des boutons de la barre d'outils.|  
|Tester vos fonctions de gestionnaire.|Régénérez le programme et utilisez les outils de débogage intégrés pour vérifier que les gestionnaires fonctionnent correctement.|Vous pouvez créer une procédure ou tracer le code pour voir comment les gestionnaires sont appelées. Si vous avez rempli le code du gestionnaire, les gestionnaires exécuteront les commandes. Le framework désactive automatiquement les éléments de menu et les boutons de la barre d'outils qui ne sont pas gérés.|  
|Ajouter [boîtes de dialogue](../mfc/dialog-boxes.md).|Concevez les ressources modèles de boîte de dialogue avec l'éditeur de boîtes de dialogue. Créez une classe de boîte de dialogue et du code qui gère la boîte de dialogue.|Le framework gère la boîte de dialogue et permet de récupérer les informations écrites par l'utilisateur.|  
|Initialiser, valider et récupérer les données de la boîte de dialogue.|Vous pouvez également définir comment les contrôles de la boîte de dialogue doivent être initialisés et validés. Utilisez Visual Studio pour ajouter des variables membres à la classe de la boîte de dialogue et les mapper aux contrôles de la boîte de dialogue. Spécifiez des règles de validation à appliquer à chaque contrôle au fur et à mesure que l'utilisateur entre des données. Spécifiez vos validations personnalisées si vous le souhaitez.|Le framework gère l’initialisation et la validation de la boîte de dialogue. Si l'utilisateur entre des informations valides, le framework affichera un message et permettra à l'utilisateur de rentrer à nouveau des données.|  
|Créer des classes supplémentaires.|Utilisez l'Affichage de classes pour créer un document, une vue et des classes de fenêtre frame supplémentaires parmi ceux générés automatiquement par l'Assistant Application MFC. Vous pouvez créer des classes de jeu d'enregistrements supplémentaires de base de données, des classes de boîte de dialogue, etc. (Avec l'Affichage de classes, vous pouvez créer des classes non dérivées des classes MFC.)|L'Affichage de classes ajoute ces classes à vos fichiers sources et vous aide à définir leurs connexions à toutes les commandes qu'ils gèrent.|  
|Ajouter des composants prêts à l'emploi à votre application.|Utilisez `New Item dialog box` pour ajouter un grand nombre d'éléments.|Ces éléments sont faciles à intégrer dans votre application et vous épargne une grande quantité de travail.|  
|Implémenter votre classe de document.|Implémentez la ou les classes de documents spécifiques à l'application. Ajoutez les variables membres pour conserver les structures de données. Ajoutez des fonctions membres pour fournir une interface aux données.|Le framework sait déjà interagir avec les fichiers de données de document. Il peut ouvrir et fermer les fichiers document, accéder en lecture et écriture aux données du document et gérer d'autres interfaces utilisateur. Vous pouvez vous concentrer sur la façon dont les données du document sont manipulées.|  
|Implémenter les commandes Ouvrir, Enregistrer et Enregistrer sous.|Code d'écriture de la fonction membre du document `Serialize`.|L’infrastructure affiche des boîtes de dialogue pour le **ouvrir**, **enregistrer**, et **enregistrer en tant que** des commandes sur le **fichier** menu. Il écrit et relit un document à l'aide du format de données spécifié dans votre fonction membre `Serialize`.|  
|Implémenter votre classe d'affichage.|Implémentez une ou plusieurs classes d'affichage qui correspondent à vos documents. Vous devez implémenter les fonctions membres de la vue que vous avez mappée à l'interface utilisateur avec l'Affichage de classes. Diverses [CView](../mfc/reference/cview-class.md)-classes dérivées sont disponibles, y compris [CListView](../mfc/reference/clistview-class.md) et [CTreeView](../mfc/reference/ctreeview-class.md).|Le framework gère la majeure partie de la relation entre un document et sa vue. Les fonctions membres d'affichage peuvent accéder au document de la vue pour afficher l'image sur l'écran ou la page imprimée et mettre à jour les structures de données du document en réponse aux commandes d'édition utilisateur.|  
|Améliorer l'impression par défaut.|Si vous devez assurer la prise en charge de l'impression multipage, remplacez les fonctions membres de la vue.|Le framework prend en charge la **impression**, **mise en Page**, et **Aperçu avant impression** des commandes sur le **fichier** menu. Vous devez lui indiquer comment diviser le document en plusieurs pages.|  
|Ajoutez le défilement.|Si vous avez besoin prendre en charge le défilement, dérivez votre classe d’affichage ou les classes de [CScrollView](../mfc/reference/cscrollview-class.md).|La vue ajoute automatiquement des barres de défilement lorsque la fenêtre d'affichage est trop petite.|  
|Créer des vues formulaires.|Si vous souhaitez fonder vos vues sur les ressources de modèle de boîte de dialogue, dérivez votre classe d’affichage ou les classes de [CFormView](../mfc/reference/cformview-class.md).|La vue utilise la ressource modèle de la boîte de dialogue pour afficher les contrôles. L'utilisateur peut tabuler de contrôle en contrôle au sein de la vue.|  
|Créer des formes de base de données.|Si vous souhaitez une application d’accès aux données de formulaire, dérivez votre classe de vue de [CRecordView](../mfc/reference/crecordview-class.md) (pour la programmation ODBC).|La vue fonctionne comme une vue de formulaire, mais ses contrôles sont connectés aux champs d’un [CRecordset](../mfc/reference/crecordset-class.md) objet représentant une table de base de données. MFC déplace des données entre les contrôles et l'ensemble d'enregistrements automatiquement.|  
|Créer un simple éditeur de texte.|Si vous souhaitez afficher un éditeur de texte simple, dérivez votre classe d’affichage ou les classes de [CEditView](../mfc/reference/ceditview-class.md) ou [CRichEditView](../mfc/reference/cricheditview-class.md).|La vue fournit des fonctions de modification, la prise en charge du Presse-papiers et les entrées/sorties de fichier. `CRichEditView` fournit le texte mis en forme avec des styles.|  
|Ajouter des fenêtres fractionnées.|Si vous souhaitez prendre en charge le fractionnement des fenêtres, ajoutez un [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) de l’objet à votre fenêtre frame SDI ou d’une fenêtre enfant MDI et raccorder dans la fenêtre [OnCreateClient](../mfc/reference/cframewnd-class.md#oncreateclient) fonction membre.|Le framework fournit des contrôles de zones de séparation en regard des barres de défilement et gère le fractionnement de la vue en plusieurs volets. Si l'utilisateur fractionne une fenêtre, le framework crée et joint les objets de vue au document.|  
|Générer, tester et déboguer votre application.|Utilisez les fonctionnalités de Visual C++ pour créer, tester et déboguer, votre application.|Visual C++ vous permet de paramétrer les options de compilation, de liaison et bien d'autres opérations. Il permet également de parcourir la structure du code source et de la classe.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ordre des opérations pour la création d’Applications OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [Ordre des opérations pour la création de contrôles ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [Ordre des opérations pour la création d’Applications de base de données](../mfc/sequence-of-operations-for-creating-database-applications.md)   
 [Génération à partir du Framework](../mfc/building-on-the-framework.md)

